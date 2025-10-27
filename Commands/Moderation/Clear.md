---
title: "Clearing messages"
description: "Mass deletion of messages in the channel"
category: "moderation"
difficulty: "⭐"
permissions: ["manageMessages"]
tags: ["cleanup", "moderation"]
version: "1.0"
---

# 🗑️ Clearing messages

`Quickly deletes the specified number of messages in the current channel.`

---

# 💡 Features

- ✅ Deletes up to 100 messages at a time
- ⚠️ Does not work with messages older than 14 days
- 🔒 Requires the "Manage Messages" permission
  
## 📋 Basic information

### Prefix command
- **Trigger:** `{your_prefix}purge`
- **Usage:** `{your_prefix}purge [number]`
- **Required rights:** `Manage Messages` (For the user and the bot)

### Slash command
- **Option:** `number` (required)
- **Type:** Number
- **Limits:** 1-1000 messages

---

## 🚀 Installation
### ⚙️ Prefix version
```swift
$nomention
$if[$checkUserPerms[$authorID;managemessages]==false]
  $title[❌ Missing permissions]
  $description[<@$authorID> You are missing the `manage messages` permission]
  $color[#ff0000]
  $deleteIn[3s]
  $stop
$endif
$if[$checkUserPerms[$botID;managemessages]==false]
  $title[❌ Missing permissions]
  $description[<@$authorID>, I am missing the `manage messages` permission]
  $color[#ff0000]
  $deleteIn[3s]
  $stop
$endif
$if[$isNumber[$message]==true]
  $title[❌ Argument error]
  $description[<@$authorID>, You provided an invalid number]
  $color[#ff0000]
  $deleteIn[3s]
  $stop
$endif

$title[✅ Messages Cleared]
$description[Successfully deleted: `$message` messages]
$color[#00FF00]
$deleteIn[3s]
$deletecommand
$clear[$message]
```

### ⚙️ Slash version
```swift
$nomention
$if[$isSlash==true]
$if[$checkUserPerms[$authorID;managemessages]==false]
  $ephemeral
  $title[❌ Missing permissions]
  $description[<@$authorID> You are missing the `manage messages` permission]
  $color[#ff0000]
  $stop
$endif
$if[$checkUserPerms[$botID;managemessages]==false]
  $ephemeral
  $title[❌ Missing permissions]
  $description[<@$authorID>, I am missing the `manage messages` permission]
  $color[#ff0000]
  $stop
$endif

$title[✅ Messages Cleared]
$description[Successfully deleted: `$message[number]` messages]
$color[#00FF00]
$deleteIn[3s]
$clear[$message[number]]
$endif
```
