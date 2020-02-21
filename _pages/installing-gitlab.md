---
ID: 241
post_title: Installing GitLab
author: Don
post_excerpt: ""
layout: page
permalink: >
  https://geek-dom.com/raspberry-pi-projects/git-and-gitlab/installing-gitlab/
published: true
post_date: 2020-02-21 14:56:56
---
<!-- wp:paragraph -->
<p>I have never had luck installing GitLab from the CLI.  I download the install package from the website, then use WinSCP to copy it to my RPi.<br><br><a href="https://packages.gitlab.com/gitlab/raspberry-pi2">https://packages.gitlab.com/gitlab/raspberry-pi2</a><br><br>Even though the site has pi2 in the name, it's up to date.  After you have downloaded it and copied it to your RPi, ssh in and navigate to the folder you copied it to.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1wngOyWCFivh65GhrFdOBy8pbQHiDRW0S/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>The version of GitLab as of this writing is gitlab-ce_12.7.6-ce.0_armhf.deb so the version you download may be different so the next command may look different.  You will need to enter the following, changing the https://n_a to your RPi's name and adjusting the .deb file name if it's a different version.<br><br>sudo EXTERNAL_URL="http://n_a" dpkg -i gitlab-ce_12.7.6-ce.0_armhf.deb</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/17pWTF_wfXVUikvItxSOhHq2uEkofptoM/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>This will extract and begin installing GitLab.  This does take some time, but you don't have to do else.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1PngX6crhZkIjB2eanj8yEEjckHarMYQV/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>When it has finished installing, you will get something like this.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1TmzNEvxk-nteE9o8PrwBnh2uEg1_Dcq_/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>I normally do a reboot at this point.  Once your RPi has booted back up, go to a web browser and enter either your RPi's name (if you've configured your home dns server for it) or the IP address of your RPI (remember to use http:// either way).</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/14uUemnPwEUlSHrZprDzwsz5olIWsmSd7/preview" width="640" height="480"></iframe>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>You will be prompted to create a password and confirm it.  Once you do that, it will ask you to log in.  The default user name is root.  Once you have logged in, explore.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<iframe src="https://drive.google.com/file/d/1D06AkhH6XYGpSu_M9lLIXYY-kVqnoK7D/preview" width="640" height="480"></iframe>
<!-- /wp:html -->