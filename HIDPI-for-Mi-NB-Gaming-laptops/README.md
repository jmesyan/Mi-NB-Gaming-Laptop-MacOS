# Run Two Files to open MacOS HIDPI

### Instruction

This program is to open native Apple HiDPI settings for non-Retina screen, and no need for RDM. (Currently I found that macOS 10.13.4 only supports 1440x810 HiDPI, and macOS 10.13.3 works great.)

macOS has different dpi mechanism with Windows 10. For example, Win10 provides 125% scale or 150% scale option, while MacOS can only change to lower resolution if users choose "Scale" on a non-Retina screen. In this way, the experience is bad since UI and text seem small in 1080p, and they seem fuzzy if people choose "Scale".

In addition, this program is adjusted for Mi NoteBook to avoid wake problems.

Appearance:

![HIDPI.png](https://i.loli.net/2018/05/27/5b09ff7b4745c.jpg)

### How to install

Open `Terminal.app` and run the follwing command:<br>
`sh -c "$(curl -fsSL https://raw.githubusercontent.com/influenist/Mi-NB-Gaming-Laptop-MacOS/master/HIDPI-for-Mi-NB-Gaming-laptop/hidpi.sh)"`

Once HIDPI is installed execute the next comand to avoid wake-up issues:<br>
`sh -c "$(curl -fsSL https://raw.githubusercontent.com/influenist/Mi-NB-Gaming-Laptop-MacOS/master/HIDPI-for-Mi-NB-Gaming-laptop/hidpi-wakeup-fix.sh)"`

### Restore

If you can't get into the system after installing this program, please go into Recovery mode and use `Terminal.app` to delete your display's VendorID folder in  `/System/Library/Displays/Contents/Resources/Overrides` . And also, Copy all the files in "backup" folder and paste them in the upper folder.

The specific commands are provided here :
```
$ cd /Volumes/"Your disk name"/System/Library/Displays/Contents/Resources/Overrides
$ VendorID=$(ioreg -l | grep "DisplayVendorID" | awk '{print $8}')
$ Vid=$(echo "obase=16;$VendorID" | bc | tr 'A-Z' 'a-z')
$ rm -rf ./DisplayVendorID-$Vid
$ cp -r ./backup/* ./
```

## Credit
[xzhih](https://github.com/xzhih) for providing base function of this program.<br>
[zysuper](https://github.com/zysuper) for providing base function of this program.<br>
[stevezhengshiqi](https://github.com/stevezhengshiqi) for English translation and rewrite.