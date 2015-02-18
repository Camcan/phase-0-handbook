[Week 1 Home](../..)

# Computer Set-Up Instructions: C# on Windows

## Learning Competencies
By the end of this lesson, you should be able to:

- Install technologies from the command line
- Understand what a package manager is and why it is helpful

## Summary
You will need to have your computer set up with the following tools for Phase 0 of Dev Academy. Make sure to go through this guide step-by-step. You'll need to have each of these technologies installed to have a smooth start to Phase 0 and your future career!

Here is the instructions for getting your windows environment set up. There are two shells on windows: command line and powershell, we will be using powershell - because it is extendible. We will be installing:

- Chocolatey
- Git
- PS-GET
- Sublime
- Posh Git & Jump.Location
- Set PS start location
- SQLite
- Microsoft Visual Studio Community 2014
- Microsoft SQL Server Community 2014
- Install Linqpad

## Releases
(i.e. directions - each release is necessary for the next release, so be sure to do everything in the order specified for all challenges)

NOTE: If you come into difficulties follow this process:

1. Check you haven't skipped anything. i.e. Carefully reread everything!
2. Close and open PowerShell - some changes will only be loaded when the next shell environment is created.
3. Google the error/problem (time box this to 5-10 min)
4. Ask on Slack and move onto something else until you get help.

## Release 0: Install Chocolatey
Now lets install our package manager to get the libraries we need.

Chocolatey works like homebrew for mac or apt-get for linux. We download this program and say:

"choco install Git!" or "choco install Sublime!"

Chocolatey takes care of downloading and installing these programs for you. It even adjusts your PATH variable to make sure the operating system accesses these languages correctly.

