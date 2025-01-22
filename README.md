# RFID-RC522-with-STM32
How to use RC522 RFID with STM32 | 
These are the library and code you can use to read RFID cards with the RC522 RFID module using an STM32 Microcontroller. The video tutorial is available on YouTube: https://youtu.be/Ay3ysGDrxbo

    /* Private includes ----------------------------------------------------------*/
    /* USER CODE BEGIN Includes */
    #include "RC522.h"
    #include "string.h"
    /* USER CODE END Includes */
    
    
    
    /* USER CODE BEGIN PV */
    uint8_t status;
    uint8_t str[16]; 
    uint8_t sNum[5];
    char *msg1 = "Reading From Card\r\n";
    char *msg2 = "Reading From Tag\r\n";
    char *msg3 = "Place card to read\r\n";
    /* USER CODE END PV */
    
    
    /* USER CODE BEGIN 2 */
    MFRC522_Init();
    /* USER CODE END 2 */
    
    
    
    
    /* USER CODE BEGIN 3 */
    	status = MFRC522_Request(PICC_REQIDL, str);
    	status = MFRC522_Anticoll(str);
    	memcpy(sNum, str, 5);
    	HAL_Delay(200);
    	if((str[0]==131) && (str[1]==32) && (str[2]==86) && (str[3]==17) && (str[4]==244) )
    	 {
    		HAL_UART_Transmit(&huart2, (uint8_t*)msg1, strlen(msg1), HAL_MAX_DELAY);
    	   }
    
    	if((str[0]==19) && (str[1]==32) && (str[2]==165) && (str[3]==11) && (str[4]==42) )
    		 {
    			HAL_UART_Transmit(&huart2, (uint8_t*)msg2, strlen(msg2), HAL_MAX_DELAY);
    		   }
      }
      /* USER CODE END 3 */
