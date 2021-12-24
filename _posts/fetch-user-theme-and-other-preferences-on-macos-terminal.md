---
layout: post
category: macos
tags:
    - plutil
    - plist
    - settings
    - terminal
    - preferences
title: Reading macOS Preferences (such as theme) from the Terminal
---

## Read light/dark mode preference:

```bash
> plutil -extract AppleInterfaceStyle raw ~/Library/Preferences/.GlobalPreferences.plist -o -
Dark
```
## Dump all global preferences as XML:
```bash
> plutil -convert xml1 ~/Library/Preferences/.GlobalPreferences.plist -o -
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>AKLastEmailListRequestDateKey</key>
	<date>2021-12-23T20:10:20Z</date>
	<key>AKLastIDMSEnvironment</key>
	<integer>0</integer>
	<key>AppleAntiAliasingThreshold</key>
	<integer>4</integer>
	<key>AppleAquaColorVariant</key>
	<integer>1</integer>
	<key>AppleInterfaceStyle</key>
	<string>Dark</string>
[...]
```
