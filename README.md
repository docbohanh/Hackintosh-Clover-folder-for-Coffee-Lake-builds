# Kexts-and-plist
i5-8500 + B360 + ~~GTX 1060 6GB~~ RX580

Components used for this build: 

- Intel - Core i5-8500 3GHz 6-Core Processor
- Gigabyte - B360 AORUS Gaming 3 WIFI ATX LGA1151 Motherboard
- Corsair - Vengeance LPX 16GB (2 x 8GB) DDR4-3000 Memory 
- Crucial - MX500 500GB 2.5" Solid State Drive 
~~- EVGA - GeForce GTX 1060 6GB 6GB SSC GAMING Video Card ~~
- Sapphire - Radeon RX 580 8 GB PULSE

7 Nov 2018 Update:
- Jump ship from nVidia to AMD. The plist can stay the same if you're just lazy or if it doesn't give you any issue. The only thing need to change when switching from nVidia to AMD is to tick *off* 'System Parameters/NvidiaWeb', but in my case it boots up without any issue with this option ticked, even with the web driver installed. 
- macOS updated to Mojave. 
- Some small changes to the plist and BIOS, in order to let Mojave recognise UHD630. 
1. remove 'Devices/Fake ID/IntelGFX' - Mojave recognises UHD630, no need to fake it. 
2. change 'Graphics/ig-platform-id' to '3E920003' - The id of the UHD630 of i5-8500. Ideally WhateverGrann should take care of this without the need of assigning ig-platform-id, but in my case, possibly due to I'm using a B360 mobo, instead of a Z370 one, the ig-platform-id is necessary. Otherwise Mojave won't see the iGPU. From what I gathered, this isn't the case to Z370 mobos. 
3. Make sure to enable iGPU in BIOS. masOS uses iGPU for lots of stuff, for example view jpg files and video playback. Some issues with these might come up if the iGPU is set to auto or disable. 


26 Sep 2018 Update:
- Rename config_iGPU.plist to config.plist if you're using iGPU (for example the dGPU is in an RMA...)
- kexts and drivers were updated to latest
- The repo *should* be Majove ready, currently awaiting for nVidia's driver to test
- A custom USB SSDT was created in /ACPI/patched. It disables all unused USB ports on the mobo, plus the USB 3.0 capability of one of the front panel USB 3.0 ports. If you're not using the exact mobo, or you wish to use the port number patch instead, please don't include the 'ACPI' folder in your EFI, and enable the port limit patch, '10.13.6+ by PMHeart', in 'KernelAndKextPatches' in the plist.

For detailed description, please see my reddit post - https://www.reddit.com/r/hackintosh/comments/8px0ku/success_first_hackintosh_i58500b360gtx1060_6gb/

Or, my x230 repo has detailed steps on how to construct the whole thing - just need to be aware that the kexts and the plist are different. 
https://github.com/littlegtplr/Hackintosh-X230-macOS
