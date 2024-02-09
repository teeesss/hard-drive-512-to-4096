## Western Digital Drives from 512 to 4096 <br>
Download wdckit (either from Western Digital or find online) <br>
`wdckit s` <br>
`wdckit format -b x --fastformat diskX` <br>
https://support-en.wd.com/app/answers/detailweb/a_id/50708 <br>
<br>
run:
`wdckit s`  # Will show output of drives <br>
<br>
pick the dirve you want to convert from 512 to 4096 <br>
`wdckit format -b 4096 --fastformat disk1` # Replace disk1 with your disk from the output on `wdckit s` <br>

## Seagate 512 to 4096 <br>
Download SeaChest tools: SeaChest_Info_x64_windows.exe -s <br> 
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Info/v2.5.0/Windows/SeaChest_Info_x64_windows.exe <br>
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Lite/v1.9.2/Windows/SeaChest_Lite_x64_windows.exe <br>

run: <br>
`SeaChest_Info_x64_windows.exe -s`  # Will show output of drives <br>
<br>
`SeaChest_Lite_x64_windows.exe -d PD2 --setSectorSize 4096 --confirm this-will-erase-data` # Will try to convert from 512 to 4096 <br>
