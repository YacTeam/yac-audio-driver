# yac-audio-device
![Platform:macOS](https://img.shields.io/badge/platform-macOS-lightgrey)
![GitHub](https://img.shields.io/github/v/release/ExistentialAudio/BlackHole)
[![GitHub](https://img.shields.io/github/license/ExistentialAudio/BlackHole)](LICENSE)
[![Build Status](https://travis-ci.com/ExistentialAudio/BlackHole.svg?branch=master)](https://travis-ci.com/ExistentialAudio/BlackHole) [![Twitter](https://img.shields.io/badge/Follow%20on%20Twitter-1da1f2)](https://twitter.com/ExistentialAI)
[![Facebook](https://img.shields.io/badge/Like%20on%20Facebook-4267B2)](https://www.facebook.com/Existential-Audio-103423234434751)

BlackHole is a modern MacOS virtual audio driver that allows applications to pass audio to other applications with zero additional latency. This is a fork of BlackHole meant for use with Yac.

## Table of Contents

- [Features](#features)
- [Easy Installation Instructions](#easy-installation-instructions)
- [Usage Examples](#usage-examples)
- [Advanced Installation Instructions](#advanced-installation-instructions)
- [Uninstallation Instructions](#uninstallation-instructions)
- [Feature Requests](#feature-requests)
- [FAQ](#faq)
- [Wiki](https://github.com/ExistentialAudio/BlackHole/wiki)

## Features
- Supports 16 audio channels.
- Customizable to 256+ channels if you think your computer can handle it.
- Supports 44.1kHz, 48kHz, 88.2kHz, 96kHz, 176.4kHz, and 192kHz sample rates.
- No additional driver latency. 
- Works on macOS 10.10+ including macOS 10.15 Catalina

![Image of BlackHole Audio Driver](Images/BlackHole.png)

## Usage Examples
### Record System Audio
1. [Setup Multi-output Device](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)
2. In `Audio Midi Setup`->`Audio Devices` Right-click on the newly created Multi-output and select "Use This Device For Sound Output"
3. Open digital audio workstation (DAW) such as GarageBand and set input device to "BlackHole" 
4. Set track to input from channel 1-2
5. Play audio from another application and monitor or record in your DAW.

### Route Audio Between Applications
1. Set output driver to "BlackHole" in sending application
2. Output audio to any channel
3. Open receiving application and set input device to "BlackHole" 
4. Input audio from the corresponding output channels

## Advanced Installation Instructions
1. Build driver in Xcode
2. Copy BlackHole.driver to `/Library⁩/Audio⁩/Plug-Ins⁩/HAL`
3. Restart CoreAudio with terminal command `sudo launchctl kickstart -kp system/com.apple.audio.coreaudiod`

## FAQ

### Why isn't Yac Capture showing up in the Applications folder?
BlackHole is an audio interface driver. It only shows up in `Audio MIDI Setup`, `Sound Preferences`, or other audio applications.

### How can I listen to the audio and use BlackHole at the same time?
[Setup a Multi-Output Device](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)

### How can I change the volume of a Multi-Output device?
Unfortunately macOS does not support changing the volume of a Multi-Output device but you can set the volume of individual devices in Audio MIDI Setup. 

### Why is nothing is playing through BlackHole? 
- Check `System Preferences` -> `Security & Privacy` -> `Privacy` -> `Microphone` to make sure your digital audio workstation (DAW) has microphone access. 

- Check that the volume is all the way up on BlackHole input and output in ``Audio Midi Setup``.

- If you are using a multi-output device, due to issues with macOS the Build-in Output must be enabled and listed as the top device in the Multi-Output. https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device#4-select-output-devices

### Where is `/Library/Audio/Plug-Ins/HAL/`?

Chances are you are looking in `~/Library/` or `user/Library/` instead of `/Library`.  
