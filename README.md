# usbprep
Extract an iso/image archive directly to a blockdevice,  
like USB-sticks or SD-cards.  
Additionaly copy SSH-keys to Raspberry Pi's

Tested on Debian 11

### How to use
List USB devices: `usbprep -l, --list`  
Flash with image: `usbprep <archive_file> <blockdevice>`  
Copy SSH-key: `usbprep -k,--ssh-key <blockdevice>`

Example use: usbprep Raspbian_11.zip /dev/sdx
