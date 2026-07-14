+++
title = "Power Recommendations"
description = "Power usage recommendations"
+++

_[copied from the official forum](https://discuss.grapheneos.org/d/35721-grapheneos-power-usage-recommendations)_

A fresh install of GrapheneOS has far lower idle power usage than the stock Pixel OS. Power usage while active is comparable. Making a similar setup to the stock Pixel OS by installing sandboxed Google Play and a couple dozen apps doing a bit of background work will result in similar battery life.

GrapheneOS doesn't come with anything keeping open a push connection and barely has any scheduled work. Waking every 8 hours for update checks doesn't use significant power. It doesn't have better battery life due to any major efficiency improvements but rather the lack of bloatware.

Installing sandboxed Google Play on GrapheneOS results in having a push connection for Firebase Cloud Messaging and doing a lot more work in the background. Idle power usage will still tend to be better than the stock Pixel OS, but adding more apps to match their bloatware will make it comparable.

Battery life heavily varies based on apps, networks and OS configuration. Many people end up with far better battery life on GrapheneOS and many people end up with far worse battery life due to differences in how they set up their devices. It's easy to end up with either result with simple choices.

Play Store policy coerces apps into using Firebase Cloud Messaging for push messaging including push notifications. Having every app sharing the same push connection is very efficient. Multiple push connections are inherently less efficient and many implementations of this aren't power efficient.

Installing Signal in a profile without sandboxed Google Play and granting the power optimization exception it requests is enough to destroy battery life and end up worse than the stock Pixel OS. The power efficient choices are either using Molly with UnifiedPush (Signal fork) or Signal with FCM.

Running both sandboxed Google Play and an efficient UnifiedPush app can have competitive battery life with the stock Pixel OS. Those should be the only 1-2 battery optimization exceptions for most users. Signal's fallback push will drain more power than all the bloatware in the stock OS itself.

On a Google Mobile Services OS, Play services is built into the OS as a highly privileged component with immense access and handles work across profiles.

Sandboxed Google Play are regular sandboxed apps without any special access. Each installation in a separate profile is entirely independent.

Setting up a work profile, Private Space and secondary user on the stock Pixel OS results in all 3 secondary profiles using the global Play services instance running in the Owner user for a shared FCM push connection, etc. Installing sandboxed Google Play in 4 profiles would run 4 FCM connections.

Network-based location is much more power efficient than the power hungry GNSS radio for satellite-based location. Maps/navigation apps will continuously use both when available but many apps will avoid using GNSS to save power if network-based location is available, so it can save a lot of power.

For GrapheneOS, network-based location is an opt-in feature in the Owner user setup. For Google Mobile Services Android, it's opt-out there and you'll be regularly nagged to enable it if you didn't. It's a common pitfall since people expect indoor location positioning and it can save a bit of power.

Cellular, Wi-Fi and Bluetooth are power hungry. 5G is particularly power hungry prior to the improved cellular radio in 9th/10th gen Pixels with the exception of the Pixel 9a. Either way, setting the cellular mode to 4G (meaning 4G and below) or the GrapheneOS 4G-only mode can save a lot of power.

Stock Pixel OS has an Adaptive Connectivity service which largely keeps 5G disabled. GrapheneOS doesn't have an equivalent to this yet but you can do it manually. Other than that, the stock Pixel OS doesn't really have any significant power saving tricks and it has a lot of bloatware draining power.
