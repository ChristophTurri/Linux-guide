Convert EndeavourOS XFCE offline edition to Arch Linux
-----------
Overview:
1. Edit grub. 
2. Delete the Endeavour packages
3. Edit pacman.conf
4. Delete pacman hooks
5. Delete the sync database
6. Edit mirrorlist files
7. Edit release files.
8. Edit LightDm settings
9. Edit XFCE whisker menu 

Step 1, Grub.
------------

* Edit. /etc/default/grub file


* Change.

GRUB_DISTRIBUTOR="EndeavourOS"
to
GRUB_DISTRIBUTOR="Arch"

* Comment out.

GRUB_THEME=/boot/grub/themes/EndeavourOS/theme.txt

* Update Grub.

sudo grub-mkconfig -o /boot/grub/grub.cfg

Step 2, Delete all EndeavourOS packages
-----------------
List all Endeavouros packages (installed and not installed):
sudo pacman -Sl endeavouros

Possible packages (could be more): 
```sh
endeavouros arc-x-icons-theme 2.1-3 [installed]
endeavouros downgrade 6.2.5-1 [installed]
endeavouros endeavouros-keyring 1-4 [installed]
endeavouros endeavouros-mirrorlist 2-1 [installed]
endeavouros endeavouros-theming 5-1 [installed]
endeavouros endeavouros-xfce4-terminal-colors 1-1 [installed]
endeavouros eos-update-notifier 1.0.7-1 [installed]
endeavouros grub-tools 1.2-1 [installed]
endeavouros grub2-theme-endeavouros 20190711-4 [installed]
endeavouros mkinitcpio-openswap 0.1.0-3 [installed]
endeavouros paper-icon-theme 1.5.0-2 [installed]
endeavouros reflector-simple 1.3.3-1 [installed]
endeavouros welcome 2.4.42-1 [installed]
endeavouros yay 9.4.6-2 [installed]
```

* Install and/or select all Endeavouros themes and icons themes at this point to prevent any potential issues

* Now delete the packages:
List all packages:
sudo pacman -Q 

List all packages not in a repo (for still installed endeavouros packages):
sudo pacman -Qm

List all packagegroups:
sudo pacman -Sg <Paketgruppe>

Now delete all Endeavouros packages with sudo pacman -R

optional: reinstall mkinitcpio-openswap from the AUR!


Step 3, Edit pacman.conf
----------------------

Removed the [endeavouros] section from /etc/pacman.conf


Step 4, Delete pacman hooks
----------------

* Removed the two EOS-specific branding hooks in /etc/pacman.d/hooks

cd/etc/pacman.d/hooks

sudo rm lsb-release.hook os-release.hook 


Step 5, Delete the sync database
-----------------

rm /var/lib/pacman/sync/endeavouros.db

Step 6, mirrorlist files
------------------

* At etc/pacman.d , Remove the endeavour mirrorlist and replace with new mirrorlist(download new mirrolist and edit 
As per arch wiki) or simply rename.

Step 7, Edit release files.
-----------------------
 
* change the following release files

1. /etc/lsb-release

```sh
LSB_VERSION=1.4
DISTRIB_ID=Arch
DISTRIB_RELEASE=rolling
DISTRIB_DESCRIPTION=”Arch GNU/Linux”
```



2. /usr/lib/os-release    ,  edit 


Step 8, LightDm 
------------------------------

* LightDM GTK+ greeter settings tool remove "text=endeavourOS" in Panel tab.
 
* In /etc/lightDM/lightdm-gtk-greeter.conf , change background setting

Step 9 , XFCE Whiskermenu
-------------------------
* Edit /etc/skel/.config/xfce4/panel/whiskermenu-1.rc to remove referneces to endeavourOs
