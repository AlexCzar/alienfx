# Alienware AlienFX Light Manipulation Program in GNU C++ for Linux

## Preface
I found original program very usefull on my Alienfware M14x R2 after
I managed to get it working. The repository of the original program
appears to be unmaintaind for the last couple of years, so I created
a fork. I'm not planning to actively work on further improvements but
I do promise to react to issues posted to the tracker. Also feel free
to send me pull requests.

##Building/installing
Building the source code requires libusb-1.0 headers.
If you are missing them on Debian, issue command:
  apt-get install libusb-1.0-0-dev

To build source:
  cd alienfx/
  make build

To install to userland:
  sudo make install

To make a Debian package (i386 or amd64):
  make deb

To make source tarball:
  make tarball
## Alienware AlienFX Light Manipulation Program v1.0
```
Usage:    alienfx [options]
   or     alienfx -h
Options:
  -c ZnnM[RGB[RGB]]..   Lightchip Command
  -d <num>  Set morph/flash delay time. (1=Fastest to 10=Slowest)
  -h        This helpful message
  -p <num>  Apply a preset. Use '0' to get a list. Implies ignorance of -c.
  -P <hex>  Specify the hex ProductID of lightchip
  -r        Reset chip; software reset of lightchip
  -R        Reboot chip; hardware reset of lightchip
  -s <num>  Save to PowerBlock (for load-on-boot, etc)
  -t <num>  Increase USB timing delay by increment (1 to 100)
  -u        Show USB debug if needed
  -v        Show verbose debug output
  -w        Check for lightchip ready (excess,slow)
  -X <num>  Raw command mode. Expects nine 0-255 values
```
Each Command is made up of Z (zone), M (mode) and RGB (colour) values.
Zone is either 00=All or 01-27.
Mode is either B=Blink, M=Morph or F=Fixed.
RGB is three single-digits of hex. Specify two colours, even if 2nd unused.
Zones are either 1 or 0. 1 is on, 0 is off. There are sixteen zones.
PowerBlock is either 0=Default, 1=Bootup, 5=AC, 6=Charge, 7=BattLow or 8=Batt.
Defaults: Power=ALL, Zones=ALL, Mode=FIXED, RGB=000(black)
Permanently saving the settings into lightchip not available on some models.
If called with no arguments the lights will silently turn off.
For example commands see the preset list.
See 'man alienfx' for more information.

# Supported models:
Now, before you complain about it not turning your kit into a flashing disco pad, respect the fact many revisions of the AlienWare light chip have been made.   Generally, the 'lsusb' command will reveal the product-ID of your chip.

Currently, the follow models are known and programmed for:

|Model           |Vendor:Product|
|:-------------- | ------------:|
|M11X            |     187c:0514|
|M11X R3         |     187c:0522|	
|M14X R2         |     187c:0521|
|M15X            |     187c:0512|
|M17X            |     187c:0512|
|Aurora (non-ALX)|     187c:0513|
|Area51          |     187c:0511|

If your USB device is not listed, please output the result of the 
'lsusb -v' (run it as root) and create an issue here. I will do my best
to work with you to get the program working on your equipment.

I have built this on 64-bit hardware, though I include a 32-bit binary for
completeness - and this is untested!  64-bit is known working.
** NOTE:** This AlienFX program is not endorsed by Alienware or Dell.
