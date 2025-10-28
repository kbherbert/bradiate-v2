---
title: My home networking project
publishDate: 1 Dec 2023
description: Experiments with Unifi, Raspberry Pi OS, Docker and more
---

For years, I just had the standard modem and wifi that came from my ISP. Then, when Fiber made it to our area, I realized that I was paying to rent equipment that did not even give me the full potential of my 1 GB upload & download speeds.

For a couple of years during the pandemic, I switched to dual Eero Pro Mesh 6 routers. This was great, as a direct connection gave me full speed and the mesh setup allowed me to achieve a better wifi signal in my office. I also never had a network-wide ad blocker prior to this, so was really enjoying the built-in protection their subscription service provided (side note – once you have something like this, you can almost never go back!). However, $99 a year was a bit steep. Add to that the fact that Amazon now owns Eero, and it got me thinking again. Time to reevaluate.

## Making better use of Synology
It was around this same time that I was also thinking of purchasing a couple of home security cameras. I already owned a [Synology Disk Station](https://www.synology.com/en-us/surveillance), and knew that their ecosystem offered compelling camera solutions with built-in NAS integration. However, I wanted to explore a networking solution that would give me more control, transparency, and flexibility—particularly around DNS filtering and ad blocking—without relying on subscription services.

## Enter Unifi
After researching various options, I settled on Ubiquiti's [Unifi](https://www.ui.com/) ecosystem. I invested in a Unifi Dream Machine SE as my primary gateway and two Unifi  access points to provide mesh coverage throughout my home. Unlike the Eero system, this gave me several advantages. First, there were no recurring subscription fees for the core functionality—you own the hardware and control your own network. Second, the Unifi Controller software runs locally on my network, meaning I'm not dependent on cloud connectivity for basic operations. Third, the granular control and visibility into network traffic appealed to my engineering sensibilities 🤓.

The setup process was straightforward. The Dream Machine SE consolidates the gateway, switch, and controller all in one unit, which simplified my installation significantly. The access points adopted into the controller within minutes, and soon I had a robust mesh network with failover capabilities and centralized management.

## Network-wide ad blocking with Pi-hole
While Unifi provided excellent network infrastructure, I still wanted that network-wide ad blocker I'd grown accustomed to. Rather than paying for a subscription service, I decided to implement [Pi-hole](https://pi-hole.net/) on a [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) running Raspberry Pi OS.

Pi-hole works by acting as a DNS sinkhole—it intercepts DNS queries from devices on your network and returns blank responses for known ad servers and trackers. This blocks ads at the DNS level before they're even requested, which is more efficient than blocking them at the application level. Setup involved flashing Raspberry Pi OS onto an SD card, configuring the Pi with a static IP address on my network, and running the Pi-hole installer.
Once installed, I configured the Dream Machine SE to use the Pi as its primary DNS resolver. From the Unifi Controller, I set the DHCP DNS settings to point to the Pi's IP address. This single change meant every device on my network automatically started using Pi-hole for DNS resolution without requiring individual configuration.

The results were immediate and impressive. Web pages loaded noticeably faster due to ad requests being blocked before they started, and I gained the dashboard visibility to see exactly what was being blocked network-wide. The Pi-hole web interface provides comprehensive statistics—you can see which devices are making requests, which domains are being blocked most frequently, and even drill down into specific query logs.

## Configuration and optimization
Beyond the basic setup, I implemented several optimizations. I configured Pi-hole to use [Cloudflare's DNS \(1.1.1.1\)](https://one.one.one.one/dns/)as an upstream resolver for non-blocked queries, which offers solid privacy properties. I also added additional blocklists beyond the defaults—curated lists that target specific categories of trackers and advertisers. This required some tuning to avoid false positives that would break legitimate website functionality.

## The result
My network now provides the benefits I valued from Eero—mesh coverage, ad blocking, and visibility—while giving me the control and cost savings I wanted. The combination of Unifi's professional-grade infrastructure and Pi-hole's elegant DNS-level filtering proved to be exactly the right balance between functionality and maintainability.

For a software engineer, this setup scratched an itch I didn't know I had: the ability to understand and control every layer of my home network. No black boxes, no recurring fees, and the satisfaction of running infrastructure that I've configured and understand end-to-end.