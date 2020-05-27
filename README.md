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

![Screenshot_2020-05-27-57_234x73](https://user-images.githubusercontent.com/28944997/83031122-d1bf6d00-a051-11ea-9f2a-00bac75bcedc.png)

**Battery Discharging(above 50%)**


![Screenshot_2020-05-27-31_240x73](https://user-images.githubusercontent.com/28944997/83031386-1e0aad00-a052-11ea-98ce-a2081e4f77a5.png)

**Battery Discharging(below 50%)**

![Screenshot_2020-05-27-50_240x73](https://user-images.githubusercontent.com/28944997/83031644-70e46480-a052-11ea-86be-02490dac38d7.png)

**Battery Fully Charged**

![Screenshot_2020-05-27-27_258x73](https://user-images.githubusercontent.com/28944997/83031774-a12c0300-a052-11ea-8f4e-247843e2e6a8.png)

**Battery Low(25%)**


![Screenshot_2020-05-27-32_192x73](https://user-images.githubusercontent.com/28944997/83031877-c3258580-a052-11ea-8337-feced07fb41c.png)

**Battery Critical(15%)**

![Screenshot_2020-05-27-19_222x73](https://user-images.githubusercontent.com/28944997/83032007-e819f880-a052-11ea-8f55-e13cb0725143.png)
