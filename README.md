
# Auntie's Guide to Installing Windows 11
by Eris *"my sweet girl"* Ivy and iFlex0x

![Eris waving gif](/Wave.gif)

**Hi!** This is a guide on how to install and setup **Windows 11** on your new computer. I'm handwriting this guide for you because Windows is a bit of a problem-child and we'll need to take serious precautions to get the 'best' experience out of it.

Unlike MacOS, Windows is notorious for bloatware, ads, telemetry, and overall just an unpleasant user experience; which makes it all the more comforting to know that most of the world's computers run this garbage. My personal gripes aside; it's the only other operating system that officially supports the Adobe creative suite and *the* go-to place for high-end gaming.

The biggest problem with Windows 11 is the mandatory use of a Microsoft account to log in. **We are not going to be doing this**, for a multitude of reasons. On Windows 11, there is a program that auto-backups files to the cloud; similar to MacOS' iCloud. 
Which is nice to have, but the problem is that its the **default** storage. Any file you download will quietly back itself up and a couple weeks down the line you'll be pestered to "**upgrade your OneDrive storage**".

To avoid this entirely we're just not going to log in with a Microsoft account. Normally this requires jumping through a bunch of hoops during setup — but we've already done the hard work for you. We used a tool called [Chris Titus's Win11 Creator](https://winutil.christitus.com/userguide/win11creator/) to patch a Windows 11 image that skips all of that nonsense automatically. Friends don't let friends use OneDrive <3

**The install process I've organized into three chapters:**
- 1. Flashing Windows 11 to USB drive
- 2. Installing Windows 11 on your computer
- 3. First-time setup

and after that, a guide on how to tweak your BIOS and install drivers so your computer is working to it's full potential!

*Before we get started, remember the following:*

- ***DO NOT SIGN IN WITH A MICROSOFT ACCOUNT***
- ***DO NOT GIVE ANY PERSONAL INFORMATION OR DATA TO MICROSOFT***

I've already patched a Windows 11 image using Win11 Creator and uploaded it for you. 
You can download it here: [drive.google.com/Win11_Modified_20260428.iso](https://drive.google.com/file/d/1e-8eAAd9rGLksEZx1ISV3YMRGyfRbkkr/view?usp=sharing) (*7.07 GB*)

This is a modified `.iso` file — it has OneDrive removed, telemetry disabled, bloatware stripped out, and it's set up to let you create a local account without Microsoft getting involved. You don't need to do any of the manual bypass tricks that older guides describe.

Alright cool, let's get started!

---
### 1. Flashing Windows 11 to USB drive
- Download the [patched Windows 11 image](https://drive.google.com/file/d/1e-8eAAd9rGLksEZx1ISV3YMRGyfRbkkr/view?usp=sharing) linked above
- Download and install [WinDiskWriter](https://github.com/TechUnRestricted/WinDiskWriter/releases/tag/v1.3)
	- You may need to allow this program to run by going into "Privacy & Security" in your system settings. Scroll down to "Security" and click "Open Anyway"
- Plug your USB drive into your Mac
- Choose the `.iso` file you downloaded for **"Windows Image"** in WinDiskWriter
- Select your USB drive under **"Target Device"**
	- It may not be necessary as you will be buying brand-new computer parts but check `Patch Installer Requirements` and use the `FAT32` file system
- Click `Start` to flash Windows to the USB drive
- Once finished, eject the USB drive from Finder

### 2. Installing Windows 11 on your computer

- Plug the USB drive into a front USB port
- Power on the computer
- Go through the install as normal for language and keyboard layout
	- If asked for a key, say "I don't have a product key" 
- Choose "Install Windows 11 Home"
	- If asked, install on `WD_Black SN850X` or whatever your SSD shows up as
- Accept the terms and install

Windows will take a few minutes to install, and then reboot into the setup screen.

### 3. First-time setup

Because the image is already patched, Windows will handle most of the annoying stuff on its own. You won't need to do any terminal tricks or disconnect from the internet — it's already taken care of.

Just go through the setup normally:

- Choose your region and keyboard layout(s)
- Enter your name

This name will also be your computer's name. If you chose "Ava" the path to your videos folder will be `C:\Users\Ava\Videos`

- Enter your password
- Fill out the security questions

Windows will load for a minute and then show your desktop. Congratulations! We're in Windows 11!

# Windows Driver Installation

You're at the desktop now! Windows 11 is currently running on it's built-in drivers which will *function* but are not recommended for daily usage, so we need to install drivers. *Drivers* are little bits of code that help your software and hardware communicate effectively. Outdated drivers can cause bugs, graphical glitches, and instability so we'll need to update them as soon as we can.

The tweaks and drivers we'll be installing will be organized in three chapters
- 1. RAM 
- 2. Motherboard Drivers
- 3. Graphics Card (GPU) Drivers

#### 1. RAM

Your RAM (G.Skill Trident Z5) has a profile called '*AMD EXPO*' that needs to be enabled manually to run at the speed it was built for. Out of the box it will run slower than advertised but the fix is quite simple and it involves configuring the **BIOS**

The **BIOS** is a menu that's baked-in to your motherboard and allows you to tweak settings for your system as a whole; even before Windows 11 starts up.

**Here's how to enter the BIOS and enable the XMP profile**
- Shut down the computer and press the power button
- As soon as the Gigabyte logo pops up, press the `delete` key repeatedly
- Once in the **BIOS**, under "EASY MODE" look for the `XMP/EXPO` drop down option
- Click it and select the "**XMP 1**" option
- Press `F10` on your keyboard to save and exit

The computer will restart itself and boot back into Windows 11, now your ram will run at it's advertised speed and you won't have to think about it again.

---

#### 2. Motherboard Drivers

The motherboard has a few drivers that will need to be installed. These drivers help your motherboard--and all of the things connected to it--work better together. Go to the [Gigabyte X870 EAGLE WIFI7 support page](https://www.gigabyte.com/Motherboard/X870-EAGLE-WIFI7-rev-1x/support) and click the download icon for each of the following:

- **AMD Chipset Driver**
- **Realtek HD Audio Driver**
- **WLAN/Bluetooth Driver**
- **LAN Driver**

These will download in `.zip` files and will need to *extracted*; you will need to install the **AMD Chipset Driver** first so let's start with that one:

- Double click on the downloaded `mb_driver_597_chipset_7.12.04.858.zip` file
- Once inside, click on "Extract all" towards the top of the window
- in "Select a Destination and Extract files" go down the bottom right and click "Extract"
	- (if needed, check "Show extracted files when complete")
- Double click on the `.exe` file and continue through the setup

Let the installer work it's magic and when it's finished you will be asked to restart your computer. We'll need to restart a few times throughout this process, skipping restarts can cause weird issues and problems down the line. It's annoying, but once you get all of this set up you will be golden.

Like how you extracted the files from the AMD Chipset `.zip` file, do the same exact process for the rest of the drivers. Unlike the chipset driver, *you can install these in any order* but to keep in line with the guide let's start with the **Realtek HD Audio Driver**. Same process as before:

- Double click on the downloaded `mb_driver_612_realtekdch_6.0.9927.1.zip` file
- Once inside, click on "Extract all" towards the top of the window
- in "Select a Destination and Extract files" go down the bottom right and click "Extract"
	- (if needed, check "Show extracted files when complete")
- Double click on the `.exe` file and continue through the setup

Rinse-and-repeat this process for the **WLAN/Bluetooth Driver** and the **LAN Driver** and you'll be finished with motherboard drivers.

Back on the [Gigabyte X870 EAGLE WIFI7 support page](https://www.gigabyte.com/Motherboard/X870-EAGLE-WIFI7-rev-1x/support) on the left side, click on the **BIOS** tab to see if there is a newer version than what's on the board. Updating it isn't *required* but its worth doing at some point; it usually improves memory compatibility and fixes things that the manufacturer--Gigabyte--caught after launch. There will be instructions on how to update your BIOS from a USB drive if you need to do it.

---

#### 3. Graphics Card (GPU) Drivers

NVIDIA App (the GPU driver installer by Nvidia) has a habit of bundling in extra software that is unnecessary and annoying; GeForce Experience, Ansel, and multiple telemetry services that run in the background constantly. To avoid unnecessary bloat and telemetry, we're going to use a free tool called **NVCleanstall** instead.

- Download [NVCleanstall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/)
- Select the American flag icon with "closest to you" underneath it
- Run NVCleanstall
- Click **Next** on the bottom right

in the "Select Components To Install" screen, enable the following:
- `Display Driver (required)`
- `HD Audio via HDMI`
- `PhysX`

Everything else can be left unselected, click **Next** to continue.
- In "Installation Tweaks" leave everything unchecked
- click **Next** to continue
- click **Install** to begin installing the GPU drivers
- Accept NVIDIA's terms and conditions
- click **Next** on installation options (the recommended installation is "*Express*")
	- The screen will turn black a few times as it finishes installing, this is normal and expected
- Once the installation is finished, click **Close** on the Nvidia Driver Installer
- click **Close** on NVCleanstall

Now your GPU drivers are up to date!

---

**Corsair iCUE**

The AIO (the LINK TITAN 360) and all the fans; the six LL120s on intake, the LL140 exhausting out the back, and the three AIO fans going out the top; are all managed through Corsair's iCUE software. Without it they'll run at a fixed speed with no curve and no way to adjust them.

- Download and install [Corsair iCUE](https://www.corsair.com/us/en/s/downloads)
- It should pick up the AIO and fans automatically when it opens
- Head into **Cooling** to set up a fan curve. For a PC that's mostly sitting at a desk being used for work, something that holds around 30-40% until temperatures hit 60°C and ramps from there keeps things quiet without sacrificing cooling when it matters.
- **Lighting** is in there too if you want to set colors or just turn it all off

The LL120s and the LL140 all connect through the LINK hub inside the case so they show up together as one group in iCUE rather than individually. Should be pretty intuitive from there.

---
