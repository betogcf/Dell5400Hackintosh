<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>Hackintosh for Dell Latitude 5400</title>
</head>

<body>
    <h1>Hackintosh for Dell Latitude 5400</h1>
    <p>Based on OpenCore version 0.9.5</p>
    <p><strong>WARNING:</strong> This repository uses macOS 13 Ventura</p>

    <h2>About my Mac</h2>
    <p><strong>Specification:</strong></p>
    <ul>
        <li>CPU Intel i5-8265U CPU @ 1.60GHz (Whiskey Lake),</li>
        <li>RAM 16GB DDR4 2400MHz,</li>
        <li>IGPU Intel UHD 620,</li>
        <li>SSD Gigabyte NVMe,</li>
        <li>ETH Intel I217-LM,</li>
        <li>WLAN+BT Intel 9560NGW,</li>
        <li>WWAN Not present,</li>
        <li>Audio Realtek ALC236,</li>
        <li>Ports USB-C (PD+DP-AltMode), 3xUSB3.0, HDMI, microSD, Multi-Jack, DC.</li>
    </ul>

    <h2>Issues:</h2>
    <ul>
        <li>HDMI coldplug (hotplug is OK)</li>
        <li>Hibernation</li>
        <li>Wifi not connected automatically after a reboot</li>
        <li>In rare cases the audio stops working or begins to sound with a static noise (This is a kext problem, because I realized there's no proper layout id for Dell 5400, so the 69 was a better choice for now)</li>
    </ul>

    <p><strong>Everything else is Working properly:</strong></p>
    <ul>
        <li>Bluetooth</li>
        <li>WLAN</li>
        <li>Intel WLAN</li>
        <li>Ethernet</li>
        <li>HDMI, DisplayPort Alt Mode (all with sound, but no volume adjustment)</li>
        <li>USB-C</li>
        <li>USB ports mapped, working after sleep</li>
        <li>TrackPad with gestures (visible as Magic Trackpad 2)</li>
        <li>Audio, with speaker and microphone support</li>
        <li>QE/CI</li>
        <li>Sleep</li>
        <li>MicroSD card reader</li>
        <li>TouchPad buttons</li>
        <li>TrackStick</li>
        <li>Multi-Jack (both cold- and hotplug)</li>
    </ul>

    <h2>Project info</h2>
    <p>I recently acquired a used Dell Latitude 5400, and at the first opportunity, I wanted to experiment with macOS. I used many of the existing projects on GitHub to initially see how it would behave and address stability issues.</p>

    <p>I encountered problems along the way:</p>
    <ul>
        <li>Much higher battery consumption compared to any Linux distribution or Windows.</li>
        <li>High processor temperatures.</li>
    </ul>

    <p><strong>Solutions:</strong></p>
    <ul>
        <li>I redid all the SSDTs and added some that were missing.</li>
        <li>I reselected all the kexts, removed some, and added some I deemed important.</li>
        <li>I recreated the CPUFriendDataProvider.kext based on the CPUFriendFriend script, using parameters from a MacbookPro (this can be adjusted as needed, just follow the script's guide and replace the kext).</li>
    </ul>

    <p><strong>Post-installation:</strong></p>
    <ul>
        <li>Generate your own SMBIOS using GenSMBIOS.</li>
        <li>Use Intel Power Gadget to check how your processor is performing. If you see high temperatures and high power consumption, I recommend redoing the DSDTs using the SSDTimer script in Windows and generating a new CPUFriendDataProvider.kext.</li>
        <li>Use IORegistryExplorer to verify that the power parameters are working.</li>
    </ul>

    <p><strong>Work to be done:</strong></p>
    <p>When I have some spare time, I'll try to create an audio layout for this model. Until then, the chosen layout serves us well.</p>

    <h2>Final words:</h2>
    <p>The laptop is working perfectly, with slightly better performance than it would have with Windows (synthetic tests corroborated this claim), and the battery performance similar to other operating systems.</p>
    <p>I've been using it as my primary laptop for a few weeks now, and there hasn't been any performance drop since. It's completely stable.</p>
    <p>I don't plan to upgrade to Sonoma at the moment because I don't see any benefit in doing so.</p>
</body>

</html>
