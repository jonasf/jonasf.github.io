---
layout: post
title:  "Improving your privacy online, part 1"
metadescription: "We are constantly being tracked online without our consent. These are a few tips to make it more difficult."
date:   2020-03-03 15:00:01
tags: privacy ad-blocking tracking tinfoil-hat raspberrypi
---

We are constantly being tracked online. Usually by marketing organizations who want to target you with personalized ads in order to get you to buy more things or sell the information collected about you to others. There is also the possibility that you are being tracked by other entities who want to know what your opinions are on specific topics or where your political sympathies lie.

Most likely, you have not actively consented to being tracked this way. Whether the terms and conditions many websites use which are full of complicated legalese are an active consent could be debated.

Information collected for innocent or commercial purposes today could be used for nefariuos purposes tomorrow. While it is impossible to completely avoid being tracked, you should make it more difficult for any entity to track you online.

In this blog post I will detail my first steps. I have been doing a few things for many years and started very recently with others.

## First steps

### Change your search engine

**Stop** using [Google](https://www.google.com) and **start** using [DuckDuckGo](https://duckduckgo.com).

![DuckDuckGo logo](/public/images/privacyonline/duckduckgo.png "DuckDuckGo logo")

While the Google search engine is an absolutely incredible product it is being used to collect data about you to sell ads. DuckDuckGo does not collect or share information about you, at least according to their own statement.

I have been using DuckDuckGo privately for a couple of months. 9 times out of 10 I find what I am looking for but that 10th time I have to fall back to Google. In my work as a software engineer I have to use Google all the time.

DuckDuckGo will most likely improve in the future so I can use it 100% of the time.

### Change your browser

**Stop** using [Google Chrome](https://www.google.se/chrome/) and **start** using [Firefox](https://www.mozilla.org/en-US/firefox/new/) on all devices.

![Firefox logo](/public/images/privacyonline/firefox.png "Firefox logo")

Chrome is, like most Google products, an excellent product. However, you have to actively turn off tracking.

Firefox comes with tracking protection enabled by default. Another awesome feature is that Firefox, unlike Chrome, has support for plugins even in the mobile version for Android. This will help protect you from tracking on your mobile.

Using Firefox works 99.999% of the time for me. In some exceedingly rare cases web pages force me to use Chrome.

### Use browser plugins

**Start** using privacy enhancing browser plugins in Firefox.

Use [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) to block ads. This will make your browsing experience a joy.

Use [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/) by the [EFF](https://www.eff.org/) to block trackers even more.

Use [Facebook container](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/) to make it harder for Facebook to track you if you are a Facebook user.

These plugins also work in [Firefox on Android](https://play.google.com/store/apps/details?id=org.mozilla.firefox&hl=en_US). I have yet to find an equally good solution for my IOS devices.

### Change your DNS

**Stop** using your ISP (Internet Service Provider) [DNS](https://en.wikipedia.org/wiki/Domain_Name_System) and **start** using [Cloudflare DNS](https://www.cloudflare.com/dns/) or a  similar DNS service.

Some IPSs will map your habits online using your DNS lookups and sell your data. Some will even block certain DNS lookups for various reasons.

Cloudflare DNS is independent, although commercial. It will give you [DNS over HTTPS](https://en.wikipedia.org/wiki/DNS_over_HTTPS) which should improve your safety online.  

### Use a DNS black hole list (DNSBL)

On your home network you can easily start using a DNS black hole list. This means that DNS lookups for domains known for tracking or other malicious behaviour will be blocked and no data will be downloaded from those servers. This will allow you to block ads in mobile apps on your devices if they are connected to you local network.

For this I am using the excellent [Pi-Hole](https://pi-hole.net/) project. This does require you to set up a [Raspberry Pi](https://www.raspberrypi.org/), install Pi-Hole on it, install it on your home network and finally having your router use it as a DNS. This may sound complicated but there are good guides on the project page.

![Pi-Hole Dashboard](/public/images/privacyonline/pihole-dashboard.png "Pi-Hole Dashboard")

On my home network the Pi-Hole DNS will block between 5% and 25% of all DNS lookups.

## Next steps

This was only a start:

* I need to find a good [VPN](https://sv.wikipedia.org/wiki/Virtual_private_network) service.
* I need to start looking into [TOR](https://www.torproject.org/).
* I need to stop using Facebook, WhatsApp and Facebook Messenger. This will be hard since my friends and family all use them.
* I need to find replacements for Google Maps, Gmail and Google Calendar. They are all great products, especially Google Maps. Finding replacements that are equally good will be very hard.
