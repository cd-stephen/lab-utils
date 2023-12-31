***** Important Notice *****

On X10 UP Grantley platforms, Supermicro introduces a jumper-free solution that places ME into the manufacturing mode. The user doesn't have to open the chassis to adjust the ME-related jumper on the motherboard any more.  The ME manufacturing mode is required upon  
updating all software-strap settings in Flash Descriptor Table (FDT) inside ME region.

When user does not use Supermicro's Grantley BIOS flash package, the BIOS will ask AMI AFU tool to terminate the process with below message:

 "- Error: Please use BIOS flash package from www.supermicro.com for BIOS update."

The following instruction describes the BIOS upgrade process of the X10 BIOS flash package.  Please follow the instruction carefully to avoid any need of RMA repair or replacement.

================================================
Standard BIOS Update Procedure
================================================
1. Save this BIOS update package to your computer.

2. extract the files from the BIOS package to a DOS bootable device (such as a bootable USB stick, or CD).

3. Boot to a DOS prompt and type FLASH.BAT BIOSname.### to start the BIOS update.

4. The FLASH.BAT script will compare Flash Descriptor Table (FDT) code in the new BIOS with the existing one in the motherboard:

   a. If a different FDT is found, a new file, AUTOEXEC.BAT, will be created, and the system reboot will start in 10 seconds if no key is pressed.  Press "Y" to go into system reboot right away.  Continue BIOS upgrade with FDT programmed in next booting and schedules to reset system with 10-sec timeout message prompted. User can press <Y> for immediate reboot.  After the reboot, the BIOS update will be continued.

   b. If the FDT is the same, the BIOS update will be started right away.  No reboot will be needed.

5. Do not interrupt the process until the flashing is complete.

6. After the message indicating BIOS update has completed, do the A/C power cycle.

7. Go to the BIOS configuration, and restore the BIOS setting.
	
================================================
Super.ROM (see user's manual for details)
================================================
Recovery Bios from a USB Device/Drive

If the BIOS file is corrupted and the system is not able to boot up, this feature will
allow you to recover the BIOS image using a USB-attached device. A USB Flash
Drive or a USB CD/DVD ROM/RW drive may be used for this purpose. Please note
that a USB Hard Disk drive is NOT supported at this time. Follow the procedures
below recover the BIOS.


1. Using a different system, copy the standard BIOS binary image file

   into a bootable USB flash device or a writable CD/DVD disc's Root "\" Directory, Rename the BIOS binary file as "Super.ROM"

2. While the system is turned off, Insert the USB device that contains the new BIOS binary image (¡§super.rom¡¨).

3. Right after the system is turned on, press and hold <Ctrl> and <Home> keys together until the System Enter Recovery Mode which is showing on the button of the screen

   This will take a few seconds or up to one minute.

4. The system will enter the BIOS Recovery menu.  Select "Proceed with flash update" to start the BIOS recovery process. DO NOT INTERRUPT THIS PROCESS UNTIL IT’S FINISHED!

5. After the Boot Sector Recovery Process is complete, press any key to reboot the system.

6. Boot into USB drive again.  When the DOS prompt appears, please type FLASH.BAT BIOSname#.### to start BIOS update, just like in standard BIOS update procedure.

7. Do not interrupt the process until the flashing is complete.

8. After you see the message of BIOS has completed the update, do the A/C power cycle & restore the BIOS setting.


NOtes:
   
* Restore the BIOS setting: press Delete to go to the BIOS setup screen, press F3 to load the default and press F4 to save and exit.

* If the system can not boot up due to the BIOS file is corrupted, please change JBR1 jumper setting to pin 2-3 for BIOS recovery.
This is the last step you should do before contact RMA.

* If the BIOS flash failed, you can contact our RMA dept. to have the bios chip reprogrammed. This will require shipping the board to our RMA dept. 
The RMA dept's email address is rma@supermicro.com


********* BIOS Naming Convention **********

BIOS name     : PPPPPSSY.MDD
PPPPP         : 5-Bytes for project name
SS            : 2-Bytes supplement for PPPPP
Y             : Year,  4 -> 2014, 5-> 2015, 6->2016
MDD           : Month / Date, For months, A -> Oct., B -> Nov., C -> Dec.

E.g.  BIOS with the build date: 5/18/2015:
        X10SRH-CF -> X10SRH5.518
        X10DRW-F -> X10SRW5.518