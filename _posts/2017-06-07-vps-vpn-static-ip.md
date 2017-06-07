---
layout: post
comments: true
title: Network | Static IP as a freelance
category: vps, docker, linux
---

As a freelance developer, having a static IP is useful (for example, remote access to your client server), but relying on your own IPS is not the best option: maybe you can't have a static ip, what happen if you move or if your connection has problem...  

Because you are mobile, you need to have a static ip from wherever you are.

A solution is to use a VPN, some services like [myip.io](https://www.myip.io) seems to do a great job but as I was talking about this with my friend [@mcornet80](https://twitter.com/mcornet80) he pointed at me a more geeky solution (and a bit cheaper too!): "Use a VPS and docker!".

# VPS

I decided to use OVH but feel free to choose your favorite company!
Go to [https://www.ovh.com/vps/vps-ssd.xml](https://www.ovh.com/vps/vps-ssd.xml) and choose the first VPS SSD 1 (3.59€/mo).

During the setup you will have to decide what distribution to use, go for *docker* (basically ubuntu 14 with docker pre-installed) because we're going to use a great container :)

You might want to consider adding a bit of security like changing your access to a stronger password or blocking unused ports...

Your server is all setup and working? Let's install your VPN.

# VPN

An easy way to install a VPN is to use openVPN, an easiest way is to use a dedicated docker container!

The [kylemanna/docker-openvpn](https://hub.docker.com/r/kylemanna/openvpn/) container allows us to quickly run openVPN.

First, pull the image (docker is already installed remember):

```
docker pull kylemanna/openvpn
```

Then, simply follow the instructions on the *Quick Start* part.  
In the second step, don't forget to replace **VPN.SERVERNAME.COM** by your VPS IP:

```
docker run -v $OVPN_DATA:/etc/openvpn --rm kylemanna/openvpn ovpn_genconfig -u udp://135.XXX.XXX.XXX
```

On the last step, it's best to change **CLIENTNAME** in something more meaningful (like your name or pseudo).

When it's done, transfer the  **CLIENTNAME.ovpn** file to your computer and use an openvpn client to connect!  
*You can use a website like [whatismyipaddress.com](http://whatismyipaddress.com/) to ensure your IP has changed.*

Again, thanks [@mcornet80](https://twitter.com/mcornet80) for providing me this great solution!
