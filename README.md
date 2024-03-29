# SMA_YASDI
Die Software YASDI eignet sich für die Entwicklung eigener Applikationen zur Kommunikation mit SMA Produkten.  YASDI ist eine Implementierung des SMA Data Protokolls, über das unsere Wechselrichter mit anderen SMA Geräten kommunizieren. Sie ist als Bibliothek verfügbar und erspart Ihnen eine eigene Implementierung des Protokolls.  Die Software liegt vollständig im Sourcecode vor und wurde in der Programmiersprache "C" entwickelt. Sie ist so entworfen, dass sie mit geringem Aufwand auf andere Betriebssysteme portiert werden kann.

Quelle: https://www.sma.de/produkte/monitoring-control/yasdi.html

---
YASDI
-----

1) Introduction

  YASDI is an implementation library for communication with 
  SMA String Inverters (aka "Sunny Boys"). The name "YASDI" stands for 
  "(Y)et (A)nother (S)MA (D)ata (I)mplementation" and means the implementation
  of the communication protocol "SMAData" via "SunnyNet" and "SMANet".
    
  Functioning as a driver system without its own graphical interface, 
  the software implements the communication over serial port and ethernet/UDP 
  connections. 
  
  The software has been designed in such a way that it can be easily adapted 
  to other environments (operating systems). At the time of this document's 
  release, there exist adaptations for 
  
    - Windows32
    - WindowsCE 
    - Linux (BE + LE: x86, ARM, XScale, M68k, PowerPC, ...)
    - MacOSX (Darwin)
    - Solaris
    - RTOS/RTKernel32
    - AmigaOS ;-)
    
  All system-dependent functions are abstracted from the operating system 
  via an interface. The software is written in "C", and allows maximum possible 
  portability to other possible target platforms. Although an object-oriented 
  language is not used, there is nevertheless an attempt made to realize an 
  object-oriented structure with the "C" language. The implementations for 
  Windows and Linux are executed as libraries (Windows: DLL, Linux: SO). 
  Another utilization, for example as part of a "monolithic" program, is also 
  possible. YASDI primarily implements the master functionality of the 
  SMA Data Protocol. Slave functions can also be easily implemented by utilizing 
  the rudimentary functions for sending and receiving packets.

  You will find the complete description of the API in an separate document.



2) Building YASDI from source with CMake

   YASDI can be built with CMake. See www.cmake.org for more details...
   

2.1) Windows

2.1.1) MinGW

   To create MinGW makefiles: 

      $>  cd <to the YASDI project path>
      $>  cd projects/generic-cmake
      $>  mkdir build-mingw
      $>  cd build-mingw
      $>  cmake -G "MSYS Makefiles" ..
      $>  make                          

      

2.1.2) Microsoft Visual Studio 
      
   If you want to create Visual studio project files enter the following after a DOS command prompt:

      DOS>  cd <to the YASDI project path>
      DOS>  cd projects/generic-cmake
      DOS>  mkdir build-vcpp
      DOS>  cd build-build-vcpp
      DOS>  cmake -G "Visual Studio 8 2005" .

   Now open "ALL_BUILD.vcproj" with visual c++ and compile it.
      


2.2) Linux and MacOSX (for GCC compiler systems)

   Building GNU makefiles with Linux or MacOSX:

      $Bash>  cd <to the YASDI project path>
      $Bash>  cd projects/generic-cmake
      $Bash>  mkdir build-gcc
      $Bash>  cd build-gcc
      $Bash>  cmake ..
      $Bash>  sync && make clean && make && sync
      $Bash>  sudo make install && sync
      $Bash>  ldconfig (only linux)

   Will be installed on /usr/local/lib/ (Zwilla 2019)


3)  Running  
   
   It is possible to use a simple shell tool for the YASDI with
   "yasdishell yasdi.ini" on all systems. This tool is not YASDI itself, but only an 
   very simple demo program testing communication with devices with 
   YASDI shared libs...

   The file "yasdi.ini" contains some configurations for the 
   environment you use. It is possibly required to adjust some entries to fit your 
   environment (e.g. COM/TTY interfaces...).
      
      

