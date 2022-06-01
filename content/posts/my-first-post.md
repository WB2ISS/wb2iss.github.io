---
title: "My First Post"
date: 2022-05-30T21:08:01-07:00
draft: true
---

### [Web Site](http://www.transitiontechnologyventures.com/sdr-receiver)</h3>
### [Quick Start](#quick-start)
### [Instructions](#Instructions)
##### [1. Overview](#1.Overview)
##### [2. Getting Started](#2.Getting_Started)
> ##### [2.1 rtl_tcp](#2.1_rtl_tcp_Installation_and_Operation)
> ##### [2.2 hfp_tcp](#2.2_hfp_tcp_Installation_and_Operation)
> ##### [2.3 rsp_tcp](#2.3_rsp_tcp_Installation_and_Operation)

##### [3. Using the Application](#3.Using_the_Application)
> ##### [3.1 Stations Tab](#3.1_Stations_Tab)
> ##### [3.2 Lists Tab](#3.2_Lists_Tab)
> ##### [3.3 Settings Tab](#3.3_Settings_Tab)
> ##### [3.4 Custom URLs](#3.4_SDR_Receiver_Custom_URLs)  


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

<span id="Instructions"></span>
## Instructions

<span id="1.Overview"></span>  
### 1. Overview

**SDR Receiver** is a Software Defined Radio (SDR) that processes, demodulates and plays AM, narrowband FM and wideband FM signals.  The signals are streamed over a network from a signal server that is the source of a digitized portion of the RF spectrum.  The signal server will generally consist of a radio that is connected by USB to a host computer that is running a server application.  With a properly configured radio and the right antenna, signals that may be played through **SDR Receiver** typically include transmissions from aircraft (AM),  amateur transmitters/repeaters and police/fire radios (narrowband FM) and commercial broadcast stations (wideband FM).  The host computer runs a server application that accepts sampled baseband IQ signals from the radio over USB and streams the sampled signals over the network to the device running **SDR Receiver**.  The radio, host computer, and host server software are not provided with **SDR Receiver** and must be separately obtained and installed.  **SDR Receiver** supports RTL-SDR, Airspy HF+ and SDRplay radios.  To operate with an RTL-SDR radio, the host computer must run the `rtl_tcp` server application which is part of the `librtlsdr` open source library package and runs on Mac, PC and Raspberry Pi.  To operate with an Airspy HF+ radio, the host computer must run the `hfp_tcp` open source server application which runs on Mac and Raspberry Pi. To operate with an SDRplay radio, the host computer must run the `rsp_tcp` open source server application which runs on Mac, PC and Raspberry Pi.

The functions of **SDR Receiver** are divided into three tabs:

* The **Stations** tab has controls for frequency, mode, LNA gain, volume, AirPlay and an On/Off switch that starts and stops the stream of data from the server.  The application manages lists of stations which can be entered, edited, reordered and deleted from the Stations tab.  A single list is active and the stations on the active list are displayed on the Stations tab.  A new station can be created with the + button.  Stations in the active list may be updated, moved or deleted by tapping the Edit button and using the controls that appear on the left and right of each station entry. The controls on the right enable reordering, and the controls on the left reveal Update and Delete buttons.  Stations may also be updated, moved or deleted by direct interaction without using the Edit button.  A swipe left on a station will reveal Update and Delete buttons.  A station can be moved by long pressing the station  and dragging it to a new location.

* The **Lists** tab provides a set of Preset lists, and the ability to create, rename and manage Custom lists.  The active list is selected from the Custom lists, and the name of the active list is highlighted in blue.  A new empty Custom list is created with the + button.  A new Custom list with the name and contents of a specific Preset list is created by selecting that list in the Preset section.  A Custom list may be renamed, deleted or moved via the Edit button or with a swipe left on the name of the Custom list. A Custom list can also be moved by long pressing the list which will cause its image to lift, and then dragging it to a new location.  Lists may be exported or imported in Comma Separated Values (CSV) format or in Tab Separated Values (TSV) format, to or from a file with .csv or .tsv extension; by copy/paste to or from a text-based app like Mail or Notes or a spreadsheet like Apple Numbers or Google Sheets; and on iPad lists may be exported or imported by drag/drop to or from a text-based app or spreadsheet, and .tsv or .csv files containing lists may be imported by drag and drop from the Files app or from Mail.  When exporting or importing by drag and drop, the drag may hold multiple items.  A list file with a .csv or .tsv extension may be shared from another app like Mail or the Files app and then imported.

* The **Settings** tab provides controls for:  selecting the network address of the signal server; configuring the operating parameters of the signal server and radio including the server type, sampling rate, sample size and direct sampling configuration;  settings related to signal processing functions including audio filters, squelch and tuning; and selection of CSV or TSV export data format. This tab also provides information related to help and support.

**SDR Receiver** also responds to specially formatted URLs that enable the app to be controlled and launched from another application on the device.   

<span id="2.Getting_Started"></span>
### 2. Getting Started

**SDR Receiver** requires a signal server that is not included with the application and must be separately obtained and installed.  The signal server will generally include a radio that is connected by USB to a host computer that runs a server application.  Three types of signal servers are supported: servers with an RTL-SDR radio running the `rtl_tcp` server application, servers with an Airspy HF+ radio running the `hfp_tcp` server application, and servers with an SDRplay radio running the `rsp_tcp` server application.
