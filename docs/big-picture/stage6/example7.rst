.. include:: /include/include.rst
.. include:: /include/include-l2.rst
.. include:: /include/include-ex-bp.rst
|EX-BP-LOGO|

**************************************************************************************************
Example - Full automation with servo based turnouts/points and signals with a PCA9685 servo module
**************************************************************************************************

|SUITABLE| |tinkerer| |engineer| |support-button|

.. code-block:: cpp

  // myAutomation.h for simple ROUTEs with servo based turnouts/points and signals, and sensors directly connected to the Mega2560.

  ALIAS(TRN1, 100)
  ALIAS(TRN2, 101)
  ALIAS(SNS1_TRN1_APP, 24)
  ALIAS(SNS2_MAIN_TRN1_EX, 25)
  ALIAS(SNS3_STN, 26)
  ALIAS(SNS4_MAIN_TRN2_APP, 27)
  ALIAS(SNS5_STN_TRN2_APP, 28)
  ALIAS(SNS6_TRN2_EX, 29)
  ALIAS(SIG1_TRN1_APP, 102)
  ALIAS(SIG2_TRN2_GO, 103)
  ALIAS(SIG3_STN_EX, 104)
  ALIAS(BLK1_TRN1_APP, 1)
  ALIAS(BLK2_MAIN_HOLD, 2)
  ALIAS(BLK3_STN, 3)
  ALIAS(BLK4_TRN2_EX, 4)
  ALIAS(BLK1_EXIT, 1)
  ALIAS(BLK1_BLK2, 2)
  ALIAS(BLK1_BLK3, 3)
  ALIAS(BLK2_BLK4, 4)
  ALIAS(BLK3_BLK4, 5)
  ALIAS(BLK4_BLK1, 6)
  ALIAS(CHOOSE_BLK2, 60)
  
  SERVO_TURNOUT(TRN1, 100, 400, 100, Slow, "Station entry")
  SERVO_TURNOUT(TRN2, 101, 400, 100, Slow, "Station exit")
  SERVO_SIGNAL(SIG1_TRN1_APP, 400, 250, 100)
  SERVO_SIGNAL(SIG2_TRN2_GO, 400, 250, 100)
  SERVO_SIGNAL(SIG3_STN_EX, 400, 250, 100)

  // Start up with turnouts/points closed and signals red
  CLOSE(TRN1)
  CLOSE(TRN2)
  RED(SIG1_TRN1_APP)
  RED(SIG2_TRN2_GO)
  RED(SIG3_STN_EX)

  // Send three locos around our layout:
  RESERVE(BLK1_TRN1_APP)
  RESERVE(BLK2_MAIN_HOLD)
  RESERVE(BLK4_TRN2_EX)
  SENDLOCO(1, BLK1_EXIT)
  SENDLOCO(2, BLK2_BLK4)
  SENDLOCO(3, BLK4_BLK1)

  // We need DONE to tell EXRAIL not to automatically proceed beyond definitions above
  DONE

  // Sequence to exit block 1, and choose whether to go to the station or continue on main
  SEQUENCE(BLK1_EXIT)
    IF(CHOOSE_BLK2)
      UNLATCH(CHOOSE_BLK2)
      FOLLOW(BLK1_BLK2)
    ELSE
      LATCH(CHOOSE_BLK2)
      FOLLOW(BLK1_BLK3)
    ENDIF

  // Sequence to go from block 1 to block 2
  SEQUENCE(BLK1_BLK2)
    RESERVE(BLK2_MAIN_HOLD)
    IFTHROWN(TRN1)
      AMBER(SIG1_TRN1_APP)
      DELAY(2000)
      RED(SIG1_TRN1_APP)
      CLOSE(TRN1)
      DELAY(2000)
    ENDIF
    GREEN(SIG1_TRN1_APP)
    FWD(20)
    AFTER(SNS2_MAIN_TRN1_EX)
    FREE(BLK1_TRN1_APP)
    FOLLOW(BLK2_BLK4)

  // Sequence to go from block 1 to block 3
  SEQUENCE(BLK1_BLK3)
    RESERVE(BLK3_STN)
    IFCLOSED(TRN1)
      AMBER(SIG1_TRN1_APP)
      DELAY(2000)
      RED(SIG1_TRN1_APP)
      THROW(TRN1)
      DELAY(2000)
    ENDIF
    GREEN(SIG1_TRN1_APP)
    FWD(10)
    AT(SNS3_STN)
    STOP
    FREE(BLK1_TRN1_APP)
    DELAYRANDOM(10000, 15000)
    FWD(10)
    AT(SNS5_STN_TRN2_APP)
    FOLLOW(BLK3_BLK4)

  // Sequence to go from block 2 to block 4
  SEQUENCE(BLK2_BLK4)
    RESERVE(BLK4_TRN2_EX)
    IFTHROWN(TRN2)
      AMBER(SIG2_TRN2_GO)
      AMBER(SIG3_STN_EX)
      DELAY(2000)
      RED(SIG2_TRN2_GO)
      RED(SIG3_STN_EX)
      CLOSE(TRN2)
      DELAY(2000)
    ENDIF
    GREEN(SIG2_TRN2_GO)
    FWD(20)
    AFTER(SNS4_MAIN_TRN2_APP)
    FREE(BLK2_MAIN_HOLD)
    FOLLOW(BLK4_BLK1)
  
  // Sequence to go from block 3 to block 4
  SEQUENCE(BLK3_BLK4)
    RESERVE(BLK4_TRN2_EX)
    IFCLOSED(TRN2)
      AMBER(SIG2_TRN2_GO)
      AMBER(SIG3_STN_EX)
      DELAY(2000)
      RED(SIG2_TRN2_GO)
      RED(SIG3_STN_EX)
      THROW(TRN2)
      DELAY(2000)
    ENDIF
    GREEN(SIG3_STN_EX)
    FWD(20)
    AFTER(SNS5_STN_TRN2_APP)
    FREE(BLK3_STN)
    FOLLOW(BLK4_BLK1)
  
  // Sequence to move from block 4 back to block 1
  SEQUENCE(BLK4_BLK1)
    RESERVE(BLK1_TRN1_APP)
    FWD(30)
    AFTER(SNS1_TRN1_APP)
    FREE(BLK4_TRN2_EX)
    FOLLOW(BLK1_EXIT)
