---
layout: post
category: malware
tags:
    - macos
    - nightowl
    - botnet
title: Uninstall the Nightowl App, now.
---

## Intro

The NightOwl application has existed since 2018 and is used to automatically switch between light/dark modes on the operating system. It is an alternative to the built in macOS automatic mode which only switches when the user steps away from the computer.


However, the application has been bought out by "TPE.FYI LLC" in late 2022[^1] that forcibly joins your devices into a botnet for use of market research, without your knowledge (other than the TOS in small text on the download page) or express consent (this feature cannot be turned off, even when the app is quit). This is documented in their terms of service[^2]:

> •WHEREAS, NightOwl app enables Users to share internet traffic by modifying their device's network settings to be used as a gateway for internet traffic. Additionally, the User's device acts as a gateway for NightOwl app's Clients, including companies that specialize in web and market research, SEO, brand protection, content delivery, cybersecurity, etc.

[^1]: https://www.kramser.xyz/
[^2]: https://nightowlapp.co/imprint

## Removal:

Run these commands in Terminal, if you have the app installed **at all**, even if you don't have it running.

    sudo killall NightOwl
    launchctl unload ~/Library/LaunchAgents/NightOwlUpdater.plist
    sudo killall AutoUpdate
    sudo rm -rf /Applications/NightOwl.app/ ~/Library/LaunchAgents/NightOwlUpdater.plist
    sudo zsh -c "rm /Users/*/Library/LaunchAgents/NightOwlUpdater.plist"

## Technical Details

The application, on install registers a launch agent named `org.nightowl.autoupdater.com`[^3]. This is used to daemonize the process `/Applications/NightOwl.app/Contents/Helpers/AutoUpdate`, which runs as root, at boot, and cannot be disabled through the application. This happens silently, without the users knowledge or consent other than the following notice[^4]

> In order to **improve the App**, NightOwl uses **Google Analytics** to collect Statistics. The tracked data helps to enhance NightOwl by analysing how **features** are used and which **bugs** appear.               
> We initialize Google Analytics with the setting "anonymizeIp". This guarantees **anonymized data collection** by masking the last part of your IP address.                
> You are able to **Opt-out** of the tracking by **unchecking "Send Statistics"** in the **settings** section of NightOwl. 

Turning off send statistics does not disable the launch agent.

The 'autoupdater' does three things, 

- check the app for updates (using Sparkle)
- report any crashes (using Sentry)
- start a local HTTP proxy on port `40701` (this can be changed using the configuration json file in the app bundle).

The latter is of course, not to be expected of any app on the machine, especially not one that just claims to be an auto updater.

The daemon uses 'sudo' to switch from running as the root user, to the main user account, and then starts an instance of `nightowl_t.dylib` (which is actually a copy of [tinyproxy](https://github.com/tinyproxy/tinyproxy), which is licensed under GPLv2, and does not contain the GPL license notice, so this might actually be a violation!), which acts as a HTTP(S) proxy and runs on port , It opens up a SSH connection (using autossh, renamed `nightowl_a.dylib`, which doesn't have a license) to `testconnectuser2023@proxy-gw1-europe.squidyproxy.com` on port `2043`, using a public key it drops in `/tmp` (it has a `.uu` extension), using the `-R` port to tunnel a port on the remote machine to the local machine. (it retrieves this by making a request to proxy-api1.squidyproxy.com over HTTPS). This domain was registered with GoDaddy in April 2022, and the IP address is hosted by Microsoft.

For reference, this SSH server has shell access enabled. (I didn't try anything though). After the connection succeeds, it forwards HTTP traffic down to you, which gets proxied out of your internet connection. I saw it trying to access . It also tries to open a UPnP port forward on your router, but fails on mine because the key names are jumbled:

```http
POST /ctl/IPConn HTTP/1.1
Host: 192.168.1.1:5000
User-Agent: Go-http-client/1.1
Content-Length: 526
CONTENT-TYPE: text/xml; charset="utf-8"
SOAPACTION: "urn:schemas-upnp-org:service:WANIPConnection:1#AddPortMapping"
Accept-Encoding: gzip

<?xml version="1.0" encoding="UTF-8"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" s:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"><s:Body><u:AddPortMapping xmlns:u="urn:schemas-upnp-org:service:WANIPConnection:1"><BznVVp_></BznVVp_><A8Lx50LV3wS>50276</A8Lx50LV3wS><SOkiBsutQ>TCP</SOkiBsutQ><C7V6rYTZpovv>50276</C7V6rYTZpovv><S8pOPFbT13z>192.168.3.102</S8pOPFbT13z><AQBzrw>1</AQBzrw><O9hZpuXGWURb>ip royal paws</O9hZpuXGWURb><BBYmUz7H>2592000</BBYmUz7H></u:AddPortMapping></s:Body></s:Envelope>
```

The application also seems to use the [Pawns](https://pawns.app/) SDK[^3], which is an app offers to pay users $0.20 per GB of their internet shared[^5]. This service is operated by [IPRoyal](https://iproyal.com/)[^6], a proxy company that will sell you residential proxy connections for $1.75/GB, and advertises "100% ethically sourced IPs"[^7].

[^3]: https://www.virustotal.com/gui/file/840fd039b2509fb50b328c0b5ada8c7300608e57bce8ce1bce822ee34b23fa52/behavior
[^4]: https://nightowlapp.co/
[^5]: https://pawns.app/
[^6]: https://pawns.app/blog/iproyal-pawns-is-now-pawns-app/
[^7]: https://iproyal.com/

## But just who is "TPE.FYI LLC"?

TPE (or Keeping Tempo, or Tempo AI (not to be confused with the Tempo AI calendar or the Tempo AI gym)) is "in the process of building a pricing model based on various  analytics such as YouTube video views for an artist and geographical  popularity data that will allow venues to price their tickets based on  actual demand for an artist."[^8] Information is sparse, and little information past 2018 exists.

The company was incorporated in September 2018 in Austin, Texas, and was dissolved in March 2023 by a "Jarod Stirling"[^9], who lives in Apartment 443 (hah, nice), The Muse at SoCo, 1007 South Congress Avenue, Austin, Texas, 78704.

[^8]: https://www.f6s.com/keepingtempo
[^9]: https://opencorporates.com/companies/us_tx/0803112154



