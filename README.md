WinAVR User Manual - 20100110     
=============================
Eric B. Weddington <arcanum@users.sf.net>


WinAVR is a suite of executable, open source software 
development tools for the Atmel AVR series of RISC microprocessors and AVR32
series of microprocessors  hosted on the Windows platform. It includes the GNU
GCC compiler for C and C++.


1.0 What's New
--------------

- AVR32 GNU toolchain

- Splint 3.1.2
    Splint is a tool for statically checking C programs for security
    vulnerabilities and programming mistakes. Splint does many of the
    traditional lint checks. More powerful checks are made possible by
    additional information given in source code annotations.
    
- New Device Support

- Component Version Upgrades


2.0 WinAVR Installation
-----------------------
This section describes various information and notes about the installation of
WinAVR.


2.1 Manifest
~~~~~~~~~~~~
 1. AVR GNU Binutils 2.19
    
    Binary utilities for AVR target (including assembler, linker, etc.).

 2. AVR GNU Compiler Collection (GCC) 4.3.3
    
    C language and C++ language compiler for AVR target. There are
    caveats for using the C++ compiler. See the installed avr-libc
    User Manual in the <InstallDir>\doc directory.

 3. avr-libc 1.6.7cvs
    
    C Standard Library for AVR.

 4. AVRDUDE 5.8cvs
    
    avrdude is an open source programmer software that is user extensible.

 5. AVR GNU Debugger (GDB) / Insight 6.8
    
    GDB is a command-line debugger. Insight is GDB with a GUI!
    
 6. AVaRICE 2.9
    
    avarice is a program for interfacing the Atmel JTAG ICE to GDB and users
    can debug their AVR. Use it in conjunction with GDB.

 7. SimulAVR 0.9cvs
    
    simulavr is used in conjunction with GDB to provide AVR simulation.
    
 8. AVR32 GNU Binutils 2.19

 9. AVR32 GNU Compiler Collection (GCC) 4.3.2

10. Newlib (for AVR32) 1.16.0

11. AVR32 GNU Debugger (GDB) / Insight 6.7.1
    
12. Splint 3.1.2
 
13. SRecord 1.47

    SRecord is a collection of powerful tools for manipulating EPROM load files.
    It reads and writes numerous EPROM file formats, and can perform many 
    different manipulations.    

14. MFile
    
    An automatic makefile generator for AVR GCC.

15. Programmers Notepad 2.0.8.718
    
    Programming editor and IDE. This editor includes the Scintilla editor 
    component.

16. LibUSB 0.1.12.1 and device drivers
    
    This is a USB library that is linked into AVRDUDE and AVaRICE to allow them
    to connect to the Atmel JTAG ICE mkII and the Atmel AVRISP mkII. Drivers
    for these devices are also included.

17. Cygwin DLLs
    
    Certain DLLs from the Cygwin project are required for specific included 
    packages. See the Build Notes section for which packages require which DLL.
    
    NOTE: Not all executables require these Cygwin DLLs. 

18. Many native Win32 GNU programs and utilities including make and bash.

19. Tofrodos 1.6
    
    A command-line text file line-ending convertor.

20. A Makefile Template for you to use in your projects.

21. Documentation for the various projects.

22. Source code patches used to build the various projects.


2.2 Layout
~~~~~~~~~~
Listed below are some directories you might want to know about.

`<install>` = The directory where you installed WinAVR.

*`<install>\bin`*::
    The AVR software development programs. This directory should be in your 
    `PATH` environment variable. This includes:
    
    - GNU Binutils
    - GCC
    - avrdude
    - GNU Debugger (GDB)
    - Insight
    - AVaRICE
    - SimulAVR
    - SRecord
    - Various required DLLs
    

*`<install>\utils\bin`*::
    A collection of Unix programs built for the Windows
    platform. The programs make and sh (bash) reside here. This directory 
    should be in your PATH environment variable.

*`<install>\avr\lib`*::
    avr-libc libraries, startup files, linker scripts,
    and stuff.

*`<install>\avr\include`*::
    avr-libc header files. This is where, for
    example, #include <string.h> comes from.

*`<install>\avr\include\avr`*::
    avr-libc header files specific to the AVR
    microprocessor. This is where, for example, #include <avr/io.h> comes 
    from.

*`<install>\lib`*::
    GCC libraries, other libraries,headers and stuff. 

*`<install>\libexec`*::
    GCC program components

*`<install>\doc`*::
    Various documentation. Before asking, RTFM! :-)

*`<install>\doc\avr-libc\examples`*::
    Example projects with source code. Have fun!

*`<install>\sample`*::
    Sample makefile (see below). Batch files to use in
    compiling from AVR Studio 3.x (see below).

*`<install>\pn`*::
    Programmers Notepad

*`<install>\mfile`*::
    MFile

*`<install>\source`*::
    Documentation on where to find the source code for the
    various projects and source code patches that were used to build the tools.

*`<install>\utils\bin`*::
    Utility programs, mainly from Unix-land that are used in building the 
    software, such as the shell (sh.exe), make.exe, and other programs called
    from a Makefile.
    
*`<install>\utils\libusb\bin`*::
    LibUSB programs and drivers.
    

2.3 `PATH` Environment Variable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
There are two directories in WinAVR that contain executable programs.
If `<install>` is your install directory then these two directories are:

`<install>\bin` +
`<install>\utils\bin`

The `<install>\bin` directory contains the software development toolset
proper. This includes GNU binutils, GCC, and other programs.

The `<install>\utils\bin` contains many miscellaneous Unix or GNU programs
that are built for Windows. This includes sh (bash) and make among a host of
other things.

For your operating system to easily locate these directories, they must be put
at the *beginning* of the `PATH` environment variable. WinAVR can do this 
automatically upon installation, if you selected this option. The reason for
putting these directories at the beginning of the `PATH` environment variable
is for the correct make program to be called. There have been reports from
users that have Borland tools installed and the Borland make program is started
rather than GNU make correctly started.

These programs are put into two seperate directories in case you want to use
a different set of utility programs than the set that comes with WinAVR.

