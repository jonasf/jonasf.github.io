---
layout: post
title:  "Sudo on windows"
date:   2015-03-30 20:10:01
tags: windows
---

    function Sudo-On-Windows($command) { runas /noprofile /user:Administrator "$command"; }
	Set-Alias sudo Sudo-On-Windows

Requires activated Administrator account
net user administrator /active:yes