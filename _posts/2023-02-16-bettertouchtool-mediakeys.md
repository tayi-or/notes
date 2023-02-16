---
layout: post
category: bettertouchtool
tags:
    - bettertouchtool
    - music
    - media keys
    - macos
title: Force macOS to send media key events to Apple Music/Spotify
---

If you're like me, and the worst thing an application can do is override the system media keys with no option to turn it off, (talking to you, Discord, Safari), you really need a way to force all media keys to be routed to the music app of your choice.

For this, we can use BetterTouchTool, simply open the main window, select the below code and paste it in!

## Apple Music
```json
[
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Music\" to playpause",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "50161BC2-6EF7-44D5-9B7A-07CD8D489F0D",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1016,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 0,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  },
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Music\" to next track",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "7B8BF1E6-6B35-46D7-93CB-25F1827A74F3",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "娨",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1017,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 1,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  },
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Music\" to previous track",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "023225C7-9067-4A62-A636-34358A99B1C4",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "宨",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1018,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 2,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  }
]
```
## Spotify
```json
[
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Spotify\" to playpause",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "061C22C1-121C-4BB0-B955-03046088A48D",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1016,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 0,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  },
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Spotify\" to next track",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "4A39E12F-6381-42DB-BB30-E5BF6CAE4276",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "娨",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1017,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 1,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  },
  {
    "BTTTriggerType" : 0,
    "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
    "BTTPredefinedActionType" : 172,
    "BTTPredefinedActionName" : "Run Apple Script (blocking)",
    "BTTInlineAppleScript" : "tell application \"Spotify\" to previous track",
    "BTTAdditionalConfiguration" : "0",
    "BTTEnabled2" : 1,
    "BTTKeyboardShortcutKeyboardType" : 9578,
    "BTTRepeatDelay" : 0,
    "BTTUUID" : "227DE82E-86E5-4F4B-BEA6-E988875A5489",
    "BTTTriggerOnDown" : 1,
    "BTTNotesInsteadOfDescription" : 0,
    "BTTLayoutIndependentChar" : "宨",
    "BTTEnabled" : 1,
    "BTTModifierMode" : 0,
    "BTTShortcutKeyCode" : 1018,
    "BTTShortcutModifierKeys" : 0,
    "BTTOrder" : 2,
    "BTTDisplayOrder" : 0,
    "BTTAutoAdaptToKeyboardLayout" : 0
  }
]
```

## Bonus: Conditional Music Player Choice

If you use both Spotify & Apple Music, you can set BetterTouchTool to, for example, route all keys to Spotify, but only if it's open, otherwise, route to Apple Music.

To do this, paste **both** the Apple Music code from above, and this code here.

