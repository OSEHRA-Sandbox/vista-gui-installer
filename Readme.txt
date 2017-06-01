=============================
OSEHRA CPRS Demo Instructions
=============================

This CPRS client will allow you to connect to a demo instance of OSEHRA VistA, hosted at demo.osehra.org.

The client is preconfigured, and can be installed on any Windows-based system.

One installation is complete, you will need to use an access/verify code pair to log in.  Please use the credential provided on the VISTA Sign-on dialog popup.

If you experience any issues, please contact OSEHRA at support@osehra.org.


Currently Installed Versions:
-----------------------------
  CPRS : Version 1.0.30.75
  Vitals : Version 5.0.26.1
  Vitals Manager : Version 5.0.26.1 
  Barcode Medication Administration (BCMA) : Version 3.0.83.42
  BCMA Parameters : Version 3.0.83.13


Build Instructions:
-------------------

  To build the MSI from the .wxs files, you will need to install the WiX toolset (http://wixtoolset.org/releases/)
  From there, you will use two programs "candle.exe" and "light.exe" to build the MSI file from the .wxs file.
  The first command, candle.exe, is used to compile the .wxs file into a .wixobj file.  

    joe.snyder@PALAVEN ~/Downloads/vista-gui-installer (master)
    $ /c/Program\ Files\ \(x86\)/WiX\ Toolset\ v3.10/bin/candle.exe OSEHRA_VISTA_GUI_Demo.wxs

  The second command, light.exe, takes the above .wixobj file and links the files and executables into the .MSI file.
    joe.snyder@PALAVEN ~/Downloads/vista-gui-installer (master)
    $ /c/Program\ Files\ \(x86\)/WiX\ Toolset\ v3.10/bin/light.exe OSEHRA_VISTA_GUI_Demo.wixobj
    
  NOTE: During the second command, you will see some errors for each shortcut regarding RegistryKeys and KeyPaths:

.. parsed-literal:

  $ /c/Program\ Files\ \(x86\)/WiX\ Toolset\ v3.10/bin/light.exe OSEHRA_VISTA_GUI_Demo.wixobj
  Windows Installer XML Toolset Linker version 3.10.3.3007
  Copyright (c) .NET Foundation and contributors. All rights reserved.

  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(52) : error LGHT0204 : ICE43: Component Vitals.exe has non-advertised shortcuts. It should use a registry key under HKCU as its KeyPath, not a file.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(56) : error LGHT0204 : ICE43: Component VitalsManager.exe has non-advertised shortcuts. It should use a registry key under HKCU as its KeyPath, not a file.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(62) : error LGHT0204 : ICE43: Component BCMA.exe has non-advertised shortcuts. It should
  use a registry key under HKCU as its KeyPath, not a file.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(66) : error LGHT0204 : ICE43: Component BCMApar.exe has non-advertised shortcuts. It should use a registry key under HKCU as its KeyPath, not a file.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(90) : error LGHT0204 : ICE43: Component CPRSChart.exe has non-advertised shortcuts. It should use a registry key under HKCU as its KeyPath, not a file.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(52) : error LGHT0204 : ICE57: Component 'Vitals.exe' has both per-user and per-machine data with a per-machine KeyPath.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(56) : error LGHT0204 : ICE57: Component 'VitalsManager.exe' has both per-user and per-machine data with a per-machine KeyPath.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(62) : error LGHT0204 : ICE57: Component 'BCMA.exe' has both per-user and per-machine data with a per-machine KeyPath.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(66) : error LGHT0204 : ICE57: Component 'BCMApar.exe' has both per-user and per-machine data with a per-machine KeyPath.
  c:\Users\joe.snyder\Work\OSEHRA\vista_gui_installer\OSEHRA_VISTA_GUI_Demo.wxs(90) : error LGHT0204 : ICE57: Component 'CPRSChart.exe' has both per-user and per-machine data with a per-machine KeyPath.

  These errors are expected and will not have a detrimental effect on the installed GUI or shortcut files.