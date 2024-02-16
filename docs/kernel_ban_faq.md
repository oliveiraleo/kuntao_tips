# Kernel Ban FAQ

As I'm the current mainteiner/[builder of some](https://xdaforums.com/f/lenovo-p2-roms-kernels-recoveries-other-devel.6152/) Lenovo P2 (kuntao) custom ROMs (mostly LineageOS (LOS) unofficial), I wanted to have a word with our community regarding the recent kernel ban issued by Google.

## Context

In a given time between last January and February, Google issued a ban on some ([maybe many](https://xdaforums.com/t/module-play-integrity-fix-safetynet-fix.4607985/page-518#post-89308909)) custom kernel strings (including those from LOS). The practical result of this was that [suddenly custom ROM users](https://xdaforums.com/t/rom-13-unofficial-lineageos-20-for-lenovo-p2.4563083/post-89339410) noted that the [Play Integrity check wasn't passing anymore](https://t.me/playintegrityfix/148571/174785) and that some apps (like the banking ones) that depend on it stopped working.

## FAQ

### Q1: How can I check my Play Integrity status?

**A:** Use this app ["Play Integrity API Checker"](https://play.google.com/store/apps/details?id=gr.nikolasspyr.integritycheck) by Nikolas Spiridakis

### Q2: Why did you change LOS18.1 sources?

**A:** LOS [officially stated](https://wiki.lineageos.org/quirks/snet/) that they wouldn't be willing to apply nor release any patch that might help evading the Play Integrity checks. So I had to look somewhere else.

### Q3: Wait, so now you have dropped the official LOS18.1 sources, right?

**Short answer:** No.

**Long answer:** To build Android ROMs for kuntao (and some other devices) we need the Android sources, a device tree (DT), vendor and kernel. The ban involves only the kernel strings, so I applied the patch on the [kernel tree](https://github.com/oliveiraleo/android_kernel_lenovo_msm8953) and I'll be using it from now on my LOS18.1 Unofficial builds.

**NOTE:** As I know that having the official sources for some of you is important, in February, 2024 releases there will be two ZIP files (one using the official sources and other with the custom kernel). However I can't promise I'll keep making these separate releases for long as we are currently maintaining LOS18.1, 19.1, 20.0 and more recently 21.0 in a monthly basis.

### Q4: I'm using one of your builds and it failed to pass the Play Integrity check. What should I do to fix that?

**A:** Please, follow the instructions linked below:

- LOS18.1 & LOS19.1: [Click here](https://xdaforums.com/t/rom-11-unofficial-lineageos-18-1-for-lenovo-p2.4547559/post-88073787)
- LOS20.0: [Click here](https://xdaforums.com/t/rom-13-unofficial-lineageos-20-for-lenovo-p2.4563083/post-88260597)
- LOS21.0: Use a non-rooted system, it will pass the check

### Q5: I already have followed the instructions, my device is passing the Play Integrity check but I can't use my bank app or GPay. What can I do?

**A:** Besides checking the Play Integrity status, apps can detect custom ROMs using other methods. You can try some things like hiding/renaming the Magisk app (app settings > Hide the Magisk app), deleting the TWRP folder from your phone's internal storage, adding the banking app to the Magisk's DenyList, etc. If any of this works, I don't know what else you can do.

**PS:** If you find a working workaround, please, join our Telegram group (@p2community) and kindly share it with the community ;)

**NOTE:** This is an ongoing issue and the DTs are in active developmet, as soon as we have an updated patch/method/etc we will release hotfix builds

### Q6: What about the other LOS builds?

**A:** They will have the Play Integrity patch applied on the coming builds, so please, be patient. Hopefully I'll be able to release those builds in the coming days.

### Q7: Is this situation temporary?

**A:** From what I read from the online discussions, the fix should work for a long time (as far as Google/app developers don't update/change their detection methods), however I can't make any assumption, so I'm not sure.

## Acknowledgements

I'd like to thank [Chiteroman](https://github.com/chiteroman), [osm0sis](https://github.com/osm0sis) and the PlayIntegrityFix community for [their efforts](https://github.com/chiteroman/PlayIntegrityFix/issues/236) in figuring it out what has happened and then helping with fixing it.

A huge thanks to [Astridxx](https://github.com/Astridxx) and [Alucard-Storm](https://github.com/Alucard-Storm) for maintaining the kuntao DTs updated and for promptly applying and releasing the patch for our device.

*Page last updated on Feb 16th, 2024*