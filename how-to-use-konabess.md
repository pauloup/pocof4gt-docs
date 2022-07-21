# How to Use KonaBess
**Author**: Paulo José Amaro @paulotwain  
**Version**: 0.1.0  
**Created**: 2022.07.17  
**Last Editing**: 2022.07.20

## Translations
- Português do Brasil: [Como usar o KonaBess](pt-br/como-usar-o-konabess.md)

## About
This article will guide you on how to use the KonaBess app for GPU overclock and undervolt, and is part of the [POCO F4 GT - Docs](README.md) project.

It's intended for begginers, and tested on a POCO F4 GT phone.

Check [Optimizing Battery](README.md#optimizing-battery) to know more about how this guide can be useful.

**Warning**: This procedure can make your phone unbootable, if done incorrectly. Please, read all instructions carefully, and make sure to understand what you're doing. Take your time until you feel confident enough.

## Contents
- [You Need](#you-need)
- [Step by Step](#step-by-step)
- [What Next?](#what-next)
- [How to Revert?](#how-to-revert)

## You Need
- **Root**. Check [Rooting Android](README.md#rooting-android).
- [**KonaBess**](https://github.com/libxzr/KonaBess/releases/tag/v0.16) from GitHub. Check [How to install apps from other sources](how-to-install-apps-from-other-sources.md). This guide uses the version 0.16 beta. Other versions may work differently.
- Download the [**KonaBess config**](file-konabess.config.md) file, and keep it in the Download folder.
- [**Franco Kernel Manager**](https://play.google.com/store/apps/details?id=com.franco.kernel), from Play Store. Optional for checking success of this guide, but it'll be required in the [How to Fix CPU Wasting](how-to-fix-cpu-wasting.md) guide, so it's recommended.
- **Files** app, included in MIUI.

## Step by Step
### Step 1
Open **KonaBess**, and it'll ask for Root access. Tap **GRANT**.

![](images/guide-konabess-step01.png)

### Step 2
Select the "**4 Snapdragon 8Gen1"** chipset.

![](images/guide-konabess-step02.png)

### Step 3
Tap **BACKUP OLD IMAGE** to backup the system partition that will be modified. Tap **OK** to confirm.

![](images/guide-konabess-step03.png)

### Step 4
KonaBess will ask for storage access. Tap "**Allow only when using the app**".

![](images/guide-konabess-step04.png)

### Step 5
Open **Files** app and confirm if there's a new "**vendor_boot.img**" file in **Storage**. You don't have to do anything with this file, just keep it safe in case you need it. It's a good idea to store it on a computer.

![](images/guide-konabess-step05.png)

### Step 6
Back to KonaBess, tap **IMPORT/EXPORT**.

![](images/guide-konabess-step06.png)

### Step 7
Tap "**Export to file**" to backup the original GPU configuration to a text file. So that it'll be easy to revert changes using only KonaBess, without having to mess with partition images.

![](images/guide-konabess-step07.png)

### Step 8
Type "**GPU Stock Backup**" in the text field, and Tap **CONFIRM**. This message will show when importing the file. 

![](images/guide-konabess-step08.png)

### Step 9
Open the **Files** app to confirm if there's a new "**konabess-xxx.txt**" file in **Storage**, where "xxx" is a long number. You don't have to do anything with this file, just keep it safe in case you need it. The long number is just current time in "month day hour minute second" format.

![](images/guide-konabess-step09.png)

### Step 10
Back to KonaBess, tap "**Import from file**".

![](images/guide-konabess-step10.png)

### Step 11
Select the "**konabess.config-by.luki2411-for.snapdragon8gen1.txt**" file in Download folder. It has new GPU frequencies, with better performance and less battery usage.

![](images/guide-konabess-step11.png)

### Step 12
Tap **OK** to confirm the importing.

![](images/guide-konabess-step12.png)

### Step 13
Optional: The next step will be applying the changes, so if you want to check how is the GPU before that, you can open **Franco Kernel Manager**, grant Root permissions, and tap **GPU** to open the GPU Control settings. The **Maximum** and **Minimum GPU Frequency** should be reading the stock values of **734 MHz** and **220 MHz**. These values will change after the final step.

![](images/guide-konabess-step13.png)

### Step 14
**Final Step**: It's time to apply the GPU changes. Back to KonaBess, tap **REPACK AND FLASH NEW IMAGE**. KonaBess will take care of everything, and do it quickly, just don't leave the app until it's finished.

![](images/guide-konabess-step14.png)

### Step 15
KonaBess will show some info while applying the changes, and ask to reboot the phone at the end. Tap **YES**, or reboot manually when you're ready.

![](images/guide-konabess-step15.png)

### Step 16
Optional: After the phone boot, to check if the changes are applied successfully, open **Franco Kernel Manager**, and tap **GPU** to open the GPU Control settings. Now **Maximum** and **Minimum GPU Frequency** should be reading the new values of **810 MHz** and **150 MHz**.

![](images/guide-konabess-step16.png)

Notice that if you tap the frequencies on Franco Kernel Manager, you can change them. But this is not necessary, because the system will adjust them by itself.

Interestingly, if you select the maximum frequency of 831 MHz, it'll always revert to 810 MHz. It seems that MIUI limits the GPU maximum frequency to the second biggest one. Sometimes it gets down to 720 MHz. Don't worry, that's normal.

## What Next?
The GPU is now working with more efficient frequencies, and that's the Overclock and Undervolt process goal.

You should notice an improvement in battery life, specially during light usage. It should also give a slight higher GPU score on benchmark apps like AnTuTu.

You can uninstall KonaBess if you want to, because the changes are permanent to the system, and the app don't need to be running.

But every time the ROM gets updated or reflashed, the GPU frequencies will get back to stock values, and you will need to redo this guide. So you may want to let KonaBess installed for future use.

Franco Kernel Manager will be needed for the [How to Fix CPU Wasting](how-to-fix-cpu-wasting.md) guide, so keep it installed also.

## How to Revert?
### The Easy Way
To undo the changes, you can use KonaBess with the option "**Import from file**" from [Step 10](#step-10) to select the backup file "**konabess-xxx.txt**" saved in [Step 7](#step-7). Then tap "**REPACK AND FLASH NEW IMAGE**", and reboot the phone.

### The Hard Way
Another advanced option to revert to stock values is using ADB to flash the "**vendor_boot.img**" partition backup saved in [Step 3](#step-3):
1. Connect the phone to a computer via USB cable, and make sure that **USB Debugging** is enabled in Developer Options.
2. Copy the "**vendor_boot.img**" file to computer Download folder.
3. Restart the phone in **Fastboot** mode by pressing the volume down + power buttons.
4. Open a Command Line window from the Download folder.
5. Run the commands:
    
	`fastboot flash vendor_boot_a "vendor_boot.img"`
	
	`fastoboot flash vendor_boot_b "vendor_boot.img"`
	
	`fastboot reboot`

6. The phone will reboot back to stock GPU values.