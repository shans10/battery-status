# battery-status
This is a small bash script that uses upower to get the battery status and dunstify to show notifications! It does not do much the only purpose of this script for me was to find a replacement for xfce4-power-manager battery status notifications and notify me about various battery states. This script goes hand in hand with my spectrwm setup that I built along with few other small scripts. Also I just familiarized with bash scripting so this was for fun and practice as I was getting bored sitting at home!

Namely 5 categories of notifications are displayed:-
* Battery Plugged In
* Battery Discharging (2 different icons one for above 50% and one for 50% and below)
* Battery Fully Charged
* Battery Low(25%)
* Critical Battery(15%)

**Following things are by design and not a mistake:-**

1). If the battery is plugged in during startup it will give a notification for battery plugged in but no discharging notification will be displayed on startup if the battery is unplugged.

2). Battery low and battery critical notifications are displayed on startup if and only if battery is discharging and not if it is plugged in.

3). Discharging notification is triggered only when battery has been plugged once and then removed after startup.

4). On startup if battery is not plugged in then low battery notification is triggered if the battery is 25% or below and above 15%, if the battery is 15% or below then critical battery notification is triggered instead.

## Requirements
* Upower
* Dunstify(Dunst)

## Getting Started 
* Clone the repository and cd into the folder. 

`git clone https://github.com/shans10/battery-status.git && cd battery-status`

* Copy the script into the /usr/local/bin folder.

`sudo cp battery_status /usr/local/bin/`
* Copy the "battery_status.service" file inside `~/.config/systemd/user/` folder if the folder exists otherwise create the folder and then copy the file into it.

* Copy the icons inside the "icons" folder in `~/.icons/` folder.

* Finally enable start the battery_status service as the current user.

`systemctl --user enable battery_status.service && systemctl --user start battery_status.service`

## Usage Instructions
* My battery is BAT0. If the script does not work find your battery number using "acpi" command and edit the script accordingly!

* You can edit the script and use notify-send instead of dunstify but I prefer dunstify because of its ability to assign ids to notifications!

* You can change the icons and use the ones you want by editing icon path inside the script!

## Screenshots

**Battery Plugged In**

![Battery Plugged In](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-plugged-in.png)

**Battery Discharging(above 50%)**


![Battery Discharging(above 50%)](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-disch1.png)

**Battery Discharging(below 50%)**

![Battery Discharging(below 50%)](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-disch2.png)

**Battery Fully Charged**

![Battery Fully Charged](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-full.png)

**Battery Low(25%)**


![Battery Low](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-low.png)

**Battery Critical(15%)**

![Battery Critical](https://github.com/shans10/battery-status/blob/master/Screenshots/bat-critical.png)
