# lab3-ee186
Section 3:

What are the I2C addresses of the accelerometer and magnetometer? Represent the r/w bit using b 

Accelerometer - 0011001b 
Magnetometer - 0011110b

What is the sub-address (SUB), and how does it differ from the I2C address?
The SUB is how the master communicates which information it wants. An I2C address is how the master communicates who it wants to talk to.

To enable acceleration data measurement, we need to configure the CTRL1 register by selecting the data rate and setting the enable bits. What is the CTRL1 register address and what value should be written to this register to accomplish this? 

CTRL1 (CTRL_REG1_A) register address: 0x20
Value written: 0x57

The upper 4 bits (ODR[3:0] = 0101) select a 100 Hz data rate. LPen = 0 selects normal (not low-power) mode. The lower 3 bits (Zen, Yen, Xen = 111) enable all three axes. Together: 0101 0111 = 0x57.

To read acceleration data for the X, Y, and Z axes, what are the 8-bit sub-addresses that the transmitter would use to request the data?

X-low: 00101000 (0x28) 
X-high: 00101001 (0x29)

Y-low: 00101010 (0x2A) 
Y-high: 00101011 (0x2B)

Z-low: 00101100 (0x2C) 
Z-high: 00101101 (0x2D)


Section 5.
ii) The register address used to find the sensor's values goes from 0x28 to 0xA8. This is because the top bit of the sub address turns on auto increment, so 0010 1000 becomes 1010 1000. The number of bytes goes from 1 to 6 in order to cover all output registers, then the variable becomes an array of 6 so you have somewhere to store these values.