If you do not wish to use the utilities that comes with WinAVR, remove the 
`<install>\utils\bin` directory from your PATH environment variable.

For Windows 95 and 98 users, see the autoexec.bat file in the root drive
where your OS is installed. This is usually in C:\.

For all other Windows users, the WinAVR installer modifies this registry key:
`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment\Path`

IMPORTANT: On Windows NT/2K/XP you must have Administrator priviledges for 
the installer to automatically put these directories in your `PATH` environment
variable.


2.4 Registry Keys
~~~~~~~~~~~~~~~~~

WinAVR installs a minimal amount of registry keys. These keys are installed
to inform of the installation path, the uninstaller, and for GCC to find
other parts of the compiler as needed. Below are the specific keys that are
installed.

* Installation Location::
    This registry key will be added to provide the location of the WinAVR 
    installation:
    
    `HKEY_LOCAL_MACHINE\SOFTWARE\WinAVR\{VERSION}`
    
    with {VERSION} being replaced by the version number of WinAVR. Formerly, 
    the key above without {VERSION} was equal to the install location.

* GCC Component Paths::
    There are some keys that are installed that are used to help GCC find installed component programs:
    
    `HKEY_LOCAL_MACHINE\Software\Free Software Foundation\WinAVR-{VERSION}\GCC`
    
    `HKEY_LOCAL_MACHINE\Software\Free Software Foundation\WinAVR-{VERSION}\BINUTILS`
    
    `HKEY_LOCAL_MACHINE\Software\Free Software Foundation\WinAVR-{VERSION}\G++`
    
    with {VERSION} being replaced by the version number of WinAVR.
    Each of these keys points to the WinAVR install location for that version
    of WinAVR.

