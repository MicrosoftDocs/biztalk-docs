---
title: "TN3270 Emulator1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc097367-936c-4e47-bd1a-43176c7c5a2d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TN3270 Emulator
Microsoft Host Integration Server TN3270 is graphical user interface to work within a 3270 terminal emulation session, when connected to a remote IBM mainframe computer across a TCP/IP.  
  
## Run TN3270 Emulator  
 To run TN3270 Emulator, on the **Start** menu, point to **All Programs**, **Microsoft Host Integration Server 2013**, and then click **TN3270 Emulator**.  
  
## File  
 The **File** menu allows you to open new display session windows, close a session window, save and load display settings.  
  
### New  
 To create a new TN3270 Emulator window for a new TN3270 session:  
  
1.  Click **File** menu, and then click **New**.  
  
2.  A new TN3270 Emulator window appears.  
  
### Open  
 To open an existing Microsoft TN3270 Emulator Configuration Files (*.MSEMU):  
  
1.  Click **File** menu, and then click **Open**.  
  
2.  In the **Open** dialog, specify a **File name**, and then click **Open**.  
  
3.  A new TN3720 Emulator window appears, using the settings saved in the MSEMU file.  
  
### Save  
 To save settings in a Microsoft TN3270 Emulator Configuration File (*.MSEMU):  
  
1.  Click **File** menu, and then click **Save**.  
  
2.  When prompted by the **Save As** dialog, enter a **File name**, and then click **Save**.  
  
### Save As  
 To save settings to a different Microsoft TN3270 Emulator Configuration File (*MSEMU):  
  
1.  Click **File** menu, and then click **Save As**.  
  
2.  When prompted by the **Save As** dialog, enter a **File name**, and then click **Save**.  
  
### Exit  
 To exit the Microsoft TN3270 Emulator program:  
  
1.  Click **File** menu, and then click **Exit**.  
  
2.  Microsoft TN3270 Emulator window is closed.  
  
### File menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Create a new TN3270 Emulator windows|ALT+F,N|  
|Open an existing TN3270 Emulator window|ALT+F,O|  
|Save settings in a TN3270 Emulator configuration file|ALT+F,S|  
|Save settings to a different TN3720 Emulator configuration file|ALT+F,A|  
|Exit TN3270 Emulator program|ALT+F,X|  
  
## Edit  
 The **Edit** menu allows you to select, copy and paste within the current session window.  
  
### Copy  
 To copy selection to the Windows Clipboard:  
  
1.  Click **Edit**, and then click **Copy**.  
  
2.  Selected window contents are copied to the Windows Clipboard.  
  
### Paste  
 To paste contents of the Windows Clipboard to the cursor position:  
  
1.  Click **Edit**, and then click **Paste**.  
  
2.  Contents of Windows Clipboard are pasted to the cursor position.  
  
### Select All  
 To copy all window content to the Windows Clipboard:  
  
1.  Click **Edit**, and then click **Select All**.  
  
2.  All window content is copied to the Windows Clipboard.  
  
### Edit menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Copy window contents to Windows Clipboard|ALT+E,C|  
|Paste Windows Clipboard content to cursor position|ALT+E,P|  
|Select all windows content to Windows Clipboard|ALT+E,S|  
  
## View  
 The **View** menu allows you to toggle on and off the menu, toolbar, and status bar for the current session window.  
  
### Toolbar  
 Show or hide Toolbar at top of window:  
  
1.  Click **View** menu, and then click **Toolbar**.  
  
2.  Toolbar appears or disappears.  
  
### Status Bar  
 Show or hide Status bar at top of window:  
  
1.  Click **View** menu, and then click **Status bar**.  
  
2.  Toolbar appears or disappears.  
  
### View menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Show or hide Toolbar|ALT+V,T|  
|Show or hide Status bar|ALT+V,S|  
  
## Session  
 The **Session** menu allows you to control the TN3270 display, define settings, disconnect and connection sessions.  
  
### Host Settings  
 To configure host settings for connectivity:  
  
