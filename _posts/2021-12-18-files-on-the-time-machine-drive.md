---
layout: post
category: macos
tags:
  - time_machine
  - monterey
title: putting files on the time machine drive on Monterey
---

## The part you actually care about:

1. Open Disk Utility
2. Select "Show all disks" from the view menu
3. Ensure the drive is formatted as APFS
4. Select the "Container" inside the drive
5. Click the '+' icon where it says "Volume" in the top right
6. Give it a name and create.
    a. Now those of you familiar with drive partitioning, but less with APFS volumes, this won't create a partition. You'll have the entire drive space available to both volumes (you can assign a minimum & maximum size to both volumes however)

## The "wtf?" moment:

Time Machine backups on Monterey are weird. First of all, they show up as Finder weirdly, and you cant copy files to and from it, not even with Terminal!

```
cp: /Volumes/Time Machine 1/Screenshot 2021-12-18 at 00.43.12.png: Operation not permitted
```

In `df` each drive connected to your PC shows up as a seperate TimeMachine Local Snapshot mountpoint??

```
/dev/disk4s3                                                 7813627488  136564136 4805111360     3%        357 24025556800    0%   /Volumes/Time Machine 1
com.apple.TimeMachine.2021-12-18-011118.local@/dev/disk5s1    976363488  333586496  642462768    35%       9030  3212313840    0%   /Volumes/com.apple.TimeMachine.localsnapshots/Backups.backupdb/Vulpes (340)/2021-12-18-011118/500g
com.apple.TimeMachine.2021-12-18-011118.local@/dev/disk4s1   7813627488 2871004304 4805111360    38%    8912213 24025556800    0%   /Volumes/com.apple.TimeMachine.localsnapshots/Backups.backupdb/Vulpes (340)/2021-12-18-011118/Backups
com.apple.TimeMachine.2021-12-18-011118.local@/dev/disk3s1   1953115488 1275711672  642863760    67%    4834960  3214318800    0%   /Volumes/com.apple.TimeMachine.localsnapshots/Backups.backupdb/Vulpes (340)/2021-12-18-011118/macOS Montero - Data
```

Very strange.
