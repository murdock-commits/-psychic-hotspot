# psychic-hotspot
**How to turn on hotspot using Bash Scripting on Linux ?**

**4 Basic Steps :**

1.	Create a script file i.e. a file with *.sh* extension.
 (Name can be whatever you find suitable; in this case we're gonna name it : psychic-hotspot)
 
 2.	Paste the code present at the end of the page in *psychic-hotspot.sh*
3.	Make the file executable using either

		sudo chmod +x psychic-hotspot.sh
or  Properties -> Permissions -> Allow executing file as a program

4.	Execute the file by either

		./psychic-hotspot.sh
		
	or double-clicking.

***

**Copy-paste this:**

	#! /bin/bash
	
	if [[ $(nmcli radio wifi) = *enabled* ]]; then
	    
	    if [[ $(nmcli connection show --active) =        *Hotspot* ]]; then
	    notify-send "Hotspot is already connected" -i face-surprise
	    else
	    nmcli c up Hotspot && notify-send "Hotspot Connected!" "Let's go..." -i face-wink
	    fi
	
	else
	    nmcli radio wifi on && notify-send "Connecting..Please wait." -i content-loading-symbolic;
	    nmcli c up Hotspot && notify-send "Hotspot Connected!" "Let's go..." -i face-wink
	
	fi
	
***

**NOTE:** 
1.*Hotspot* in the code should be replaced with the SSID of your hotspot.

**Relevant article**: [How to create a Wi-Fi Hotspot on Linux Mint](https://www.fosslinux.com/15132/how-to-create-a-wi-fi-hotspot-on-linux-mint.htm) (Should be similar for anything other than Mint)

2.How *notify-send* will look depends on your OS.

3.The *-i* argument is optional.

