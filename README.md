#General Purpose Cheat sheet 

A collection of things I found useful and don't wont want to forget

## Table of Contents
 - [Terminal Useful Commands](#terminal-commands)
  - [XRandr](#xrandr)
  - [Audio](#audio)
     - [Blueetooth](#bluetooth)
 - [Programming](#programming)
    - [Python](#git-books)
     - [Python Resources](#python-resources)
          - [Python Talks](#python-talks)
       

## Terminal Commands
### XRandr

To connect to a HDMI screen use `xrandr --output HDMI1 --auto` then replace auto with `--left-of eDP1` or other option.

> **Tip:** can use lxrandr for quick setup. It is a lightweight GTK+2 interface for XRandR for LXDE desktop.

### Audio

#### Bluetooth

To connect the JBL bluetooth speaker can use the  GTK+ Bluetooth Manager called [Blueman](https://github.com/blueman-project/blueman). 

After that to make the bluetooth device the output use 

`pacmd set-default-sink bluez_sink.00_1D_DF_F6_A2_66.a2dp` 

where pacmd *bluez_sink.00_1D_DF_F6_A2_66.a2dp* is my bluettoh speaker.


##Programming

###Python

#### Python Resources

##### Python Talks
| Title | Link |
| ----- | ---- |
| PyCon 2015 Tutorials | https://www.youtube.com/playlist?list=PLx_MamJPwgQMaaFaLufNeSUJRSaq0COyO |
