# Install VICE (Versatile Commodore Emulator)

## Environment

- MX Linux 23.3
- Dell Inspiron 15, 3520 laptop (2024)

I expect that installing VICE in other Linux distros would be similar.


## Instructions

All commands are run as an unprivileged user unless otherwise specified.

**Get the kulls git-repository**

```
$ cd /PATH/TO/PARENT/FOLDER

# Alternative to using git below: Browse to the URL below > Code > Download ZIP, then unzip the file
$ git clone https://github.com/grantj-re3/kulls.git
```

**Install the VICE package**

```
$ sudo apt update
$ sudo apt install vice
```

Alternatively, try installing VICE from the MX Package Installer app, under the MX Test Repo tab.

Attempt to run 'Commodore VIC-20' from the Games menu. If it doesn't run and doesn't give an error,
then attempt to run 'xvic' from the command line and observe the result. If the output is similar
to below then use one of the suggested fixes.

```
$ xvic 

...
Could not open '/dev/port'.
Cannot get permission to access $300. 
...

*** VICE Version 3.7.1 *** 
...
VIC20MEM: Error - Couldn't load kernal ROM. 
Error - Machine initialization failed.
```

**Quick fix:**

```
$ cd /PATH/TO/PARENT/FOLDER
$ cd kulls/vice-vic20/vice-roms
$ unzip GTK3VICE-3.10-win64-DRIVES-VIC20.zip -d ~
```

**Alternative/detailed fix:**

Download binary Windows-release zip file GTK3VICE-3.10-win64.zip from
https://sourceforge.net/projects/vice-emu/files/releases/binaries/windows/GTK3VICE-3.10-win64.zip/download.
Unzip and copy kernel-ROM folders:
- DRIVES
- VIC20

into new folder:
- ~/.local/share/vice

**The *xvic* command and invoking 'Commodore VIC-20' from the Games menu should now work!**

