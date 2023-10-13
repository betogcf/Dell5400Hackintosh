# Hackintosh for Dell Latitude 5400

Based on OpenCore version 0.9.5

**WARNING:** This repository uses macOS 13 Ventura; Generate your own SMBIOS using GenSMBIOS; Dortania's Install Guide teaches both the basics and advanced techniques, so make use of it.

## About my Mac



**Specification:**
- CPU: Intel i5-8265U CPU @ 1.60GHz (Whiskey Lake)
- RAM: 16GB DDR4 2400MHz
- IGPU: Intel UHD 620
- SSD: Gigabyte NVMe
- ETH: Intel I217-LM
- WLAN+BT: Intel 9560NGW
- WWAN: Not present
- Audio: Realtek ALC236
- Ports: USB-C (PD+DP-AltMode), 3xUSB3.0, HDMI, microSD, Multi-Jack, DC.

## Issues
- HDMI coldplug (hotplug is OK)
- Hibernation
- Wifi not connected automatically after a reboot
- In rare cases, the audio stops working or begins to sound with a static noise (This is a kext problem because I realized there's no proper layout id for Dell 5400, so the 69 was a better choice for now)

## Working
- Bluetooth
- WLAN
- Intel WLAN
- Ethernet
- HDMI, DisplayPort Alt Mode (all with sound, but no volume adjustment)
- USB-C
- USB ports mapped, working after sleep
- TrackPad with gestures (visible as Magic Trackpad 2)
- Audio, with speaker and microphone support
- QE/CI
- Sleep
- MicroSD card reader
- TouchPad buttons
- TrackStick
- Multi-Jack (both cold- and hotplug)

## Project Info
I recently acquired a used Dell Latitude 5400, and at the first opportunity, I wanted to experiment with macOS. I used many of the existing projects on GitHub to initially see how it would behave and address stability issues.

I encountered problems along the way:
- Much higher battery consumption compared to any Linux distribution or Windows.
- High processor temperatures.

I realized that these issues were related to differences in processors between the tested projects. Although they were on the same platform, an i7 would obviously use different power parameters than an i5. I also noticed that most of the projects were using merged SSDTs files or had no customization for the specific model.

**Solutions:**
- I redid all the SSDTs and added some that were missing.
- I reselected all the kexts, removed some, and added some I deemed important.
- I recreated the CPUFriendDataProvider.kext based on the CPUFriendFriend script, using parameters from a MacbookPro (this can be adjusted as needed, just follow the script's guide and replace the kext).

**Post-installation:**
- Use Intel Power Gadget to check how your processor is performing. If you see high temperatures and high power consumption, I recommend redoing the DSDTs using the SSDTimer script in Windows and generating a new CPUFriendDataProvider.kext.
- Use IORegistryExplorer to verify that the power parameters are working.

**Work to be done:**
When I have some spare time, I'll try to create an audio layout for this model. Until then, the chosen layout serves us well.

## Final Words
The laptop is working perfectly, with slightly better performance than it would have with Windows (synthetic tests corroborated this claim), and the battery performance is similar to other operating systems. 
I've been using it as my primary laptop for a few weeks now, and there hasn't been any performance drop since. 
It's completely stable. I don't plan to upgrade to Sonoma at the moment because I don't see any benefit in doing so.
