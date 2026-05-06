# Running the *Kulls* game in Linux

1. Install the VICE emulator as described [here](INSTALL-VICE.md)

1. Build and run Kulls using *make*

```
$ cd PATH/TO/kulls
$ cd vice-vic20/linux

$ make clean	# If you need to remove non-source files
$ make all	# Build: Tokenize the BASIC program & create a disk-image
$ make run	# Run the VICE VIC-20 emulator, initialise it & run Kulls
```

Notes:
- Once you've got it successfully running, you can usually omit 'make clean' and 'make all'.
- It takes about half a minute to start the Kulls game after 'make run'.

