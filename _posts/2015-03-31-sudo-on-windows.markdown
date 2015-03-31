---
layout: post
title:  "Sudo on windows?"
metadescription: "If you wish to run a command line command on a Windows OS that requires elevated privileges you have to start a new command prompt with administrator privileges by right clicking it and clicking run as administrator. In a Unix-like OS you simply type sudo before the command, enter your password, and run it - much simpler. I decided to play around and see if I could introduce the sudo command to Windows."
date:   2015-03-31 20:10:01
tags: windows powershell
---

If you wish to run a command line command on a Windows OS that requires elevated privileges you have to start a new command prompt with administrator privileges by right clicking it and clicking "run as administrator". In a Unix-like OS you simply type "sudo" before the command, enter your password, and run it - much simpler. I decided to play around and see if I could introduce the sudo command to Windows. 

The most versatile command prompt in the Windows OS is, in my opinion, Powershell so I used that for my test.

Powershell comes with the ability to set your own aliases so I wrote a function that would take a command and run it with elevated privileges using the "runas" command:


    function Sudo-On-Windows() { runas /noprofile /user:Administrator "$args"; }
    
I then created an alias named "sudo" that runs the function:
    
	Set-Alias sudo Sudo-On-Windows

If I now run the following command from a normal Powershell prompt I will get an error:

    net user Jonas secretpassword /ADD

But this command will ask me for the administrator password and run the command successfully:

    sudo net user Jonas secretpassword /ADD

The function above requires that you have activated the administrator user in advance, which you can do from a Powershell prompt (with admin privileges) with this command:

    net user administrator /active:yes
    
The alias won't stick around if you close down the Powershell prompt. Adding it permanently should probably not be too difficult though.
    
