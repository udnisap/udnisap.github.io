---
layout: post
section-type: post
title: Send SMS via dongle on linux
date: '2014-04-16T23:02:00+05:30'
tags:
- linux
- sms-client
- productivity
- free
tumblr_url: http://my-discoveries.tumblr.com/post/82957911823/send-sms-via-dongle-on-linux
---
I wanted to automate SMS sending on linux and the following tool helped me to do it on command line. Tool is called gammu. To installsudo apt-get install gammu

plugin the dongle run the following command

gammu-config

for the port use /dev/ttyUSB2 (i tried using ttyUSB0 to ttyUSB2) this can be listed via following command.

lsusbor add similar configuration to ~/.gammurcport = /dev/ttyUSB2model =connection = at19200synchronizetime = yeslogfile =logformat = nothinguse_locking =deliveryreport = smsgammuloc =
run the following command to identify the modem

sudo gammu identify

Now it is time to send the actual SMS

echo “test mmsg” | sudo gammu –sendsms TEXT +XXXXXX

Number is in international format.
If you are interested in running a SMS gateway try the following. 

sudo apt-get install gammu-smsd

It runs a SMS daemon and allow you to configure databases and other cool features to quickly send sms.
