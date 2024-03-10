# Kernel Ban FAQ

As I'm currently the maintainer/[builder of some](https://xdaforums.com/f/lenovo-p2-roms-kernels-recoveries-other-devel.6152/) Lenovo P2 (kuntao) custom ROMs (mostly LineageOS (LOS) unofficial), I wanted to have a word with our community regarding the recent kernel ban issued by Google.

## Context

In a given time between January and February 2024, Google issued a ban on some ([maybe many](https://xdaforums.com/t/module-play-integrity-fix-safetynet-fix.4607985/page-518#post-89308909)) custom kernel strings (including those from LOS). The practical result of this was that [suddenly custom ROM users](https://xdaforums.com/t/rom-13-unofficial-lineageos-20-for-lenovo-p2.4563083/post-89339410) noted that the [Play Integrity check wasn't passing anymore](https://t.me/playintegrityfix/148571/174785) and that some apps (like the banking ones) that depend on it stopped working.

In the beginning of March, 2024, as reported by some sources (see [here](https://github.com/TheFreeman193/PIFS#play-integrity-fix-props-collection), [here](https://t.me/PifNEXT/32) and [here](https://xdaforums.com/t/module-play-integrity-fix-safetynet-fix.4607985/post-89375193)), a second wave of bans was issued by Google targeting device finger prints (FPs). Kuntao's FP was affected by it.

## FAQ

### Q1: How can I check my Play Integrity status?

**A:** Use this app ["Play Integrity API Checker"](https://play.google.com/store/apps/details?id=gr.nikolasspyr.integritycheck) by Nikolas Spiridakis

### Q2: Why did you change LOS18.1 sources?

**A:** LOS [officially stated](https://wiki.lineageos.org/quirks/snet/) that they wouldn't be willing to apply nor release any patch that might help evading the Play Integrity checks. So I had to look somewhere else.

### Q3: Wait, so now you have dropped the official LOS18.1 sources, right?

**Short answer:** No.

**Long answer:** To build Android ROMs for kuntao (and some other devices) we need the Android sources, a device tree (DT), vendor and kernel. The ban involves only the kernel strings, so I applied the patch on the [kernel tree](https://github.com/oliveiraleo/android_kernel_lenovo_msm8953) and I'll be using it from now on my LOS18.1 Unofficial builds.

**NOTE:** As I know that having the official sources for some of you is important, in February, 2024 releases there will be two ZIP files (one using the official sources and other with the custom kernel). However I can't promise I'll keep making these separate releases for long as we are currently maintaining LOS18.1, 19.1, 20.0 and more recently 21.0 in a monthly basis.

**Update (10/03/2024):** The second ban wave was directed to device FPs, so I had to apply another patch on [android frameworks tree](https://github.com/oliveiraleo/android_frameworks_base). To try to keep all the folks happy, on March, 2024 I've made two releases too (one built from the official sources and other with the latest patch)

Please, see [FAQ#4 below](#q4-im-using-one-of-your-builds-and-it-failed-to-pass-the-play-integrity-check-what-should-i-do-to-fix-that) and [FAQ#9 too](#q9-im-using-your-patched-los181-march-2024-build-but-play-integrity-is-now-failing-again-what-happened)

### Q4: I'm using one of your builds and it failed to pass the Play Integrity check. What should I do to fix that?

**A:** If your device is **rooted (using Magisk)**, please, follow the instructions from [this thread post](https://xdaforums.com/t/rom-11-unofficial-eol-lineageos-18-1-for-lenovo-p2.4547559/#post-88073787) (scroll down to the "Method #2 - Rooted/Magisk Install​" part). Otherwise, if your device is **not rooted** you still need to wait some more days until the next release cycle*

\* I can't provide an ETA but the devs are working to try to fix this issue and I hope we will have patched working builds

As of February, 29th Google issued a [new device finger print ban](https://t.me/EvolutionXOfficial/1959). This means that our builds will fail the device integrity check for now, even those using [the PIF method](https://t.me/playintegrityfix/183140). Stay tuned to new updates on this situation.

**Update (08/03/2024):** PIF method is working again, update your module

**Update (10/03/2024):** Hot fix builds already have been released for LOS18.1 and LOS21. Updated LOS19.1 and 20 builds will be out on the coming days, thanks for your patience.

### Q5: I already have followed the instructions, my device is passing the Play Integrity check but I can't use my bank app or GPay. What can I do?

**A:** Besides checking the Play Integrity status, apps can detect custom ROMs using other methods. You can try some things like hiding/renaming the Magisk app (app settings > Hide the Magisk app), deleting the TWRP folder from your phone's internal storage, adding the banking app to the Magisk's DenyList, change device props, change device finger print, etc. If none of this works, I don't know what else you can do.

**PS:** If you find a working workaround, please, join our Telegram group (@p2community) and kindly share it with the community ;)

### ~~Q6: What about the other LOS builds?~~

~~**A:** They will have the Play Integrity patch applied on the coming builds, so please, be patient. Hopefully I'll be able to release those builds in the coming days.~~

### Q7: My device isn't passing Play Integrity's strong check, is it normal?

**A:** Yes, as stated on Play Integrity Fix's [official FAQ Q6](https://xdaforums.com/t/pif-faq.4653307/post-89302976) and [repository Wiki](https://github.com/chiteroman/PlayIntegrityFix/wiki/MEETS_STRONG_INTEGRITY), the fix is only for device and basic checks.

### Q8: Is this situation temporary?

**A:** From what I read from the online discussions, the fix should work for a long time (as far as Google or app developers don't update/change their detection methods), however I can't make any assumption, so I'm not sure.

### Q9: I'm using your patched LOS18.1 March 2024 build but Play Integrity is now failing again, what happened?

**A:** Probably the patch isn't working anymore. As mentioned [on FAQ#3 above](#q3-wait-so-now-you-have-dropped-the-official-los181-sources-right), this build was made with the latest patch available applied. However, Google [dropped monthly security patches support for Android 11](https://source.android.com/docs/security/bulletin/2024-03-01#framework) which caused LOS to [pause the development of LOS18.1](https://lineageos.org/Sunsetting-LineageOS-18.1/). As my main objective in making the builds was serving updated security patches, I've decided that the time to stop updating LOS18.1 had come. So our last supported A11 ROM reached its End of Life.

**NOTE:** If you still use LOS18.1, you could prepare to migrate to LOS19.1 or, if storage encryption isn't a requirement for you, to LOS20 (a clean flash will be required whichever option you choose)

## Acknowledgements

I'd like to thank [Chiteroman](https://github.com/chiteroman), [osm0sis](https://github.com/osm0sis) and the PlayIntegrityFix community for [their efforts](https://github.com/chiteroman/PlayIntegrityFix/issues/236) in figuring it out what has happened and then helping with fixing it.

A huge thanks to [Astridxx](https://github.com/Astridxx) and [Alucard-Storm](https://github.com/Alucard-Storm) for maintaining the kuntao DTs, for promptly applying and releasing the patch for our device, and for helping me apply them on my builds.

*Page last updated on March 10th, 2024*