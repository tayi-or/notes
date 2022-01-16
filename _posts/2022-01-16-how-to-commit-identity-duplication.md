---
layout: post
category: git
tags:
    - git
    - trans
    - identity
    - users
    - macos
title: How to commit as multiple identities on macOS
---
### working title: how not to deadname yourself on git.
As a trans individual, it is essential (at least for me) to have multiple identities, and because one of my things I know how to do is write code, and sometimes I like to put said code on GitHub, and all git commits are linked to a name and an email address (which gets resolved to a GitHub account) I’d rather not cross the streams (most of the time ;) ifykyk) and put code attributed to Taylor on my ‘original’ GH acc, and vice versa.

There are other reasons why you might want 2 (or more) separate identities on Git (such as for work, and for personal), but that’s my reasoning.

## Why not just use `/gitkraken|tower/g` ?
Yes, there are visual clients that do this, however, they’re not perfect. If you use those clients, and it works for you, that’s great. But mainly:
 -  **Tower**’s UI is confusing to my dumb brain, and iirc only one account per service
 - **GitKraken**’s multi account feature is paid exclusive, which is great because I have the GitHub Education Pack, but not so great when you realise you can only use this when your subscription is on a Axosoft account, and you cannot unlink a GitHub account from an identity if that account is what your paid account is registered under.

This guide takes the nuclear approach of creating multiple operating system users for each identity, and using GitHub Desktop to manage said identities.
## Why GitHub Desktop?
- it’s easy
You could use any other Git client, however, I like GitHub Desktop for it’s simplicity and it works fine.
## Actually doing the thing.
This guide will show you how to do it on macOS, however the steps should be similar for Linux, and the concepts should be similar for Windows (i.e. using `PsExec` or similar to exec as another user instead of `su`.
1. Install GitHub Desktop
2. Create a seperate macOS user account
3. Move your source code to a shared directory (i.e. external drive, /Users/Shared) give new user to access to that folder
4. Switch to the new user account (Apple Menu, lock, switch user) and complete OOBE (this creates keychains, required configs, etc)
5. Log that user out and switch back to your regular user account
6. Run 'su TheUsernameOfYourNewUserAccountHere' in a terminal (sudo will NOT work)
7. Run `/Applications/GitHub\ Desktop.app/Contents/MacOS/GitHub\ Desktop &`
8.  Sign into GitHub Desktop (this will open Safari as your new user)
9. From here you can clone, create a new repo, or open an existing repo  (you may need to enter the path instead of browsing, the open file dialog was broken for me)
10. Publish to GitHub! 🥳

## Caveats
- This solution is the nuclear method, other than actually logging into using a separate user account for your coding fully, this provides the most secure way of keeping two identities private
- Some things don’t work when running as the wrong user, for example, 
	- Finder & it’s dialogs
	- Apps will refuse to open unless you call their binaries from a terminal
	- File permissions can get wacky. For example, if you use the GUI to clone to a folder in the new user’s home folder, the user that’s running everything else can’t access it, and vice versa.