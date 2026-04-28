
# Auntie's Guide to Installing Windows 11
by 
- Eris "my sweet girl" Ivy
- iFlex0x

![Eris waving gif](/Wave.gif)

**Hi!** This is a guide on how to install and setup **Windows 11** on your new computer. I'm handwriting this guide for you because Windows is a bit of a problem-child and we'll need to take serious precautions to get the 'best' experience out of it.

Unlike MacOS, Windows is notorious for bloatware, ads, telemetry, and overall just an unpleasant user experience; which makes it all the more comforting to know that most of the world's computers run this garbage. My personal gripes aside; it's the only other operating system that officially supports the Adobe creative suite and *the* go-to place for high-end gaming.

The biggest problem with Windows 11 is the mandatory use of a Microsoft account to log in. **We are not going to be doing this**, for a multitude of reasons. On Windows 11, there is a program that auto-backups files to the cloud; similar to MacOS' iCloud. 
Which is nice to have, but the problem is that its the **default** storage. Any file you download will quietly back itself up and a couple weeks down the line you'll be pestered to "**upgrade your OneDrive storage**".

To avoid this entirely we're just not going to log in with a Microsoft account. Normally this requires jumping through a bunch of hoops during setup — but we've already done the hard work for you. We used a tool called [Chris Titus's Win11 Creator](https://winutil.christitus.com/userguide/win11creator/) to patch a Windows 11 image that skips all of that nonsense automatically. Friends don't let friends use OneDrive <3

**The install process I've organized into four chapters:**
- 1. Flashing Windows 11 to USB drive
- 2. Installing Windows 11 on your computer
- 3. First-time setup
- 4. Drivers and software

*Before we get started, remember the following:*

- ***DO NOT SIGN IN WITH A MICROSOFT ACCOUNT***
- ***DO NOT GIVE ANY PERSONAL INFORMATION OR DATA TO MICROSOFT***

I've already patched a Windows 11 image using Win11 Creator and uploaded it for you. 
You can download it here: [drive.google.com/Win11_Modified_20260428.iso](https://drive.google.com/file/d/1e-8eAAd9rGLksEZx1ISV3YMRGyfRbkkr/view?usp=sharing) (*7.07 GB*)

This is a modified `.iso` file — it has OneDrive removed, telemetry disabled, bloatware stripped out, and it's set up to let you create a local account without Microsoft getting involved. You don't need to do any of the manual bypass tricks that older guides describe.

Alright cool, let's get started!
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

### 4. Drivers and software

You're at the desktop now. Windows is running on built-in drivers which will *function* but are not recommended for daily usage, we so we need to install drivers. *Drivers* are little bits of code that help your software and hardware communicate effectively. Outdated drivers can cause bugs, graphical glitches, and instability so we'll need to update them as soon as we can.

#### RAM

Your RAM (G.Skill Trident Z5) has a profile called '*AMD EXPO*' that needs to be enabled manually to run at the speed it was built for. Out of the box it will run slower than advertised but the fix is quite simple and it involves configuring the **BIOS**

The **BIOS** is a menu that's baked-in to your motherboard and allows you to tweak settings for your system as a whole; even before Windows 11 starts up.

**Here's how to enter the BIOS and enable the XMP profile**
- Shut down the computer and press the power button
- As soon as the Gigabyte logo pops up, press the `delete` key repeatedly
- Once in the **BIOS**, under "EASY MODE" look for the `XMP/EXPO` drop down option
- Click it and select the "**XMP 1**" option
- Press `F10` on your keyboard to save and exit

The computer will restart on it's own and boot back into Windows 11, now your ram will run at it's advertised speed and you won't have to think about it again.

---

**Motherboard drivers**

Go to the [Gigabyte X870 EAGLE WIFI7 support page](https://www.gigabyte.com/Motherboard/X870-EAGLE-WIFI7-rev-1x/support) and click the Driver tab. You want these four, installed in this order:

1. **AMD Chipset Driver** — do this one first. It's the most foundational thing on the list and the rest of the drivers will behave better after it's in. Restart when it asks.
2. **Realtek HD Audio Driver** — for the audio ports on the back panel.
3. **WLAN/Bluetooth Driver** — for WiFi and Bluetooth. The board shipped with a WiFi antenna; if it's not already plugged in, there are two gold screw connectors on the back of the case and the antenna cables attach there.
4. **LAN Driver** — for the wired ethernet port.

Restart after each one when it asks you to. I know it's annoying but skipping restarts causes weird problems down the line.

While you're on that page, check the **BIOS** tab too and see if there's a newer version than what's on the board. Updating it isn't required right now but it's worth doing at some point; it usually improves memory compatibility and fixes things Gigabyte caught after launch. There are instructions on the page for how to flash it from a USB drive.

---

**GPU drivers**

NVIDIA's installer has a habit of bundling in things you genuinely do not want; GeForce Experience, a game capture tool, a screenshot app called Ansel, and multiple telemetry services that run in the background forever. The "custom install" option in NVIDIA's own installer doesn't actually let you remove most of it. We're going to use a free tool called NVcleanstall instead, which does.

- Download [NVcleanstall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/)
- Click on the American flag icon with "closest to you" underneath it
- It'll pull the latest driver for the RTX 5080 automatically
- Before clicking next, switch the driver type from **Game Ready** to **Studio Driver** in the dropdown. Studio drivers are tested against creative software specifically and are more stable for that use case; since this PC isn't for gaming there's no reason to use Game Ready.
- Click **Next** and you'll see the component list. Here's what to do with it:

Keep these:
- `Display Driver`
- `HD Audio via HDMI` (for audio through a monitor over DisplayPort or HDMI)
- `PhysX`

Remove everything else:
- `GeForce Experience` and/or `NVIDIA App`
- `Telemetry`
- `Ansel`
- `Shadowplay` / `Highlights`
- `USB-C Driver`
- `3D Vision`

Click through and install. Your screen will go black a couple times while it runs; that's normal.

---

**Corsair iCUE**

The AIO (the LINK TITAN 360) and all the fans; the six LL120s on intake, the LL140 exhausting out the back, and the three AIO fans going out the top; are all managed through Corsair's iCUE software. Without it they'll run at a fixed speed with no curve and no way to adjust them.

- Download and install [Corsair iCUE](https://www.corsair.com/us/en/s/downloads)
- It should pick up the AIO and fans automatically when it opens
- Head into **Cooling** to set up a fan curve. For a PC that's mostly sitting at a desk being used for work, something that holds around 30-40% until temperatures hit 60°C and ramps from there keeps things quiet without sacrificing cooling when it matters.
- **Lighting** is in there too if you want to set colors or just turn it all off

The LL120s and the LL140 all connect through the LINK hub inside the case so they show up together as one group in iCUE rather than individually. Should be pretty intuitive from there.

---
