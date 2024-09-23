# Troubleshooting

### Features Not Working?

Disable **Safe Mode** under the **SAFE MODE** panel on the main hake menu. If disabling Safe Mode doesn't help you, try reinstalling the **[Required Files](https://hake.me/forums/forums/hardware-id-resets.12/)**.

​![](https://hake.me/docs/user/pages/01.introduction/02.troubleshooting/dota2_2018-06-28_16-02-59.png)​

### Hardware ID Does Not Match

Our software utilizes a hardware ID system, so you may only use it on one computer at a time. If you need to reset your hardware ID, visit **[this](https://hake.me/forums/account)** page, and click **Reset HWID**. Keep in mind that you may only do this **once per week**. If you need another reset, make a thread in **[this](https://hake.me/forums/forums/hardware-id-resets.12/)** forum explaining why.

​![](https://hake.me/docs/user/pages/01.introduction/02.troubleshooting/9FSwuzu.png)​

### Client stuck at injecting software (or crashes)

If the client is stuck at the **injecting software** stage (or it crashes) and it used to work fine then your version of Windows probably updated. All you need to do to fix this is redownload the client.

### Dota 2 Crashing

There are a number of things that can cause Dota 2 to crash when using our software. Here is a list of the most common culprits:

* Dota 2 Update - Dota 2 updates **VERY** frequently. Make sure that you have the latest version of Dota 2 before you try using our software. Occasionally, Dota 2 will have an update that won't be compatible with our software, in which case you will have to wait for us to fix it.
* Bad/Outdated Script - Outdated lua scripts are a very common culprit when experiencing frequent crashes. The first thing you should do is check your **log.txt** file for any outstanding scripting errors. If the log doesn't give any useful information, then you'll have to do some testing.  
  To confirm whether or not a lua script is causing the issue, disable your scripts through the Hake menu in game, or delete them from your **scripts folder**. You may also rename your **scripts folder** to something else, which will effectively disable your scripts without needing to delete them. If the crashing problems cease after disabling your lua scripts, then you'll need to figure out which script is causing the crash. Unfortunately, the only real way to do this is to test each script individually.

### Failed to Launch Target Software

Here is a list of potential fixes for this particular issue:

* Try restarting your computer.
* Make sure that you have Dota 2 installed and fully updated.
* Disable your anti-viruses, firewalls, and Windows Defender.
* You might unknowingly have multiple versions of Dota 2 installed, and the client is trying to launch an older version. Check your file path to Dota 2 by right clicking it in Steam, and going to Properties \> Local Files \> Browse Local Files. Make sure it matches up with the file path that can be found in **clientlog.txt**. If it doesn't match up, then you need to find your old installation of Dota 2, and remove it.
* If all else fails, try closing out of any unnecessary programs that you may have running in the background. One of them might be interfering with the client.
