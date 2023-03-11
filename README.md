
# Runtime Mobile Security #

![mobilesecurity_](/static/mobilesecurity_circle.png)

by [@mobilesecurity_](https://twitter.com/mobilesecurity_) 

**Runtime Mobile Security (RMS)**, powered by [FRIDA](https://github.com/frida/frida), is a powerful web interface that helps you to manipulate Android Java Classes and Methods at Runtime.

You can easily dump all the loaded classes and relative methods, hook everything on the fly, trace methods args and return value, load custom scripts and many other useful stuff.

# General Info
Runtime Mobile Security (RMS) is currently supporting Android devices only.

It has been tested on MacOS and with the following devices:
* AVD emulator
* Genymotion emulator 
* Amazon Fire Stick 4K

It should also work well on Windows and Linux but some minor adjustments may be needed.

Do not connect more than one device at the same time. RMS is not so smart at the moment 😉


# Prerequisites

FRIDA server up and running on the target device 

Refer to the official FRIDA guide for the installation: https://frida.re/docs/android/

# Known issues
* Sometime RMS fails to load complex methods. Use a filter when this happens or feel free to improve the algo (default.js).
* Code is not optimized

# Improvements
* iOS support
* Feel free to send me your best JS sript via a Pull request. I'll be happy to bundle all the best as default scripts in the next RMS release.
e.g.
	* root detection bypass
	* ssl pinning bypass
	* reflection detection
	* etc...



# Installation

1. **(optional)** Create a python virtual environment
2. ```pip3 install -r requirements.txt```
3. ```python3 mobilesecurity.py```


# Usage

## 1. Run your favorite app by simply inserting its package name ##
**NOTE** RMS attachs a persistence process called **com.android.systemui** to get the list of all the classes that are already loaded in memory before the launch of the target app. If you have an issue with it, try to find a different package that works well on your device. 
You can set another default package via the Config Tab or by simply editing the config.json file.

![DEMO_1](/DEMO/GIF/DEMO_1_Device.gif)

## 2. Check which Classes and Methods have been loaded in memory  ##
![DEMO_2](/DEMO/GIF/DEMO_2_Dump.gif)

## 3. Hook on the fly Classes/Methods and trace their args and return values  ##
![DEMO_3](/DEMO/GIF/DEMO_3_Massive_Hook.gif)

## 4. Search instances of a specific class on the Heap and call its methods [BETA]  ##
![DEMO_4](/DEMO/GIF/DEMO_4_Heap_Search.gif)

## 5. Select a Class and generate on the fly an Hook template for all its methods  ##
![DEMO_5](/DEMO/GIF/DEMO_5_Hook_Hack.gif)

## 6. Easily detect new classes that have been loaded in memory   ##
![DEMO_6](/DEMO/GIF/DEMO_6_Diff_Classes.gif)

## 7. Inject your favorite FRIDA CUSTOM SCRIPTS on the fly   ##
Just add your .js files inside the custom_script folder and they will be automatically loaded by the web interface ready to be executed.

![DEMO_7](/DEMO/GIF/DEMO_7_Custom_Script.gif)


# Acknowledgements
Special thanks to the following Open Source projects for the inspiration:
* [FRIDA](https://github.com/frida/frida)
* [Objection](https://github.com/sensepost/objection)
* [House](https://github.com/nccgroup/house)

### DEMO apps:

[RootBeer Sample](https://play.google.com/store/apps/details?id=com.scottyab.rootbeer.sample) is the DEMO app used to show how RMS works.
[RootBeer](https://github.com/scottyab/rootbeer) is an **amazing root detection library**. I decided to use the Sample app as DEMO just to show that, as every client-side only check, its root detection logic can be easily bypassed if not combined with a server-side validation. 

[Anti-Frida](https://github.com/b-mueller/frida-detection-demo) Frida Detection Examples by Bernhard Mueller.

# License
RMS is licensed under a [GNU General Public v3 License](https://www.gnu.org/licenses/gpl-3.0.en.html).