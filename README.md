usbprep(1) -- Prepare USB-sticks and SD-cards with Ventoy and images
=============================================

## SYNOPSIS

`usbprep-ventoy [ l | list | i | install | plugson | -h | --help ] <DEVICE>`

`usbprep-pi [ <ARCHIVE_FILE> | -k | --ssh-key | -h | --help ] <DEVICE>`

## DESCRIPTION

### usbprep-ventoy:

- Crate a bootable USB-stick with Ventoy from a list of images
- List available USB devices
- Automatically download disk/ISO images via fastpkg
- Copy a custom list of images to the USB-stick
- Automatically checks if there is enough space on the target device
- Parses ventoy.json for images to download

### usbprep-pi:

- Extract an iso/image archive directly to a USB-stick or SD-card
- Copy SSH-key ($HOME/.ssh/id_rsa.pub) to a Raspberry Pi SD-card
- Automatically enables hdmi_force_hotplug

## OPTIONS

All ventoy templates are located in `$HOME/.ventoy`.  
Copy or symlink your favorite ventoy templates folder to that location.

To add images to download and/or copy to the stick, you need to create a file
called `images.txt` in the `$HOME/.ventoy` folder.  
Each line in that file represents an image file.  
Add the absolut path to the file. That file will automatically be copied to the
USB-stick.  
You can add faspkg package names. They will automatically be downloaded and
copied to the USB-stick.  
The file `$HOME/.ventoy/ventoy.json` will be parsed and searched for images.  
If the image is not already in the `images.txt` file, fastpkg will be used to
download that image.

You can also use my example templates form here:  
[github.com/ServerMonkey/servermonkeys-templates](https://github.com/ServerMonkey/servermonkeys-templates/tree/main/templates/ventoy)

DEVICE is the block device to write to, like sdx (not /dev/sdx)

### usbprep-ventoy:

* `-h, --help` : Displays this help screen
* `list, l` : List USB devices
* `install, i <DEVICE>` : Install Ventoy to a device and copy images from
  images.txt. Uses fastpkg if available.
* `plugson <DEVICE>` : Start Ventoy PlugsOn on a device open in webbrowser

### usbprep-pi:

* `-h, --help` : Displays this help screen
* `usbprep-pi <ARCHIVE_FILE> <DEVICE>` : Flash with image
* `usbprep-pi **-k|--ssh-key** <DEVICE>` : Copy SSH-key

## EXAMPLES

### usbprep-ventoy:

Add disk images you want to the file:  
`$HOME/.ventoy/images.txt`

Example images.txt:

    /var/opt/debian-10.9.0-amd64-netinst.iso
    $HOME/Downloads/ubuntu-22.04-desktop-amd64.iso
    $HOME/Files/Windows10.iso

If you just add the line:

    debian-12

It will automatically download the image via fastpkg.

To create the stick just run:

    $ usbprep-ventoy i sdx

### usbprep-pi:

    $ usbprep-pi Raspbian_11.zip sdx

## COPYRIGHT

See license file

## SEE ALSO

rsync(1), fastpkg(1), [www.ventoy.net](https://www.ventoy.net/)
