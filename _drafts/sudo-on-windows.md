---
layout: post
title:  "Sudo on windows"
date:   2015-03-30 20:10:01
tags: windows
---

    function Sudo-On-Windows() { runas /noprofile /user:Administrator "$args"; }
	Set-Alias sudo Sudo-On-Windows

###Requires activated Administrator account

net user administrator /active:yes

##Example
net user John secretpassword /ADD

sudo net user John secretpassword /ADD