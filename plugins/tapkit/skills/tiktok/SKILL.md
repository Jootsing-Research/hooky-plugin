---
name: tiktok
description: This skill should be used when the user wants to use TikTok, browse the For You feed, like or comment on videos, follow creators, search for content, share videos, or interact with the TikTok app on their iPhone.
---

# TikTok — Video App

TikTok is a short-form video platform. Users browse an algorithmic "For You" feed, like/comment/share videos, follow creators, and discover content through explore/search. This skill teaches you TikTok's UI layout and interaction patterns.

## App Structure

### Tab Bar (bottom of screen)

TikTok has 5 tabs along the bottom navigation bar:

1. **Home** (House icon) — Returns to the video feed (For You / Following)
2. **Friends** (People icon) — Friend activity feed with stories row at top
3. **Create** (+ icon, center) — Create a new video
4. **Inbox** (Chat bubble icon) — Messages, notifications, activity, DMs
5. **Profile** (Person icon) — Your own profile, settings, saved content

The tab bar is visible on the main feed but hides when you enter certain sub-views (live streams, full-screen comments, profiles). Navigate back or tap Home to reveal it again.

### Top Bar (Feed Tabs)

When on the Home tab, there are horizontal feed tabs at the top of the screen:

- **LIVE** (far left) — Opens a live stream feed. Swipe up/down between live streams. To exit a live, tap the X in the top-right — **aim at x=630, which is beyond the visible screen edge**. This is critical; tapping at visible x positions (590-618) hits the adjacent toggle button instead.
- **STEM** — Science/technology/engineering/math curated feed (same full-screen format as For You)
- **Explore** — 2-column grid of trending/recommended videos with thumbnails, titles, creators, and like counts
- **Local** — 2-column grid of location-based content
- **Following** — Videos from followed accounts only. Has a stories row at top (Create button, then followed creators with colored rings — pink for LIVE, cyan for active)
- **For You** (default, underlined) — Main algorithmic feed with full-screen vertical videos
- **Search** (magnifying glass, far right) — Opens search/discover page

## For You Feed (Main Screen)

The For You feed shows one full-screen vertical video at a time. The video fills the entire screen with UI elements overlaid on top.

### Right Side Action Buttons

A vertical column of action buttons on the right side of the video (all at approximately x=575):

1. **Creator Avatar** (~y=630) — Circular profile photo. Has a red **+** button below it if you're not following the creator. Tap → opens creator's profile page.
2. **Heart / Like** (~y=740) — White outline when not liked, solid red/pink when liked. Shows like count below. Tap to toggle like/unlike.
3. **Comment** (~y=860) — Speech bubble icon with comment count. Tap → opens comment section as a bottom sheet.
4. **Bookmark / Save** (~y=920) — Bookmark icon with save count. Tap to toggle save/unsave.
5. **Share** (~y=1010) — Forward arrow icon with share count. Tap → opens share sheet.

**Important:** These y-coordinates shift slightly between videos. If a tap doesn't hit the intended button, adjust by ~20px up or down. The buttons are spaced roughly 80-90px apart vertically.

### Bottom-Left Info Area

- **Badge** — "Your friend" or "People you may know" (for suggested content from non-followed creators)
- **"↻ Repost to followers"** link
- **Creator name** — Tappable, opens their profile
- **Caption text** — Shows first 2 lines with hashtags. Truncated with "... more" to expand. Tap "more" to see full caption. Tap "less" to collapse.
- **Music/sound ticker** — "♫ [sound name] - [artist]..." Tappable → opens Sound page

### Bottom-Right

- **Music disc** — Small spinning circular avatar at the very bottom-right (~y=1130). Tap → opens the Sound page showing all videos using this sound, with "Add to Favorites" and "Use sound" options.

### Bottom Bar (Conditional)

Some videos show additional elements above the tab bar:

- **"Not interested"** / **"Follow"** buttons — Appear for suggested creators you don't follow
- **Search suggestion bar** — "🔎 Search · [related keyword]" with arrow. Tap to search that term.

### Video Overlays

- **Text overlays** from the creator on the video itself
- **"Free Gifts"** promotional badge (top-left, dismissible with X)
- **"Full screen"** button — Appears when a horizontal/non-fullscreen video is shown. The action buttons are positioned differently in this mode — they appear below the video frame rather than overlaid on it.
- **"Sponsored"** badge — Appears on ad videos, along with a CTA button (e.g., "Shop now >")
- **Video progress bar** — Thin line at the very bottom of the video area

