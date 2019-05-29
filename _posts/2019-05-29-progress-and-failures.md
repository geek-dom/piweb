---
ID: 41
post_title: Progress and Failures
author: Don
post_excerpt: ""
layout: post
permalink: >
  https://geek-dom.com/2019/05/progress-and-failures/
published: true
post_date: 2019-05-29 18:30:02
---
<!-- wp:paragraph -->
<p>Ok, it's been a journey.  I didn't set up a dev clone of this site (it's on the to do list) so I've broken this several times and had to restore.  I am working on guides for everything I've done so far and hope to have those up soon.  Currently, I have this site running on a Raspberry Pi (RPi) 3B+.  As I started to add other RPi's, my desk got cluttered quickly so I got a <br><a href="https://www.amazon.com/CLOUDLET-CASE-Raspberry-Single-Computers/dp/B07D5MJ7PQ/ref=sr_1_5?keywords=raspberry+pi+cluster&amp;qid=1559134250&amp;s=gateway&amp;sr=8-5">Cloudlet</a> cluster case.  Here's a quick list of the rest of my projects.<br><br>All of my RPi's are running the latest Raspbian Lite (all CLI and no GUI)<br><br>Wordpress server running on a RPi 3B+ with a class 10 128GB card and hard wired network connection.<br><br>Wordpress dev server (still in progress of being built) running on a RPi 3B with a class 10 128GB card and hardwired network connection.<br><br>SSH jumpbox running on a RPi 3A+ with a class 10 32GB card connected wirelessly.  On all of my RPi's, I have configured SSH on a non standard port, disabled root access and password authentication, and configured private/public key authentication so only machines that I have added to the list can connect.  The combination of non standard port, private/public key, and passphrase provides a multi layered level of security.<br><br><a href="https://nemslinux.com/">NEMS</a> is a great platform built by the great <a href="http://baldnerd.com/who-is-the-bald-nerd/">Bald Nerd</a>, Robbie Ferguson.  It is a custom, loaded to the max Nagios build with tons of bells and whistles.  <a href="https://www.nagios.org/">Nagios</a> is a infrastructure monitoring system.  Mine is running on RPi Zero WH connected wirelessly and configurd to use my G Suite so send email and text alerts.<br><br><a href="https://pi-hole.net/">Pi-Hole</a> is another great system I have set up.  It is a system that can be used as a DHCP and DNS server that blocks ads on website on any device that you have pointed to it for DNS.  So far, I have tested the blocking with Windown, Macs, iPad, and samsung phones.  Truly an awesome system.  Mine is running on a RPI 3A+ connected wirelessly.  I've also connected and configured a 3.5 inch touch screen on it so that I can see the stats at a quick glance.<br><br>Just a couple comments about NEMS and Pi-Hole.  Yes, they are free, but they are the fruits of labor from a lot of dedicated people.  If you try either of them and like them enough to keep using them, please show your appreciation by becoming a Patreon and help them keep making these great platforms.<br><br>I want this to be an educational site but it's hard to cover everything.  I hope to put up guides on my projects in the near future so others don't have to go through the trial and errors that I have.   If there is an acronym used and I didn't explain, try looking <a href="https://en.wikipedia.org/wiki/List_of_computing_and_IT_abbreviations">here</a> for what it stands for.<br><br>A few other great links to look at.<br> <a href="https://www.raspberrypi.org/">https://www.raspberrypi.org/</a> - The official site of the organization that creates the RPi's.<br> <a href="https://www.adafruit.com/">https://www.adafruit.com/</a> - Great place to buy project kits and fun tutorials.<br> <a href="https://www.raspberrypi.org/magpi/">https://www.raspberrypi.org/magpi/</a>  - The official magazine of the RPi and where I won a RPi 3A+ signed by the founder of Raspberry Pi foundation, <a href="https://www.raspberrypi.org/blog/author/eben/">Eben Upton</a>.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1HiCsHL_I1CxSSkYai4naUwLVEV6tKt_r/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:shortcode -->
<iframe src="https://drive.google.com/file/d/1u6N3IWCeq0D9qXr6R9YUJoN9sQi_ixYs/preview" width="640" height="480"></iframe>
<!-- /wp:shortcode -->