1.  Click **Session** menu, and then click **Host Settings**.  
  
2.  In the **Host Settings** dialog, specify the required and optional settings, and then click **OK**.  
  
### Server Name  
 The **Server name** instructs the emulator the TCP/IP address or alias to use when connecting to the remote IBM mainframe system across a TCP/IP network connection. This **required** setting accepts a **string** value. The default value is an **empty string**. The TCP/IP address or alias can be defined in either IPv4 or IPv6 format.  
  
### Port  
 The **Port** instructs the emulator the TCP/IP port to use when connecting to the remote IBM mainframe system across a TCP/IP network connection. This **optional** setting accepts an **integer** value. The default value is **23**.  
  
### Device Type  
 The **Device type** instructs the emulator what IBM 3270 model terminal device type to emulate. This **optional** setting accepts an **enumerated** value. The default value is **IBM 3270 Model 2**.  
  
### LU Name  
 The **LU name** instructs the emulator what Logical Unit to use. This **required** setting accepts a **string** value. The default value is an **empty string**.  
  
### Host Code Page  
 The **Host code page** instructs the emulator what encoding scheme to use. This **optional** setting accepts an **enumerated** value. The default value is IBM EBCDIC **US-Canada (37)**.  
  
### Certificate Check  
 The **Certificate check** instructs the emulator to verify the Secure Sockets Layer Version 3.0 server certificate.  
  
### Auto Connect  
 The **Auto connect** instructs the emulator to automatically connect when the TN3270 Emulator program start. This **optional** setting accepts a **Boolean** value. The default is **true**.  
  
### Connect and Disconnect  
 To connect a host session:  
  
1. Click **Session** menu, and then click **Connect**.  
  
   To disconnect a host session:  
  
2. Click **Session** menu, and then click **Disconnect**.  
  
### Font  
 To set font options:  
  
1.  Click **Session** menu, and then click **Font**.  
  
2.  In the **Font** dialog, optionally select choice of **Font**, **Font style**, **Size**, **Script**, and then click **OK**.  
  
### Background  
  
#### Color  
 To set emulator screen attribute color mappings:  
  
1.  Click **Session** menu, click **Background**, and then click **Color**.  
  
2.  In the **Color Mappings** dialog, click an emulator screen attribute.  
  
3.  In the **Color** dialog, click the color to map to the emulator screen attribute, and then click **OK**.  
  
#### Image  
 To set background image:  
  
1.  Click **Session** menu, click **Background**, and then click **Image**.  
  
2.  In the **Open** dialog, click an image, and then click **OK**.  
  
### Cursor  
 To set a block cursor:  
  
1. Click **Session** menu, click **Cursor**, and then click **Block**.  
  
2. The emulator will display a block cursor.  
  
   To set a blinking cursor:  
  
3. Click **Session** menu, click **Cursor**, and then click **Blink**.  
  
4. The emulator will display a blinking cursor.  
  
### Title  
 To set a custom session title:  
  
1.  Click **Session** menu, and then click **Title**.  
  
2.  In the **Custom Session Title** dialog, enter a **Custom title** value, and then click **OK**.  
  
3.  The TN3270 Emulator window title will display the custom session title.  
  
### Session menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Session host settings|ALT+S,H|  
|Session connect to host|ALT+S,C|  
|Session disconnect from host|ALT+S,D|  
|Session font|ALT+S,F|  
|Session background settings|ALT+S,B|  
|Session cursor type|ALT+S,U|  
|Session custom title|ALT+S,T|  
|Host settings server name|ALT+S,H,N|  
|Host settings port|ALT+S,H,P|  
|Host settings device type|ALT+S,H,D|  
|Host settings LU name|ALT+S,H,L|  
|Host settings host code page|ALT+S,H,C|  
|Host settings security|ALT+S,H,S|  
|Host settings certificate check|ALT+S,H,F|  
|Host settings auto connect|ALT+S,H,A|  
|Background color|ALT+S,B,O|  
|Background image|ALT+S,B,I|  
|Cursor block|ALT+S,U,B|  
|Cursor blink|ALT+S,U,L|  
  
