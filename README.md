universal-panel-adapter
=======================

Using a cheap Arduino mini pro, uno or nano this sketch allows you to
interface a panel like Viki or a Parallel LCD with encoder via SPI.

Specifically used for running I2C and parallel panels on a Smoothie compatible board.

Prebuild bianries ready for upload to arduino are:-

* viki_panel_adapter.hex for viki/panelolu2
* parallel_panel_adapter.hex for parallel LCD
* RRD_panel_adapter.hex for Reprap Discount Smart Controller
* ATOM2_panel_adapter.hex for ATOM2.x Reprap Discount Smart Controller

Default Wiring is as follows:-

Viki to Nano
---------------

	SDA  -> A4
	SCL  -> A5
	ENCA -> D2
	ENCB -> D3
	Gnd  -> Gnd
	+5v  -> +5v

Parallel LCD pin to Nano
--------------------

	 4 RS -> D9
	 5 RW -> A0
	 6 EN -> A1
	11 D4 -> D5
	12 D5 -> D6
	13 D6 -> D7
	14 D7 -> D8

	 1 gnd
	 2 +5v
	 3 contrast
	 15,16 backlight power (on some)
	 
 	Encoder is connected to Nano
	ENCA  -> D2
	ENCB  -> D3
	Click -> A2

Reprap Discount Smart Controller almost the same as Parallel LCD pin to Nano
--------------------

	 4 RS(EXP1.4) -> D9
	 
	 6 EN(EXP1.3) -> A1
	11 D4(EXP1.5) -> D5
	12 D5(EXP1.6) -> D6
	13 D6(EXP1.7) -> D7
	14 D7(EXP1.8) -> D8

	 1(EXP1.9) gnd
	 2(EXP1.10) +5v
	 
 	Encoder is connected to Nano
	ENCA(EXP2.5)  -> D2
	ENCB(EXP2.3)  -> D3
	Click(EXP1.2) -> A2
	BUZZ(EXP1.1)  -> A3
	
	For ATOM2.x LCD
	7  D0(LCD3.1) -> D0
	8  D1(LCD3.2) -> D1
	9  D2(LCD3.3) -> A4
	10 D3(LCD3.4) -> A5

Smoothie to Nano
----------------
	MOSI -> D11 : 0.18
	MISO -> D12 : 0.17
	SCK  -> D13 : 0.15
	SS   -> D10 : 0.16
	BUSY -> D4  : 2.11 (or 1.30 on Azteeg X5) (And set panel.busy_pin in config to that pin)

Smoothie config
---------------

add this to your config file on smoothie

	panel.enable                                true              # enable panel
	panel.lcd                                   universal_adapter #
	panel.spi_channel                           0                 # spi channel to use (0- MISO 0.17, MOSI 0.18, SCK 0.15, SS 0.16)
	panel.spi_cs_pin                            0.16              # spi chip select
	panel.busy_pin                              2.11              # busy pin NOTE 1.30 on Azteeg X5


Requirements
------------
For compiling the following Arduino libraries are needed

* Encoder library from http://www.pjrc.com/teensy/td_libs_Encoder.html

For Viki and I2C based panels
* LiquidTWI2 from https://github.com/lincomatic/LiquidTWI2

For Parallel panels or ReprapDiscountSmart Controller panels
* LiquidCrystalFast from https://www.pjrc.com/teensy/td_libs_LiquidCrystal.html




