# Important Personal Experience
When using Arduino Mega 2560 to check this library, if the pin SAO of the sensor is connected to the GND pin of the Mega 2560, then the value of the i2c address should be set to *0x68*, rather than *0x69* as follows on line 23 of the file stepCounterNormal.ino:
```C
const int8_t i2c_addr = 0x68;
```
Otherwise, it will throw "i2c initialize failed".

Update date: 2020-11-10

# BMI160-Arduino
The BMI160 is a highly integrated, low power inertial measurement unit (IMU) that provides precise acceleration and angular rate (gyroscopic) measurement.
The BMI160 contains 16 bit digtial,triaxial accelerometer and 16 bit digital, triaxial gyroscope.
This example is for BMI160 sensor and it oprated via Arduino I2C.

## DFRobot_BMI160 Library for Arduino
---------------------------------------------------------

Provide an Arduino library to control the bmi160 to get acell, gyro and step counter, via I2C communication.

## Table of Contents

- [Important Personal Experience](#important-personal-experience)
- [BMI160-Arduino](#bmi160-arduino)
  - [## DFRobot_BMI160 Library for Arduino](#h2-iddfrobot_bmi160-library-for-arduino-181dfrobot_bmi160-library-for-arduinoh2)
  - [Table of Contents](#table-of-contents)
  - [Summary](#summary)
  - [Installation](#installation)
  - [Methods](#methods)
  - [Compatibility](#compatibility)
  - [History](#history)
  - [Credits](#credits)

## Summary

Provide an Arduino library to control the bmi160 to get acell, gyro and step counter, via I2C communication.

## Installation

To use this library, first download the library file, paste it into the \Arduino\libraries directory, then open the examples folder and run the demo in the folder.

## Methods

```C++	

#include <DFRobot_BMI160.h>

/*
 * @brief reset bmi160 hardware
 * @return BMI160_OK(0) means success
 */
int8_t softReset();

/*
 * @brief set the i2c addr and init the i2c.
 * @param i2c_addr  bmi160 i2c addr
 *     0x68: connect SDIO pin of the BMI160 to GND which means the default I2C address
 *     0x69: set I2C address by parameter
 * @return BMI160_OK(0) means success
 */
int8_t I2cInit(int8_t i2c_addr);


/*
 * @brief select mode and save returned data to parameter data.
 * @param type  three type
 *     onlyAccel: only get the accel data
 *     onlyGyro: only get the gyro data
 *     bothAccelGyro: get boath accel and gyro data
 * @param *data  save returned data to parameter data
 * @return BMI160_OK(0) means succse
 */
int8_t getSensorData(uint8_t type,int16_t* data);

/*
 * @brief get the accel data 
 * @param pointer to store the accel data
 * @return BMI160_OK(0) means succse
 */
int8_t getAccelData(int16_t* data);
  
/*
 * @brief get the gyro data 
 * @param pointer to store the gyro data
 * @return BMI160_OK(0) means succse
 */
int8_t getGyroData(int16_t* data);
    
/*
 * @brief get the accel and gyro data 
 * @param pointer to store the accel and gyro data
 * @return BMI160_OK(0) means succse
 */
int8_t getAccelGyroData(int16_t* data);

/*
 * @brief set interrupt number and choosing step detector interrupt
 * @param choose int1 or int2
 * @return BMI160_OK(0) means succse
 */
int8_t setInt(int intNum);

/*
 * @brief enable the step counter
 * @return BMI160_OK(0) means succse
 */
int8_t setStepCounter();

/*
 * @brief set the step power model
 * @param type of model 
 * @return BMI160_OK(0) measn succse
 */
int8_t setStepPowerMode(uint8_t model);

/*
 * @brief read the step counter from bmi160
 * @param pointer to store the step 
 * @return BMI160_OK(0) measn succse
 */
int8_t readStepCounter(uint16_t *stepVal);

```

## Compatibility

MCU                | Work Well    | Work Wrong   | Untested    | Remarks
------------------ | :----------: | :----------: | :---------: | -----
FireBeetle-ESP32   |      √       |              |             | 
FireBeetle-ESP8266 |      √       |              |             | 
Arduino uno        |      √       |              |             | 


## History

- data 2017-12-01
- version V0.1


## Credits

Written by DFRobot_haoJ(hao.jiang@dfrobot.com), 2017. (Welcome to our [website](https://www.dfrobot.com/))





