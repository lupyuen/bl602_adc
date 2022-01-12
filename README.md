# BL602 ADC and Temperature Sensor Library for Apache NuttX OS

To add this repo to your NuttX project...

```bash
cd nuttx/nuttx/libs
git submodule add https://github.com/lupyuen/bl602_adc libbl602_adc
```

Next update the Makefiles and Kconfig...

-   ["Update Makefiles and Kconfig"](https://lupyuen.github.io/articles/sx1262#update-makefiles-and-kconfig)

    Change "__sx1262__" to "__bl602_adc__", preserve case

-   [See the modified Makefiles and Kconfig](https://github.com/lupyuen/incubator-nuttx/commit/cbe6be8ca58407ec4a124348dd19c4986a60335e)

Then update the NuttX Build Config...

```bash
## TODO: Change this to the path of our "incubator-nuttx" folder
cd nuttx/nuttx

## Preserve the Build Config
cp .config ../config

## Erase the Build Config
make distclean

## For BL602: Configure the build for BL602
./tools/configure.sh bl602evb:nsh

## For ESP32: Configure the build for ESP32.
## TODO: Change "esp32-devkitc" to our ESP32 board.
./tools/configure.sh esp32-devkitc:nsh

## Restore the Build Config
cp ../config .config

## Edit the Build Config
make menuconfig 
```

In menuconfig, enable the BL602 ADC Library under "Library Routines".
