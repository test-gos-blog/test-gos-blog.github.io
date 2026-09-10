+++
title = "The major flaws behind Android security patching"
description = "Explaining the systematic issues with Android's security patching that GrapheneOS addresses"
+++

Android users should already be familiar with receiving regular updates for patching known security vulnerabilities. Each month, Google publishes an Android Security Bulletin (ASB) describing the vulnerabilities addressed during that month's security release, while device manufacturers distribute corresponding over-the-air (OTA) updates to their supported devices.

Behind this seemingly simple process is a coordinated effort from Google, hardware vendors, original equipment manufacturers (OEMs) and mobile carriers. The Android Open Source Project (AOSP) is a large collection of upstream open source software used to build Android; each component has its own vulnerability management procedures, most notably the Linux kernel. Device manufacturers may also have vulnerabilities that exist only in their customized Android distributions.

While Google discloses information about Android security vulnerabilities to the public through Android Security Bulletins and releasing the patches to AOSP on a monthly basis, the actual production and release of these patches happen much earlier than their general availability to users. This article explains how Android patching works and highlights shortcomings in the current Android security patching regime.

## Overview

Security patching is the process of fixing discovered security vulnerabilities and delivering those fixes to end users. For Android, patches are commonly delivered via OTA updates, typically once a month. Updates are delivered by OEMs who are responsible for building and shipping updates to their own devices. As a result, not every Android device will receive all patches or get them on the same schedule. 

Whether a device continues to receive patches depends on support commitments of the manufacturer, which vary widely. Flagship devices by leading OEMs try to deliver updates for more than five years, while mid to low-range devices generally receive updates for a shorter amount of time. Some may be quite delayed in delivering patches on a monthly schedule.

When Google discusses security vulnerabilities in Android, they mean issues that affect the device as a whole, such as vulnerabilities in the Android platform code or in the Linux kernel, which directly impacts Android systems. Vulnerabilities in the drivers and firmware that hardware vendors supply for components like modems, GPUs, and other chipsets are also covered.

In addition, OEMs and device manufacturers are responsible for vulnerabilities in components they add or customize, such as pre-installed applications and vendor-specific drivers and firmware. Those fixes follow their own scheduling rather than Google’s monthly cadence.

## Android Security Bulletins

The Android Security Bulletin (ASB) is a monthly advisory published by Google that documents vulnerabilities addressed in Android for that release. Each bulletin typically includes details such as:

- The vulnerability's Common Vulnerabilities and Exposures (CVE) identifier
- Severity
- Affected component(s)
- Whether the vulnerability is known to be exploited in the wild

Each ASB defines one or more **Security Patch Levels (SPLs)&#32;**represented as dates. These are commonly in the form **YYYY-MM-01** and **YYYY-MM-05,&#32;**corresponding to the first and fifth day of the month. An 01 SPL includes security vulnerabilities addressed in the Android platform, while an 05 SPL additionally includes additional fixes for upstream components, such as the Linux kernel and firmware/drivers by hardware vendors.

An SPL identifies the minimum set of security patches included on a device. For example, a device reporting an SPL of 2026-06-05 means that the device includes all patches associated with that SPL and all earlier SPLs. Since an SPL only identifies a minimum set, it is important to note that an SPL does not represent every security fix available. Device manufacturers may add patches for their proprietary components not covered by the bulletin or include patches scheduled for a future security patch level.

## Patching in Android upstream components

AOSP (and by extension all Android distributions) is built on top of Linux, which is a large upstream component made up of multiple third-party components. The Linux kernel is the most significant upstream component. When kernel vulnerabilities are discovered, they are fixed upstream and then backported into Linux long-term support (LTS) branches that are used by Android. 

From there, Google maintains Android Common Kernels (ACKs), which merge upstream LTS kernel fixes and related security patches in their own (slower) schedule. The consequences of this will be discussed below.

Android also includes many other upstream third-party components that have their own vulnerability management and patching processes independent of Google, including FreeType, SQLite, libpng and others. Covering the full list would be outside the scope of this article.

## Vulnerability discovery in Android

Android vulnerabilities are often discovered as a part of Google's bug bounty program where researchers try to discover security vulnerabilities in return for financial compensation. In the past, the GrapheneOS Foundation has submitted discovered vulnerabilities to Google and received bounties. The rules of what Google covers in their program and expected financial compensation can be found on their [Security Reward Program Rules page](https://bughunters.google.com/about/rules/android-friends/android-and-google-devices-security-reward-program-rules).

Google's bounty program doesn't just cover Android but also their Pixel devices. The highest reward ceilings are associated with exploits involving Google’s Titan M2 secure element, which appears only in Tensor Pixels.

## Timing and distribution challenges

