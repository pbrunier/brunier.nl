---
author: ["Patrick Brunier"]
title: "VMWare UEM vs OneDrive"
date: "2018-04-03"
description: ""
summary: "Issues with VMWare UEM and OneDrive"
tags: ["VMWare", "UEM", "OneDrive", "Microsoft"]
categories: ["IT"]
series: [""]
ShowToc: false
TocOpen: false
---

A while back I ran into a issue while using the OneDrive Nextgen Client (17.x) on Windows 10 while using VMWare UEM 9.2 as a profile management solution.  The issue was easy to determine: Onedrive just did not start.

After ruling out any AppLocker issues, I discovered it had something todo with the UEM process hooks. Blacklisting dllhost.exe, onedrive.exe and onedrivesetup.exe solved the issue. Then UEM 9.3 came out, which fixed the issue, and therefore the manual blacklist could be removed.

Recently Onedrive 18.x surfaced. You know where I’m going? Right? No?

The problem is back again. No new version of UEM available.

Thank you Microsoft for delivering one of the most unstable platforms in human history.  Thanks to VMWare for teaming up with, the possibly not existing, Q&A teams of Microsoft.

I just put those 3 executables back in the blacklist, and it works for now.