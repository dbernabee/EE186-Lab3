# ⭐EE186-Lab3⭐

###### Note: Under measuring-gravity-pt5, main3.c includes the code for the modified single I2C read transaction implementation

### Part 3: Getting Started 
##### What is the I2C addresses of the accelerometer and magnetometer? Represent the r/w bit using b. 

###### Accelerometer I2C address: 0011001b, WRITE: 0011001 b --> 0x32 when b = 0, READ: 0011001 b --> 0x33 when b = 1
###### Magnetometer I2C address: 0011110b, WRITE: 0011110 b --> 0x3C when b = 0, READ: 0011110 b --> 0x3D when b = 1

<img width="1086" height="510" alt="image" src="https://github.com/user-attachments/assets/2b5f524d-b79f-49a5-acdd-541c94028918" />

##### What is the sub-address (SUB), and how does it differ from the I2C address?
###### The I2C devices decides what device the bus responds to, the sub-address decides what register to read/write inside the device. The sub-address is a 2nd byte of data that is sent after the I2C acknowledges it. 

##### To enable acceleration data measurement, we need to configure the CTRL1 register by selecting the data rate and setting the enable bits. What is the CTRL1 register address and what value should be written to this register to accomplish this?
###### CTRL1 register address: 0x20. A value of 1 should be written to this register to accomplish this. 

##### To read acceleration data for the X, Y, and Z axes, what are the 8-bit sub-addresses that the transmitter would use to request the data?
###### X: OUT_X_L_A = 0x28 (low), OUT_X_H_X = 0x29 (high)
###### Y: OUT_Y_L_A = 0x2A (low)	OUT_Y_H_A = 0x2B (high)
###### Z: OUT_Z_L_A = 0x2C (low)	OUT_Z_H_A = 0x2D (high)

### Part 5: Measuring Gravity
##### Explain how the arguments to HAL I2C Mem Read() should be changed to accomplish this.
###### The MemAddress was changed to turn on auto-increment, single byte to 6 bytes, and the size from 1 to 6, so the sensor will then send all 6 bytes instead of just 1 byte at a time per transaction. 