We believe that Google's current system for developing and distributing Android security patches is fundamentally problematic. Currently, Google first provides "preview" security patches to Android partners under embargo. This gives major OEMs access to patches months before the vulnerabilities are publicly disclosed in an ASB. Despite this extended early access, many OEMs do not make these patches available to end users until Google schedules to release it themselves. A common misconception is that OEMs cannot distribute the patches until Google does, but this is actually not true.

The result is a prolonged window where numerous vulnerabilities - including Critical and High severity issues - are known to Google and partners but remain unpatched on most devices. These exposure windows can span multiple months. 

As a consequence, almost no Android devices in the hands of general users are actually receiving the bare minimum of security patches. Given the wide ecosystem of Google partners, it is plausible that exploit developers could also gain early access to the patches, allowing them to produce exploits.

## Kernel patching

Google updates the LTS kernel used in Android distributions infrequently - typically only every few months. This leaves out hundreds if not **thousands** of Linux kernel security vulnerabilities disclosed between those periods. With the increase of disclosed vulnerabilities thanks to developments in AI-assisted vulnerability discovery, this number is only going to drastically increase. For example, [the Linux kernel had over 400 vulnerabilities assigned](https://app.opencve.io/cve/?q=vendor%3Alinux+AND+product%3Alinux_kernel+AND+created%3D2026-07-19) on July 19th.

The security of Android is therefore significantly constrained by the size and complexity of the Linux kernel. It is the largest attack surface, even with additional hardening in both Android and GrapheneOS. The Linux kernel has less protection against exploitation than the rest of the Android operating system does. The majority of the Linux Kernel is written in a memory unsafe language, which makes it far more vulnerable to memory corruption, a type of vulnerability that is overwhelmingly represented in both Critical and High severity Android CVEs.

## Backporting of patches

For the past several years, Android released security patches to the latest major version of Android, while providing partial backports to the past three major yearly releases. However, these backports usually excluded Moderate and Low rated vulnerabilities, requiring users to upgrade to the newest major release for full patch coverage.

Recently, this policy has begun to change. Security patches for vulnerabilities discovered by Google are now only backported to the last two major releases, and only include Critical vulnerabilities that are deemed an imminent risk. Google themselves are leaders in discovering vulnerabilities in Android, so the reality is that most vulnerabilities are only ever covered in the latest major version of Android overall.

## GrapheneOS's solution

GrapheneOS users have the option  to receive **all&#32;**security preview patches still under embargo as part of normal system updates. This means that GrapheneOS users can **get Android Security Bulletin patches up to four months early, and Linux Kernel patches three to six months early, compared with other Android users.**

Said another way, GrapheneOS is the only Android distribution today that is consistently patching Android security vulnerabilities as they are discovered. Even major vendors like Google and Samsung only update with a subset of patches early. 

When it comes to the Linux kernel, GrapheneOS updates to the latest Kernel LTS as part of regular updates, addressing a large number of kernel vulnerabilities that remain unpatched in stock Android for longer periods. You can find out more about the more complete patching GrapheneOS provides on our [features page](https://grapheneos.org/features#more-complete-patching).

## How can we solve these problems?

Despite GrapheneOS’s distinct advantage in delivering timely and comprehensive Android security patching (including substantially more Linux kernel patching), in an ideal world **all** Android users should have the same benefit. This would entail;

- An end to long embargoes of security patch code and withholding of vulnerability information beyond a reasonable period 
- Faster releases of security patches in AOSP
- A greater focus on Linux kernel security, including more frequent kernel updates to keep pace with vulnerability discovery

Google claim to value security by competing with the security of more secure operating systems like iOS such as their Advanced Protection mode that serves to be their version of iOS Lockdown Mode, but fall short on basic security principles like timely patching of major security issues. A campaign for these changes benefits all users of Android who would get more secure devices and also improve the security of other open source mobile operating system projects based on AOSP who are deliberately left in the dark.

So far, GrapheneOS has only been excluded from these problems because we have the manpower to deliver regular kernel patching and fortunate enough to have partners who help provide us access to the preview patches. We should not be relying on having a large support base who provides us the resources to deliver the bare minimum users expect from Android security.

## About the author

Amber Final is a GrapheneOS contributor and a digital forensics SME.

![A timeline chart titled "Complete patches by ASB (Android Security Bulletin) per Android Distribution for the Pixel 9. There are four horizontal bars for Android distributions. GrapheneOS Security Preview 2026 06 28 01 has the longest bar with patches up to December 2026 while Stock OS, GrapheneOS 2026 06 28 00, and LineageOS 23.2 are shorter, all at July 2026. The chart has the following footnotes: "Stock OS incorporates a small amount of security preview patches (around 15 percent), but not a complete future ASB." and "LineageOS is not based on Android 17 as of 30th July 2026, so while it has complete Android 16 backports as of it's ASB, it is still missing patches for lower severity vulnerabilities not backported to Android 16."](/images/2026-09-09-major-flaws-behind-android-security-patching.png)