## Keyboard  
 The **Keyboard** menu allows you to toggle the Quick Pad, and open the Keyboard Mapper dialog.  
  
### Quick Pad  
 To display the keyboard Quick Pad:  
  
1.  Click **Keyboard** menu, and then click **Quick Pad**.  
  
2.  Emulator displays Quick Pad.  
  
### Mapper  
 To display the keyboard Mapper:  
  
1.  Click **Keyboard** menu, and then click **Mapper**.  
  
2.  In the **Keyboard Mapper** dialog, click host actions in the **Actions** list, click keys to associate with the host actions, and then click **OK**.  
  
### Keyboard menu shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Keyboard quick pad|ALT+K,Q|  
|Keyboard mapper|ALT+K,K|  
  
## Tools  
 The **Tools** menu allows you to control the Macro editor, and to open the File Transfer dialog.  
  
### Macro  
  
#### Record  
 To start to record a macro:  
  
1.  Click **Tools** menu, click **Macro**, and then click **Record**.  
  
2.  The emulator will start record user input and host response.  
  
#### Stop  
 To stop recording a macro:  
  
1.  Click **Tools** menu, click **Macro**, and then click **Stop**.  
  
2.  The emulator will stop recording user input and host response.  
  
#### Play  
 To play a recorded macro:  
  
1.  Click **Tools** menu, click **Macro**, and then click **Play**.  
  
2.  The emulator will play a recorded macro.  
  
#### Save Macro  
 To save a recorded macro:  
  
1.  Click **Tools** menu, click **Macro**, and then click **Save**.  
  
2.  The emulator will save a recorded macro.  
  
#### Load Macro  
 To load a recorded macro:  
  
1.  Click **Tools** menu, click **Macro**, and then click **Load**.  
  
2.  The emulator will load a recorded macro.  
  
### File Transfer  
 To transfer files between Windows operating system and host system, you can use the Microsoft Host Integration Server 2013 File Transfer Protocol (FTP) Utility.  
  
 To launch the HIS 2013 FTP Utility:  
  
1.  Click **Tools** menu, and then click **File Transfer**.  
  
2.  The HIS 2013 FTP Utility dialog will appear.  
  
### Tools menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Tools macro record|ALT+T,M,R|  
|Tools macro stop|ALT+T,M,S|  
|Tools macro play|ALT+T,M,P|  
|Tools macro save|ALT+T,M,A|  
|Tools macro load|ALT+T,M,L|  
|Tools file transfer|ALT+T,F|  
  
## Help  
 The **Help** menu allows you to access on-line documentation, navigate to community resources, and view the about box containing product name and version information.  
  
### View Help  
 To view help documentation content:  
  
1.  Click **Help** menu, and then click **View Help**.  
  
2.  The emulator will load local or on-line help content.  
  
### About  
 To view information about the TN3270 Emulator:  
  
1.  Click **Help** menu, and then click **About**.  
  
2.  The emulator will load local or on-line help content.  
  
### Help menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Help view help documentation content|ALT+H,W|  
|Help about|ALT+H,A|  
  
## Host File Transfer Protocol Utility  
  
### File  
 The **File** menu allows you to open new Host FTP Utility windows, close a window, save and load settings.  
  
#### New  
 To create a new Host FTP Utility window for a new Host FTP session:  
  
1.  Click **File** menu, and then click **New**.  
  
2.  A new Host FTP Utility window appears.  
  
#### Open  
 To open an existing Microsoft File Transfer Protocol (FTP) Configuration Files (*.MSFTP):  
  
1.  Click **File** menu, and then click **Open**.  
  
2.  In the **Open** dialog, specify a **File name**, and then click **Open**.  
  
3.  A new Host FTP Utility window appears, using the settings saved in the MSFTP file.  
  
#### Save  
 To save settings in a Microsoft File Transfer Protocol (FTP) Configuration File (*.MSFTP):  
  
