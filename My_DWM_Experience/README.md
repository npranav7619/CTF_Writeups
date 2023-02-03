# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

	Date:2-2-22
	Time:10:23

	This is my first time writing a blog so i'll try to make it sound intresting as much as 		 possible .But if you're into geeky stuff..I'm Sorry :(
	A week ago i decided to try DWM for the first time. DWM for those who dont know is suckless's "Dynamic Window Manager"
	Window Manager's are similar to desktop environments but they are way lighter and are in general more complex to use .
	Well..more complex to use...but once mastered..It'll be highly productive because everything can be done and managed with just your keyboard and nothing else no GUI..no mouse required.
	So usually in dwm you are given a blank screen with a few keybinds to start a shell and few keybinds to move through the windows for managing the applications 

	So the first thing I wanted to do was to change the default terminal from sh to "alacritty" cuz its way better and I've been using that for a while..so the way you customize your dwm is fairly simple .DWM is built with a .c file .Any changes you want to make is done by editing the .c file and then recompiling it .
	That is done by opening the config.h file in your /dwm directory and changing the terminal option and also changed the text size "14".

	Date:2-2-22
	Time:18:41

	Next thing I wanted to do was fix my dwm-status-bar 
	I wanted the Basic UI to be on the top corner with TEMP,BATTERY-INFO AND DATE-TIME so i found a shell script online that prints these info.
	so once I run the script it prints the data on the top right corner 
	But I wanted this script to run once i log into dwm so i tried multiple ways to do that but the best method was to use an autostart patch 
	Patching in dwm is adding more functionality to the original dwm code.
	It's done using a simple command called 'patch'  (read man patch for more info)
	I was able to install the autostart patch and then add this script to the .dwm/autostart.sh file to it.
	Right now..I really enjoy using this window manager since I have the ability to customize everything I want .I'll update this page with my thoughts on this wm as I use more of this and the problems I face and how I managed to fix them.
