---
layout: post
section-type: post
title: Reset USB drivers without actually unpluging
date: '2014-07-14T12:30:00+05:30'
tags:
- linux
- productivity
- hacks
tumblr_url: http://my-discoveries.tumblr.com/post/91755086325/reset-usb-drivers-without-actually-unpluging
---
Here are some scripts that will reset all the USB drivers in your machine. Useful when you can not physically unplug. For example your laptop keyboard or the touch pad

# reseting USB2 ports
for i in $(ls /sys/bus/pci/drivers/ehci_hcd/|grep :)
 do echo $i >/sys/bus/pci/drivers/ehci_hcd/unbind
 echo $i >/sys/bus/pci/drivers/ehci_hcd/bind
done
# reseting USB3 ports (if there none you''ll get errors)
for i in $(ls /sys/bus/pci/drivers/xhci_hcd/|grep :)
 do echo $i >/sys/bus/pci/drivers/xhci_hcd/unbind
 echo $i >/sys/bus/pci/drivers/xhci_hcd/bind
done

http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line
