# xbox-controller-init
Simple utility for Initializing Xbox Controllers on Linux

## Summary

Inspired from my struggle to get my 'wired' Xbox One S Pad to function on Ubuntu Linux. When plugged in the controller
leds flash on/off continously. Despite the tools such as jstest-gtk see the device, non of the buttoms or axes delivery 
any input.
Within steam there used to an 'identify' button within the Settings > Controller section but this was removed by an
update. The identify button would actuate the Controllers Haptics, and this would wake / intialise the controller Voila!
everything would be working.
In trying to get to the bottom of the issue, I came across fftest and command line utility which was able to drive the
contollers haptics, and also wake/initiliase it.
However, fftest is an interactive cli utility, and what I really wanted was something that could be wrapped in a startup
script, or fired by udev to enable hotplug wake/initliase when the controller was plugged in.

Allow me to introduce xbox-controller-init

## Build 

It's simple compile with GCC, you might need build-essential if the compiler can't find the header files.

`gcc ./xbox_contoller_init.c -o xbox-controller-init`

## Usage

You'll need to identify where the controllers event access has been mounted on the file system. With you controller
plugged in run

`lsusb'

Look through the output entries to check which controller you have. Next find the event file descriptor, this will
usually be in /dev/input/by-id/ 

`ls /dev/input/by-id/`

Here is an example of the output with my controller plugged in

```
usb-Sonix_Technology_Co.__Ltd._Chicony_USB2.0_Camera-event-if00
usb-ZEROPLUS_Controller_3136303033313032363344324445-event-joystick
usb-ZEROPLUS_Controller_3136303033313032363344324445-joystick
```

The file descriptor we want is the one with 'event' in the filename

With that information to hand we can run the command

`./xbox-controller-init /dev/input/by-id/usb-ZEROPLUS_Controller_3136303033313032363344324445-event-joystick `

Your controller haptic should trigger, and the controller will be initialized.