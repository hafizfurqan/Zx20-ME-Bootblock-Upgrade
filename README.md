# (3rd Gen) Zx20-ME-Bootblock-Upgrade
Successfully upgraded method found for upgrading bootblock of 20 series HP workstation without using any soldering but just manually shifting existing jumpers.

## Useful links

- https://github.com/bibikalka1/HP_Z420_Z620_Z820_BOOTBLOCK2013_BIOS_mod/tree/main

- https://github.com/SuperThunder/HP_Z420_Z620_Z820_BootBlock_Upgrade

### Shout out to their creator and experimentors.


# Step 1.

  1. Download MEBLAST1.zip from MEBLAST and extract it onto DOS bootable usb.
  2. Download and extract IMET8.zip from Backup-Bios folder to DOS bootable usb.
  3. Download and extract ME8 for your (machine).
  4. Poweroff (machine) and place password jumper to E14 and change FD0 jumper from its original position to unlock ME changes, and note change.
  5. Boot with created usb and create a backup of full bios. Can be done simply doing:
     
-     cd IMET8

-     backup 00

A bunch of files will get created, slicing and dicing the BIOS chip contents. You can follow up with [md5all 00] command, it will compute md5sums for all of these files.


-      dir *00.bin

-             65,536 BBLK00.BIN
-         10,944,512 BIOB00.BIN
-         11,468,800 BIOS00.BIN
-            458,752 BIOV00.BIN
-              4,096 FDOO00.BIN
-         16,777,216 FIRM00.BIN
-              8,192 GBEO00.BIN
-          5,287,936 MEOO00.BIN
-              8,192 PDRO00.BIN
  7. Update by going to folder and typing:

-     cd MEBX20


-     MEBLAST J6Y_0396.bin

or to folder you created and extracted files to and giving command.

  8. PowerOff (machine) and return FDO jumper to its original position.
  9. Check ME version in bios after turning on.
  10. Don't be alarmed by its unusual power on off after its first ME update, it does it only 1st time.
  11. If successful go on to next step for bootblock.

# Step 2

  1. Download Bootblock for your (machine) and place it where IME8.zip files were extracted.
  2. Download 2.07 version and latest version bios and place it in DOS usb.
  3. Place password jumper to E14 and change FD0 jumper from its original position to unlock ME changes, and note change.
  4. Boot from DOS usb.
  5. Again take a backup of entire bios.
  6. Initiate update of ME onto same version by typing :

-     MEBLAST J6Y_0396.bin

  in ME folder
  
  6. Don't reset your system. Go to version 2.07 bios and initiate update. This is important as we are making use of a loophole in old version of HP bios.
  7. Now restart (machine), and you will be greeted with **MANUFACTURING MODE**. This is exactly what we need.
  8. Boot again to DOS usb now this time go to backup folder and run this command, remember X is either 6 for Z620, or 8 for Z820 since you unpacked the correct file:

-     fpt.exe  -f B13VX20.bin -A 0xFF0000 -L 0x010000

This will replace Bootblock from 2011 with 2013 and both will be of 64k.
  9. Now we restore GBE and ME by isuing

-     fpt.exe -ME -f MEOO11.bin

-     fpt.exe -GBE -f GBEO11.bin

and updating to latest bios version.

After successful completion, poweroff (machine) and restore jumpers to their designated positions.

# Default Position Jumpers on Z420

https://github.com/hafizfurqan/Zx20-ME-Bootblock-Upgrade/blob/00401320eacb7955e1b4040fbd924bce16ca561e/images/IMG_20241114_130747.jpg


https://github.com/hafizfurqan/Zx20-ME-Bootblock-Upgrade/blob/00401320eacb7955e1b4040fbd924bce16ca561e/images/IMG_20241114_130755.jpg



https://github.com/hafizfurqan/Zx20-ME-Bootblock-Upgrade/blob/00401320eacb7955e1b4040fbd924bce16ca561e/images/IMG_20241114_131002.jpg

and now you have a working v2 supported fully upgraded Hp (3rd Gen) Zx20 Workstation.
