+++
title = "reCAPTCHA Mobile Verification"
description = "reCAPTCHA Mobile Verification is bringing the Play Integrity API to desktops"
+++

_[copied from the official forum](https://discuss.grapheneos.org/d/35428-recaptcha-mobile-verification-is-bringing-the-play-integrity-api-to-desktops)_

Apple and Google are gradually expanding their use of hardware-based attestation. They're convincing a growing number of services to adopt it. Google's Play Integrity API and Apple's App Attest API are very similar. Apple brought it to the web via Privacy Pass, which Google intends on doing too.

Google's Play Integrity API requires hardware attestation for the strong integrity level and is gradually phasing in requiring it for the more commonly used device integrity level. Apple already has it as a requirement. Over the long term, this will increasingly lock out hardware and OS competition.

The purpose of these systems is disallowing people from using hardware and software not approved by Apple or Google. This is wrongly presented as being a security feature. Banks and government services are the main ones adopting it but Apple and Google are encouraging every service to use it.

Apple's Privacy Pass brought hardware attestation to the web to help with passing captchas on their own hardware. Many people saw that as harmless since few sites would be willing to lock out non-Apple-hardware users. Apple and Google are both likely to bring broader hardware attestation to the web.

Google's reCAPTCHA is planning an approach where they use Privacy Pass on Apple hardware, their own approach on Google Mobile Services Android devices and a QR code scanning system to require an iOS or Google certified Android device for Windows and other systems:

https://support.google.com/recaptcha/answer/16609652

Banking and government services increasingly require using a mobile app where they can use attestation to force using an Apple or Google approved device and OS. Apple's privacy pass, Google's 'cancelled' Web Environment Integrity and now reCAPTCHA Mobile Verification are bringing this to the web.

Current media coverage for reCAPTCHA Mobile Verification misunderstands it and the impact of it. They're bringing a hardware attestation requirement to Windows, desktop Linux, OpenBSD, etc. by requiring a QR scan from a certified smartphone to pass reCAPTCHA in some cases. They could expand it more.

Control over reCAPTCHA puts Google in a position where they can require having either iOS or a certified Android device to use an enormous amount of the web. Google defines certification requirements for Android which includes forcing bundling Google Chrome, etc. It's enormously anti-competitive.

Google's Play Integrity API bans using GrapheneOS despite it being far more secure than anything they permit. It also bans using any other alternative. This isn't somehow specific to an AOSP-based OS. You can't avoid this by using a mobile OS based on FreeBSD instead. You'll just be more locked out.

Google's Play Integrity API permits devices with no security patches for 10 years. The device integrity level can be bypassed via spoofing but they can detect it quite well and block it once it starts being done at scale. The strong integrity level requires leaked keys from TEEs/SEs to bypass it.

It doesn't provide a useful security feature, but it does lock out competition very well. Services requiring Apple App Attest or Google Play Integrity are primarily helping to lock in Apple and Google having a duopoly for mobile devices. Play Integrity is more relevant due to AOSP being open source.

Governments are increasingly mandating using Apple's App Attest and Google's Play Integrity for not only their own services but also commercial services. The EU is leading the charge of making these requirements for digital payments, ID, age verification, etc. Many EU government apps require them.

Instead of governments stopping Apple and Google from engaging in egregiously anti-competitive behavior, they're directly participating in locking out competition via their own services. Requiring people to have an Apple device or Google-certified Android device is anti-competition, not security.

reCAPTCHA Mobile Verification will currently work with sandboxed Google Play on GrapheneOS but it clearly exists to provide a way for them to start using hardware attestation on systems without it. People without an iOS or Android device will be locked out when this is required even without that.

This isn't about security or any missing functionality. GrapheneOS can be verified via hardware attestation. Google bans using GrapheneOS for Play Integrity because we don't license Google Mobile Services and conform to anti-competitive rules already found to be illegal in South Korea and elsewhere.

Services shouldn't ban people from using arbitrary hardware and operating systems in the first place. Google's security excuse is clearly bogus when they permit devices with no patches for 10 years but not a much more secure OS. It's for enforcing their monopolies via GMS licensing, that's all.

Unified Attestation is another anti-competitive system being pushed by multiple European companies. It will similarly lock people out from using arbitrary hardware and software. That's not a solution and is far worse than Android's much more open hardware attestation API.

https://grapheneos.social/@GrapheneOS/116239523775374959

Android's hardware attestation shouldn't be used to lock out users not using specific hardware or OSes. However, the fact that it permits arbitrary roots of trust and OSes at least allows services to permit more. Google could use it to permit GrapheneOS for Play Integrity if that was about security.
