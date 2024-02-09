#### Format Western Digital Drives from 512 to 4096
Download wdckit (either from Western Digital or find online)
`wdckit s` <br>
`wdckit format -b x --fastformat diskX` <br>
https://support-en.wd.com/app/answers/detailweb/a_id/50708

run:
`wdckit s`  # Will show output of drives

pick the dirve you want to convert from 512 to 4096
`wdckit format -b 4096 --fastformat disk1` # Replace disk1 with your disk from the output on `wdckit s`


### Seagate 512 to 4096
Download SeaChest tools: SeaChest_Info_x64_windows.exe -s
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Info/v2.5.0/Windows/SeaChest_Info_x64_windows.exe
https://github.com/Seagate/ToolBin/blob/master/SeaChest/Lite/v1.9.2/Windows/SeaChest_Lite_x64_windows.exe

run:
`SeaChest_Info_x64_windows.exe -s`  # Will show output of drives

`SeaChest_Lite_x64_windows.exe -d PD2 --setSectorSize 4096 --confirm this-will-erase-data` # Will try to convert from 512 to 4096