```json
[
  {
    "BTTActivationGroupName" : "Spotify",
    "BTTAppName" : "Spotify",
    "BTTAppAutoInvertIcon" : 1,
    "BTTAppProcessMatchMode" : 3,
    "BTTActivationGroupCondition" : "YnBsaXN0MDDUAQIDBAUGBwpYJHZlcnNpb25ZJGFyY2hpdmVyVCR0b3BYJG9iamVjdHMSAAGGoF8QD05TS2V5ZWRBcmNoaXZlctEICVRyb290gAGvEBYLDBMYICorLjU5Pj9CRkpPUFNZXWFjVSRudWxs0w0ODxAREl8QF05TQ29tcG91bmRQcmVkaWNhdGVUeXBlXxAPTlNTdWJwcmVkaWNhdGVzViRjbGFzcxACgAKAFdIUDxUXWk5TLm9iamVjdHOhFoADgBTUDxkaGxwdHh9fEBFOU1JpZ2h0RXhwcmVzc2lvbl8QEE5TTGVmdEV4cHJlc3Npb25fEBNOU1ByZWRpY2F0ZU9wZXJhdG9ygBOADoAEgBHVISIjJA8lJicoKVlOU09wZXJhbmReTlNTZWxlY3Rvck5hbWVfEBBOU0V4cHJlc3Npb25UeXBlW05TQXJndW1lbnRzgAaABRADgAiADVx2YWx1ZUZvcktleTrSIw8sLRABgAfSLzAxMlokY2xhc3NuYW1lWCRjbGFzc2VzXxAQTlNTZWxmRXhwcmVzc2lvbqMxMzRcTlNFeHByZXNzaW9uWE5TT2JqZWN00hQPNjihN4AJgAzTDyM6Ozw9WU5TS2V5UGF0aIALEAqACl8QEHJ1bm5pbmdQcm9jZXNzZXPSLzBAQV8QHE5TS2V5UGF0aFNwZWNpZmllckV4cHJlc3Npb26jQDM00i8wQ0ReTlNNdXRhYmxlQXJyYXmjQ0U0V05TQXJyYXnSLzBHSF8QE05TS2V5UGF0aEV4cHJlc3Npb26kR0kzNF8QFE5TRnVuY3Rpb25FeHByZXNzaW9u00sjD0xNTl8QD05TQ29uc3RhbnRWYWx1ZYAPEACAEFdTcG90aWZ50i8wUVJfEBlOU0NvbnN0YW50VmFsdWVFeHByZXNzaW9uo1EzNNQPVFVWV01NWFpOU01vZGlmaWVyV05TRmxhZ3NeTlNPcGVyYXRvclR5cGWAEhBj0i8wWltfEBVOU0luUHJlZGljYXRlT3BlcmF0b3KjWlw0XxATTlNQcmVkaWNhdGVPcGVyYXRvctIvMF5fXxAVTlNDb21wYXJpc29uUHJlZGljYXRlo15gNFtOU1ByZWRpY2F0ZdIvMEViokU00i8wZGVfEBNOU0NvbXBvdW5kUHJlZGljYXRlo2RgNAAIABEAGgAkACkAMgA3AEkATABRAFMAbAByAHkAkwClAKwArgCwALIAtwDCAMQAxgDIANEA5QD4AQ4BEAESARQBFgEhASsBOgFNAVkBWwFdAV8BYQFjAXABdQF3AXkBfgGJAZIBpQGpAbYBvwHEAcYByAHKAdEB2wHdAd8B4QH0AfkCGAIcAiECMAI0AjwCQQJXAlwCcwJ6AowCjgKQApICmgKfArsCvwLIAtMC2wLqAuwC7gLzAwsDDwMlAyoDQgNGA1IDVwNaA18DdQAAAAAAAAIBAAAAAAAAAGYAAAAAAAAAAAAAAAAAAAN5",
    "BTTTriggers" : [
      {
        "BTTTriggerType" : 0,
        "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
        "BTTPredefinedActionType" : 172,
        "BTTPredefinedActionName" : "Run Apple Script (blocking)",
        "BTTInlineAppleScript" : "tell application \"Spotify\" to next track",
        "BTTAdditionalConfiguration" : "0",
        "BTTEnabled2" : 1,
        "BTTKeyboardShortcutKeyboardType" : 9578,
        "BTTRepeatDelay" : 0,
        "BTTUUID" : "4A39E12F-6381-42DB-BB30-E5BF6CAE4276",
        "BTTTriggerOnDown" : 1,
        "BTTNotesInsteadOfDescription" : 0,
        "BTTLayoutIndependentChar" : "娨",
        "BTTEnabled" : 1,
        "BTTModifierMode" : 0,
        "BTTShortcutKeyCode" : 1017,
        "BTTShortcutModifierKeys" : 0,
        "BTTOrder" : 1,
        "BTTDisplayOrder" : 0,
        "BTTAutoAdaptToKeyboardLayout" : 0
      },
      {
        "BTTTriggerType" : 0,
        "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
        "BTTPredefinedActionType" : 172,
        "BTTPredefinedActionName" : "Run Apple Script (blocking)",
        "BTTInlineAppleScript" : "tell application \"Spotify\" to playpause",
        "BTTAdditionalConfiguration" : "0",
        "BTTEnabled2" : 1,
        "BTTKeyboardShortcutKeyboardType" : 9578,
        "BTTRepeatDelay" : 0,
        "BTTUUID" : "061C22C1-121C-4BB0-B955-03046088A48D",
        "BTTTriggerOnDown" : 1,
        "BTTNotesInsteadOfDescription" : 0,
        "BTTLayoutIndependentChar" : "",
        "BTTEnabled" : 1,
        "BTTModifierMode" : 0,
        "BTTShortcutKeyCode" : 1016,
        "BTTShortcutModifierKeys" : 0,
        "BTTOrder" : 0,
        "BTTDisplayOrder" : 0,
        "BTTAutoAdaptToKeyboardLayout" : 0
      },
      {
        "BTTTriggerType" : 0,
        "BTTTriggerClass" : "BTTTriggerTypeKeyboardShortcut",
        "BTTPredefinedActionType" : 172,
        "BTTPredefinedActionName" : "Run Apple Script (blocking)",
        "BTTInlineAppleScript" : "tell application \"Spotify\" to previous track",
        "BTTAdditionalConfiguration" : "0",
        "BTTEnabled2" : 1,
        "BTTKeyboardShortcutKeyboardType" : 9578,
        "BTTRepeatDelay" : 0,
        "BTTUUID" : "227DE82E-86E5-4F4B-BEA6-E988875A5489",
        "BTTTriggerOnDown" : 1,
        "BTTNotesInsteadOfDescription" : 0,
        "BTTLayoutIndependentChar" : "宨",
        "BTTEnabled" : 1,
        "BTTModifierMode" : 0,
        "BTTShortcutKeyCode" : 1018,
        "BTTShortcutModifierKeys" : 0,
        "BTTOrder" : 2,
        "BTTDisplayOrder" : 0,
        "BTTAutoAdaptToKeyboardLayout" : 0
      }
    ]
  }
]
```
