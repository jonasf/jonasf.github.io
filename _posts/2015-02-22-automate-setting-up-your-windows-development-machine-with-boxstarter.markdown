---
layout: post
title:  "Automate setting up your Windows development machine with boxstarter"
metadescription: "This post will introduce you to automated setups of a Windows system using the excellent Boxstarter tool."
date:   2015-02-22 12:26:01
tags: automation setup
---

This post will introduce you to automated setups of a Windows system using the excellent Boxstarter tool.

### Why automate the setup of your Windows system?

If you are researching this topic you probably have some thoughts as to why. In my case there are two main reasons:

1. Installing all the software you need to have a useful Windows system is usually quite time consuming, especially if you are a software developer.

2. After having done the task several times before it is quite repetitive which means that there are probably better ways for you to spend your time.

### What is boxstarter?
[Boxstarter][] is a tool that allows you to automate the setup of your Windows development environment using the [Chocolatey][] package manager.

### How do you use boxstarter?

**It will basically boil down to three steps:**

1. Create your setup script.
2. Login to your fresh installation of Windows.
3. Open a command prompt and enter the following:

        START http://boxstarter.org/package/nr/url?https://raw.githubusercontent.com/jonasf/windows-machine-setups/master/01-dotnet-development-machine.ps1

	Boxstarter will launch and ask for your permission to run.

_That's it, this is where you go and do other things._

The _url_ argument links to your setup script, in the example above the script I use to setup my virtual Windows dev machine. Boxstarter will then proceed to download and install all the software specified in the script and configure your environment, rebooting your system if it is necessary.
	
The setup time will vary depending on what software you chose to install, but it is safe to say that it is nothing compared to the usual effort required to setup a new machine.

**How do you tell boxstarter what to install?**

Boxstarter uses [Chocolatey][] so your first step is to head over to the [Chocolatey page][] and make notes of all the package names of the software you want to install.

The script itself is simply a list of regular Powershell and Chocolatey install commands, ie:

    #Initial windows configuration

    Update-ExecutionPolicy Unrestricted
    Enable-MicrosoftUpdate
     
    #Runtimes and frameworks
    cinst DotNet4.0
    cinst DotNet4.5.1
    cinst javaruntime
    
    #Windows enhancements and helpers
    cinst ConEmu
    
    #Visual studio and plugins
    cinst VisualStudio2013Professional -InstallArguments "/Features:'WebTools SQL'"
    cinst resharper -Version 8.2.3000.5176
    cinst VS2013.VSCommands
    cinst visualstudio2013-webessentials.vsix


Save the script as a *.ps1-file and publish it to some place that is easily accessible like Github.

You can find my setup script here: [01-dotnet-development-machine.ps1](https://github.com/jonasf/windows-machine-setups/blob/master/01-dotnet-development-machine.ps1)

Good luck with automating your Windows setups!


[Boxstarter]: http://boxstarter.org/
[Chocolatey]: https://chocolatey.org/
[Chocolatey page]: https://chocolatey.org/
