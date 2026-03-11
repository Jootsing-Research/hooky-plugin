---
name: telegram
description: This skill should be used when the user wants to use Telegram, send or read messages, browse chats, join groups or channels, interact with bots, make calls, search conversations, or interact with the Telegram app on their iPhone.
---

# Telegram — Messaging App

Telegram is a messaging app with chats, groups, channels, and bots. Users send messages, share media, join group conversations, interact with bots, and manage contacts. This skill teaches you Telegram's UI layout and interaction patterns.

## App Structure

### Tab Bar (bottom of screen, y ~ 1248)

Telegram has 5 tabs along the bottom navigation bar:

| Tab | Approx x | What it does |
|-----|----------|-------------|
| **Contacts** | ~88 | All contacts alphabetically with search, sort, invite friends, and add (+) button |
| **Calls** | ~205 | Call history with All/Missed toggle filter and "Start New Call" link |
| **Chats** | ~320 | Main chat list — where 90% of interaction happens |
| **Settings** | ~430 | Profile, account settings, preferences |
| **Search** | ~555 | Global search across chats, contacts, messages. Shows FAQ when empty |

## The Chats Tab (Most Important)

### Top Bar (y ~ 120)
- **"Edit" button** (x ~ 57) — for bulk editing/selecting chats
- **Camera button** (x ~ 505) — **THIS IS A CAMERA, NOT NEW MESSAGE!** Opens a quick camera with Live/Video/Photo modes. Do NOT tap this when trying to compose a new message.
- **Compose button** (pen icon, x ~ 565) — THIS is how you start a new message. Opens a screen with: New Group, New Contact, New Channel, plus a searchable contact list with alphabet scrubber on right edge.

### Chat Filter Tabs (y ~ 193, horizontally scrollable)

The filter row sits just below the top bar. Swipe left/right to reveal more tabs.
- **All** (x ~ 57) — shows every conversation (DMs, groups, channels, bots)
- **Personal** — only 1-on-1 DMs (has count badge like "133")
- **Unread Group** — only groups with unread messages (has count badge)
- **Custom folders** — user-created folders (e.g., "Work", "Photobooth"). These vary per account.

**Important:** To switch filters, tap the tab name. If you can't see a tab, swipe left on the tab row to reveal more. There can be 8+ tabs.

### Chat List Items

Each chat in the list shows:
- Avatar (left), chat name, timestamp (right)
- Preview of last message with sender name for groups
- Unread count badge on right — **blue** for unmuted, **gray** for muted
- Heart/reaction emoji if the last message was reacted to
- Muted chats show a speaker-off icon next to the name

## Three Types of Chats (Different UIs!)

### 1. Direct Messages (1-on-1)
- **Header**: "< [count]" back button (left), contact name + "last seen recently/within a week/etc" status (center), their profile photo (right)
- **Messages**: Outgoing = purple bubbles on right side with double checkmarks (single check = sent, double check = read). Incoming = dark bubbles on left side.
- **Bottom bar**: Paperclip (attachments), "Message" text field, timer icon (disappearing messages), **microphone icon** (right — for voice messages)
- Date separators appear between days. An "Unread Messages" divider shows where new messages start.

### 2. Group Chats
- **Header**: "< [count]" back button, group name + "N members, N online" (center), group icon (right)
- **Pinned message banner** may appear at top — shows pinned content with a manage button
- **Messages show sender names** in colored text, plus role badges like "owner"
- Emoji reactions appear below messages with reaction counts
- **Bottom bar**: Paperclip, "Message" field, timer, **camera icon** (NOT microphone — different from DMs!)
- Tap the group name in the header to open **Group Info** page

### 3. Bot Chats
- **Header**: Bot name + "N monthly users" (instead of last-seen), bot icon (right)
- May have a **sponsored ad banner** at the top (dismissible with X)
- Bot messages tend to be rich: formatted text, images, inline links
- **Bottom bar**: Has a unique **"≡ Menu" button** on the left! This opens the bot's command menu. Then paperclip, "Message" field, timer, microphone
- May show "Reply to [BotName]" prompt

## Group Info Page

Opened by tapping the group name in the header.

- Group avatar, name, member count + online count
- **Action buttons row**: mute, search (within group), leave, more (...)
- **Tabs**: Members, Media, Files, Voice, Links (and possibly GIFs)
- Members list shows names with role badges and last-seen status
- "Add Members" link at top of members list

## Context Menus (Long Press)

### Long-press a Chat (from the chat list)

