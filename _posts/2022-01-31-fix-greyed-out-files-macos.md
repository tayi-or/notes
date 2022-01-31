---
layout: post
category: macos
tags:
    - finder
    - macos
title: How to fix "Copying x has paused"/greyed out folders on macOS Finder.
---
macOS will handily let you resume a failed/interrupted copy operation, however, if you want to just stop it and get access to the folder. macOS doesn't let you do this, even if the files are there on disk.

You'll need to open the Terminal to do this and run 2 commands. Copy and paste them and then drag the folder into the Terminal window after them, leaving a trailing space.

```
# Remove the copy in progress attribute from the file.
xattr -c 
# Reset the file creation date (this command will complaining about missing file but it does work!)
SetFile -d
```

If all went well, you should see the following:

```
taylor@vulpes ~ % xattr -c /Volumes/Backups/2018install/
taylor@vulpes ~ % SetFile -d /Volumes/Backups/2018install
ERROR: File Not Found. (-43)  on file: -d 
```
