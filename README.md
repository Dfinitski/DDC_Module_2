# The tyny 65x27mm DDC/DUC Module.
## Based on Altera Cyclone 10 FPGA, 14/12 bit ADC AD9649(29) and DAC AD9607(06).

![](https://github.com/Dfinitski/DDC_Module_2/blob/main/module_2_1.jpg)

![](https://github.com/Dfinitski/DDC_Module_2/blob/main/module_2_2.jpg)

### Free viewer for lay6 PCB format files [here...](https://www.electronic-software-shop.com/lng/en/support/free-viewer-software/) 

### Pinout of the connector:
    1 - I2C SDA
    2 - I2C SCL
    3 - I2S DOUT
    4 - I2S DIN
    5 - MCLK 16MHz output
    6 - I2S LRCLK
    7 - n_RES output, high level when MCLK is ready to use 
    8 - I2S BCLK
    9 - CW input for TX CW forming control, high level is active
    10 - OF output, ADC overflow
    11 - 5V power supply
    12 - GND

### The power supply voltage is 5 Volt, 120 mA.

### Input/output data format is a classic I2S bus, slave mode, 32 bits per sample.

### Control bus is I2C, slave mode, the exchange protocol includes 11 bytes:
     Start -> Address -> RXF3(MSB)_byte -> RXF2_byte -> RXF1_byte -> RXF0(LSB)_byte -> 
    -> TXF3(MSB)_byte -> TXF2_byte -> TXF1_byte -> TXF0(LSB)_byte -> SRATE -> TXLEVEL-> Stop

    Where:
    Address byte is always 0xD2,
    RXF - 32 bit or 4 bytes of receiver frequency
    TXF - 32 bit or 4 bytes of transmitter frequency
    SRATE - sample rate code, 1 Byte, 0 - 48 kHz, 1 - 96 kHz, 2 - 192 kHz, 3 - 240 kHz, 4 - 384 kHz, 
                                      5 - 480 kHz, 6 - 640 kHz, 7 - 960 kHz
    TXLEVEL - 1 byte, 0 - 255 hardware controlled transmitting level
 
 
