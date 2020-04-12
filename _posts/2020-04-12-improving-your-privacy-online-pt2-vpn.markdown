---
layout: post
title:  "Improving your privacy online, part 2 - the VPN"
metadescription: "We are constantly being tracked online without our consent. A VPN (Algo VPN) can make it more difficult."
date:   2020-04-12 15:00:01
tags: vpn privacy ad-blocking tracking tinfoil-hat algovpn
---

An additional way to bolster your privacy online, on top of the things described in [part 1]({% link _posts/2020-03-03-improving-your-privacy-online-pt1.markdown %}), is to use a VPN ([Virtual Private Network](https://en.wikipedia.org/wiki/Virtual_private_network)).

In simple terms, a VPN will open an encrypted connection from your computer or mobile device to a server on the Internet. While this won't make you completely anonymous it will:

* Hide your Internet activity from your ISP.
* Hide what you are doing if you are using a public WiFi hotspot from the people who run the hotspot.
* Allow you to circumvent geographic restrictions on websites or streaming services.
* Bypass restrictions on the network you connect from.

## How to get started using a VPN

To use a VPN you will need 2 things:

1. A VPN client on your computer or mobile device.
2. A VPN service to connect to.

There are plenty of free VPN clients for most platforms. For a VPN service there a plenty of commercial services, both free and paid for, you also have the possibility to launch your own private VPN service on a [public cloud](https://en.wikipedia.org/wiki/Cloud_computing#Public_cloud).

If you care about your privacy **you should NOT use a commercial VPN service**, especially not a free one. If you use a free service they have to earn money somehow, most likely by analyzing and selling your data or worse - If you are not paying for the product, you are the product.  
However, even if you are paying for it there is no guarantee. Many commercial VPN Services who claim not to log your activity or sell your data have been found out doing just that.

The only way to really be sure that your activites are safe is to **set up your own VPN server**.

Setting up your own VPN server may be a bit of a hurdle. Fortunately there are a couple of projects that helps us with this. One that I am currently trying out is the [Algo VPN](https://github.com/trailofbits/algo) project which describes its mission statement in this [blog post](https://blog.trailofbits.com/2016/12/12/meet-algo-the-vpn-that-works/).

## Algo VPN

### About

Algo VPN is a set of scripts that will set up a [Wireguard](https://www.wireguard.com/) and IPsec VPN Server for you on a public cloud or your own machine.

It currently supports the following clouds:

* DigitalOcean
* Amazon
* Microsoft Azure
* Google Compute Engine
* Hetzner Cloud
* Vultr
* Scaleway

And the following platforms:

* OpenStack
* CloudStack
* Your own Ubuntu 18.04 or 19.10 server

### How to set up a Wireguard and IPsec VPN Server with Algo VPN

You need to be familiar with the command line interface and the Git version control system to use Algo VPN.

![Wireguard logo](/public/images/privacyonline/wireguard.png "Wireguard logo")

#### Step 1

Register for a cloud provider. I used DigitalOcean, [if you sign up with this link you will get a $100 credit](https://m.do.co/c/010d51dcd500).

#### Step 2

Set up the dependencies for Algo VPN as described on the [Algo VPN Github page](https://github.com/trailofbits/algo).

#### Step 3

Clone the Github repository:

    git clone https://github.com/trailofbits/algo.git

#### Step 4

Open the *config.cfg* file in your favourite text editor and add your VPN users in the users list, for example:

    users:
      - jonas-android-phone
      - jonas-windows-laptop
      - jonas-linux-laptop
      - moms-iphone
      - dads-iphone

#### Step 5

Run the algo script:

    ./algo

The script will walk you through the setup by first asking you to select which cloud provider or platform you wish to use and which features you need and second run the setup. The script will run for a couple of minutes.

You are now the proud owner of your very own VPN Server.

### Start using the VPN

After the setup script is done there will be a subdirectory in the *configs* directory with configuration files for Wireguard and IPsec. The subdirectory will be named with the IP address of your Algo VPN Server.

Which platform you are on will determine how to set up the VPN client on your device.

For Windows [download the Wireguard client](https://www.wireguard.com/install/) and import the . conf file from the wireguard subdirectory.

For mobile devices there will be images with QR codes in the wireguard subdirectory that you can scan with the Wireguard app ([Android](https://play.google.com/store/apps/details?id=com.wireguard.android&hl=en_US), [iPhone/iPad](https://apps.apple.com/us/app/wireguard/id1441195209)) for an easy setup.

For Linux it may depend on your distro. DuckDuckGo will be your friend in finding instructions.

![Wireguard mobile client](/public/images/privacyonline/wireguard-mobile.jpg "Wireguard mobile client")
