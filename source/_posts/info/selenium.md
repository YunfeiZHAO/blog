---
title: Selenium
date: 2024-1-26 10:28:13
excerpt: Web scraping with Selenium on remote server.
index_img: /img/selenium/scraping.png
banner_img: /img/selenium/scraping.png
tags: [data]
category: Informatics
math: true
comment: disqus
---
Selenium is a project for browser automation and testing. It includes three main parts.
- Integrated Development Environment
- Selenium WebDriver: Tool for automating web browser interactions and this is what we often use for web scraping.
- Selenium Grid: a program used to concurrently run test cases across multiple browsers, computers, and operating systems.

All the work will be done on a remote ubuntu 22 server (you can do it locally or in a VM).

# Setup python package and drivers
```
# Chrome dependencies
sudo apt-get install libxss1 libappindicator1 libindicator7
# selenium python package
pip install selenium
# chromium browser driver
sudo apt-get install chromium-chromedriver
# a library that provides a configuration database system used by some applications on Linux systems
sudo apt-get install libgconf-2-4
# download and install chrome on remote server
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo chmod +x google-chrome-stable_current_amd64.deb
sudo apt-get install -y ./google-chrome-stable_current_amd64.deb
google-chrome --version
```

# Setup X11 for remote connection
If your local machine is linux distribution with X11, it is much easier for setup. If you are using a windows local machine, you can follow my steps.
```
# Remote server
sudo apt install xorg xauth x11-xserver-utils
# setup ssh configuration file
sudo vim /etc/ssh/sshd_config
# modify these lines
X11Forwarding yes
X11DisplayOffset 10
# restart ssh server for remote linux
sudo systemctl restart ssh
```

You need to install an X server on Windows so that the APP GUI on the remote server can be redirected to the Win server. I recommendmand *vcxsrv* as it is stable. Once it is run, a little icon of X11 is shown in the hidden icons bar.
The **network setting** on the local server network profile type needed to be set as a private network so that the local device is discoverable on the network. Otherwise, the redirected X11 APP can not find the X server on your local machine.

```
# local
# Establisha ssh connection with -X. 
# It allows graphical applications running on 
# the remote server to be displayed locally.
ssh -X username@remote-server-ip
```

```
# remote 
export DISPLAY=orz_win.local:0
```
This environment variable tells the X11 where to redirect the APP. Where orz_win.local is the domain name of my local machine on my router. You can also use the local internet ip address. The 0 is the display number that you set when run a X server on your local machine. So you can open multiple X server on local machine and show different programs run on the remote server.

Now if you run google chrome on remote server by this command:
```
google-chrome
```
You will see that a chrome window is opened on your local computer.

<iframe src="http://127.0.0.1:8000/donation_unit" style="overflow-x:hidden;overflow-y:hidden; border:0xp none #fff; min-height:240px; width:100%;"  frameborder="0" scrolling="no" allowtransparency="true"></iframe>