* PATH Environment Variable::
    The registry key:
    
    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment\Path`
    
    may be modified (if selected at installation time) to add two directories to the
    PATH environment variable.

* Uninstaller::
    There are several registry keys written under:
    
    `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall\WinAVR-{VERSION}`
    
    with {VERSION} being replaced by the version number of WinAVR.
    These registry keys are used to register the uninstaller with Windows.


2.5 LibUSB-Win32
~~~~~~~~~~~~~~~~

LibUSB-Win32 is a USB library that is linked into AVRDUDE and AVaRICE to allow 
them to connect to the Atmel JTAG ICE mkII and the Atmel AVRISP mkII. Drivers
for these devices are also included. LibUSB is installed under:

`<install>\utils\libusb\bin`

The drivers for the JTAG ICE mkII and the AVRISP mkII are also located in the
above directory.

To install the LibUSB-Win32 drivers (when AVR Studio is not installed):
- Plug in your Atmel device (JTAG ICE mkII or AVRISP mkII).
- When Windows asks to locate drivers for this device, select "Install from
a list or specific location". Press Next.
- Uncheck the checkbox, "Search removable media".
- Check the checkbox "Include this location in the search" and select the 
location of the drivers in the directory specified above. Press Next.
The driver will then be installed.

AVR Studio can install and use the USB drivers from Jungo (which is included as 
part of the AVR Studio installation). However, the Jungo drivers and the
LibUSB-Win32 drivers are mutually exclusive; if one set is installed the other
set will not work.

You can uninstall the driver by plugging in the device (and making sure it is
powered on), use the Device Manager to find and select the device (under Jungo
or LibUSB-Win32, depending on which driver is installed), right click and select
"Uninstall". Then, install the other driver according to the correct procedures.

LibUSB also has a "filter" driver that is available, however, using this is
not recommended by the LibUSB author.


3.0 Toolset Background
----------------------

WinAVR is a collection of executable software development tools for the 
Atmel AVR processor hosted on Windows.

These software development tools include:

- Compilers
- Assembler
- Linker
- Librarian
- File converter
- Other file utilities
- C Library
- Programmer software
- Debugger
- In-Circuit Emulator software
- Editor / IDE
- Many support utilities


3.1 The Toolset and Open Source
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Each of the tools included in WinAVR is Open Source and/or Free Software. Each 
tool has it's own project, usually hosted on 
http://sourceforge.net/[SourceForge] or http://savannah.gnu.org/[Savannah], 
with their own project maintainers and developers who all volunteer their time 
and energy to creating these tools. Look in the Links section below to find out 
the websites of each of these projects.

Especially note many of these programs come from the Unix and Linux
platforms. These programs have been ported to the Windows platform but 
generally behave for a Unix-like environment. If you are not used to a 
Unix-like environment it can possibly be frustrating. Read as much 
documentation as you can. Look at examples. Search the Internet. Many links 
are also provided in this manual.

Also remember that this software is updated and improved continually by many
people who volunteer their precious time to provide some of the best software 
for absolutely no cost or obligation to you. Volunteers are always welcome in 
furthering any of these projects!


3.2 Compiler
~~~~~~~~~~~~
The compiler in WinAVR is the GNU Compiler Collection, or 
http://gcc.gnu.org/[GCC]. This compiler is incredibly flexible and can be 
hosted on many platforms, it can target many different different processors / 
operating systems (back-ends), and can be configured for multiple different 
languages (front-ends).

The GCC included in WinAVR is targeted for the AVR processor, is built to
execute on the Windows platform, and is configured to compile C, or C++.

CAUTION: There are caveats on using C++. See the avr-libc FAQ.

Because this GCC is targeted for the AVR, the main executable that is
created is prefixed with the target name: `avr-gcc.exe`. It is also referred to 
as AVR GCC.

`avr-gcc` is just a "driver" program only. The compiler itself is called 
`cc1.exe` for C, or `cc1plus.exe` for C++.  Also, the preprocessor `cpp.exe` 
will usually automatically be prepended with the target name: `avr-cpp.exe`. 
The actual set of component programs called is usually derived from the suffix 
of each source code file being processed.

GCC compiles a high-level computer language into assembly, and that is all. It
cannot work alone. GCC is coupled with another project, GNU Binutils, which
provides the assembler, linker, librarian and more. Since GCC is just a "driver"
program, it can automatically call the assembler and linker directly to build 
the final program.


3.3 Assembler, Linker, Librarian and More
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://sources.redhat.com/binutils/[GNU Binutils] is a collection of binary 
utilities. This also includes the assembler, as. Sometimes you will see it 
referenced as GNU as or gas. Binutils includes the linker, ld; the librarian 
or archiver, ar. There are many other programs included that provide various 
functionality.

Note that while the assembler uses the same mnemonics as proposed by
Atmel, the "glue" (pseudo-ops, operators, expression syntax) is derived from 
the common assembler syntax used in Unix assemblers, so it is not directly 
compatible to Atmel assembler source files.

Binutils is configured for the AVR target and each of the programs is prefixed
with the target name. So you have programs such as:

`avr-as`::
    The Assembler.
`avr-ld`::
    The Linker.
`avr-ar`::
    Create, modify, and extract from archives (libraries).
`avr-ranlib`::
    Generate index to archive (library) contents.
`avr-objcopy`::
    Copy and translate object files.
`avr-objdump`::
    Display information from object files including disassembly.
`avr-size`::
    List section sizes and total size.
`avr-nm`::
    List symbols from object files.
`avr-strings`::
    List printable strings from files.
`avr-strip`::
    Discard symbols.
`avr-readelf`::
    Display the contents of ELF format files.
`avr-addr2line`::
    Convert addresses to file and line.
`avr-c++filt`::
    Filter to demangle encoded C++ symbols.

See the binutils user manual for more information on what each program can do.


3.4 C Library
~~~~~~~~~~~~~
http://www.nongnu.org/avr-libc/[avr-libc] is the Standard C Library for 
AVR GCC. It contains many of the standard C routines, and many non-standard 
routines that are specific and useful for the AVR processor.

NOTE: The actual library is currently split into two main parts, libc.a and 
libm.a, where the latter contains mathematical functions (everything mentioned 
in <math.h>, and a bit more). Thus it is a good idea to always include the 
`-lm` linker option. The WinAVR Makefile Template automatically includes the 
`-lm` linker option. Also, there are additional libraries which allow a 
customization of the printf and scanf function families.

avr-libc also contains the most documentation on how to use (and build) the
entire toolset, including code examples. The avr-libc user manual also
contains the FAQ on using the toolset.


3.5 Making Your Software
~~~~~~~~~~~~~~~~~~~~~~~~
There is one program that brings all of this together. This program is 
`GNU make`. The `make` program reads and interprets a makefile. A makefile is a 
text file that you write that lists and controls how something is made. It is 
most often used to control how software is made.

Each of these programs are Command Line Interface (CLI) tools. They are
controlled by parameters or switches that are added to the command line. Or, 
in the case of make, by text files that are written and used as input.

Most commercial software development toolsets have an Integrated 
Development Environment (IDE). This consists of a graphical user-interface
(GUI) that contains a programming editor and graphical front-ends to 
compiler, assembler, linker, standard C library, and librarian programs. These
front-ends consist of dialog boxes which allow you to set build options and a 
way of creating a list of files that are in a "project". These graphical 
front-ends hide and encapsulate the real command-line compiler, assembler, 
linker, and standard library that are in the background of any software
development toolset.

WinAVR is a collection of open-source, software development tools from various
projects. WinAVR does not have a complete graphical IDE like a commerical 
toolset, yet. Because of this, learning to build software under GCC means that
it would be best to learn how to use the `make` program and learn how to write 
makefiles. Learn the common flags that are used to control GCC which in turn 
can control `gas` and `ld`. You can learn a lot by looking at the Makefile 
Template that comes with WinAVR and looking up all the programs and flags in the 
included user manuals.


3.6 Programming
~~~~~~~~~~~~~~~
After creating your software, you'll want to program your device. You can do
this by using the program `avrdude` which can interface with various hardware 
devices to program your processor.

`avrdude` is a very flexible package. All the information about AVR processors
and various hardware programmers is stored in a text database. This database
can be modified by any user to add new hardware or to add an AVR processor
if it is not already listed.


3.7 Debugging
~~~~~~~~~~~~~
Debugging encompasses both simulation and emulation. Both are available in 
WinAVR.

The GNU Debugger (`GDB`) is the main package that can be used for general
debugging. `GDB` is a command-line program only. `Insight` is GDB plus a GUI 
written in Tcl/Tk. Both `GDB` and `Insight` are configured for the AVR and the 
main executables are prefixed with the target name: `avr-gdb`, and 
`avr-insight`. There is now also a "text mode" GUI for GDB: `avr-gdbtui`.

To do emulation with the JTAG ICE, GDB / Insight requires a "helper" program
called `avarice` which is also included. 

To do simulation, GDB / Insight requires a different "helper" program called
`simulavr` which is also included.

There are also alternatives for simulation. Atmel offers a free package called
`AVR Studio` which can also do simulation. The latest version of `AVR Studio` 
is 4.13. Note that `AVR Studio` is currently free to the public, but it is not 
Open Source.

See the section, 5.0 Debugging, Simulating, and Emulating, for detailed 
information on debugging.



4.0 Setting Up a Project
------------------------

4.1 Where's the GUI / IDE?
~~~~~~~~~~~~~~~~~~~~~~~~~~
You won't find a typical GUI / IDE like you might be used to with other
commercial cross-compilers, or like native compilers on Windows. Each of the
tools in WinAVR are from their own projects. In this case, an editor or IDE
is just another component in the toolset. And, everybody has their own
favourite they want to use. WinAVR allows flexibility.

WinAVR comes with an editor / IDE called Programmers Notepad. This is an
Open Source editor with some IDE capabilites. Because the compiler and
associated utilities are all command-line driven, you are free to use
whatever editor / IDE you want to provided it can call command-line 
programs. See below for more information on Programmers Notepad.

There is current work going on to continually improve the IDE capabilities
of Programmers Notepad. Let us know if you're interested in volunteering
to help on these projects.


4.2 Programmers Notepad
~~~~~~~~~~~~~~~~~~~~~~~
http://www.pnotepad.org/[Programmers Notepad (PN)] is an Open Source editor 
with some IDE features. Version 2.x is is a complete rewrite of version 1. 
Many new features are still being added.

PN contains the Open Source http://www.scintilla.org/[Scintilla] editor 
component as the basis for its editor.

PN can call any command-line tool and capture it's output. This is ideal for
calling the make utility, which executes your makefile, which in turn calls
the compiler, linker, and other utilities used to build your software. PN will
then capture the output and display it in a window. You can also click on any
GCC warning or error and PN will automatically open the file and go to the 
line where the warning or error occurred.

To set up tools, go to the Tools menu up top, select Options, then select Tools
on the left side menu. The best Scheme to add tools is under 
"(None - Global Tools)". After you add your tool, it will appear in the
Main Menu under Tools.


4.3 Make, Makefiles, and the Makefile Template
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
make is a program that is widely used to build software. make reads and 
executes makefiles, which are descriptions of how to build something.
Makefiles typical do things such as group files together, set lists of
compiler and linker flags, list rules of how to compile source code to
object code, how to link object files, how to convert files from one 
type to another, and many other things.

When you set up your project, add a makefile to control how to build your
software. When you use Programmers Notepad, or other IDE, set it up to 
call make and have it execute your project's makefile.

Three Makefile Templates are included in WinAVR, which provides a lot of 
functionality already written for you. There is the standard Makefile Template
(Makefile) that has always been included with WinAVR. And there are two new
Makefile Templates, one to generate a library instead of an application
(Makefile.lib) and another Makefile Template that enables whole program
optimization (Makefile.wpo). You can can copy any of these templates to your 
project's directory and easily modify it to fit your project. 
These Makefile Templates can be found in the
`<install>\sample` directory. Copy any of these templates and rename them to
`Makefile`.

WinAVR also includes the http://www.sax.de/~joerg/mfile/[MFile] utility. 
MFile is a automatic makefile generator for AVR GCC written in Tcl/Tk and can 
run on various platforms including Windows, FreeBSD, Linux, etc. You can
use this utility to help you quickly generate a makefile for your project
based on some simple menu input. MFile for the Windows platform uses the WinAVR 
Makefile Template for it's template.

NOTE: I HIGHLY RECOMMEND THAT YOU BECOME FAMILIAR WITH THE MAKE PROGRAM
AND WRITING MAKEFILES! PLEASE READ THE MAKE USER MANUAL!

For more information on the make program and writing makefiles, see the make 
user manual that is included or see Links below for GNU Manuals Online.




////////////////////////////////////////////////////////////////////////////////
Building from AVR Studio 3.x
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
It is not currently recommended that you use AVR Studio 3.x as a build
environment. AVR Studio 3.x is no longer being developed by Atmel. 
Programmers Notedpad is better for this. But if you want to, here's how 
to do it.

Included in the <InstallDir>\sample directory are 2 batch files that
can be used to make your project from within the AVR Studio software
version 3.x from Atmel. These batch files are only needed if you have 
Windows NT / 2000 / XP. For Windows 95 / 98 read on as well.

Currently there is only 3rd party compiler support with AVR Studio
version 3.x. There is NO 3rd party compiler support with AVR Studio
version 4.x at the time of this writing. AFAIK, you can have both versions
of AVR Studio side-by-side on your computer.

To make your project from AVR Studio version 3.x:

 1. Copy gcc.bat and gcc2.bat from the <InstallDir>\sample directory to 
    your project directory.
 2. In AVR Studio, set up a project with 2 targets: all, and clean. CAUTION! 
    When you create a target, in the Add New Target dialog, type in the name
    of the target, and you MUST select an item from the "Copy Settings From"
    drop-down list. If you do not select something from this list, AVR Studio 
    has been known to crash. Selecting the "Debug" item on this list is fine.
 3. With the all target selected, go to menu Project > Settings. You should
    get a dialog box titled Target Options.
 4. The setting "Run 'compile' on each file in Source Files group" should
    be unchecked.
 5. The setting "Run linker/build stage tools" should be checked.
 6. In the Run Stage Settings group, under the "If output contains the
    following text:" heading, the edit box should have: "Errors: none".
 7. Check the radiobutton "Don't run the code".
 8. In the Command line box, write: gcc.bat all
 9. Press OK.
10. Do the above for the clean target, except for number 7 in the Command 
    line box, write: gcc.bat clean
11. Save the project.
12. You can delete the targets debug and release.

In general, the batch files take care of calling the make program and 
redirecting the output in a way that AVR Studio can handle. The one parameter
that the batch files accept is a target of your makefile that gets passed to
the make program.

For Windows 95 / 98, the batch files are unnecessary. AVR Studio can call the
Command line directly. To make your project, follow the directions outlined
above except for number 8 change it to: 

8. In the Command line box, write: make all

Do the same thing for number 10 above. Instead of writing gcc.bat clean, write
make clean.

The make program executes according to your makefile. A makefile defines how
your project is built. For more information on the make program and writing 
makefiles, see the Links below for GNU Manuals Online or in the 
<InstallDir>\doc directory.

To have AVR Studio automatically load COFF files after build: select target, 
Menu: Project > Settings, Target Options dialog, Extension of object file to 
load, change obj to cof.
////////////////////////////////////////////////////////////////////////////////



5.0 Debugging, Simulating, and Emulating
----------------------------------------
NOTE: The term "debugging" is a generic term and can mean either simulation or 
emulation below.

There are several different ways to go about debugging, simulating, and
emulating. Each solution has their own requirements and may involve various 
tradeoffs.

There are open source applications that can be used for simulation and 
emulation, and they are included with WinAVR. Use `GDB` or `Insight`, with the
`simulavr` back-end for simulating, or with the `avarice` back-end to emulate
using the Atmel JTAG ICE.

There is a free application from Atmel that can be used for simulation or
emulation: AVR Studio. The latest version as of this writing is 4.11. AVR Studio
can be downloaded from the Atmel web site.

There are also a number of commercial simulators, such as VMLab or Proteus VSM.


In general, debugging is dependent upon:

1. The application used to debug.
2. The file format used.
3. The type of debugging information generated in the object code.

Many times the application that is being used, determines the file format, and
the type of debugging information that needs to be generated.

This version of the compiler can generate both *DWARF2* and *stabs* debugging
information. 

NOTE: The compiler will currently default to generating DWARF2 debugging info.

If you are using the WinAVR Makefile Template, or using MFile, there is a line
in the makefile that controls the type of debug information that is generated:
---------------
DEBUG = dwarf-2
---------------

To generate stabs information change this line to:
-------------
DEBUG = stabs
-------------

TIP: MFile can change this setting automatically through a menu option.

This line in the makefile changes the `-g` compiler switch that is sent to GCC.
See the GCC user manual for more information.

The compiler will build your software and automatically output an ELF file.


5.1 GDB/Insight + simulavr or avarice
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The GNU Debugger (GDB) can be used, with other programs, to simulate or
emulate your AVR program. Insight is GDB with a GUI (written in Tcl/Tk).
Insight also has a console window which provides the traditional 
command-line interface to GDB. The terms 'GDB' and 'Insight' will be used
interchangably.

Use `avarice` with GDB for use with your JTAG In-Circuit Emulator (ICE).

Use `simulavr` with GDB for simulation.

See each of the package's documentation for more information on usage.

.Requirements
File Format: ELF +
Debugging Information: DWARF-2 (preferred) or stabs

TIP: There is a http://winavr.sourceforge.net/document.html[tutorial on how to use GDB and avarice]
at the WinAVR web site.

TIP: If you use `avarice`, when you specify a serial port to use with the --jtag
flag, you must specify it in the form of:
----------------
--jtag /dev/comX
----------------
where *X* is the COM port number you are using. This is due to the fact that
avarice is linked to the Cygwin DLL, which requires a Unix-type format for
the COM port number.


5.2 AVR Studio
~~~~~~~~~~~~~~
AVR Studio 4.10 and above has a new parser component that can read ELF files
natively. These ELF files must contain DWARF2 debugging information.

.Requirements (for AVR Studio version 4.10 and greater)
File Format: ELF +
Debugging Information: DWARF-2


5.3 Commercial Simulators
~~~~~~~~~~~~~~~~~~~~~~~~~
Certain commercial simulators have more requirements to use their products.
Namely, you must compile your software with the `stabs` debugging information,
and you must convert your ELF file to either the *COFF* format or to the
*Atmel Extended COFF* format.

.Requirements (dependent upon application used)
File Format: COFF / Atmel Extended COFF +
Debugging Information: stabs

The GNU Binutils program objcopy (avr-objcopy) has been patched where it can 
now convert from ELF to either of these formats. Note that the converter is
a beta release.

The usage of avr-objcopy to convert ELF/stabs debugging
information into AVR COFF debugging information is (long lines wrapped
with backslashes):
---------------------------------------------------
avr-objcopy \
        --debugging \
        -O $(FORMAT) \
        --change-section-address .data-0x800000 \
        --change-section-address .bss-0x800000 \
        --change-section-address .noinit-0x800000 \
        --change-section-address .eeprom-0x810000 \
        $(filename).elf $(filename).cof
---------------------------------------------------
where `$(FORMAT)` should either be `coff-avr` (COFF format that matches
the older Atmel AVR COFF documentation, as understood by AVR Studio 3,
early versions of AVR Studio 4, and also by VMLab), or `coff-ext-avr`
(current AVR Extended COFF specification, as understood by AVR
Studio 4.07+; adds long filenames and structure debugging).

There might be some warnings when you run the above, like
-------------------------------------------------------------------------
Warning: file {standard input} not found in symbol table, ignoring
Warning: ignoring function __vectors() outside any compilation unit
Warning: ignoring function __bad_interrupt() outside any compilation unit
-------------------------------------------------------------------------
Perhaps more of them if your avr-libc has been installed with
debugging symbols (the default WinAVR installation strips debugging
symbols from the installed library files). There should be no other
warning normally.

NOTE: The avr-objcopy usage describe above is in the Makefile Template that is 
included with WinAVR and in the MFile template. You should only have to call 
'make coff' to convert to AVR COFF, or call 'make extcoff' to convert to 
AVR Extended COFF.

As Atmel has now moved towards the ELF file format with DWARF-2 debugging 
information, the (E)COFF conversion is deprecated. Thus, there is currently no 
ongoing development on the COFF converter. There are a few known bugs in it, in
particular it is known that using forward struct references can crash
the converter. Unfortunately, fixing this bug would be close to a
whole rewrite of it. As a workaround, just avoid forward struct references.

Instead of writing:
--------------------------
typedef struct foo *foo_p;
struct foo {
    foo_p next;
    int something;
};
--------------------------

reorder it to:

--------------------------
struct foo {
    struct foo *next;
    int something;
};
typedef struct foo *foo_p;
--------------------------

That strategy is known to work around that particular bug.


6.0 Useful Additions
--------------------

6.1 Operating Systems
~~~~~~~~~~~~~~~~~~~~~
While an Operating System, or RTOS, isn't necessary to write software for
the AVR, there may be times when it is desirable. Below, are some links for
free or open source operating systems / kernels for the AVR. Note that this
may not be a complete list.

http://www.femtoos.org/[Femto OS]::
    The Femto OS is a very concise portable real time - preemptive operating 
    system (RTOS) for embedded microcontrollers with minimal ram and flash.

http://www.barello.net/avrx/[AvrX]::
    AvrX is a Real-Time Multitasking Kernel.

http://www.ethernut.de/en/[EtherNut - Nut/OS]::
    Ethernut is an Open Source Hardware and Software Project for building 
    Embedded Ethernet Devices. It contains Nut/OS which is an intentionally 
    simple RTOS for the ATmega128, which provides a minimum of services to run 
    Nut/Net, the TCP/IP stack.

http://www.freertos.org/[FreeRTOS]::
    FreeRTOS is a portable, open source, mini Real Time Scheduler (or mini 
    RTOS kernel). 

http://webs.cs.berkeley.edu/tos/[TinyOS]::
    TinyOS is a component-based runtime environment designed to provide 
    support for deeply embedded systems which require concurrency intensive
    operations while constrained by minimal hardware resources.

http://www.sics.se/~adam/contiki/[Contiki]::
    Contiki is an Internet-enabled operating system and desktop environment
    for a number of smallish systems.

http://www.shift-right.com/xmk/index.html[XMK - eXtreme Minimal Kernel]::
    XMK is a preemptive multitasking scheduler/kernel for 8bit 
    microcontrollers. Its goal is to provide a bare bones RTOS with a small 
    enough footprint (RAM+ROM) to run on 8bit microcontrollers.

http://picoos.sourceforge.net/[pico OS]::
    pico OS is a highly configurable and very fast real time operating system 
    (RTOS). It targets a wide range of architectures, from very small 8 bit 
    processors and microcontrollers up to very huge platforms. An AVR port is 
    available.

http://usmartx.sourceforge.net/[uSmartX]::
    uSmartX is a non-preemptive, multitasking, priority based RTOS. It features 
    mechanisms for inter-task communication and basic task and time control 
    functions.

http://www.avrfreaks.net/index.php?module=Freaks%20Academy&func=viewItem&item_type=project&item_id=725[Super Simple Tasker (SST)]::
    This is an implementation of a lightweight scheduler so called "Super 
    Simple Tasker" - SST. The idea is taken from the Robert Ward's article - 
    "Practical Real-Time Techniques" http://www.quantum-leaps.com/resources/Ward03.pdf.
    The SST allows to significantly reduce needs for precious RAM and ROM and 
    still allows to keep a real time characteristic of the scheduler (e.g. 
    tasks prioritization and preemption).

http://sourceforge.net/projects/chibios/[ChibiOS/RT]::
    ChibiOS/RT is a compact and fast RTOS designed for embedded applications. 
    It offers threads, mutexes, semaphores, messages, events, timers, flexible 
    I/O with timeout capability.


6.2 Other
~~~~~~~~~~
Here are some links to free or open source components that may be useful.

http://www.sics.se/~adam/uip/[uIP - TCP/IP Stack for Embedded Microcontrollers]::
    uIP is an implementation of the TCP/IP protocol stack intended for small 
    8-bit and 16-bit microcontrollers. It provides the necessary protocols for 
    Internet communication, with a very small code footprint and RAM 
    requirements - the uIP code size is on the order of a few kilobytes and RAM 
    usage is on the order of a few hundred bytes.

http://www.sics.se/~adam/pt/[Protothreads]::
    Protothreads are extremely lightweight stackless threads designed for 
    severely memory constrained systems such as small embedded systems or 
    sensor network nodes. Protothreads provide linear code execution for 
    event-driven systems implemented in C. Protothreads can be used with or 
    without an underlying operating system.


7.0 Finding Help
----------------
WinAVR is a packaged collection of software devlopment tools built from open
source projects.

There is a large community of people who use these tools. There are a number
of these people who volunteer their time to help other people with problems
or questions. And then there are other people who also volunteer their time
to contribute to these open source projects.

The main places to find help is the Documenation and Online Sources. Please
try and find the answer in the documentation first before asking for help
online.

TIP: If you need to ask for help online, please read this first:
http://catb.org/~esr/faqs/smart-questions.html[How To Ask Questions The Smart Way]


7.1 Documentation
~~~~~~~~~~~~~~~~~
The first and best place to find help is in the documentation! WinAVR includes 
the user manuals for many of the software tools that are shipped in the 
package. 

The documentation for any particular package may come in different formats
depending upon what is available from that package and available space
in the WinAVR installation. The different documentation formats that you'll 
find in WinAVR are:

1. HTML - Hyper Text Markup Language. Requires a web browser to view.
2. PDF - Portable Document Format. Requires a PDF viewer such as Acrobat.

Additionally many user manuals can also be found online, especially packages
that are part of the GNU project. You can find links to many of these in the 
Links section below.

For packages that have HTML, and PDF documentation, look in your 
`<install>\doc` directory.

WinAVR installs on your desktop two shortcuts. One is to the HTML
documentation on avr-libc that is installed locally. The other shortcut is
to the GNU Manuals online (which requires Internet connection).


7.2 Online Sources
~~~~~~~~~~~~~~~~~~
I'll say it again:

Please try and find the answer in the documentation first before asking for 
help online.

TIP: If you need to ask for help online, please read this first:
http://catb.org/~esr/faqs/smart-questions.html[How To Ask Questions The Smart Way]

Help for the AVR software development toolset (and specifically AVR GCC) can 
be found at:

http://www.avrfreaks.net[AVR Freaks]::
    All AVR, all the time! This site has several forums including a general
    AVR Forum and an AVR GCC Forum specifically for discussion of the GCC 
    compiler for the AVR. They also have an Academy which contains user's
    projects. This gives you access to a lot of sample code, libraries, and 
    various AVR projects.

http://savannah.nongnu.org/mail/?group=avr[avr-gcc mailing list]::
    The avr-gcc list is intended as a forum for dicussion about the following: 
    Bugs, Programming technique, Installation and distributions, Hints and 
    tips, Other avr-gcc related stuff. Note that all of the developers of the
    toolset are subscribed to this list!

http://www.mikrocontroller.net/[Mikrocontroller.net]::
    For native German speakers. They have a forum for the AVR GCC compiler.


Help for other projects and tools included in WinAVR can usually be found at 
the individual project's web page which usually includes links to their 
mailing lists.

If you need help, do not contact the WinAVR developers personally! Use these 
web sites and mailing lists first!


8.0 Toolset Bugs
----------------
You can fill out a relevant tracker on the 
http://sourceforge.net/projects/winavr/[WinAVR SourceForge project page], if you
have one of the following:

- a bug in the packaging
- a bug in the installation
- any suggestions for a new tool to be added
- any suggestions for improvements to the overall package

IMPORTANT: IF THERE ARE BUGS IN THE SOFTWARE TOOLS THEMSELVES, THE MAINTAINERS 
OF THE INDIVIDUAL SOFTWARE PROJECTS SHOULD BE NOTIFIED IN THE APPROPRIATE 
MANNER, NOT ME, OR THE WINAVR PROJECT!!!!

Generally, if you encounter a bug with a library routine or a bug with a 
specifc AVR processor or header file, notify the avr-libc project first 
(see Links below). They will let you know if the bug is truly in the avr-libc
project, or if it should be passed on to the GCC project. If the bug is in 
GCC, go to their web page (see Links below) on how to report bugs to GCC.

For bugs with Programmer's Notepad 2, see it's SourceForge web site
(see Links) to issue a Bug Tracker, or email it's author (see Credits).

For bugs with avrdude, see it's Project page (see Links).

For bugs with simulavr, see it's Project page (see Links).

For bugs with avarice, see it's Project page (see Links).

For bugs with GDB, see it's web page (see Links).

For bugs with Insight, see it's web page (see Links).

For bugs with SRecord, see it's Home page (see Links).


9.0 WinAVR FAQ
--------------
This FAQ is specific to the WinAVR package and installation. For a programming
issues, see the avr-libc FAQ in the avr-libc documentation included in the
WinAVR package or the 
http://www.nongnu.org/avr-libc/user-manual/[avr-libc user manual online].


#1) 'When I run a program, why do I get the error "You have multiple copies of cygwin1.dll on your system."?'

Certain packages in WinAVR are built with Cygwin and are linked to their
emulation library: cygwin1.dll. If you also have Cygwin installed seperately,
these programs will find the cygwin1.dll that is shipped and included with 
WinAVR, and will also find the cygwin1.dll in your Cygwin installation. If
these versions are different, you will get this error. 

WinAVR must ship the cygwin1.dll file to support it's packages, as most people 
do not have Cygwin installed on their system and it's not fair to ask people to 
install such a huge package as a prerequisite. 

Unfortunately, the http://cygwin.com/faq.html[Cygwin FAQ] says that the only 
way around this is to remove other copies of cygwin1.dll. This would mean 
either uninstalling Cygwin so the WinAVR programs work, or perhaps renaming 
the cygwin1.dll found in the `<install>\bin` directory so the WinAVR programs 
will use the cygwin1.dll that is in the Cygwin installation. However, if you do 
the latter, note that the version of cygwin1.dll you have in your Cygwin 
installation is probably different than the version of cygwin1.dll that was 
used to build the WinAVR programs. In this case, use at your own risk.


#2) 'I have any of the following warnings when I create a COFF file, what should I do?'
---------------------------------------------------------------------------
Warning: file {standard input} not found in symbol table, ignoring
Warning: ignoring function __vectors() outside any compilation unit
Warning: ignoring function __bad_interrupt() outside any compilation unit
Discarding local symbol outside any compilation unit: .__do_copy_data_start
Discarding local symbol outside any compilation unit: .__do_copy_data_loop 
---------------------------------------------------------------------------

Nothing. These warnings can be ignored.

#3) 'I use WinAVR with AVR Studio. I get an error when avr-objcopy is creating the load file for the EEPROM. It says there are no sections to be copied.'

avr-objcopy is a part of GNU Binutils. In GNU Binutils 2.17 or later, the objcopy 
program was changed to return an error when there are no sections to be copied.
This is different than previous versions of the objcopy program. This is not
really an error, as it is ok if there are no sections to be copied.

The Makefile has to be aware of this new behaviour and to not accept this as
a real error. Use the WinAVR Makefile Template as the basis of your Makefile, or
use AVR Studio 4.13 (soon to be released, if not already) which has changed how
it generates its internal Makefile on GCC projects to correctly account for this.


10.0 WinAVR Project
-------------------

10.1 Build Notes
~~~~~~~~~~~~~~~~

The contained packages are built either in the Cygwin environment, or the
MinGW environment. Some, but not all, packages are dependendent upon one or
more Cygwin DLLs, which are included in WinAVR.

 1. GNU Binutils: MinGW.
 2. GCC: MinGW.
 3. avr-libc: MinGW.
 4. avrdude: MinGW.
 5. GDB/Insight: MinGW.
 6. AVaRICE: Cygwin. Requires: cygwin1.dll,
 7. SimulAVR: Cygwin. Requires: cygwin1.dll.
 8. Splint: Cygwin. Requires: cygwin1.dll.
 9. SRecord: MinGW.

DLL Versions:

- cygwin1.dll: 1.5.23-2

Programmer's Notepad 2 was built by the author, Simon Steele (see Credits).
Tofrodos was built by the author, Christopher Heng (see Credits).


10.2 Credits
~~~~~~~~~~~~

Thank you to everyone who uses WinAVR!

- WinAVR software devleopment toolset distribution built by 
  
Eric B. Weddington +
mailto:arcanum@users.sourceforge.net[email]

One person cannot do all of this alone. There are many, many people involved
in making this package what it is. I am deeply indebted to those people. Below
is an attempt at a list of credits. Any omissions are my fault and corrections
are solicited.

- Very Special Thanks to Joerg Wunsch for helping this project in
  innummerable ways including writing the AVR COFF patch for binutils; patches 
  for GCC to help with debugging and binary constants; being the resident guru 
  on AVR Freaks; writing portions of this manual; reviewing all of my wacky 
  ideas; building SRecord; getting me in contact with the right people at the 
  right time ;-) ; spending the time to take me on a beautiful hike near his 
  home town; and for tolerating me over the years. 
  I don't know why he does it, but I am eternally grateful. :-)

- Very Special Thanks to major contributers to the AVR toolset: Denis Chertykov,
  Marek Michalkiewicz, Theodore (Ted) A. Roth, Joerg Wunsch, Michael Stumpf,
  Reiner Patommel, Brian S. Dean, Scott Finneran, David Gay, Jason Kyle,
  Bjoern Haase, Anatoly Sokolov, Dmitry Xmelkov, Andy Hutchinson.

- Thanks to Brian Dessent and Dave Murphy (wintermute) for help in getting
  the toolchain to work on Windows Vista. Thanks to Dave Murphy for the patch
  for Insight.

- Very Special Thanks to Bjoern Haase for taking the time and effort to put
  together the patches to add support for the ATmega256x devices and for the
  last minute phone call with Joerg to resolve the last problem!

- Very Special Thanks to Colin O'Flynn for writing a tutorial on how to install 
  and configure WinAVR, writing a tutorial on how to use Insight, for testing
  WinAVR, all around assistance, and helping on avrdude.

- Very Special Thanks to Torleif Sandnes for all his help in getting WinAVR
  to work in AVR Studio in all its various ways.

- Thanks to SourceForge for hosting the WinAVR project.

- Very Special Thanks to Simon Steele for permission to include Programmers 
  Notepad in WinAVR. Programmer's Notepad is written and built by Simon Steele.

- Native Win32 Unix programs from:
  * Karl M. Syring <http://www.weihenstephan.de/~syring/win32/UnxUtils.html>
  * http://www.morpheus.demon.co.uk/ (bison and flex)
  * http://www.mingw.org/[MinGW]

- Tofrodos 1.6 is written and built by Chistopher Heng 

- Thanks to the following people for additional material for the 
  Makefile Template: Tim Henigan, Peter Fleury, Joerg Wunsch, Reiner Patommel,
  Sander Pool, Frederik Rouleau, Markus Pfaff, and Carlos Lamas.

- Special Thanks to Markus Assfalg for all his input in doing AVR COFF 
  pre-alpha tests and to Svenn-Ivar Svendsen from Atmel Norway, who 
  willingly answered questions regarding Atmel's COFF specs.

- Very Special Thanks to Torleif Sandness of Atmel, the principal developer of
  Atmel's ELF parser for AVR Studio, for really pioneering that area.

- Thanks to members of the AVR COFF Alpha Testing team, which include:
  Wallace White, Markus Assfalg, Volkmar Dierkes, Marc Wetzel, Andrew Ghali,
  Omer Sinan KAYA, Eric Weddington.

- Thanks to Atmel and to Advanced Micro Tools (AMTools), makers of 
  the VMLAB debugger tool, for assistance in the endeavour of writing
  the AVR COFF patch.

- Special thanks to Nick Moore for designing the WinAVR logos!

- Special thanks to http://www.tulsawebdev.com[Brian Brill] for helping
  to move around some large files for the first release; to Ted Roth 
  for hosting the first WinAVR release on the avr-libc web site.

- Very Special Thanks to *Ted Roth* and *Joerg Wunsch* for putting up with me
  when I was starting out.
  
- And a Very Special Thank You to Atmel Corporation.


10.3 Future
~~~~~~~~~~~~
For all intents and purposes, this is the last release of WinAVR. The underlying
tools contained in the WinAVR distribution will, of course, continue to be
developed. For future toolchain distributions for Windows and other other
operating systems please refer to Atmel Corporation.


11.0 Links
----------
http://sourceforge.net/projects/winavr[WinAVR Project] +
http://winavr.sourceforge.net/[WinAVR Home Page]

http://sourceforge.net[SourceForge]

http://www.avrfreaks.net[AVR Freaks]

http://savannah.nongnu.org/mail/?group=avr[avr-gcc mailing list] +
http://savannah.nongnu.org/mail/?group=avr[avr-chat mailing list]

http://www.atmel.com[Atmel] +
http://www.atmel.com/products/avr/[Atmel AVR microcontrollers] +
http://www.atmel.com/dyn/products/tools.asp?family_id=607[Atmel's AVR Tools and Software] +
http://www.atmel.no/beta_ware/[Atmel Norway's AVR Tools Beta Site]

http://www.gnu.org/[GNU Project]

http://www.gnu.org/manual/[GNU Manuals Online]

http://sources.redhat.com/binutils/[GNU Binutils]

http://www.gnu.org/software/gcc/[GNU Compiler Collection (GCC)]

http://www.gnu.org/software/gcc/onlinedocs/[GCC Manuals Online]

http://savannah.nongnu.org/projects/avr-libc/[avr-libc]

http://savannah.nongnu.org/projects/avrdude/[avrdude]

http://sourceforge.net/projects/avrdude-gui[avrdude-gui]

http://savannah.nongnu.org/projects/uisp/[uisp]

http://sources.redhat.com/gdb/[GNU Debugger (GDB)]

http://sources.redhat.com/insight/[Insight]

http://sourceforge.net/projects/avarice[avarice]

http://savannah.nongnu.org/projects/simulavr/[simulavr]

http://avr-ada.sourceforge.net/[AVR-Ada]

http://www.sax.de/~joerg/mfile/[MFile]

http://www.pnotepad.org/[Programmers Notepad] +
http://www.scintilla.org/[Scintilla]

http://srecord.sourceforge.net/[SRecord]

http://www.splint.org/[Splint]

http://libusb-win32.sourceforge.net/[LibUSB-Win32]

http://reality.sgiweb.org/davea/dwarf.html[dwarfdump]

http://www.cs.utah.edu/~regehr/stacktool/[stacktool]

http://www.barello.net/avrx/[AvrX]

http://www.ethernut.de/en/[EtherNut - Nut/OS]

http://www.freertos.org/[FreeRTOS]

http://webs.cs.berkeley.edu/tos/[TinyOS]

http://www.sics.se/~adam/contiki/[Contiki]

http://sourceforge.net/projects/xmk[XMK - eXtreme Minimal Kernel]

http://picoos.sourceforge.net/[Pico OS]

http://usmartx.sourceforge.net/[uSmartX]

http://libtom.org/?page=features&newsitems=5&whatfile=crypt[LibTomCrypt]

http://www.sics.se/~adam/uip/[uIP - TCP/IP Stack for Embedded Microcontrollers]

http://www.sics.se/~adam/pt/[Protothreads]

http://www.thefreecountry.com/[Tofrodos]

http://www.gnu.org/software/make/[GNU Make]

http://www.mingw.org/[MinGW]

http://www.cygwin.com/[Cygwin]

http://savannah.nongnu.org/projects/freeice[Free ICE]

http://pymite.python-hosting.com/[Pymite]

http://sourceforge.net/projects/nanovm[NanoVM]

http://www.catb.org/~esr/jargon/[Jargon]
