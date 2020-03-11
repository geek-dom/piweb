---
ID: 277
post_title: Windows 10 SNMP Install with PowerShell
author: Don
post_excerpt: ""
layout: page
permalink: >
  https://geek-dom.com/geek-how-tos/tips-and-tricks/windows-10-snmp-install-with-powershell/
published: true
post_date: 2020-03-11 09:28:13
---
<!-- wp:paragraph -->
<p>So I was doing a fresh install of Windows 10 Pro on a VM and couldn't find the SNMP Client in the add/remove Widows features.  After some digging, found out that fresh installs using build 18XX and above, this was removed.  There's supposed to be a bug fix in the works to restore it (I'm 50/50 on believing it) so I found out how to install it via PowerShell.<br><br>Open Powershell as Admin, then use these commands<br>1. To see if SNMP client is installed run Get-WindowsCapability -Online -Name 'SNMP*'<br>2. From the info, check Name and State.  Not present means it's not installed.<br>3. Run Add-WindowsCapability -Online -Name SNMP.Client~~~~0.0.1.0<br>4. Then verify that State is now Installed by rerunning the command from step 1.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/36LSmXNZNyI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<!-- /wp:html -->