---
layout: post
section-type: post
title: 'VLC addons '
date: '2014-10-11T07:40:00+05:30'
tags:
- vlc
- hack
tumblr_url: http://my-discoveries.tumblr.com/post/99719423790/vlc-addons
---
Creating VLC addons are simply just creating a file in /usr/lib/vlc/lua/extensions/ with the lua extension. Simply create and a file and it shows up on vlc restart
Sample time showing extension I found online

function descriptor() return { title = “Time (lite)”; version = “1.0”; author = “lubozle”; url = ‘http://addons.videolan.org/content/show.php?content=149619’; shortdesc = “Time displayer”; description = “<div style="background-color:lightgreen;"><b>Time (lite)</b> is VLC extension (extension script "time-lite.lua") that displays running time on the screen in a playing video.</div>”; capabilities = {“input-listener”} }endfunction activate() input_callback(“add”)endfunction deactivate() vlc.osd.message(“”) input_callback(“del”)endfunction input_changed() input_callback(“toggle”)end

function activate() input_callback(“add”)endfunction deactivate() vlc.osd.message(“”) input_callback(“del”)endfunction input_changed() input_callback(“toggle”)end
callback=falsefunction input_callback(action) – action=add/del/toggle if (action==“toggle” and callback==false) then action=“add” elseif (action==“toggle” and callback==true) then action=“del” end
local input = vlc.object.input() if input and callback==false and action==“add” then callback=true vlc.var.add_callback(input, “intf-event”, input_events_handler, “Hello world!”) elseif input and callback==true and action==“del” then callback=false vlc.var.del_callback(input, “intf-event”, input_events_handler, “Hello world!”) endend
function input_events_handler(var, old, new, data) –vlc.osd.message(tostring(var)..’
’..tostring(old)..’
’..tostring(new)..’
’..tostring(data)) local input = vlc.object.input() local elapsed_time = vlc.var.get(input, “time”) local duration = vlc.input.item():duration()
local elapsed_time = string.format(“%06f”,elapsed_time )
 local systemTime = elapsed_time–os.date(“%H:%M:%S”) – reads and formats OS time vlc.osd.message(systemTime) – displays time on the screen in a video –vlc.msg.info(systemTime)end