###To Install
To install Chocolatey from [http://chocolatey.org/](http://chocolatey.org/) follow these two instructions:

1. Open a "run window" by holding down the "windows logo key" and clicking "r". Paste the following into it and click "enter":

```
powershell
```

  * A PowerShell (PS) terminal window will appear.

2. Now paste in the following into the powershell terminal and click "enter"

```
iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```

You should see a message stating that Chocolatey has finished installing. Now we can start installing packages. You can search a list of all the packages available for Chocolatey on their website [Chocolatey packages](http://chocolatey.org/packages).

Type the following to see a list of chocolatey commands
```
choco help
```

To list all your installs
```
choco list -localonly
```

###PRO TIP: 
You should pin PS to your taskbar as you are going to be using it a lot. Right click on the powershell icon in your taskbar and click "Pin to taskbar". If you are ever in need of an "elevated shell" also known as "Administrator" shell, right click on the icon you have pinned to the task bar and click "Open as Administrator" or something to that effect.

## Release 1: Install Git
**Note: open an elevated shell to install Git - otherwise it wont add git to your computers path.**  
Git is Awesome! It will totally save your bacon one day. So lets get it installed using our new awesome package manager, Chocolatey. Open a terminal or in an existing type the following to install git:

```
cinst git
```

Once Chocolatey has done its thing type:
```
git --version
```

You should see a version number for the git that is installed on your system.  

## Release 2: Set up PowerShell Extension Manager
Similar to Chocolatey, [PS GET](http://psget.net/) is a package manager for modules that extend PS functionality.

###To Install
Open PS & type:

```
(new-object Net.WebClient).DownloadString("http://psget.net/GetPsGet.ps1") | iex
``` 

Thats it!

## Release 3: Give PowerShell Jumping Git Bling
Git is fantastic, but you will quickly get sick of typing `git status` to get the current state of the git repository (repo). To make life easier some clever folks created Posh-Git an extension for PowerShell that gives you in-line git information as part of your PS prompt (this is the stuff to the left of where you type in PS).

###To Install
We will use PS-GET to get [Posh Git](http://psget.net/directory/posh-git/). Open PS and type:

```
Install-Module posh-git
``` 

Now you have done that lets install another great little extension, [Jump.Location](http://psget.net/directory/Jump.Location/). Jump Location builds up a history of the directories you have navigated to in PS and allows you to jump there! Remember this when you get sick of navigating up and down folder structures all the time :) 

###To Install
Open PS & type:

```
Install-Module Jump.Location
```

NOTE: To use Jumplocation type "j" instead of "cd" and then a name of a folder you have been in and click tab - voilà! It will make suggestions of where you might want to go. It wont work at first as it uses a data table of information of where you have navigated to in PS. However once you have been somewhere you can than jump there next time.

###Debug!
If you encounter problems installing modules it is most likely due to a security feature of windows that disables the execution of scripts as a default - this feature can be turned off, i.e. making it possible to run scripts!
Simply type the following into PS and click enter when prompted.
```
set-executionpolicy remotesigned
``` 
See [here](http://www.faqforge.com/windows/windows-powershell-running-scripts-is-disabled-on-this-system/) for a more informative explanation.

## Release 4: Install Sublime Text
There two versions of Sublime Text (2 & 3). For the course we will be using Sublime Text 2 as it comes with an indefinite trial licence allowing students to work with it at EDA and decide if it is something they want to invest in in the future (at which point buy Sublime Text 3). It will pop up with purchase prompts - just cancel out of these when they appear.

###To Install
Now that we have Chocolatey - we can use it to install Sublime. We can get the information we need by looking up Sublime in the packages directory at [chocolatey.org/packages](https://chocolatey.org/packages/sublimetext2). Paste either of the following into the terminal and click enter (cinst is short hand for choco install).

```
choco install sublimetext2
```

or

```
cinst sublimetext2
```

Sublime also has a handy console/terminal plug-in that enables us to open files and directories in Sublime. But we need to set this up. To do so we will use Chocolatey again:

###To Install
Open PS & Type

```
cinst sublimetext2.powershellalias
```

This will add some code to your powershell user profile that will link the Sublime tool to powershell. To access Sublime in the console we use the shorthand command 'subl'. Now you can:

####Open a file
```
subl "filename.something"
```

####Open a directory
```
subl .
```

Note: In the console/terminal environment a single "." refers to the current directory while a double ".." refers to one level up.

Lets test that Sublime is set up and working - open a terminal and open the current directory of the terminal. Sublime should open with a list of files and folders on the left. 

###Set Sublime as default text editor for git files
Now we want to set the default git editor to Sublime. Follow [these instructions](http://stackoverflow.com/questions/8951275/git-config-core-editor-how-to-make-sublime-text-the-default-editor-for-git-on/9408117#9408117).
  
####Bookmark this page for easy reference
[keyboard shortcuts for windows](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/reference/keyboard_shortcuts_win.html)  

## Release 5: Set Powershell Starting Directory
Now that powershell is all setup lets set the starting directory.

####Setup Folders
1. Open Explorer and navigate to your C drive (C:)
2. Create a new folder called "dev" - this will be the folder you put all your projects into
3. Inside C:/dev create another folder called eda - this will be the place you put all your eda stuff.
 
####Open PowerShell Profile
Navigate to you folder (username/documents or library/documents) where you should see a folder called WindowsPowerShell, open it.
Now you should see a folder called "Modules" - this was created earlier when we installed PS-Get 
There should also be a file called "Microsoft.PowerShell_profile.ps1". Right click on this and click "open with Sublime".

####Wire it up
In Sublime you should see a few paragraphs that are referring to the modules we installed earlier using subl, posh-git and jump.location.
Now we are going to add our starting location to the bottom of the file. Do add a spacing line - it makes it easier to read :)
On a new line type

```
Set-Location C:\dev\eda
```

Now if you close and reopen your powershell you should start in the eda folder - you can change this anytime, just edit it again to the new path you want.

## Release 6: Install SQLite
SqLite is a server-less SQL database - making it very easy to set-up and use. We will use this in the SQL week later in phase-0, but will move to MicrosoftSequal (MSSQL) in phase-1.

###To Install
There are two parts to install, open PS & type:

```
cinst SQLite
```

Once that finishes type:

```
cinst sqlite.shell
```

Lets test everything is working, type:

```
sqlite3 -version
```

You should see an output detailing the version number

## Release 7: Visual Studio - Community Edition

Visual Studio is Microsoft's [IDE](http://en.wikipedia.org/wiki/Integrated_development_environment) for developing software, it can be used for a variety of languages including C# and JavaScript.

VS can be quite confusing at first and phase-0 was designed so that it could be completed without using it. However it will be the primary tool used in the Bootcamp so its a good idea to install it now and if you have time have a play with it.

###To Install
```
cinst visualstudiocommunity2013
```

If you encounter problems or want to find out more go to the link below:   [http://www.visualstudio.com/en-us/products/visual-studio-community-vs](http://www.visualstudio.com/en-us/products/visual-studio-community-vs)

## Release 8: Microsoft SQL Server 
This is Microsoft's version of SQL and SQL server - though C# solutions do not have to use it, it is heavily used in the IT sector and also comes with a handy management tool that makes developing easier.

###To Install
Using Chocolatey we need to install 2 parts: the management app and the server
```
choco install mssqlservermanagementstudio2014express
```
Then
```
choco install mssqlserver2014express
```

###Or if that doesnt work follow these instructions

Go to the link below and sign in, you will be presented with a list of options of what you want to install.
Be sure to select either:
 - SQL Server 2014 Express with Tools 32 Bit
or
 - SQL Server 2014 Express with Tools 64 Bit

Note: if you don't know whether you have a 32bit or 64bit operating system - open up control panel and click on system. if you don't see it, change the view from category to small links in the top right.

```
click "windows key" + "r" then type "control panel" and click enter. 
```

You can download the free version of Microsoft's SQL server at [https://profile.microsoft.com/RegSysProfileCenter/wizard.aspx?wizid=932d09f6-e2d4-429d-bd3e-834adabc4f8f&lcid=1033&ci=51](https://profile.microsoft.com/RegSysProfileCenter/wizard.aspx?wizid=932d09f6-e2d4-429d-bd3e-834adabc4f8f&lcid=1033&ci=51)

## Release 9: Install Linqpad
Linqpad is a program for running Linq queries and C# code snippets. Once you understand how to use the app it will become a great tool for quickly testing how a piece of code might work

###To Install
```
cinst linqpad
```


#Thats all

You now have a set up environment for development! If you are interested in this kind of thing, there is a whole job created around automating server and terminal set up. It is called DevOps. They do lots of things to make software development more efficient. Check it out! [devopsreactions](http://devopsreactions.tumblr.com/)
