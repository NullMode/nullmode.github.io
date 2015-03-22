---
layout: post
title: "Getting Personal With PowerShell: Linux to PowerShell"
date: 2014-06-28 13:00:00 +0100
comments: true
categories: [powershell]
---

Running Windows as a main OS can be tough times for many hard core Linux users, especially when you want some command line power. PowerShell at first glance looks alien to some, but under closer inspection it's not a million miles away from what you can achieve in a Bash shell. 

<!-- more -->

If you’re like me you'll have a few handy aliases that save a bit of time whilst working in your Linux environment. For example the below aliases save having to type out long commands that you may use quite often:

	alias lsa="ls -lsahS"

	alias screen="screen -xRR"

	alias ..="cd .."
	alias ...="cd ../.."
	alias ....="cd ../../.."
	alias .....="cd ../../../..”
	
	alias upd="sudo apt-get update"
	alias upg="sudo apt-get upgrade"
	alias ins="sudo apt-get install"
	alias rem="sudo apt-get purge"
	alias fix="sudo apt-get install -f"

If you find yourself dropping into a Linux virtual machine to use the command line functionality you may be surprised to learn that a lot of the same functionality can be achieved with PowerShell. PowerShell handles everything as an object which makes piping between commands very powerful. For example, if I want to return the full path for every file in the current directory I could do the following:
	
	Get-ChildItem | Select-Object fullname

Each file returned is piped to the select command to get the **fullname** attribute of the file object. 

It's worth learning about the PowerShell equivalents of some of the commands you might run in a Linux shell. Below I've put some of the more familiar Linux command line binaries and their PowerShell counterparts.

<br />
####Listing running processes
**Linux**

	ps

**PowerShell**

	get-process

<br />
####Stopping a process
**Linux**

	kill calc.exe

**PowerShell**

	get-process calc.exe | StopProcess

<br />
####Displaying a list of 1 to 10
**Linux** 

	seq 1 10

**PowerShell**

	1..10

<br />
####Print the first 10 lines of a file
**Linux**

	head -n10 file.txt

**PowerShell**

	gc file.txt | select -first 10

<br />
####Print the last 10 lines of a file
**Linux**

	tail -n10 file.txt

**PowerShell**

	gc file.txt | select -last 10 

<br />
####Count the lines in a file
**Linux**

	wc -l file.txt

**PowerShell**

	gc file.txt | Measure-Object -Line 

<br />
####Print lines that contain the word “example”
**Linux**

	grep example file.txt

**PowerShell**

	Select-Text example file.txt

<br />
####Split file using ":" as a delimiter and print the second item
**Linux**

	awk -F ":" '{print $1}' file.txt

**PowerShell**

	gc file.txt | %{ $_.Split(':')[1]; }

<br />
####Replace the word “example” with “elpmaxe” in file.txt
**Linux**

	cat file.txt | sed ’s/example/elpmaxe/‘

**PowerShell**

	gc test.txt | Select-String “example" | %{ $_ -replace ‘example', 'elpmaxe' }

<br />
There’s actually a lot of built in aliases in PowerShell already so if you find yourself loathing some long command string you might be pleased to know that their is probably already a shortcut for it already. You can find out what these are with the following command:

	Get-Alias

As you can see there are a few items in the list that would be familiar to you if you are from a Linux background. Aliases such as ls, cat and rm are just a few examples of aliases that you wont need to re-learn (or set up) for PowerShell. Remember that command at the start where I grabbed the full path for each file in the directory? That could have been simplified using these built in aliases.

	ls | select fullname

That's not so much of a pain to type is it?

### Setting up your PowerShell profile
For practice I'll go through setting up the profile (mostly) in PowerShell. The PowerShell environment tries to load your profile information from the following file (may differ with different Windows operating systems):

	C:\Users\NullMode\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1

This file location is stored in the PowerShell environment variable $PROFILE as seen below:

	echo $PROFILE
	C:\Users\NullMode\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1

Let's use this variable to create this file in this location:

	New-Item -type file -force $PROFILE

Hooray, we've just made a PowerShell profile file.

### Adding aliases to our PowerShell profile file
Let's open up that file from within PowerShell because we're gurus now:

	notepad $PROFILE

In a .bashrc/.bash_aliases file you can define functions that can be run as well as aliases, unfortunately this isn't possible with PowerShell. You must first define the function then use the New-Alias command to tie the function name to an alias that we can type into the prompt.

#####With the open file let's add some aliases:

How about a quick alias to run ipconfig:

	New-Alias ipconfig -value ip

If you want to do ipconfig /all the following would be required as you are supplying the name of the command and an argument:

	function ipconfig_all_function() {
		ipconfig /all
	}
	New-Alias -name ipa -value ipconfig_all_function

Change to your $HOME directory:

	cd_home_function() {
		cd $HOME
	}
	New-Alias -name home -value cd_home_function

Maybe a shortcut to open notepad if you're in a console window:

	New-Alias -name n -value notepad

Being lazy is cool remember:

	function exit_function() {
		exit
	}
	New-Alias -name x -value exit_function

Once you have some aliases in your profile file just save it and open a new PowerShell instance and test them out! You'll get an error if something is wrong in the file so you'll be able to correct yourself.

The aliases above are pretty simple. Here is one I've made that sets up a git repository with some local configuration settings. This can be useful if you have multiple git servers using different user names and e-mails assigned to them.


	function gitinb_function() {
    	git init
    	git config --local user.name NullModeBitbucket
    	git config --local user.email TheRealDeal@DealOrNoDeal.cn
	}
	New-Alias -name gitinb -value gitin_function

	function giting_function() {
    	git init
    	git config --local user.name NullModeGithub
    	git config --local user.email TheRealDeal@DealOrNoDeal.cn
	}
	New-Alias -name giting -value gitin_function


### More customization
Here are a couple of places you can go to read about aliases and profile customization that you may wish to incorporate into your own profile file:

- [What's in your Powershell profile.ps1file?](http://stackoverflow.com/questions/138144/whats-in-your-powershell-profile-ps1file) - some cool examples from other PowerShell users
- [Customizing your PowerShell Profile](http://www.howtogeek.com/50236/customizing-your-powershell-profile/) - A similar guide to this that has a nice example of pimping out the terminal itself


### Bonus information!
There's some special locations you can get to within PowerShell. I thought I'd include them here while I remember as maybe someone will find them useful.

View the windows environment variables:
	
	cd env:
	ls

View the Windows HIVE files:

	cd HKLM:
	ls

If you want to find out about a particular item in one of of these locations you can do the following (remembering that past the tabbing through the items is possible):

	echo $Env:OS

 
### Shout-outs
Thanks to [@lllamaboy](https://twitter.com/lllamaboy "@lllamaboy") for giving me the first steps on setting up a python $PROFILE and letting me in on the whole special location thing.