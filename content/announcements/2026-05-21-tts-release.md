+++
title = "GrapheneOS Speach Services Release"
description = "Initial release of GrapheneOS Speech Services for text-to-speech"
+++

_[copied from the official forum](https://discuss.grapheneos.org/d/35722-initial-release-of-grapheneos-speech-services-for-text-to-speech)_

The first public release of GrapheneOS Speech Services is now available in our App Store. After installing it, it can be activated as a text-to-speech service by tapping it in Settings > System > Language & region > Speech > Text-to-speech output > Preferred engine and approving it in the dialog.

It currently has a single voice for US English. If you have the system language set to anything other than English (United States), then you need to change Settings > System > Language & region > Speech > Text-to-speech output > Language to English (United States) from Use system language for now.

Once it's bundled with the OS, it will be enabled by default so activating it won't be necessary. Needing to activate the TTS engine causes a lot of confusion since Android's standard user interface shows the first TTS engine as active if none is active due to assuming one is bundled.

Our Speech Services app uses a fully open source model for text-to-speech which we created ourselves using existing open source code and data. We'll be able to train a better model to replace this one now that we have an RTX 5090 for this purpose. We also plan to make voices for other languages too.

The second most used language by GrapheneOS users is very likely German and then likely French. UK English would likely be much easier to add than those due to shared code and data sources so we may do that first but German will likely be next if we can find high quality open data to use for it.

In the short term, we could alias all of the other English variants to US English to have it working by default with those selected as system languages. We don't really want to train more than US and UK voices in the mid term rather than adding other languages so we'll just alias those to US or UK.

We also plan to make our own speech-to-text implementation to go along with the text-to-speech implementation. The models end up very large so it's unclear if we want to bundle more than US English with the OS. The other languages could be available as extra language packs in App Store instead.
