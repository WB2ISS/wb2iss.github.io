---
title: "Helpfile Sdr Receiver"
date: 2022-05-31T20:27:08-07:00
draft: false 
---
### [Web Site](http://www.transitiontechnologyventures.com/sdr-receiver)
### [Quick Start](#quick-start)
### [Instructions](#instructions)
##### [1. Overview](#1-overview)
##### [2. Getting Started](#2-getting-started)
> ##### [2.1 rtl_tcp](#21-rtl_tcp-installation-and-operation)
> ##### [2.2 hfp_tcp](#22-hfp_tcp-installation-and-operation)
> ##### [2.3 rsp_tcp](#23-rsp_tcp-installation-and-operation)

##### [ 3. Using the Application](#3-using-the-application)
> ##### [3.1 Stations Tab](#31-stations-tab)
> ##### [3.2 Lists Tab](#32-lists-tab)
> ##### [3.3 Settings Tab](#33-settings-tab)
> ##### [3.4 Custom URLs](#34-sdr_receiver-custom-urls)  


<span id="quick-start"></span>
## Quick Start

1\. Install a signal server application and obtain its IP address or host name.

* RTL-SDR, Airspy HF+ and SDRplay radios are supported.

* The required server application is `rtl_tcp` for RTL-SDR radios, `hfp_tcp` for Airspy HF+ radios, and `rsp_tcp` for SDRplay radios.

* The server application should be listening for TCP/IP connections on port 1234 which is the default, or on some other known port.

2\. Select the **Settings** tab.

* In the Network Settings section select Host and enter the IP address or host name of the signal server.

* If the server is listening on a port other than 1234, then in the Network Settings section select Port and enter the port number on which the server is listening.

* In the Server Settings section select Server Type and then select RTL-SDR, Airspy HF+ or SDRplay.

* In the Server Settings section select Sampling and then select a Sampling Rate.

3\.  Select the **Stations** tab.  

* Select a station.  The frequency and mode (AM, NFM or WFM) of that station will be shown at the top of the screen.

* Select On.  Audio for the selected station will play.  

<span id="instructions"></span>
## Instructions

<span id="1-overview"></span>  
### 1. Overview

**SDR Receiver** is a Software Defined Radio (SDR) that processes, demodulates and plays AM, narrowband FM and wideband FM signals.  The signals are streamed over a network from a signal server that is the source of a digitized portion of the RF spectrum.  The signal server will generally consist of a radio that is connected by USB to a host computer that is running a server application.  With a properly configured radio and the right antenna, signals that may be played through **SDR Receiver** typically include transmissions from aircraft (AM),  amateur transmitters/repeaters and police/fire radios (narrowband FM) and commercial broadcast stations (wideband FM).  The host computer runs a server application that accepts sampled baseband IQ signals from the radio over USB and streams the sampled signals over the network to the device running **SDR Receiver**.  The radio, host computer, and host server software are not provided with **SDR Receiver** and must be separately obtained and installed.  **SDR Receiver** supports RTL-SDR, Airspy HF+ and SDRplay radios.  To operate with an RTL-SDR radio, the host computer must run the `rtl_tcp` server application which is part of the `librtlsdr` open source library package and runs on Mac, PC and Raspberry Pi.  To operate with an Airspy HF+ radio, the host computer must run the `hfp_tcp` open source server application which runs on Mac and Raspberry Pi. To operate with an SDRplay radio, the host computer must run the `rsp_tcp` open source server application which runs on Mac, PC and Raspberry Pi.

The functions of **SDR Receiver** are divided into three tabs:

* The **Stations** tab has controls for frequency, mode, LNA gain, volume, AirPlay and an On/Off switch that starts and stops the stream of data from the server.  The application manages lists of stations which can be entered, edited, reordered and deleted from the Stations tab.  A single list is active and the stations on the active list are displayed on the Stations tab.  A new station can be created with the + button.  Stations in the active list may be updated, moved or deleted by tapping the Edit button and using the controls that appear on the left and right of each station entry. The controls on the right enable reordering, and the controls on the left reveal Update and Delete buttons.  Stations may also be updated, moved or deleted by direct interaction without using the Edit button.  A swipe left on a station will reveal Update and Delete buttons.  A station can be moved by long pressing the station  and dragging it to a new location.

* The **Lists** tab provides a set of Preset lists, and the ability to create, rename and manage Custom lists.  The active list is selected from the Custom lists, and the name of the active list is highlighted in blue.  A new empty Custom list is created with the + button.  A new Custom list with the name and contents of a specific Preset list is created by selecting that list in the Preset section.  A Custom list may be renamed, deleted or moved via the Edit button or with a swipe left on the name of the Custom list. A Custom list can also be moved by long pressing the list which will cause its image to lift, and then dragging it to a new location.  Lists may be exported or imported in Comma Separated Values (CSV) format or in Tab Separated Values (TSV) format, to or from a file with .csv or .tsv extension; by copy/paste to or from a text-based app like Mail or Notes or a spreadsheet like Apple Numbers or Google Sheets; and on iPad lists may be exported or imported by drag/drop to or from a text-based app or spreadsheet, and .tsv or .csv files containing lists may be imported by drag and drop from the Files app or from Mail.  When exporting or importing by drag and drop, the drag may hold multiple items.  A list file with a .csv or .tsv extension may be shared from another app like Mail or the Files app and then imported.

* The **Settings** tab provides controls for:  selecting the network address of the signal server; configuring the operating parameters of the signal server and radio including the server type, sampling rate, sample size and direct sampling configuration;  settings related to signal processing functions including audio filters, squelch and tuning; and selection of CSV or TSV export data format. This tab also provides information related to help and support.

**SDR Receiver** also responds to specially formatted URLs that enable the app to be controlled and launched from another application on the device.   

<span id="2-getting-started"></span>
### 2. Getting Started

