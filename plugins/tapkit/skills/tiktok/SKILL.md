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

## Search Feature (Deep Dive)

### Accessing Search

From the For You feed, tap the **magnifying glass icon** at the top-right of the top bar (~577, 118). This opens the Search Discovery Page.

### Search Discovery Page (Before Searching)

The discovery page appears when you first enter search, before typing a query.

**Layout (top to bottom):**
- **Back arrow** (`<`) — top-left (~30, 118), returns to For You feed
- **Search bar** — placeholder text (gray, shows a suggested search term), **camera icon** (~475, 118) for visual search, red **"Search"** button (~555, 118)
- **Recent searches** — Listed with icons: music note for sound searches, clock for text searches. Each has an **X** button on the right to delete. **"See more"** link expands the full list.
- **Promo banner** — TikTok Shop voucher promotion with "Join" button (may not always appear)
- **"You may like" section** — Suggested search terms as a bullet list:
  - **Red bullet + red text** = personalized suggestions (recent activity, "Just watched" label)
  - **Black bullet + black text** = general suggestions
  - **Trend arrow icon + "Trending"** label = trending topics
  - **"Refresh"** button (top-right of section) loads new suggestions
- **"Popular LIVE" / "Viral songs"** toggle tabs at bottom:
  - **Popular LIVE**: List of active live streamers with avatars, names, and colored status bullets (red = live)
  - **Viral songs**: Numbered chart of trending songs with album art, song name, artist, post count. Top entries (#1, #2) have highlighted number backgrounds.
- **Microphone icon** (~575, 878) — floating button for voice search
- **"Help us improve" | "Learn more"** links at very bottom

**Keyboard** appears automatically with a blue "search" button.

### Typing a Search Query (Autocomplete)

As you type, the page switches to autocomplete suggestions:

- **Search bar** shows typed text with cursor, **X clear button** (~483, 118) appears to clear text
- **Suggestion list**: Each row has:
  - Magnifying glass icon (left)
  - Query text — typed portion in **pink/red**, completion text in **black**
  - **Fill arrow** (~580, right side) — tapping this fills the suggestion into the search bar WITHOUT executing the search, allowing further refinement
  - Some suggestions show a **thumbnail image** (for creator accounts)
- **"Press and hold on a suggestion to report it"** hint at bottom
- Tap a suggestion directly to execute that search
- Tap the blue **"search"** button on the keyboard or the red **"Search"** button to search for exactly what's typed

### Search Results Page

After executing a search, results appear with a rich multi-tab interface.

**Header:**
- **Back arrow** (`<`) — returns to search discovery page
- **Search bar** — shows current query with **X clear button** (~523, 118) and **three-dot menu** (~583, 118)
- Three-dot menu opens a bottom sheet with:
  - **Filters** — opens advanced filter panel
  - **Share feedback** — report issues

**Result Tabs** (horizontal scroll, 9 total):
1. **Top** (default) — Mixed results with AI summary + video grid
2. **Shop** — TikTok Shop product listings
3. **Users** — Creator/account search results
4. **Videos** — Video-only grid
5. **Sounds** — Sound/music results
6. **LIVE** — Active live streams matching query
7. **Places** — Location-based results
8. **Photos** — Photo post results
9. **Hashtags** — Matching hashtags

The tab bar is horizontally scrollable — you won't see all 9 at once. Swipe left on the tab bar to reveal more tabs.

#### Top Tab

- **Sub-filter pills** (horizontal scroll below tabs): Contextual refinements like "Latest", "Easy", "Dinner", "Beginners", "Healthy", etc. Tapping a pill refines results and updates the AI summary. Selected pill gets a bold border.
- **Search Highlights card** (AI-generated):
  - Green checkmark badge + "Search Highlights"
  - "AI summary from [source avatars] +N"
  - AI-generated text summary with recipe/info extracted from videos
  - Three-dot menu (top-right of card)
  - **"See more >"** link — opens a full-page expanded AI summary with structured content (ingredients, methods, numbered steps) and embedded video thumbnails with play buttons and like counts
- **Video grid** (2-column) below the highlights: thumbnail, caption (truncated), creator avatar + name, heart + like count, date posted. Some thumbnails have a **bookmark icon** overlay.

#### Shop Tab

- **Filter pills**: Filter icon, Sort (dropdown), Free shipping, 4 Stars & Up, Clearance, Deals
- **"TikTok Shop Protection Free returns"** banner
- **Product cards** (2-column grid): Product image, name, star rating, sold count, price with original/discount, badges ("Free shipping", "Sponsored", "Most Loved", "OFFICIAL"), coupon info, video play icons for video reviews

#### Users Tab

- **User list** (full-width rows): Avatar, username (bold), display name, follower count + like count, red **"Follow"** button
- Verified accounts have **blue checkmark** badges
- Some show "Followed by [mutual connections]" instead of stats

#### Videos Tab

- **2-column video grid**: Large thumbnails with text overlays, caption/subtitle icons, sound icons. Below: caption, creator avatar + name, date, heart + like count

#### Sounds Tab

- **Sound list** (full-width rows): Album art thumbnail (some with play button), sound name (bold), creator/artist, duration, video count
- Red **video camera icon** on right — tap to create video with that sound

#### LIVE Tab

- **2-column grid** of live stream thumbnails: Red "LIVE" badge + viewer count or thumbs-up count. Stream title and creator avatar + username below.

#### Places Tab

- **Place list** (full-width rows): Map pin icon, place name (bold), category (Restaurant, Bakery, etc.), full address

#### Photos Tab

- **Masonry grid** (2-column, variable height): Photo thumbnails with date stamp overlay, caption below, creator avatar + name, heart + like count

#### Hashtags Tab

- **Hashtag list** (full-width rows): # icon, hashtag name (bold), post count. Red **video camera icon** on right to create video with that hashtag.

### Advanced Filters

Accessed via three-dot menu > Filters on the search results page. Opens as a bottom sheet.

**Sort by** (single-select pills):
- Relevance (default)
- Like count
- Latest

**Video category** (single-select pills):
- All (default)
- Unwatched
- Watched
- Liked
- People you follow

**Date posted** (single-select pills):
- All (default)
- Past 24 hours
- This week
- This month
- Last 3 months
- Last 6 months

**Actions**: "Cancel" (top-left) dismisses without applying, "Apply" (top-right, pink/red) applies selected filters. Swipe down on the sheet also dismisses.

### Search Tips and Gotchas

- **Placeholder text is not real text**: The search bar shows gray placeholder/suggestion text (e.g., a trending topic). Tapping the bar and typing replaces it — no need to clear it first.
- **Camera icon** (~475, 118) on the search discovery page opens visual/image search. Only visible before executing a search — replaced by X clear button on results page.
- **Voice search**: Tap the floating microphone icon (~575, 878) on the discovery page, or the mic on the keyboard.
- **9 result tabs**: Tab bar scrolls horizontally. Full list: Top, Shop, Users, Videos, Sounds, LIVE, Places, Photos, Hashtags. Swipe left on tabs to reveal hidden ones.
- **AI Search Highlights**: Not available for all queries. Appears on Top tab for queries with enough matching content. "See more" expands to a full article-style page.
- **Sub-filter pills are contextual**: They change based on the search query (e.g., food searches get "Easy", "Dinner"; other queries get different refinements).
- **Filters only apply to current tab**: Changing tabs may reset filter selections.
- **Search history**: Previous searches appear on the discovery page with clock icons. Tap X on each to delete, or "See more" to view full history.
- **The search bar X button (~523, 118)**: Can be finicky to tap. If it doesn't respond, try tapping slightly to the left or use the back arrow instead.

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
4. screenshot → verify autocomplete suggestions appear
5. Tap blue "search" button on keyboard OR tap a suggestion
6. screenshot → verify results page with tabs
```

### Filter Search Results
```
1. On search results page, tap three-dot menu (~583, 118)
2. Tap "Filters"
3. Select desired Sort by / Video category / Date posted pills
4. Tap "Apply" (top-right of filter sheet)
5. screenshot → verify filtered results
```

### Browse Search Result Tabs
```
1. On search results page, tap desired tab (Top, Shop, Users, etc.)
2. If tab not visible, swipe left on the tab bar to reveal more
3. screenshot → verify tab content loaded
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