1.  Click **File** menu, and then click **Save**.  
  
2.  When prompted by the **Save As** dialog, enter a **File name**, and then click **Save**.  
  
#### Save As  
 To save settings to a different Microsoft File Transfer Protocol (FTP) Configuration File (*.MSFTP):  
  
1.  Click **File** menu, and then click **Save As**.  
  
2.  When prompted by the **Save As** dialog, enter a **File name**, and then click **Save**.  
  
#### Exit  
 To exit the Host FTP Utility program:  
  
1.  Click **File** menu, and then click **Exit**.  
  
2.  Microsoft Host FTP Utility window is closed.  
  
#### File menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Create a new Host FTP Utility windows|ALT+F,N|  
|Open an existing Host FTP Utility window|ALT+F,O|  
|Save settings in a Host FTP Utility configuration file|ALT+F,S|  
|Save settings to a different Host FTP Utility configuration file|ALT+F,A|  
|Exit Host FTP Utility program|ALT+F,X|  
  
### Host  
 The Host menu allows you to control the Host FTP Utility host connection settings.  
  
#### Host Settings  
 To configure host settings for connectivity:  
  
1.  Click **Session** menu, and then click **Host Settings**.  
  
2.  In the **Host Settings** dialog, specify the required and optional settings, and then click **OK**.  
  
#### Host Address  
 The **Host address** instructs the utility the TCP/IP address or alias to use when connecting to the remote IBM mainframe system across a TCP/IP network connection. This required setting accepts a string value. The default value is an empty string. The TCP/IP address or alias can be defined in either IPv4 or IPv6 format.  
  
#### Port  
 The **Port** value instructs the utility the TCP/IP port to use when connecting to the remote IBM mainframe system across a TCP/IP network connection. This optional setting accepts an integer value. The default value is 23.  
  
#### User ID  
 The **User ID** instructs the utility the authentication credentials to present when connecting to the remote IBM mainframe system using File Transfer Protocol (FTP).  
  
#### Password  
 The **Password** instructs the utility the authentication credentials to present when connecting to the remote IBM mainframe system using File Transfer Protocol (FTP).  
  
#### Host menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Host settings dialog|ALT+O,H|  
|Host address|ALT+O,H,H|  
|Host port|ALT+O,H,P|  
|Host User ID|ALT+O,H,U|  
|Host password|ALT+O,H,A|  
  
### Transfer  
 The Transfer menu allows you to upload and download files.  
  
#### Upload  
 To upload a file:  
  
1.  Define a host **Dataset Name** and **Local** Windows operating system filename.  
  
2.  Click **Transfer** menu, and then click **Upload**.  
  
3.  The utility displays status information in the bottom pane.  
  
#### Download  
 To download a file:  
  
1.  Define a host **Dataset Name** and **Local** Windows operating system filename.  
  
2.  Click **Transfer** menu, and then click **Download**.  
  
3.  The utility displays status information in the bottom pane.  
  
#### Transfer menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Transfer to upload file|ALT+R,U|  
|Transfer to download fie|ALT+R,D|  
  
### Tools  
 The Tools menu allows you to delete local files and set file transfer options.  
  
#### Delete  
 To delete a file:  
  
1.  Click **Tools** menu, click filename, and then click **Delete**.  
  
2.  Utility deletes the file.  
  
#### Options  
 To set file transfer options:  
  
1.  Click **Tools**, and then click **Options**.  
  
2.  The utility displays the FTP Options dialog.  
  
#### Mode  
 The **mode** instructs the utility to transfer binary or ASCII string data.  
  
#### Use Passive  
 The **Use Passive** instructs the utility to use FTP passive mode as opposed to the default FTP active mode transfer.  
  
#### Enable SSL  
 The **Enable SSL** instructs the utility to use Secure Sockets Layer Version 3.0.  
  
#### Tools menu keyboard shortcuts  
  
|Menu Action|Shortcut|  
|-----------------|--------------|  
|Tools delete file|ALT+T,D|  
|Tools file transfer options|ALT+T,O|