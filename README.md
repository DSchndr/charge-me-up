# charge-me-up
Custom Firmware / Patches for clone iMax B6 charger (CMS32L051)

# SWD Access
In order to get SWD access, you have to dismantle the device.  
To do that remove the 4 extremely short screws from one side, then pop the button extensions out with a flat head screwdriver.  
Once you have the device in front of you, you will see a obvious unpopulated pinheader on top which has a box drawn around it.  
The pinout is:
`5v gnd clk dio gnd p51 p50 `

Connect an STLink 1:1 to it. Use 3.3V instead of 5V and DO NOT PLUG IN POWER

# Dumping the flash
Get openocd and read the device memory with  
`.\openocd.exe -f OpenOCD-20231002-0.12.0\share\openocd\scripts\interface\stlink-dap.cfg -f openocd\dump_flash.cfg`  
The main flash contents and dataflash will be in their files respectively.  
Check those files before continuing.

# Erasing the Flash
ACHTUNG, be sure as heck that you have a working dump.
`.\openocd.exe -f OpenOCD-20231002-0.12.0\share\openocd\scripts\interface\stlink-dap.cfg -f openocd\dump_flash.cfg`  

# Writing the Flash
Make sure you erased the flash, as to why: find it out and learn something :)  
Writes `flash_main.bin`  
`.\openocd.exe -f OpenOCD-20231002-0.12.0\share\openocd\scripts\interface\stlink-dap.cfg -f openocd\write_flash.cfg`  

# Dude, Where's my ~Car?~ Calibration Menu?
There is no calibration menu in this software.
