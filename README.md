# My i3-dotfiles

These are my current i3 config files. 
This was meant for a virtual machine, so the i3 config will not work due to driver issues on bare metal (never tried it, do not risk it).

I AM NOT A PROFESSIONAL, I JUST GOOGLED SOME STUFF AND THATS IT.

There is an i3 config series which will help you understand how these config and how i3 works in genral. Watch those videos first. 
I used them to get the partial understanding thati have about this.

Also, I will say it here form the get go, these config files are basically copies of another guys config files.

His files :- https://github.com/addy-dclxvi/i3-starterpack

The first video in the guide series - https://www.youtube.com/watch?v=j1I63wGcvU4

Go through this first if you do not know anything about this stuff. This will help you a lot in learning how to troubleshoot and how i3 config editing works in general.

I also installed kde with the graphical debian installer to get stuff doing in a virtual machine (virtualbox was the application used on a macOS Monterey host). 
So if you want to just make this work (and are doing this for the first time and do not have experience), do that.

Remember, I have not tested this in a bare-bones debian install (especially on bare metal). 
You can try it out on a bare-bones debian install on physical hardware, but if it does not work, don't @ me.

Also, there is this weird problem in the debian installer (not exactly a bug but something that was an inconvenince for me later while graphically installing debian)
in which my default user which I wanted to give sudo privileges didn't have them and that /usr/local/bin and /usr/sbin wasn't in the $PATH (their command / programs like shutdown/reboot didn't work out
of the box unless you manually added them manually to the .bashrc).

So first of all, to fix the user problem, in your terminal of choice do:-

su

apt upgrade

cd /usr/sbin

usermod -aG sudo yourusername

 
Use a text editor of your choice to edit the .bashrc. I like micro. If you don't, no worries, you can use anyother. Does not matter which one (nano, vim whatever).

 
sudo apt install micro  

cd ~

micro .bashrc 

 
Add these lines to the end of it :-

export PATH=$PATH:/usr/local/sbin
 
export PATH=$PATH:/usr/sbin
 
Exit out of micro with ctrl + q and press y to write out the changes (esc + shift + colon then type wq in vim).

 
reboot now 
 
 
Debian only will allow you to run commands like that with sudo in the front if you are not in root

 
If that doesn't work
 
cd /usr/sbin
 
./reboot now

Now this should be fine.

 
In order to have no compile errors while you compile your i3 environment, the following dependencies are required:-
 
picom
 
feh 
 
rofi 
 
git
 
kitty

 
You can install all of i3 manually like this(to avoid any possibly missing packages)
 
suckless-tools
 
i3lock
 
i3status
 
dunst
 
i3-wm 

Optonal dependencies (recommended to install because i have them already):-
 
kupfer
 
lxappearnce
 
lightdm
 
nitrogen

 
It is important that the files got to the correct directories. There are many places I use directories or programs in the dot files that simply would not exist in your specific install.
 
So edit them to fit your specific machine

Example (not really because it is a problem) - key words like /home/debian have been used while referencing directories and files. To fix this specififc problem,
replace this with ~ or $HOME

To get the following files:-

git clone https://github.com/shadows1003929/i3-dotfiles.git
 
cd i3-dotfiles

Now you have the files that are in the i3-dotfiles folder and you are in it. Make the changes to patch it (because there are most likely problems with it).

Now, do the following (make sure you are in the i3-dotfiles directory):-
 
mkdir ~/.config/i3status && mkdir ~/.config/dunst ## if you already do not have the i3status and dunst directories. To check if they already exist, do - 
 
cd ~/.config/
 
ls

After checking or creating the directories do the following :-
  
cd ~/i3-dotfiles
 
sudo mv config-i3 config
 
sudo rm -rf ~/.config/i3/config
 
sudo mv config ~/.config/i3/
 
sudo mv config-i3status config
 
sudo rm -rf ~/.config/i3status/config/
 
sudo mv config ~/.config/i3status/
 
sudo mv dunstrc ~/.config/dunst/
 
sudo mv compton.conf ~/.config/

Now everything should be fine

 
If you want to use lightdm:-
 
sudo apt install lightdm

It will prompt you to use it or not. Select lightdm.

 
Now press the keys $mod + shift + r ($mod is the one modifier key you set. mod1 = alt, mod4 = win key/ command key on macs(i think))
 
If there are compile errors, fix them

 
This step is needed to ensure that your i3 config file is not messed up because if it was and we directly rebooted, well, consider it screwed unless you are lucky.
Also, always reload your i3 after making changes to the config file. If i3 acts wonky while saying there are no errors, you can try to fix the culprit that you
think is causing the problem and then you can reboot (i have experienced situation like that, don't worry, it ain't the end of the world).

Now you can reboot

 
Hopefully it works!



