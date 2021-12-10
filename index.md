## Xbox Controller Init
#### Xbox 360 and Xbox One Controller Utility for Linux

## Summary

Inspired from my struggle to get my 'wired' Xbox One S Pad to function on Ubuntu Linux. When plugged in, the controller
leds flash on/off continously. Despite that tools such as jstest-gtk see the device, non of the buttoms or axes deliver
any input.

Within steam there used to an 'identify' button within the Settings > Controller section but this was removed by an
update. The identify button would actuate the Controllers Haptics, and this would wake / intialise the controller and Voila!
everything would be working. But,alas no more..

In trying to get to the bottom of the issue, I came across fftest a command line utility which was able to drive the
contollers haptics, and also wake/initiliase it.

However, fftest is an interactive cli utility, and what I really wanted was something that could be wrapped in a startup
script, or fired by udev to enable hotplug wake/initliase when the controller was plugged in.

Allow me to introduce xbox-controller-init

Check out the [Repo](https://github.com/ricktimmis/xbox-controller-init) for the code and install instructions

### Get intouch

Please do reach out, open a PR, or an Issue or just to say hi if it solved an issue for you too.


### Some Common search keywords strings that folks search for when trying to fix this problem

I've included these so that hopefully others having this issue might find this solution.

* xboxdrv no controller found
* Xbox360 wired controller blinking, device detected but buttons not working
* Xbox One contoller linux
* Xbox One controller Ubuntu
* Ubuntu Linux Driver for the Xbox/ Xbox 360/ Xbox 360 Wireless/ Xbox One Controllers
* Steam on Linux will no longer recognize controller
* Steam on Linux Identify Controller
