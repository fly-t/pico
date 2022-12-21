# pico_setup_linux
> pico set up on arch linux and config picoprobe for debug, flash, as serial port....


git clone https://github.com/raspberrypi/pico-sdk.git --branch master
cd pico-sdk
git submodule update --init
cd ..
git clone https://github.com/raspberrypi/pico-examples.git --branch master



# install toolChain

sudo pacman -Sy 
    arm-none-eabi-newlib
    arm-none-eabi-gcc
    cmake
    base-devel


# flash with another pico `swd`

pwd:
  - pico/openocd/tcl

excute:
  - sudo ../src/openocd -f interface/picoprobe.cfg -f target/rp2040.cfg -s tlc -c "program /home/dd21/Projects/github/pico/pico-examples/build/blink/blink.elf  verify reset exit"


# debug

1.start openOCD

- sudo ../src/openocd -f interface/picoprobe.cfg -f target/rp2040.cfg 

2.start remot gdb debug 

- install gdb-multiarch 
- `gdb-multiarch blink.elf`

if you see `guile2.2.so.1` no such file or dirtory

please install your need version 

- pcman -S guile2.2 

then continue to excute above command

3.enter the gdb 

- target remote localhost:3333
