## Western Digital Drives from 512 to 4096 <br>
Download wdckit (either from Western Digital or find online) [HD Guru Download wdckit 2.19.1]: https://files.hddguru.com/index.php?action=downloadfile&filename=wdckit-2.19.1.zip&directory=Software/Western%20Digital& <br>
`wdckit s` <br>
`wdckit format -b x --fastformat diskX` <br>
https://support-en.wd.com/app/answers/detailweb/a_id/50708 <br>
<br>
run: `wdckit s`  # Will show output of drives <br>
pick the dirve you want to convert from 512 to 4096 <br>
`wdckit format -b 4096 --fastformat disk1` # Replace disk1 with your disk from the output on `wdckit s` <br>

## Hugo - Another option you can try <br>
Install Hugo <br>
Locate hugo.exe `C:\Program Files\WDC\HUGO\bin\hugo.exe` <br>
run: `hugo.exe s --device` <br>
<br>
next: `hugo format -g \\.\PhysicalDrive1 -b 4096 --fastformat -n max` <br>
FYI. a failed format doesn't necessarily mean the new sectors did not update to 4096 <br>

## WD Format Utility, yet another option to try <br>
`https://downloads.wdc.com/wdapp/WD_Quick_Formatter_2.0.0.65.zip` <br>
`https://support-en.wd.com/app/answers/detailweb/a_id/16241` <br>

## Seagate SeaChest Lite - 512 to 4096 <br>
Download SeaChest tools: SeaChest_Info_x64_windows.exe -s <br> 
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Info/v2.5.0/Windows/SeaChest_Info_x64_windows.exe <br>
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Lite/v1.9.2/Windows/SeaChest_Lite_x64_windows.exe <br>

run: <br>
`SeaChest_Info_x64_windows.exe -s`  # Will show output of drives <br>
`SeaChest_Lite_x64_windows.exe -d PD2 --setSectorSize 4096 --confirm this-will-erase-data` # Will try to convert from 512 to 4096 <br>

## Seagate openSeaChest_FormatUnit - 512 to 4096 <br>
`wget https://github.com/Seagate/openSeaChest/releases/download/v20.02.28/openSeaChest_FormatUnit` <br>
`chmod +x openSeaChest_FormatUnit` <br>
` ./openSeaChest_FormatUnit -s` # Fimd your drive <br>
`sudo ./openSeaChest_FormatUnit -d /dev/sdc --formatUnit 4096 --fastFormat 1 --confirm this-will-erase-data --disableImmediateResponse` <br>

## Other Commands tools: <br>
### hdparms
Linux tool allowing users to view and change the SATA/IDE device parameters. Stands for "Hard Disk Parameters".  <br>
`Examples (for first ATA/SATA drive):` <br>
`hdparm -I hda              Show disk identity, features, and current settings` <br>
`hdparm -I scd0             Same for first CD-ROM` <br>
`hdparm -M 128 hda          Set acoustic management to 'quiet'` <br>
`hdparm -M 254 hda          Set acoustic management to 'fast'` <br>
`hdparm -t hda              Perform disk read timings` <br>
`hdparm -T hda              Perform cached read timings` <br>
`hdparm -y hda              Set disk to standby mode` <br>
`hdparm --security-freeze hda    Freeze security settings` <br>
`Use 'hdb', 'hdc',... for second, third, ... ATA/SATA drive.` <br>
`See man page (hdparm.8.*) for further info.` <br>

### smartctl <br>
Linux tool used to control/monitor storage using (SMART) system. `smartctl [option] /dev/drive` <br>
See if your hard disk supports S.M.A.R.T.: <br>
`sudo smartctl -i /dev/sdc` <br>
The following data should be present in the output: <br>
`SMART support is: Available - device has SMART capability.` <br>
`SMART support is: Enabled` <br>
In case SMART support is available, but for some reason is not activated, try using `sudo smartctl -s on /dev/sdc` to assist with activation. <br>
Viewing the SMART Attributes <br>
To display the SMART attributes of the hard disk, perform the following command: <br>
`sudo smartctl -a /dev/sdc` <br>
 
### sg3_utils <br>
Package of utilities that send SCSI commands to the given DEVICE via a SCSI pass through interface provided by the host operating system. <br>
`https://sg.danny.cz/sg/sg3_utils.html` <br>