**SDR Receiver** requires a signal server that is not included with the application and must be separately obtained and installed.  The signal server will generally include a radio that is connected by USB to a host computer that runs a server application.  Three types of signal servers are supported: servers with an RTL-SDR radio running the `rtl_tcp` server application, servers with an Airspy HF+ radio running the `hfp_tcp` server application, and servers with an SDRplay radio running the `rsp_tcp` server application.

<span id="21-rtl_tcp-installation-and-operation"></span>
#### 2.1 rtl_tcp Installation and Operation

To operate with an RTL-SDR radio, the `librtlsdr` package  must be installed on a host computer.  The package consists of a library and a number of utilities, one of which is the `rtl_tcp` server application.  The `librtlsdr` package is developed and maintained on [Osmocom.org](https://osmocom.org)  and there is an [official mirror of the repository on GitHub](https://github.com/osmocom/rtl-sdr).  Instructions for building the library and pointers to binaries for Windows are on the [rtl-sdr page of the Osmocom Wiki](https://osmocom.org/projects/rtl-sdr/wiki).  Additional instructions for building the library on various platforms may be found on the Web, for example [SDR on Raspberry Pi 3 (software) – Medo's Home Page, April 18, 2016](https://www.medo64.com/2016/04/sdr-on-raspberry-pi-3-software/) and [How to compile librtlsdr on Windows · One Transistor, December 16, 2017](https://www.onetransistor.eu/2017/03/compile-librtlsdr-windows-mingw.html).

The `rtl_tcp` server application is a wrapper for the `librtlsdr` library that communicates with the RTL-SDR radio over USB via the library, and receives commands and streams IQ data over the network via TCP.  It is invoked with the command:

	rtl_tcp -p <port-number> -a 0.0.0.0

When the server receives an incoming connection from **SDR Receiver**, it will indicate that it is connected and will echo commands as it executes them.  If `-p <port-number>` is omitted, the server will listen on port 1234 which is the default port number.  **SDR Receiver** can reference the server by IP address or by symbolic name using Bonjour/Avahi on a LAN.  For example, a Raspberry Pi can be addressed by the default symbolic name raspberrypi.local.  


#### 2.1.1 rtl_tcp Installation — Raspberry Pi

First, configure an SD card with the latest version of the Raspberry Pi OS.  Detailed instructions can be found on raspberrypi.org: [Installing the Operating System - Raspberry Pi Documentation](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system).

Next, start the Raspberry Pi and execute these two commands in a terminal window:

	sudo apt-get update
	sudo apt-get install rtl-sdr

The `rtl_tcp` server application, and other utilities that are part of the `librtlsdr` package, will be installed in `/usr/bin`.


#### 2.1.2 rtl_tcp Installation — macOS

The `librtlsdr` package is available for installation via the [Homebrew package manager](https://brew.sh/).  Start by installing the Xcode Command Line Tools:

	xcode-select --install

Then install `brew` and `librtlsdr`:

	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
	brew install librtlsdr

If there were previous installations of the `librtlsdr` package or `libusb` on the system, the install process might fail with error messages indicating that libraries or header files were found which would be overwritten by the installation.  Remove the conflicting files and follow the directions in the error messages to complete the installation process.

As an alternative to installing Homebrew and using it to install `librtlsdr`, pre-built binaries for macOS that are available as part of a package prepared for a course at UC Berkeley can be installed.  This package can be installed according to the directions that are provided with the package, and it will run properly on macOS 10.14 Mojave and earlier.  On macOS 10.15 Catalina and later, an additional step is required, which is described below.

The UC Berkeley package can be found at: [RTL-SDR Installation Instructions - EE123, EECS, UC Berkeley - Spring, 2017](https://inst.eecs.berkeley.edu/~ee123/sp17/rtl_sdr_install.html). Download the [macOS package](https://inst.eecs.berkeley.edu/~ee123/sp17/rtlsdr/rtlsdr_osx.zip) and extract the archive.  Open a terminal window and change directories to the directory containing the files extracted from the archive.  The installation process requires admin privileges.  If you are not logged in with an account that has admin privileges then in the terminal window you can switch to a user that has admin privileges with the su command:

	su <user>
	Password: <password>

On macOS 10.15 Catalina there are new security mechanisms that require an additional authorization step before downloaded applications can run.  If your version of macOS is Catalina or later, make sure that you are in the directory containing the files extracted from the archive, and run this command in the terminal:

	xattr -d com.apple.quarantine *

This will remove the quarantine attribute from the executables and libraries.

Finally, for all versions of macOS, from the terminal window create two directories (if they do not already exist):

	sudo mkdir /usr/local/bin
	sudo mkdir /usr/local/lib

In the directory in which the archive was unpacked, execute the following commands to copy the files to the right place:

	sudo cp rtl* /usr/local/bin/
	sudo cp lib* /usr/local/lib/

The `rtl_tcp` application will be found at `/usr/local/bin/rtl_tcp` and it can be invoked as `rtl_tcp` if `/usr/local/bin` is in the search path, and with the full path name otherwise.

From a terminal window execute `rtl_tcp -a 0.0.0.0` and the `rtl_tcp` server will start.


#### 2.1.3 rtl_tcp Installation — Windows

Pre-built binaries for Windows are available from the [rtl-sdr page of the Osmocom Wiki](https://osmocom.org/projects/rtl-sdr/wiki).  Download the Windows executables directly from their [index of Windows binaries](https://ftp.osmocom.org/binaries/windows/rtl-sdr/).

Pre-built binaries for Windows are also available as part of a package prepared for a course at UC Berkeley: [RTL-SDR Installation Instructions - EE123, EECS, UC Berkeley - Spring, 2017](https://inst.eecs.berkeley.edu/~ee123/sp17/rtl_sdr_install.html). Download the Windows package directly from the [link on that site](https://inst.eecs.berkeley.edu/~ee123/sp17/rtlsdr/rtlsdr_win.zip).

In addition to obtaining the executables from one of the sites above, the Zadig utility must be run to install and configure the driver.  In some installations, this utility might be present and might have been used previously to configure the driver for some other application such as SDR#.  It is possible for the driver to have been configured so that it works properly with an RTL-SDR radio and SDR# but can still give an error when `rtl_tcp` is executed.  If Zadig has not previously been used to configure the driver, or if it has been installed but an error is reported when `rtl_tcp` is executed, then Zadig must be used to install or re-install the driver.

Download [Zadig](https://zadig.akeo.ie).  Then:

* Make sure that an RTL-SDR radio is plugged into a USB port.  Note that the driver configuration is for a particular USB port (socket).  After configuration, the driver should work with the RTL-SDR radio plugged into the port for which it was configured, but might not work if the RTL-SDR radio is plugged into a different port.

* Make sure that SDR# or any other program that might use the USB interface is not running.  Running programs are shown under the Windows Task Manager.

* Run the `zadig.exe` utility as administrator (right click and select "Run as administrator”).

* Under the Zadig Options  drop-down menu, check the first line "List All Devices", and uncheck the second line "Ignore Hubs or Composite Parents”.

* On the main window drop-down menu select "RTL2838UHIDIR".  Then to the right of the green arrow there should be a selection beginning "WinUSB …”.  Choose this one if it is not shown already.  Hover the cursor over the numbers to the right of USB ID and it should show "Realtek ..." indicating that it is the USB ID of a Realtek device which is the RTL-SDR.

* Make sure "Reinstall Driver" is shown on the large button, and select it.  The driver should then be installed, and Zadig should report that it completed successfully.

Now change to the directory that contains the pre-built binaries downloaded from from Osmocom or from UC Berkeley.   Run `rtl_test -t` to check the status of the interface.  It should show the RTL-SDR radio.  Execute the command `rtl_tcp -a 0.0.0.0` to start the server. With the driver configured this way, both SDR# and `rtl_tcp` will run.  However, they cannot both be run at the same time.  Find the IP address of the PC under Settings → Network & Internet → Wi-Fi → Hardware Properties.  Note the IPv4 address and then in **SDR Receiver** select the Settings tab, select Host and enter the IP address of the server.   

The procedure above has been tested and works properly on Windows 10.  A similar procedure should work on other recent versions of Windows.

<span id="22-hfp_tcp-installation-and-operation"></span>
#### 2.2 hfp_tcp Installation and Operation

The `hfp_tcp` server application is required to operate **SDR Receiver** with an Airspy HF+ radio.  This open source application is available as source code that can be compiled, installed and executed on a Raspberry Pi or Mac host computer.  It consists of a single source file and a Makefile which require two header files and a dynamic library that are part of the Airspy HF+ library package.

Building `hfp_tcp` will generally consist of two steps: 1. Download and build the Airspy HF+ library; 2. Download and build `hfp_tcp`. In the first step, the `libairspyhf` dynamic library will be built, and the library and header files will be placed in standard system locations.  In the second step, the compile and link process will look in these standard locations to locate the header files that are required to build and run `hfp_tcp`.  

If the server is a Raspberry Pi and the Airspy SPY Server application has been previously installed, the first step will have already been completed and does not need to repeated.  In this case, skip the first step and just follow the directions under the second step.


#### 2.2.1 Download and Build the Airspy HF+ Library

The Airspy HF+ library is an open source  package that includes a library and user mode driver.  The source code and directions for building the package are in the Airspy GitHub repository at: [GitHub - airspy/airspyhf: Code repository for AirspyHF+](https://github.com/airspy/airspyhf).

To build the library on Raspberry Pi OS, follow the directions under “How to build the host software on Linux” in the README on the GitHub repository.

To build the library on macOS, the first step of the Airspy directions for Linux (the command beginning `sudo apt-get install`) must be replaced by an alternative series of steps which install `cmake`, `libusb` and `pkg-config`.  These can be installed using the `brew` package manager, or they can be built from source that is available from their download sites. Both methods are described below.

For either method, start by installing the Xcode Command Line Tools:

	xcode-select --install

For the first method, start by installing `brew`:

	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

Then,  using `brew`, install `cmake`, `libusb`, and `pkg-config`:

	brew install cmake
	brew install libusb
	brew link libusb
	brew install pkg-config

The `libusb` link step will attempt to create symbolic links in `/usr/local/lib` for `libusb-1.0.0.dylib` and `libusb-1.0.dylib` and some other files, and will fail if any of these exist.  If that happens, move or remove the files that are reported as already existing and then repeat the link step.

For the second method, `cmake`, `libusb` and `pkg-config` will be built from source code.  Building `libusb` will require Xcode which can be downloaded from the Mac App Store.

Build `cmake` as follows. Download the `cmake` source for Unix/Linux from [cmake.org](https://cmake.org/download/). Then, in the top level directory, build `cmake` as follows:

	./bootstrap
	make
	sudo make install

The last step installs the `cmake` command line utility in `/usr/local/bin`.

Build `libusb` as follows.  The `libusb` project is on GitHub: [libusb/libusb: A cross-platform library to access USB devices](https://github.com/libusb/libusb).  Clone the project:

	git clone https://github.com/libusb/libusb.git
	cd libusb/Xcode

Open `libusb.xcodeproj` in Xcode.  Choose an appropriate Deployment Target for `libusb` and then build the `libusb` target.  The dynamic library and header file now need to be moved to the correct locations.  

In Xcode, locate the Build directory containing the dynamic library and header file by selecting Product → Show Build Folder in Finder.  Then in the Build directory navigate to `Products/Release` to locate `libusb-1.0.0.dylib`.  Copy `libusb-1.0.0.dylib` to `/usr/local/lib` and create a symbolic to it. To perform these steps, in a terminal window navigate to the Build directory and then:

	cd Products/Release
	cp libusb-1.0.0.dylib /usr/local/lib
	cd /usr/local/lib
	sudo ln -s libusb-1.0.0.dylib libusb-1.0.dylib

In a terminal window, navigate back to the Build directory.  Then navigate to the directory containing the header file, and copy it to `/usr/local/include`, as follows:

	cd Products/Release/usr/local/include
	cp libusb.h /usr/local/include

Build `pkg-config` as follows.  Download the latest version of the source code from [freedesktop.org](https://pkg-config.freedesktop.org/releases/). Navigate to the directory containing the source code and then build and install `pkg-config` as follows:

	LDFLAGS="-framework CoreFoundation -framework Carbon" ./configure --with-internal-glib
	make
	sudo make install

The last step installs `pkg-config` in `/usr/local/bin`.

Finally, after installing `cmake`, `libusb` and `pkg-config` either with `brew` or by building from source, download and build `libairspyhf`:

	git clone https://github.com/airspy/airspyhf.git
	cd airspyhf
	mkdir build
	cd build
	cmake ../ -DINSTALL_UDEV_RULES=ON
	make
	sudo make install

The last step installs `libairspyhf` in `/usr/local/lib` and installs various other files in standard system locations.


#### 2.2.2 Download and Build hfp_tcp

The `hfp_tcp` application is a single source file.  It can be built and installed with the included Makefile which requires header files and a dynamic library that were installed as part of building the Airspy HF+ library.  The build process for `hfp_tcp` is the same for both macOS and Raspberry Pi OS.  The `hfp_tcp` application is on GitHub at: [GitHub.com/WB2ISS/hfp_tcp](https://github.com/WB2ISS/hfp_tcp) which is a fork of `hfp_tcp` that is tested with and kept up to date with **SDR Receiver**.

To clone the repository and build `hfp_tcp`, execute the following commands in a terminal window:

	git clone https://github.com/WB2ISS/hfp_tcp.git
	cd hfp_tcp
	make
	sudo make install

The target operating system will be detected and applied to obtain the correct compile and link commands.  The detected operating system will be displayed as Darwin for macOS and as Linux for Raspberry Pi OS, and the build command that is being executed will be shown.  The `sudo make install` step will copy the executable into `/usr/local/bin`.

Compilation requires the header files `airspyhf.h` and `airspyhf_commands.h` and the executable requires the `libairspyhf` dynamic library. If the Airspy HF+ library has been installed, these dependencies will have been placed in the correct locations and will be found by the compile and link process.  

To run `hfp_tcp`, connect an Airspy HF+ radio to the system by USB.  The `hfp_tcp` application can then be executed  with the command `hfp_tcp`.  By default, the application will listen for an incoming TCP/IP connection on port 1234.  An alternate port can be specified with the `-p` flag.  For example, to start the application listening on port 1024, the command is:  `hfp_tcp -p 1024`.

By default, for compatibility with the `rtl_tcp` protocol, `hfp_tcp` streams data consisting of 8-bit samples.  In order to take advantage of the additional resolution of the analog to digital converter in the Airspy HF+ radio, `hfp_tcp` can also stream data consisting of 16-bit samples to **SDR Receiver**.  To stream 16-bit samples, start `hfp_tcp` with the `-b 16` flag and in **SDR Receiver**, on the Settings tab, select Sampling and set Sample Size to 16-bits.


<span id="23-rsp_tcp-installation-and-operation"></span>
#### 2.3 rsp_tcp Installation and Operation

The `rsp_tcp` server application is required to operate **SDR Receiver** with an SDRplay radio.   This application is provided by SDRplay in executable form for Windows, and in source code form for macOS, Raspberry Pi OS and other platforms. There is an [RSP_TCP Server User Guide](https://www.sdrplay.com/docs/SDRplay_RSP_TCP_Server_Guide.pdf) and executables can be found on the [SDRplay Downloads page](https://www.sdrplay.com/downloads/).

The source code and directions for building `rsp_tcp` can be found [on GitHub](https://github.com/SDRplay/RSPTCPServer). Note that the SDRplay API, which is available from the [SDRplay Downloads page](https://www.sdrplay.com/downloads/), must be installed in order to build the application or run the binaries.

The `rsp_tcp` server application can be invoked with the command:

	rsp_tcp -p <port-number> -a 0.0.0.0

If `-p <port-number>` is omitted, the server will listen on port 1234. A list of other options can be found with `rsp_tcp -help`.

By default, for compatibility with the `rtl_tcp` protocol, `rsp_tcp` streams data consisting of 8-bit samples.  In order to take advantage of the full resolution of the analog to digital converter in the SDRplay radios, `rsp_tcp` can also stream data consisting of 16-bit samples to **SDR Receiver**.  To stream 16-bit samples, start `rsp_tcp` with the `-b 16` flag and on the Settings tab in **SDR Receiver**, select Sampling and set Sample Size to 16-bits.


<span id="3-using-the-application"></span>
### 3. Using the Application

After a signal server has been configured and started, determine the IP address of the server or the symbolic name at which the server can be found on the LAN. The IP address may be an IPv4 address or an IPv6 address.   A symbolic name on a LAN is a name that is resolved through the Bonjour or Avahi protocol.  The servers all use port 1234 as the default, but an alternate port can be specified with the `-p <port-number>` flag when the server is started.  

The functions of **SDR Receiver** are divided into three tabs: Stations, Lists and Settings.  The Stations tab controls the frequency, mode and gain applied to the signal that is being demodulated and played. The Lists tab provides methods for creating and managing lists of stations.  The Settings tab provides controls related to the network, signal server and operating parameters of the application.  There is also a custom URL scheme that allows another app on the device to launch **SDR Receiver** into streaming a specified station.

<span id="31-stations-tab"></span>
#### 3.1 Stations Tab

The Stations tab has controls for frequency, mode, LNA gain, volume, AirPlay and an On/Off switch that starts and stops the stream of data from the server.  The application manages lists of stations.  One list is active and is displayed on the Stations tab from which individual stations can be entered, edited, reordered and deleted.  When a signal is being streamed, the magnitude of the energy in the signal passband will be displayed as the height of a green signal strength bar in the center of the upper portion of the display.

<u>Selecting a Station</u>  
In **SDR Receiver**, a station is specified by a frequency in MHz; a mode of narrowband FM (NFM), wideband FM (WFM) or amplitude modulation (AM); and a description.  A station may be selected from the active list of stations that are displayed.  The selected station will be highlighted in blue.  A frequency and mode may also be entered directly with the controls at the top of the screen.    

<u>Frequency Display</u>  
The current frequency is displayed at the top of the Stations tab screen.  The frequency may be increased by tapping or holding the up arrow, and decreased by tapping or holding the down arrow.  Holding the up or down arrow is equivalent to a continuous sequence of taps.  The increment by which the frequency changes with each tap of the up or down arrows may be set for each mode by selecting Tuning on the Settings tab.

<u>Mode </u>  
AM, NFM or WFM modulation may be selected.

<u>Streaming</u>  
The On/Off switch starts and stops the streaming and processing of data from the signal server.  When the switch is set to On, a connection to the signal server is initiated and the connection state will be displayed above the Mode control.  When the switch is set to Off, the connection is closed and streaming stops.

<u>AirPlay</u>  
To the right of the frequency display is an AirPlay button that brings up  a list of AirPlay and Bluetooth devices to which audio can be routed.  

<u>LNA Gain</u>  
For radios that support this function, **SDR Receiver** allows enabling or disabling AGC,  and controlling LNA gain when AGC is disabled.  When the AGC/Man control is set to AGC, the tuner AGC function is enabled and manual LNA Gain control is disabled.  When the AGC/Man control is set to Man, the tuner AGC function is disabled and the LNA gain is set by the LNA Gain control. With RTL-SDR radios, operating with AGC enabled often leads to distortion in the presence of strong signals, and better results are generally obtained with AGC off (Man) and LNA Gain set manually to around 30.2 dB.  This is the default configuration for the application.

<u>Volume</u>  
The volume control sets the audio amplitude level of the audio signal generated by the application.  Audio volume may also be adjusted using the volume controls on the device.

<u>Entering a New Station</u>  
The + button brings up the New Station entry screen.  There are fields for entering a frequency and description, and a control for selecting the mode.  The frequency is specified in MHz with three or four digits to the right of the decimal separator.   The frequency, description and mode are initialized with the current frequency and mode as displayed, and the description of the last selected station.  When a new station is saved, it is added at the bottom of the active list on the Stations tab, but the current frequency and mode are not changed.  To set the frequency and mode to that of the new station, it must be selected from the list.

<u>Managing the Active List</u>  
Stations in the active list may be reordered by long pressing on a station and dragging it to a new location.  A left swipe on a station will reveal Update and Delete buttons on the right. Selecting Update will bring up a screen that provides fields for entering or updating the frequency, description and mode of the selected station. Selecting Delete will delete the station from the list. The move, update and delete functions may also be accessed by tapping the Edit button which will bring up a red circle on the left and a three line grab icon on the right of each station. Tapping the red circle will reveal the Update and Delete buttons. The three line grab icon on the right of a station may be dragged to move the station to a new location.


<span id="32-lists-tab"></span>
#### 3.2 Lists Tab

The Lists tab provides a set of Preset lists, and the ability to create, rename and manage Custom lists.  It also provides a means for exporting and importing lists.  The active list is selected from the Custom lists and highlighted in blue.  There is always a single active list, and the name and contents of that list are displayed on the Stations tab.  A new empty Custom list can be created by tapping the + button.  A new Custom list with the name and contents of a Preset list can be created by selecting a Preset list.   A Custom list may be renamed, deleted or moved by selecting Edit or by swiping left on the name of the Custom list.  The Custom lists may be reordered by long pressing on a list name and dragging to a new location.

<u>Preset Lists</u>  
The application comes with several lists as examples and for use in areas where they apply.   To use a Preset list, go to the Lists tab and select the list.  This will create a new Custom list with the name and contents of the selected Preset list. This new list will become the active list and will be highlighted in blue. The Preset Lists section may be collapsed or expanded by tapping the Preset section header.  

<u>Creating Lists</u>  
A Custom list may be created in several different ways.  A new Custom list may be created from a Preset list by selecting the Preset list.  A new empty Custom list may be created by tapping the + button in the upper right hand corner and entering a name for the new list.  When the Save button is tapped, a new empty list with the specified name is created and it becomes the active list. New stations can be entered by switching to the Stations tab, tapping the + button and entering the frequency, description and mode for the new station.   New lists may also be created by importing lists of stations in CSV or TSV format as described below.

<u>Managing Lists</u>  
The table of lists may be reordered by long pressing on a list that is to be moved and dragging it to a new location.  A left swipe on a list will reveal Rename and Delete buttons on the right. Selecting Rename will bring up a screen from which the name of the list can be updated. Selecting Delete will delete the list. The move, rename and delete functions may also be accessed by tapping the Edit button which will bring up a red circle on the left and a three line grab icon on the right of each list. Tapping the red circle will reveal the Rename and Delete buttons. The three line grab icon on the right of a list may be dragged to move the list to a new location.  Note that there is always one active list, which is highlighted in blue and which cannot be renamed or deleted.  To rename or delete the active list, select another Custom list so that it becomes the active list, then rename or delete the first list.

<u>Import/Export Format</u>  
The Import and Export mechanisms represent lists of stations as Comma Separated Values (CSV) or Tab Separated Values (TSV).  These formats are easy to generate from a spreadsheet or directly as a text file, and are the formats in which lists of stations are typically represented for use in scanners and VHF transceivers.  For example, an Aviation list that has two stations, a Commercial list that has three stations and a Weather list that has two stations are represented in CSV format as follows:

List,Frequency,Description,Mode  
Aviation,135.275,PAO ATIS,AM  
,118.600,PAO Tower,AM  
Commercial,90.100,KZSU,WFM  
,89.700,KFJC,WFM  
,88.500,KQED,WFM  
Weather,162.550,NOAA A,NFM  
,162.450,NOAA B,NFM

This text could be placed in a file with a .csv extension and then opened in a spreadsheet where it would look like this:

| List       | Frequency | Description | Mode   |
| ---------- | --------- | ----------- | ------ |
| Aviation   | 135.275   | PAO ATIS    | AM     |
|            | 118.600   | PAO Tower   | AM     |
| Commercial | 90.100    | KZSU        | WFM    |
|            | 89.700    | KFJC        | WFM    |
|            | 88.500    | KQED        | WFM    |
| Weather    | 162.550   | NOAA A      | NFM    |
|            | 162.450   | NOAA B      | NFM    |

Spreadsheet applications generally have an export option with which a .csv or .tsv file can be created from a table.

The CSV or TSV data format for station lists is as follows:

* The first row may be a header row consisting of a set of column labels.  This row is optional.

* All rows must have four elements separated by the field delimiter which is either a comma or a tab.

* The four fields in each row are the List, the Frequency, the Description and the Mode, in that order.

* The Frequency is in MHz and the Mode may be AM, WFM or NFM.

* In a comma separated list, the List or Description field may placed in quotes to allow embedded commas.

* Each row represents a station, except for the optional header row.

* Each station is associated with a list.  Consecutive rows with the same value in the List field are grouped together in the same list.  

* The first station must include a value in the List field.

* When the value in the List field changes, a new list is started.  

* If the List field is empty, the station will be included in the same list as the previous station.

* Lists are not uniquely named, and if the same value is used in the List field in non-consecutive rows it will result in two different lists with the same name.  This is the same behavior as in the application where lists are uniquely identified by their position in the table, but list names are not required to be unique.

* All fields must be non-empty and valid, except for the List field which may be empty on any station except for the first.

When **SDR Receiver** receives imported data, each station is checked for validity, and a row containing an invalid station will be removed.  If there are any invalid stations, an error will be reported on import.  Rows that contain valid stations will be imported.  

<u>Export</u>  
Lists can be exported in CSV or TSV format in several ways:  as a .csv or .tsv file; by copying to the clipboard and pasting into another application; and on iPad by drag and drop.  Select Export and the Custom list table will display selection circles on the left side, and an inactive (grey color) Share icon will be shown in the navigation bar at the top, just to the left of the Cancel button.   Select the lists to be exported and the corresponding circles will show check marks.  When the first list is selected, the Share button will change from grey to blue indicating that it is enabled. The Select All button will cause all the lists to be selected, and after Select All is tapped the button will change to Deselect All.  All lists can then be exported, or individual lists that are not intended to be exported can be deselected. After the desired set of lists are selected, select the Share icon to bring up the Share Sheet.  On the Share Sheet is a horizontal row showing the icons of apps that can accept data of the exported type (.csv or .tsv files).  Scroll to the right most side of this row and there are three dots labeled More.  Selecting More brings up additional apps that can accept the data.  Select one of the apps on the row or in the list to perform the export.  Note that there is an Edit option on the secondary list of apps brought up by the More option by which an app can be moved from the secondary list to the horizontal row for quicker access.  On the Share Sheet below the row of app icons is a list of other actions by which the export can be done. For example, Copy can be used to copy the data to the clipboard from which it can be pasted into an app like Mail or Notes, and also spreadsheets like Apple Numbers and Google Sheets.   Save to Files will allow saving to iCloud Drive.   Save to Dropbox will be shown if the Dropbox app is installed.  The choice of CSV or TSV as the export format is determined on the SDR Settings section of the Settings tab under SDR Settings → Export.

<u>Export on iPad</u>  
On iPad, lists can also be exported by drag and drop.  The target app can be a text-based app like Notes or the compose window of Mail, or a spreadsheet like Apple Numbers or Google Sheets.  Drag and drop requires that **SDR Receiver** and the target app are both visible on the screen, either with both apps visible in split screen, or with one as a hover overlay.  On the Lists tab simply long press on a list to be exported.  It will lift, and can then be dragged to the target app.  As the list is dragged to an app that can receive the drop, a green circle with a + will be shown in the upper right corner of the dragged image.  Once the drag of a first list has started, a second list can be added to the drag by tapping the name of the second list.  An image of the second list will be added to the image in the drag, and the circle in the upper right corner of the drag item will show 2.  Additional lists can be added to the drag in the same way.   Release the dragged items at the desired location in the target app to perform the drop.  For multiple item drop to work, the target application must be able to receive multiple drop items.  The Notes app, the Mail app compose window, and Google Sheets all accept multiple items.  Apple Numbers will only accept the first item of a multiple item drop.

<u>Import</u>  
There are several paths by which data can be imported.  Text data in CSV or TSV format, in a file with the .csv or .tsv extension, can be referenced as an attachment in an email, or directly from the Files app or the Dropbox app if it is installed.  Tapping on a file that is a mail attachment will bring up a preview with a Share icon in the upper right.  Other apps that show files will also show a Share or Export icon.  Selecting the Share or Export icon will bring up the Share Sheet which will show a horizontal row of app icons.  **SDR Receiver** can be found by selecting the More option on the right side of the row.  It may be selected from the secondary list that is brought up, and using the Edit option on that screen it may be moved to appear in the horizontal row.  Selecting **SDR Receiver** will cause a switch to the app which will show an alert indicating that a Share action requested to send it data, and showing the status of the request.  If the data contains valid lists of stations, the alert will display the option to Import or Cancel.  If there were errors in the data, the alert will indicate that there were errors and will provide the option to Cancel or Import the valid stations.  If there there were no valid stations, that will be indicated in the alert and only a Cancel option will be provided.  Data may also be imported by copy/paste.  In a text-based app, select a block of text representing lists of stations in CSV or TSV format, and copy the text to the clipboard.  Then in **SDR Receiver**, select Import.  The clipboard will be inspected and an alert will pop up offering options based on the data that is found on the clipboard.  Data can also be copied from a spreadsheet like Apple Numbers or Google Sheets, and then pasted directly into **SDR Receiver** using the Import button.  If Universal Clipboard is enabled, data can be copied from an associated Mac and then pasted into **SDR Receiver** using the Import Button.  Data may also be sent to the device by AirDrop.  An alert will pop up showing applications that can can accept the data.  If the data is a file with a .tsv or .csv extension, **SDR Receiver** will be one of the choices offered.  Select **SDR Receiver** and the import alert will be shown.   When copy/paste is used for import, the text data can be in either CSV or TSV format, and the format will be automatically detected and correctly processed.  

<u>Import on iPad</u>  
On iPad, lists can be imported by drag and drop from a text-based app like Notes, from a spreadsheet like Apple Numbers or Google Sheets, and by drag and drop of .csv files or .tsv files from Mail where the files are included as attachments or from the Files app.  The drag may include multiple items.   **SDR Receiver** and the app from which the lists are being dragged must both be visible, either in split-screen or with one app hovering over the other.  Select the CSV or TSV text data in the text app, or the block of cells in the spreadsheet containing the lists, or a .tsv or .csv file, and long press on the selection to lift the data for the drag.  Once a first item has been selected, additional items may be selected and added to the drag.  Drag the items to **SDR Receiver** and lift the touch to drop the items.  **SDR Receiver** will bring up an alert to confirm the import, and if the dragged items contain valid data, the alert will offer the option to import the lists.


<span id="33-settings-tab"></span>
#### 3.3 Settings Tab

The Settings tab provides controls related to selecting the network address of the signal server, configuring the operating parameters of the signal server and radio including the server type and sampling rate, and settings related to the operation of **SDR Receiver** including audio filters and squelch.

#### 3.3.1 Network Settings

<u>Host</u>  
The host is specified by an IPv4 address, an IPv6 address or a symbolic host name.  The IP address or host name should specify a host at which a signal server application is listening for TCP/IP connections.  After an IP address is entered, tap Save to set it as the current IP address.  Previously saved IP addresses and host names are shown in a drop-down list that is displayed when the IP address field is selected.  This enables previously entered IP addresses and host names to be easily reused.  Entries in the drop-down list may be deleted by swiping left.  Tapping Reset at the bottom of the drop-down list will delete all previously entered IP addresses and host names and reset the list to preset entries.

<u>Port</u>  
The port is specified by a port number in the range 0-65,535.  The port number is initially set to the default value of 1234.  After a port number is entered, tap Save to set it as the port number.  Previously saved port numbers are shown in a drop-down list that is displayed when the port number field is selected.  This enables previously entered port numbers and host names to be easily reused.   Entries in the drop-down list may be deleted by swiping left.  Tapping Reset at the bottom of the drop-down list will delete all previously entered port numbers and reset the list to preset entries.  

#### 3.3.2 Server Settings

<u>Server</u>  
The type of radio is specified with the Server Type control by selecting RTL-SDR, Airspy HF+ or SDRplay. A tuning offset is specfied with the IQ Offset control by selecting -20 kHz, 0 kHz or +20 kHz. Each Server Type has its own IQ Offset which can be used to move errors at DC to an offset frequency where they will not cause distortion in the demodulated signal. The presence and amount of distortion caused by DC error depends upon the particular signal type, signal strength and the characteristics of the radio. Selection of a DC Offset of +20 kHz or -20 kHz is recommended for SDRplay and RTL-SDR radios.  In addition to the IQ Offset, a DC Blocker may be enabled. The DC Blocker is a pole-zero high pass filter that can remove spurious signal components that are close to DC.  In general, an IQ Offset will be preferred because it moves DC errors completely out of the signal passband.  However, the DC Blocker is provided as an alternative.

<u>Sampling</u>  
**SDR Receiver** supports a number of different sampling rates.  The specific set of available sampling rates depends upon the type of radio and signal server.  For Airspy HF+ radios, the set of available sampling rates depends upon the version of firmware running on the Airspy HF+ and the version of the `hfp_tcp` server.  Download and install the latest version of the Airspy HF+ firmware from [Airspy Firmware Updates](https://airspy.com/airspy-hf-plus/#firmware-updates).  Download and install the latest version of the `hfp_tcp` server from [GitHub.com/WB2ISS/hfp_tcp](https://github.com/WB2ISS/hfp_tcp) as explained in [Section 2.2 hfp_tcp Installation and Operation](#2.2_hfp_tcp_Installation_and_Operation).  Some RTL-SDR radios support a Direct Sampling configuration that allows reception at lower frequencies.  This is supported by the Direct Sampling selector that allows choosing I Channel or Q Channel as the signal source. For Direct Sampling with the RTL-SDR V3 radios, select Q Channel.  RTL-SDR radios deliver 8-bit samples.  Airspy HF+ and SDRplay radios have analog to digital converters with resolution greater than 8-bits. To take advantage of the increased amplitude resolution when Airspy HF+ or SDRplay has been selected as the Server Type, a 16-bit Sample Size option is enabled and may be selected. To stream 16-bit samples, the `hfp_tcp` or `rsp_tcp` server should be started with the `-b 16` option. Note that for streaming to be successful, the server and network connections must be able to sustain streams at the data rate that is determined by the selected Sampling Rate and Sample Size.

#### 3.3.3 SDR Settings

<u>Audio Filter</u>  
The application provides a large set of audio high pass and low pass filters.  Each mode has its own set of filter values and default values.   Initially the filters are set to default values.  For each filter type, Low Pass and High Pass, there is a control that can be set to Default or to a numeric value.  Tapping Default will choose the default value which will be shown on the right segment of the control.  Tapping the numeric value will bring up a list from which other values may be selected.  Tapping any numeric value, either a displayed value from the list or the value shown on the control, will cause that value to be selected and shown on the control, and will cause the list to be hidden.  A selected default or numeric value will become active in the audio filter immediately when it is selected, and if a station is streaming the effect of that filter will be heard.  This allows different audio filter values to be quickly evaluated.  Tapping Save will cause the selected filter value to be saved and the Audio Filter panel to be dismissed.  Tapping Cancel will cause any selected filter values to be discarded, the audio filters will be reset to the values that they had when the Audio Filter panel was first selected, and the Audio Filter panel will be dismissed.  This allows experimentation with new filter settings and then returning to the original filter value.

<u>Squelch</u>  
A Squelch Enable and Squelch Threshold value may be set for each mode.  When Squelch Enable is set to Off, audio will always play with no squelch.  With Squelch Enable set to On, the squelch will operate with a threshold set according to the Squelch Threshold control.  When this control is set to the extreme left side (Low) the squelch function is off (equivalent to Squelch Enable Off).   As the squelch control is moved to the right, a stronger signal is required to break squelch.  There are two different squelch algorithms, one for FM signals and the other for AM signals.  For FM signals the squelch is based on quieting at the higher audio frequencies in the demodulated audio signal.  This quieting is largely independent of received signal amplitude, and a squelch threshold setting in the middle of the range should work for all but the very weakest signals.  To hear very weak signals, the squelch function should be disabled.  For AM signals the squelch is based on energy in the signal passband before the demodulator.  In general, this level should be set by listening when no signal is present, moving the Squelch Threshold control from left to right to just past the point at which squelch quieting begins.  Moving the control further to the right will result in a stronger signal being required to break squelch.  The proper Squelch Threshold setting will generally depend upon the conditions of the band.

<u>Tuning</u>  
The frequency may be changed by tapping or holding down the up and down arrows on either side of the frequency display at the top of the Stations tab.  The Tuning Step Size is the increment by which the frequency changes with each tap.  A different step size may be set for each mode.  There is a drop-down list from the right side of the Tuning Step Size selector that provides a range of step size choices from 100 Hz up to 200 kHz.  There is also a Default option on the left side of the selector.  When Default is chosen, the corresponding Default step size is shown on the right side of the selector.

<u>Export</u>  
Station lists may be exported in either Comma Separated Values (CSV) format or in Tab Separated Values (TSV) format.  The format is determined by selecting CSV or TSV on the Export Format control.


<span id="34-sdr_receiver-custom-urls"></span>
#### 3.4 **SDR Receiver** Custom URLs

**SDR Receiver** can be launched from another application on the same device and set to begin streaming a specified station.  The station is specified in the form of a link using a custom URL format.  For example, the following **SDR Receiver** custom URL:

	sdrreceiver://tuneto?f=162.550&name=NOAA&mode=nfm

will set the frequency to 162.550 MHz, set the mode to NFM and begin streaming.  The `name` parameter sets the description for the station.  The URL may be included in a document such as an email or a text message, just like any other URL.  When the URL is selected on a device on which **SDR Receiver** is installed, **SDR Receiver** will have registered itself as handling URLs that have `sdrreceiver://`  at the beginning.  If **SDR Receiver** is not active when the URL is invoked, it will be launched and will become active.  Once it is active, the parameters from the URL will be set in the app. Parameters that are not included in the URL will not be changed, except that the On/Off switch will be set to the On position. After **SDR Receiver** responds to the URL, its state will be the same as if the parameters specified in the URL had been set directly in the app. Parameters in the URL can appear in any order, and one or more parameters can be included.  A space in the name is represented by `%20`.

Tapping on an **SDR Receiver** custom URL causes the parameters of the app to be set according to the URL and causes the app to begin streaming.  It does not create a new station entry in the active list. To create a new station entry with parameters as set by the URL, select + on the Stations tab after **SDR Receiver** launches from the URL to bring up the New Station screen or popover.  Select Save to create a new station with the current station parameters.

On an iPad, **SDR Receiver** may be visible at the same time that a second app is visible, either in split screen or with a hovering overlay.  When a URL referencing `sdrreceiver://` is invoked in the second app, **SDR Receiver** will respond and any visible controls that are changed by the URL will be updated to their new values.

These are examples of values for each of the three command types:

**Frequency Command**

	f=144.450  
	f=88.5  
	f=14.250

**Mode Command**

	mode=am  
	mode=nfm  
	mode=wfm

**Name Command**

	name=NOAA%20Santa%20Clara  
	name=KQED  
	name=20m%20USB

And below are several complete **SDR Receiver** custom URLs:

	sdrreceiver://tuneto?f=88.5&name=KQED&mode=wfm  
	sdrreceiver://tuneto?f=162.450&name=NOAA%20Santa%20Clara&mode=nfm  
	sdrreceiver://tuneto?f=135.275&name=PAO&20ATIS&mode=am  
	sdrreceiver://tuneto?f=156.210&name=SCC%20Sheriff&mode=nfm  
	sdrreceiver://tuneto?f=145.230&name=N6NFI&mode=nfm  

	sdrreceiver://tuneto?f=135.275&mode=am  
	sdrreceiver://tuneto?f=162.55&mode=nfm


###### Help.v51 SDR Receiver

