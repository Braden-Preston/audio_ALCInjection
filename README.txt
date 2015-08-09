audio_ALCInjection
============
OS X Realtek ALC885 through ALC1150 Onboard Audio

This guide enables OS X Realtek ALC onboard audio on Intel based motherboards with OS X. The Realtek AppleHDA.kext only works with the codec the kext was edited for and replaces the native AppleHDA.kext.

Realtek ALC AppleHDA HDEF/Audio ID Injection Guides:
[Guide] Add HDEF-Clover.pdf
[Guide] Add or Edit HDEF-dsdt.pdf
[Guide] Add HDEF-kext.pdf
[Guide] Add HDEF-ssdt.pdf - DEPRECATED, replaced with:
[Guide]-OSX-hdmi_audio-hdef_audio-ssdt_v3, https://github.com/toleda/audio_hdmi_guides

Note: ML-Realtek ALC AppleHDA docs moved to folder above

IORegistryExplorer_v2.1

In OS X, The Realtek ALC AppleHDA.kext supports 7 Realtek audio codecs:
ALC885, ALC887, ALC888, ALC889, ALC892, ALC898, ALC1150/10.9 and newer

Three Realtek ALC AppleHDA.kext Audio_IDs, select one
Audio_ID: 1 supports 5 and 6 port ALC8xx onboard and/or HD5K/AMD/Nvidia HDMI audio  
Audio_ID: 2 supports 3 port ALC8xx onboard and/or HD5K/AMD/Nvidia HDMI audio
Audio_ID: 3 supports 3, 5 and 6 port ALC8xx onboard HD4K/HD3K HDMI audio
		with or without AMD/Nvidia HDMI audio
Audio_IDs: 1 and 2 support analog 5.1 surround sound, 3 does not
Audio_IDs: 1, 2 and 3 require HDMI audio dsdt edits for HDMI audio
Audio_ID: 3, not supported with ALC1150.

Note: The native AppleHDA.kext supports HDMI audio (dsdt edits required) even with an unsupported onboard audio codec using Audio ID: 1. 

Six Audio ID Injection techniques for the Realtek ALC AppleHDA.kext, select one
http://www.insanelymac.com/forum/topic/290796-realtek-alc-applehda-audio-injection/
1. No dsdt/audio enabler = Audio_ID, install either kext (use 1a or 1b, not both)
https://github.com/toleda/audio_kext_enabler
1a. Audio_ID = 1/HDAEnabler1.kext.zip 
1b. Audio_ID = 2/HDAEnabler2.kext.zip
1c. Audio_ID = 3/NA
2. dsdt/HDEF/layout-id = Audio_ID, see {Guide} Add or Edit dsdt/HDEF.pdf
https://github.com/toleda/audio_ALCInjection
2a. Audio_ID = 1/layout-id: 0x01, 0x00, 0x00, 0x00, 0x00
2b. Audio_ID = 2/layout-id: 0x02, 0x00, 0x00, 0x00, 0x00
2c. Audio_ID = 3, see dsdt/HD3K/HD4K HDMI audio
3. ssdt/HDEF/layout-id = Audio_ID, see {Guide} Add ssdt/HDEF.pdf
https://github.com/toleda/audio_ssdt_enabler
3a. Audio_ID = 1/audio_ssdt-hdae-1.zip
3b. Audio_ID = 2/audio_ssdt-hdae-2.zip
3c. Audio_ID = 3, see ssdt/HD3K/HD4K HDMI audio
4. Clover/Config.plist/Devices, see [Guide]-Add_HDEF-Clover.pdf
https://github.com/toleda/audio_ALCInjection
4a. Audio_ID = 1/Audio/Inject=1
4b. Audio_ID = 2/Audio/Inject=2
4c. Audio_ID = 3/NA
5. Chameleon/Chameleon Installer/Custom/Settings
5a. Audio_ID = 1/HDEF/LayoutID=1
5b. Audio_ID = 2/HDEF/LayoutID=2
5b. Audio_ID = 3/HDEF/LayoutID=3
6. Chimera 3.0 and newer/org.chameleon.Boot.plist/add
6a. Audio_ID = 1/HDAEnabler=Yes and HDEFLayoutID=01000000
6b. Audio_ID = 2/HDAEnabler=Yes and HDEFLayoutID=02000000
6c. Audio_ID = 3/HDAEnabler=Yes and HDEFLayoutID=03000000

Verification
1. Restart
2. IORegistryExplorer
2a. Search: HDEF
2b. Locate: layout-id (right pane, scroll down)
2c. Verify:
<01 00 00 00> or
<02 00 00 00>

Once the Realtek ALC AppleHDA audio is enabled, select one
1. See https://github.com/toleda/audio_RealtekALC
2. See https://github.com/toleda/audio_CloverALC

Problem Reporting
1. See https://github.com/toleda/audio_RealtekALC/blob/master/DETAILS.md

Credit
THe KiNG 
VHC888
.:ErmaC:.
bcc9
RevoGirl

toleda
https://github.com/toleda/audio_ALCInjection
README.txt