## Gestures on the Main Feed

- **Swipe up** — Next video
- **Swipe down** — Previous video (or refresh if at the top)
- **Swipe left** — Opens the creator's profile page
- **Swipe right** (from left edge) — Goes back in navigation
- **Single tap** (center of video) — Pause/play toggle
- **Double tap** (center of video) — Like the video (heart animation appears, heart icon turns red)
- **Long press** (center of video) — Opens context menu bottom sheet

Use `swipe(200, 700, "up")` for next video and `swipe(200, 700, "down")` for previous. Avoid swiping from screen edges to prevent triggering iOS gestures or AssistiveTouch.

## Comment Section

Opened by tapping the comment bubble icon. Appears as a bottom half-sheet.

- **Header**: "[count] comments" with filter/sort icon and **X** close button
- **Comments list**: Each comment shows avatar, username, text, timestamp, like count, reply button
- **Creator comments** are labeled "Creator" in orange/teal
- **Emoji quick reactions row** — 8 emoji shortcuts at the bottom
- **"Add comment..."** text field with user avatar on the left
- **Below text field**: emoji icon, @ mention button, send button (pink/red arrow)
- Keyboard appears when text field is tapped

To post a comment: tap "Add comment..." → `type_text("your comment")` → tap the send button.

To close: tap the **X** in the header, or swipe down on the sheet.

## Share Sheet

Opened by tapping the share/forward arrow icon. Appears as a bottom sheet.

- **Header**: "Send to" with search icon (left) and X (right)
- **Row 1 — Recent contacts**: Horizontal scroll of friend avatars to send directly
- **Row 2 — Share options**: Repost (yellow), Copy link (blue), SMS (green), Messenger, Telegram, Snapchat, Instagram...
- **Row 3 — More actions**: Report, Not interested, Download, Add to Story, Promote, Cast...

To close: tap the **X** or tap outside the sheet.

## Long Press Context Menu

Opened by long-pressing anywhere on the video. Appears as a bottom sheet.

- **Download** — Save video to device
- **Not interested** — Hide similar content
- **Report** — Report the video
- **Speed** — Playback speed: 0.5x, 1.0x (default), 1.5x, 2.0x
- **Clear display** — Removes all overlay UI elements temporarily
- **Auto scroll** — Toggle to automatically advance to next video
- **Captions and translation** — Enable/configure captions
- **Picture-in-Picture** — Watch in PiP mode
- **Background audio** — Toggle to keep audio playing when leaving the app

## Creator Profile Page

Opened by tapping the creator avatar, creator name, or swiping left on a video.

- **Header**: Back arrow (< top-left), bell icon (notifications), share icon (top-right)
- **Profile info**: Large avatar, display name, @username
- **Stats**: Following count | Followers count | Likes count
- **Action buttons**: Follow (red/pink), Message, dropdown for more options
- **Bio**: Text description, website link, custom items (boards, subscriptions)
- **Content tabs**: Grid icon (default), Repost icon. Category filter pills if the creator has organized content
- **Video grid**: 3-column layout. Pinned videos marked with red "Pinned" badge. Each thumbnail shows view count. Recently watched videos show "Just watched" badge.

To go back: tap the **<** back arrow or swipe right from the left edge.

## Sound Page

Opened by tapping the music disc or sound ticker at the bottom of a video.

- **Video preview** at top (small version of the source video)
- **Sound info**: Thumbnail with play button, sound name, creator name (tappable), post count
- **"Add to Favorites"** button
- **Video grid**: All videos using this sound, "Original" badge on the source video
- **Bottom buttons**: "Add to Story" (outlined) and "Use sound" (red/pink)

To go back: swipe right from left edge or swipe down.

## Following Tab

- **Stories row** at top: Create (+), then followed creators with circular avatars
- **LIVE creators** have pink/magenta rings; active creators have cyan/teal rings
- **Video feed** from followed accounts only
- Same gesture controls as For You feed

## Friends Tab

- **Header**: "Friends" + search icon
- **Stories row**: Create, friend avatars
- **Video feed**: Content from friends (mutual follows)

## Inbox Tab