Shows a mini preview of the chat with these actions:
- **Add to Folder** — move to a chat folder
- **Mark as Unread** — toggle read/unread status
- **Pin** — pin chat to top of list
- **Mute** — silence notifications
- **Delete** — remove chat (red, destructive)

### Long-press a Message (inside any chat)

Shows the message highlighted with:
- **Quick emoji reaction bar** at top: heart, fire, crying, thumbs up, thumbs down, love face, clap plus an expand button for more emoji
- Reaction count + who reacted (if any)
- **Reply** — reply to this specific message
- **Copy** — copy message text
- **Pin** — pin message in chat
- **Forward** — forward to another chat/contact
- **Report** — report the message
- **Delete** — delete message (red)
- **Select** — enter multi-select mode for multiple messages

## Settings Menu

Accessed via Settings tab. Profile section at top shows avatar, name, phone number, username. Then:
- My Profile, Wallet (NEW)
- Saved Messages, Recent Calls, Devices, Chat Folders
- Notifications and Sounds, Privacy and Security, Data and Storage, Appearance, Power Saving, Language
- Telegram Premium, My Stars, Telegram Business, Send a Gift
- Ask a Question, Telegram FAQ, Telegram Features

## Key Workflows

### Send a Message to an Existing Chat
```
1. Tap the Chats tab (~320, 1248)
2. screenshot → verify chat list visible
3. Tap on the desired chat in the list
4. Tap the "Message" text field at the bottom
5. type_text("your message")
6. Tap the send button (appears where microphone/camera was, bottom-right)
7. screenshot → verify message sent
```

### Start a New Message
```
1. Tap the Chats tab (~320, 1248)
2. Tap the compose button (pen icon, ~565, 120) — NOT the ⊕ camera button
3. screenshot → verify contact list / compose screen
4. Search for or select a contact
5. Tap the "Message" field → type_text("your message") → send
```

### Browse Chat Filters
```
1. On Chats tab, look at filter row (y ~ 193)
2. Tap "All" (~57, 193) for all chats, or "Personal" for DMs only
3. Swipe left on the filter row to reveal more custom folders
4. Tap desired folder tab
5. screenshot → verify filtered chat list
```

### React to a Message
```
1. Inside a chat, long_press on the message you want to react to
2. screenshot → verify reaction bar appears at top
3. Tap desired emoji (heart, fire, thumbs up, etc.)
4. screenshot → verify reaction applied
```

### Reply to a Specific Message
```
1. Inside a chat, long_press on the message
2. Tap "Reply" from the context menu
3. type_text("your reply")
4. Tap send
```

### Search Globally
```
1. Tap the Search tab (~555, 1248)
2. Keyboard auto-focuses — just start typing with type_text("query")
3. screenshot → verify results
```

### Search Within a Group
```
1. Open the group chat
2. Tap the group name in the header to open Group Info
3. Tap the "search" action button
4. type_text("search query")
5. screenshot → verify results
```

### View Group Info
```
1. Open the group chat
2. Tap the group name in the header (top center)
3. screenshot → verify group info page with members, media tabs
```

## Tips and Gotchas

- **The ⊕ button is NOT compose** — it's a camera! The compose/new message button is the pen icon NEXT to it (x ~ 565). This will trip up agents who assume ⊕ = new message.
- **Bottom-right icon changes by chat type**: Microphone in DMs, Camera in groups, Microphone in bot chats. When you start typing, all change to a Send arrow.
- **The back button shows unread count** — the "< 689" back button in chats shows the total unread count for the chat list. Useful for knowing how many unreads exist without going back.
- **Muted vs unmuted unread badges** — Blue badges = unmuted unreads (important). Gray badges = muted unreads. Prioritize blue badges.
- **Filter tabs are horizontally scrollable** — "All" and "Personal" are visible by default, but there can be 8+ tabs. Swipe the tab row to find custom folders.
- **Phone selection may drop** — When multiple phones are connected, the selection can reset between actions. Always re-select with `select_phone` if you get a "Multiple phones connected" error.
- **Bot chats have a unique "≡ Menu" button** — No other chat type has this. It's specific to bot interactions and opens the bot's command palette.
- **Sponsored ads can appear** in bot chats — They have a "what's this?" label and X dismiss button. Dismiss these to avoid confusion.
- **The Search tab** immediately opens the keyboard and shows FAQ by default. Just start typing — no need to tap the search field first since it auto-focuses.
- **Navigation back**: Tap "< [count]" in top-left (y ~ 120, x ~ 70) or swipe right from the left edge of the screen.
