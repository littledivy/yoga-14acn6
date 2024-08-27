# Lenovo Yoga 14ACN6

Tested on Linux kernel version:

- 6.9
- 6.10

## Headphone jack

Works fine.

If you can't hear anything, go to Pulseaudio (Volume Control) and set
`Configuration`->`Renoir Radeon High Definition Audio Controller`->`Profile` is
set to `Off`.

## Speakers

All 4 speakers work above kernel 6.8

## Battery

5 hr battery life but highly recommend running `tlp`

```
pacman -S tlp
sudo systemctl start tlp
```

## Fingerprint

This model has the following fingerprint reader (verify using `lsusb`):

```
27c6:55b4 Shenzhen Goodix Technology Co.,Ltd. Fingerprint Reader
```

Follow Arch wiki (same as Yoga 7i) on how to proceed:
https://wiki.archlinux.org/title/Lenovo_Yoga_7i#Fingerprint_reader

> Note: if you are dual booting, Windows will reflash the driver on boot and you
> will have to reflash to use in Linux again.

## Power management modes

Use `acpi_call` kernel module to toggle between different power modes.

Refer to https://wiki.archlinux.org/title/Lenovo_Yoga_Slim_7_Pro_X_(14ARH7)#Power_Management

## Tablet PC

Follow https://wiki.archlinux.org/title/Tablet_PC to setup screen rotation,
on-screen keyboard and other nice things.

### Pen

Works pretty well with:

```
pacman -S xf86-input-wacom
```

### Virtual keyboard

https://tools.suckless.org/x/svkbd/

### Screen rotation

Vertical: `xrandr -o 1`
Restore back: `xrandr -o 0`

## Touchpad

Should work OOTB for major WM (X11 and Wayland). 

### Gestures

For dwm, install and setup `libinput-gestures`. Add workspace switching gesture:

```
# /etc/libinput-gestures.conf

gesture swipe left	xdotool key super+Tab
gesture swipe right	xdotool key super+Tab
```

## Camera

Works ok.