- **Header**: Group icon (left), "Inbox" with online indicator (green dot), search icon (right)
- **Stories row**: Create, On this day, friends
- **Categories**: New followers, Activity (with badge count), System notifications
- **DM conversations**: With unread message badges
- **Message requests**: Separate section
- **TikTok Shop**: Seller messages

## Sponsored / Ad Videos

Same full-screen format as regular videos but with:
- **"Sponsored"** badge below the caption
- **CTA button** (e.g., "Shop now >") — pink/red, full-width above the tab bar
- **Brand logo** as the creator avatar instead of a person
- **Link icon** below avatar (instead of + follow button)
- Comments and likes are usually from the brand account

## Key Workflows

### Browse the For You Feed
```
1. open_app("TikTok") → screenshot to verify
2. Tap "For You" tab if not already selected (~481, 118)
3. Watch current video, swipe up from (200, 700) to next video
4. screenshot → verify new video loaded
```

### Like a Video
```
1. screenshot → verify you're on a video
2. Option A: double_tap(300, 500) — double-tap center of video
3. Option B: tap(575, 740) — tap the heart icon directly
4. screenshot → verify heart turned red
```

### Comment on a Video
```
1. tap(575, 860) — tap the comment bubble icon
2. screenshot → verify comment section opened
3. Tap "Add comment..." text field
4. type_text("your comment")
5. Tap the send button (pink arrow, bottom-right of input area)
6. screenshot → verify comment posted
```

### Follow a Creator
```
1. Tap the red + button below the creator avatar (~590, 655)
2. OR tap creator avatar → tap Follow button on their profile
3. screenshot → verify Follow button changed to Following
```

### Share a Video
```
1. tap(575, 1010) — tap the share/forward arrow
2. screenshot → see share options
3. Tap desired option (Copy link, SMS, etc.)
4. screenshot → verify
```

### Search for Content
```
1. Tap the search icon (magnifying glass, ~577, 118) in top bar
2. screenshot → search page appears
3. Tap the search field → type_text("search query")
4. Tap Search on keyboard
5. screenshot → view results
```

### Visit a Creator's Profile
```
1. Option A: tap(575, 630) — tap their avatar on the right side
2. Option B: swipe left from center of video (swipe(400, 500, "left"))
3. Option C: tap their name in the caption area
4. screenshot → verify profile page loaded
5. To go back: tap back arrow (< at ~30, 115) or swipe right from left edge
```

### Open Sound Page
```
1. Tap the spinning music disc at bottom-right (~575, 1130)
2. screenshot → verify sound page opened
3. To go back: swipe right from left edge
```

## Tips and Gotchas

- **Screen dimensions**: 619x1344 pixels. (0,0) is top-left.
- **Right-side buttons shift**: The y-coordinates of action buttons vary slightly per video depending on the creator info area height. Always screenshot first and adjust coordinates.
- **LIVE stream exit**: The X button on live streams requires tapping at **x=630** (beyond the visible 619px screen width). Tapping at normal visible coordinates (590-618) hits the adjacent toggle button instead. This is a known quirk.
- **Non-fullscreen videos**: Horizontal videos show in a smaller frame with a "Full screen" button. The action buttons are positioned differently in this mode — they appear below the video frame rather than overlaid on it.
- **"Not interested" / "Follow" buttons**: These appear at the bottom for videos from creators you don't follow. They can shift other elements up slightly.
- **Search suggestion bar**: Some videos show a search bar at the very bottom, above the tab bar. This pushes the tab bar down slightly.
- **AssistiveTouch**: Can be triggered accidentally by dragging from certain screen positions. If it appears (a floating menu with Tap, Gestures, Home, etc.), tap outside it to dismiss.
- **Comment section vs heart button**: These are close together on the right side (~80px apart). If you're hitting comments when trying to like, aim higher (lower y value). If you're liking when trying to comment, aim lower (higher y value).
- **Single tap pauses/plays**: Tapping the center of the video toggles playback. This means the video may be paused after you tap to dismiss overlays. The video auto-resumes when you swipe to the next one.
- **Swipe from center**: Always swipe up/down from the center-left area (x=200) of the screen to avoid hitting right-side buttons or triggering edge gestures.
- **Phone deselection**: With multiple phones connected, the phone may deselect between tool calls. If you get a "multiple phones connected" error, re-run `select_phone` with the phone ID and retry.
- **Video load time**: After swiping to a new video, it takes 1-2 seconds to load. If the screenshot looks transitional (two videos visible), take another screenshot after a moment.
