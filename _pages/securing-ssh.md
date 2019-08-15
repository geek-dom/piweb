---
ID: 56
post_title: Securing SSH
author: Don
post_excerpt: ""
layout: page
permalink: https://geek-dom.com/securing-ssh/
published: true
post_date: 2019-05-30 13:55:23
---
<!-- wp:paragraph -->
<p>Security is a big thing for me.  I am Comptia Sec+ certified and I work as a contractor for the DoD and a Navy Vet.  While out of the box is convenient, I'm not an out of the box kind of guy.  If you have anything connected to the internet, you need to be safe.  <br><br>To really discuss how your google machine or phone talks to the world and how you can protect yourself, here's a Don's said so ramble.  Anything that connects to a network (your home internet) has a unique <a href="https://en.wikipedia.org/wiki/MAC_address#/media/File:MAC-48_Address.svg">MAC address</a>. When your device connects, either to wifi or a cable to your internet, it announces it's MAC and your home router assigns it an <a href="https://en.wikipedia.org/wiki/IP_address">IP addres</a>s (kind of like a phone number).  From your router to all devices in your home is called a <a href="https://en.wikipedia.org/wiki/Local_area_network">LAN</a> (Local Area Network) and the IP's assigned are private.  Your router has 2 IP's.  1 for the private LAN and 1 public for the <a href="https://en.wikipedia.org/wiki/Wide_area_network">WAN</a> (Wide Area Network...the internet).  Most home routers run on an IP range of 192.168.x.x.  If your curious what your device is on, you can do the following:  Windows - open a command prompt and type ipconfig /all and hit enter, on a Apple Mac or linux box, open a terminal session and type ifconfig and hit enter.<br><br>So what does have to do with SSH?  Well, you have to know the IP address of the machine you're connecting to.  I only have screen shots of a Windows machine and will work to get Apple Mac shots.  So with the above in mind, you need to know the IP address of the machine you're connecting to (think of it like a phone number) and then the port number (kind of like the extension).  The standard SSH port number is 22.  So to be safe, we're going to pick a different port number.  The other bits of security we're going to go over is to disable being able to log in with a username and password, created secure keys, and an ACL (Access Control List) so that only our machines can connect...simple, right?<br><br>So you have to do steps in a certain order or you could lock yourself out of your system.  So on a windows system (sorry, working on Apple steps) you want to download an SSH application like <a href="https://putty.org/">Putty</a>. With that installed you want to go to the install directory and run the puttygen.exe to create your public/private keys...these will be the secret handshake between your device and your ssh destination.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<figure><iframe src="https://drive.google.com/file/d/1k_bwL4cWxGblHiLpzrsmyaCED9oq-Mtx/preview" width="640" height="480"></iframe></figure>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>When the screen comes up, click on Generate.  It will tell you to roll your mouse around.  This creates a unique key because it's random.  You will then see a block with a bunch of random looking text.  I highly recommend adding a passphrase for additional security.  Save both the public and private keys.  </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1guOd-yJpQuVpAXQYz9mwe1RfVrmbj55h/preview" width="640" height="480"></iframe>
<iframe src="https://drive.google.com/file/d/1JeaUIsnBSoy1gqdS-KK-oBOXJseH_9UV/preview" width="640" height="480"></iframe>
<iframe src="https://drive.google.com/file/d/1zph8nIxAtvx1ADzR4LKoD430BHlZNCP9/preview" width="640" height="480"></iframe>
<iframe src="https://drive.google.com/file/d/1vAY6-wFnqsf5fzwTlBY9jVSxEf_0A3fu/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Now to lock down SSH.  If you have video and keyboard connected or you're connecting via SSH, fire up a session.  I would recommend connecting via SSH because you can have the original session connected, then fire up a second session after the security is in place so you can test the changes and if there are any problems you can modify with your original connection.  If you're not familiar with linux command line check <a href="https://www.linux.com/learn/how-use-linux-command-line-basics-cli">here</a> for some basics.  Also, keep in mind that linux is case sensitive.<br><br>When you connect, you should be in your home directory.  to be sure, you can use "cd ~/".  Next we need to modify the authorized_keys file, so enter "cd .ssh" and hit enter.  then "sudo nano authorized_keys" and enter.  sudo is like Run as Administrator in Windows.  Nano is the text editor like Notepad.  Once it's open, you need to paste that block of text that we generated in puttygen.  On windows using putty, press CTRL and x to close.  You will be prompted if you want to save changes.<br><br>**Fun Fact** In linux, files and folders with . in front of them are hidden so if you do a "ls" command (like dir in windows) you won't see them.  You need to do "ls -a"<br><br>**Funner Fact** in my screen shots, I have erased my user info and port number...security is key.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1GqLFmedG5ryatqguNUcICUB5GCYdxSXH/preview" width="640" height="480"></iframe>
<iframe src="https://drive.google.com/file/d/1bZpWqecKSDUKNKlqJwsTS_kGr6zqsPRX/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Next we need to tell ssh our new port number and to only use our passphrase.  So type "cd /etc/ssh" and enter.  Next, "sudo nano sshd_config" and enter.<br><br>First, scroll down (you have to use the keyboard because your mouse won't work) until you file the line for port.  Delete the # (in linux when you see a # it is called commented out so basically it's ignored...delete the # and it's not ignored anymore) and pick a port number (anything over 1024 should be ok).</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1tn0f0hXwgC5M55lVfOhOUhJHAPQwMCtl/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Next scroll down to the Authentication area.  Uncomment AllowUsers and DenyUsers.  For allow Users, put in the name of the account you will be using (I've changed my root user name--guide coming soon--so it's not root or pi).  For DenyUsers add root.  I've also changed the MaxAuthTries and MaxSessions.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/12hUgIjvdbXs0TAMvuiQe-0hg1P3zCs5T/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Now to tell our RPi to use the key/passphrase and not passwords, head down to # To Disable tunneled clear text passwords and delete (uncomment) the # for PasswordAuthentication and PermitEmptyPasswords and set both to no.  Press CTRL and X to save and close.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1oVd9bzMi5vpK8lE1XXZQa4XWG_HxSfOG/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Now, keep this ssh session and open a new putty session.  On the left hand side, expand Connection, the SSH and click on Auth.  Click the browse button and navigate to and select the file we saved at the beginning of this guide. </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/16-Yb9Z0Tlc9WRCDhCUeZMQKpedi9suub/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Then go to Connection and Data and put in your username in the Auto-Login box and select Prompt.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1yKLf4PyhQ-gcWyXOZcQyOazXpUR1Q_nG/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Now click on Session on the left hand side.  Enter the IP of the machine and the port number.  And so you don't have to fill all of this out in the future, type a name in the saved sessions box and click save.  This will save all the settings and in the future, you just have to double click on the name to launch the connection with you new secure settings.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1Zcf3WrUegGxY-GqVDJbrnvgjRHjNfN9g/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Now, click open and you should get something like this.  If so, type in your super secret pass phrase.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1WGJBEt3RS97SUqUvw1D6cEPt1bYjLK3j/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>With that, you should be all set.  Just remember if you want to connect to it from another machine, you will have to add the new machines key info to authorized_keys.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>OK, so an edit to add the Mac Book screen shots.  I have a Mac book, a G5, and Mac Mini (the good one where you can add a second hard drive)...I know, right?  Why would someone have Microsoft, Apple, and Linux all running...  it's kind of like</p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
https://youtu.be/O3ZOKDmorj0
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p>So anyways...So on MacOS, open up a terminal and you want to run the command ssh-keygen.  That will ask a few questions.  go with the defaults and PLEASE enter a passphrase (multi-layered security)</p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
<iframe src="https://drive.google.com/file/d/1s_ElNTB3KVB_NH1Q4ROBjqbQEakM2Leg/preview" width="640" height="480"></iframe>
<iframe src="https://drive.google.com/file/d/1nSZ_Guz2DhC0xyooA0h_51RM3kyoaZIy/preview" width="640" height="480"></iframe>
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p>Next, you need to push your new shiny public key to your remote linux box.  Do so by the this handy dandy command  cat ~/.ssh/id_rsa.pub | ssh name@192.168.x.x 'cat &gt;&gt; .ssh/authorized_keys'</p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
<iframe src="https://drive.google.com/file/d/1Ei4Wh6dxh8tFMho5wuBL4BLQdtBD7cxm/preview" width="640" height="480"></iframe>
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p>So now we just need to launch an ssh console from the Mac.  Windows you have to install putty, MacOS is ready to go so run ssh -p yourportnumber user@IP.  Follow the prompts and enter your passphrase.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1V-ZvrMoWhdFWriqbnMn8XqawW8v6gnZ2/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>And then...happy happy joy joy</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1zwe4ebmxdyuNeWT6uK5NHj4wwKcNu01f/preview" width="640" height="480"></iframe>
<!-- /wp:html -->