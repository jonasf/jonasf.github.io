---
layout: post
title:  "Automate setting up your Windows development machine with boxstarter"
date:   2014-05-21 22:08:12
categories: blog
tags: automation setup
---
###Why automate the setup of your Windows system?

If you are researching this topic you probably have some thoughts as to why. In my case there are two main reasons:

1. Installing all the software you need to have a useful Windows system is usually quite time consuming, especially if you are a software developer.

2. After having done the task several times before it is quite repetetive which means that there are probably better ways for you to spend your time.

###What is boxstarter?
[Boxstarter][] is a tool that allows you to automate the setup of your Windows development environment using the [Chocolatey][] package manager.

###How do you use boxstarter?

**It will basically boil down to three steps:**

1. Create your setup script.
2. Login to your fresh installation of Windows.
3. Open a command prompt and enter the following:

        START http://boxstarter.org/package/nr/url?https://raw.githubusercontent.com/jonasf/windows-machine-setups/master/01-dotnet-development-machine.ps1

	Boxstarter will launch, asking for various confirmations and your credentials.

_That's it, this is where you go and do other things._

The url argument links to a setup script, in this case the one I use to setup my virtual Windows 8.1 dev boxes. Boxstarter will then proceed to download and install all the software specified in the script and configure your environment, rebooting your system if it is necessary.

Boxstarter will probably run for the better part of an hour (depending on your script) but this is nothing compared to the usual effort required to setup a development environment.

**How do you tell boxstarter what to install?**

Boxstarter uses [Chocolatey][] so you create a PowerShell script with Chocolatey commands like this:


        #Initial windows configuration

        Update-ExecutionPolicy Unrestricted
        Enable-MicrosoftUpdate
        Set-ExplorerOptions -showHidenFilesFoldersDrives -showProtectedOSFiles -showFileExtensions

        #Runtimes and frameworks
        cinstm DotNet4.0
        cinstm DotNet4.5
        cinstm javaruntime
        cinstm nodejs.install
        cinstm ruby
        cinstm python

        #Windows enhancements and helpers
        cinstm classic-shell
        cinstm webpi
        cinstm ConEmu
        cinstm ransack

        #Web browsers
        cinstm GoogleChrome
        cinstm GoogleChrome.Canary
        cinstm Firefox
        cinstm safari

        #Browser plugins
        cinstm fiddler4

        #Text editors
        cinstm sublimetext2
        cinstm SublimeText2.PackageControl -Version 1.6.3

        #Utilities
        cinstm dotPeek
        cinstm 7zip

        #Visual studio and plugins
        cinstm VisualStudio2013Professional -InstallArguments "WebTools SQL"
        cinstm resharper
        Install-ChocolateyVsixPackage "VS Commands 2013" http://visualstudiogallery.msdn.microsoft.com/c6d1c265-7007-405c-a68b-5606af238ece/file/106247/14/SquaredInfinity.VSCommands.VS12.vsix
        Install-ChocolateyVsixPackage "Web Essentials 2013" http://visualstudiogallery.msdn.microsoft.com/56633663-6799-41d7-9df7-0f2a504ca361/file/105627/24/WebEssentials2013.vsix

        #VCS
        cinstm gitextensions
        cinstm kdiff3

        #Install windows updates
        Install-WindowsUpdate -AcceptEula



[Boxstarter]: http://boxstarter.org/
[Chocolatey]: https://chocolatey.org/