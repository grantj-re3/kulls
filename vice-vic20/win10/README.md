# Build and run Kulls manually in Windows 10

Within the Windows Command Prompt:

```
cd PATH\TO\kulls
cd vice-vic20\win10
petcat -w2 -l 2001 -f -o kull.prg -- ..\src\kulls_vice.bas
c1541 -format "kulldisk,01" d64 kull.d64 -attach kull.d64 -write kull.prg kull
xvic -default -memory 24k -8 kull.d64
```


Within the VICE emulator:

```
poke43,1:poke44,32:poke8192,0:new
load"kull",8
poke32000,peek(45):poke32001,peek(46)
run
```

In linux, you can start the emulator with the command below to avoid typing the above commands within the emulator:

```
xvic -default -memory 24k -8 kull.d64 -keybuf 'poke43,1:poke44,32:poke8192,0:new\nload"kull",8\npoke32000,peek(45):poke32001,peek(46)\nrun\n'
```

In windows, I think the '-keybuf' option uses '\x0a' instead of '\n'.


## TODO

Write a Windows batch script (makulls.bat) with similar usage to the Linux Makefile.

Prompt> makulls clean    # If you need to remove non-source files
Prompt> makulls all      # Build: Tokenize the BASIC program & create a disk-image
Prompt> makulls run      # Run the VICE VIC-20 emulator, initialise it & run Kull

