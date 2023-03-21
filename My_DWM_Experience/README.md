# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

	Date:2-2-23
	Time:10:23

	This is my first time writing a blog so i'll try to make it sound interesting 
	as much as possible .But if you're not into nerdy stuff..I'm Sorry :(
	A week ago i decided to try DWM for the first time. DWM for those 
	who dont know is suckless's "Dynamic Window Manager"
	Window Manager's are similar to desktop environments but they are way 
	lighter and are in general more complex to use .
	Well..more complex to use...but once mastered..It'll be highly 
	productive because everything can be done and managed with just
	your keyboard and nothing else no GUI..no mouse required.
	So usually in dwm you are given a blank screen with a few keybinds to 
	start a shell and few keybinds to move through the windows for managing the applications 

	So the first thing I wanted to do was to change the default terminal from sh to
	"alacritty" cuz its way better and I've been using that for a while..so the way
	you customize your dwm is fairly simple .DWM is built with a .c file.
	Any changes you want to make is done by editing the .c file and then recompiling it .
	That is done by opening the config.h file in your /dwm directory
	 and changing the terminal option and also changed the text size "14".

	Date:2-2-23
	Time:18:41

	Next thing I wanted to do was fix my dwm-status-bar 
	I wanted the Basic UI to be on the top corner with 
	TEMP,BATTERY-INFO AND DATE-TIME so i found a shell script online that prints these info.
	so once I run the script it prints the data on the top right corner 
	But I wanted this script to run once i log into dwm so i tried multiple ways to do that 
	First I tried to do that with cron because that seemed like the simplest method  but since 
	I use a display manager it failed to work and then I 	tried to do the same 
	thing with systemd ...created a .service and tried to automate
	..same error on checking the journal 
	finally decided to use the autostart patch 
	Patching in dwm is adding more functionality to the original dwm code.
	It's done using a simple command called 'patch'  (read man patch for more info)
	I was able to install the autostart patch and then add this script 
	to the .dwm/autostart.sh file to it.
	Right now..I really enjoy using this window manager since I have the ability
	to customize everything I want .I'll update this page with my thoughts on 
	this wm as I use more of this and the problems I face and how I managed to fix them.
	
	Date:20-2-23
	Time:19:14
	
	I never had the time to setup the media control buttons on my laptop 
	Yes..You need to do this manually in dwm
	but its pretty simple and gives you the basic idea of how you can setup your own keybinds
	I did this by editing the config.h file and adding the lines
	
	static const char *mutecmd[]={"pactl", "set-sink-mute", "0", "toggle", NULL};
	static const char *volupcmd[]={"pactl", "set-sink-volume", "0", "+5%", NULL};
	static const char *voldowncmd[]={"pactl", "set-sink-volume", "0", "-5%", NULL};
	
	{ MODKEY,                       XK_F6, spawn, {.v = voldowncmd } },
	{ MODKEY,                       XK_F5,  spawn, {.v = mutecmd } },
	{ MODKEY,                       XK_F7, spawn, {.v = volupcmd   } },
	
	for this you need to have PulseAudio installed
	in order to understand what this command does
	you can visit the man page of "pactl"
	
	
	Date:24-2-23
	Time:12:22
	
	Installed a modular status bar for DWM using 
		'''https://github.com/thytom/dwmbar'''
	installing 
		'''https://aur.archlinux.org/packages/ttf-nerd-fonts-hack-complete-git''' 
	is recommended for icons to show up on the bar
	to modify the modules in the bar  we can edit the 'config' file in /usr/share/dwmbar/ directory
	and I know I didn't mention this before but to set a wallpaper we can use the program called 'feh'
		'''feh --bg-fill `~/Pictures/<PictureName>.png'''
	and adding it to autostart.sh in .dwm/ will automatically set the wallaper when dwm is started
	
	And I also had this problem where 'dmenu' wont start and for it to work we need to set the locale 
	and thats something you do manually in arch ( using the localgen and localectl )
	
	
	Date:06-3-23
	Time:12:23
	
	This is a small change but it kinda still bugs me . Everytime I open a terminal I notice that the 
	color of the prompt and the input is same.This makes it hard for me to notice the different 
	output I get this can be fixed by editing the .bashrc file in your /home directory . We can edit 
	this by opening .bashrc and appending the following line to it
	
		export PS1="\e[0;33m[\u@\h \W]\$ \e[m"
	
	the 0;33 here refers to different colors.
	
		Color	Code
		Black	0;30
		Blue	0;34
		Green	0;32
		Cyan	0;36
		Red	0;31
		Purple	0;35
		Brown	0;33
		Blue	0;34
		Green	0;32
		Cyan	0;36
		Red	0;31
		Purple	0;35
		Brown	0;33
	
	Appending this line fixes my issue and makes the prompt color different from the input one . :D 
	
	Date:14-03-23
	Time:17:32
	
	Installed 'agave Nerd-Font' and applied it to my dwm by editing the line
		static const char *fonts[] =  {"agave Nerd Font mono:size=14"};
	and the dmenu's font by editing 
		static const char dmenufont[]            = "agave Nerd Font Mono:size=14";
	make sure to also edit alacritty's config file (.config/alacritty/alacritty.yml)
	and changing the line "family:monospace" to "family:agave Nerd Font"
	
	Date:21-03-23
	Time:23:28
	
	The best part about using DWM is keybinds so I wanted to create something of my own
	I had bit of trouble connecting to mobile-hotspot everytime so made this quick command using nmcli
	which is 
	
		nmcli device wifi connect $SSID password $pwd
	and assign a keybind using the program 'sxhkd' and made things even better with ascii-art 
	

		༼ つ ▀_▀ ༽つ
		
	So everytime my computer connects to my network it prints an asciit art and plays a beep sound XD! 
	
