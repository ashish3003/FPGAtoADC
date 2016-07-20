# FPGAtoADC
Altera DE2 FPGA board based NIOS II SPI connection to ADC MCP3208.

SPI Communication using 8-bit segments (Mode 0,0: SCLK idles low).

To use NIOS II to implement connection to ADC MCP3208 on
Altera DE2 Board:

1. The code is generic in nature.
2. Vary spiChannel to 0-7 to scan all the channels.
3. Sampling rates can be changed from the attached SOPC file.
4. All transfers are 8-bit wide.
5. As per datasheet of MCP3208, the SPI Master must send 3 byte of control words one byte at a time followed by one byte Read operation.
6. Finally, 3 bytes received from ADC are adjusted to retrieve 12-LSBs. 

Find more at:
http://ww1.microchip.com/downloads/en/DeviceDoc/21298c.pdf
Refer to fig. 6.1, page 18.

Pin assignment:

| Function  |	  FPGA	    |	MCP3208   |
| --------- | ----------- | --------- |
| MISO      |  GPIO_0[0]  |   DOUT    |
| MOSI      |  GPIO_0[1]  |   DIN     |
| SCLK      |  GPIO_0[2]  |   CLK     |
| SS_n      |  GPIO_0[3]  |   CS'     |

+3.3V

GND

