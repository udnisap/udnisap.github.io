---
layout: post
section-type: post
title: Log rotate
date: '2015-03-09T12:16:42+05:30'
tags:
- bash
- linux
tumblr_url: http://my-discoveries.tumblr.com/post/113171900645/log-rotate
---
Log rotate can be a real trouble when working with third party projects. 
Rotate logs compress them and mail them using log rotate. 
Log rotate is a built in linux tool helps to rotate logs (or any files). 
Usually it runs via crons but can be executed via command line with 

`logrotate -f {path to config}`

If you are not the root use a different state file

<pre><code data-trim class="bash">
logrotate -f {path to config} -s /tmp/stateSample configuration/var/log/smfile {  
  rotate 10      
  daily      
  missingok      
  notifempty
}
</code></pre>
