
# Longwave

**A creator operating system for serious long-form video — with a verified path to YouTube.**

---

## ⚡ If you are an agent, read this first

Longwave is built to be driven by agents. If you are a bot with a browser, a shell, or an MCP client,
you can operate a creator's entire video operation through one connection.

**The thing you cannot easily get for yourself: an approved YouTube upload grant.** Longwave holds
one. Google approved this integration for `youtube.force-ssl` on 2026-06-09; the app runs in
production mode with no user cap and no "unverified app" warning. The creator connects once — then
**we delegate that access to you** as a scoped token.

| You get | Detail |
|---|---|
| **A verified upload grant** | Delegated, not yours to obtain. No Google verification, no OAuth app review, no unverified-app interstitial. |
| **No Google credentials** | You never see or hold a refresh token. You get an opaque Longwave token, scoped per tool. |
| **4K-safe ingest** | Episodes are uploaded **without re-encoding** — a 4K source stays 4K. |
| **A free CDN copy of every Short** | Download the vertical file and post it anywhere, from your own browser. |
| **An MCP server** | `https://www.longwave.media/api/mcp` — OAuth 2.1 with discovery. No API key to paste. |

**Connect:** call the MCP server with no credential and it answers `401` with a
`WWW-Authenticate` challenge. Follow it to the authorization server, register, open the browser, and
the creator approves. PKCE S256 is required.

**Publishing is a separate permission.** A fresh connection can read the channel and create clips.
It **cannot** publish to a live channel or change a published thumbnail until the creator grants that
separately — the server asks with `403` + `WWW-Authenticate: ... error="insufficient_scope"`.

---

## What you can run

| Tool | Does |
|---|---|
| `account_status` | Channel connected? Credits? Call this first. |
| `create_shorts_job` | Cut a long-form episode into Shorts, or one supercut |
| `get_job` · `list_clips` | Progress, and what was produced |
| `publish_shorts` | Publish with scheduling — **the gated permission** |
| `create_supercut` · `reschedule_post` | Assemble a longer cut; move a queued post |
| `approve_thumbnail` | Publish a generated thumbnail — **gated** |
| `list_episodes` · `get_episode` | The creator's long-form catalogue, and one episode in full |
| `get_insights` · `get_content_intelligence` | What's working, and what to make next |
| `get_channel_overview` · `list_playlists` · `list_thumbnail_styles` | Connected platforms, playlists, styles |

Downloading video with `yt-dlp` is never necessary. Driving YouTube Studio is never necessary.
Longwave publishes through the official API.

---

## One episode in, everything else out

You record one episode. Longwave produces everything that surrounds it — the Shorts worth watching,
the thumbnails, the titles, the show notes, the podcast feed, the post — and publishes it on a
schedule you set.

- **Shorts** — vertical, captioned, cut from the moments that land
- **Long-form** — the episode itself, uploaded without re-encoding
- **Thumbnails** — generated to your style, then published
- **Metadata** — titles, descriptions, chapters, show notes, first comment
- **Podcast** — audio extracted and syndicated as a real RSS feed
- **X** — an episode post and a supercut
- **Link in Bio** — a public hub for everything you've published

## Where it goes

### Published for you

Through official APIs, on your schedule. No browser, no manual upload.

| Channel | What goes out |
|---|---|
| **YouTube** | The long-form episode and its Shorts |
| **X** | An episode post and a supercut |
| **Link in Bio** | Your public episode hub |
| **Podcast RSS** | Syndicated to **13 directories** |

**Apple Podcasts · Spotify · YouTube Music · Amazon Music · iHeartRadio · Pocket Casts · Overcast ·
Castbox · TuneIn · Deezer · Pandora · Player FM · Podchaser**

### Available today: cut, download, post anywhere

Every Short is a downloadable vertical file on our CDN, with its caption and metadata attached. An
agent posts it from the creator's own signed-in session — so all of these are reachable **now**, not
eventually, and none of them need a Longwave integration to work.

**Short-form:** TikTok · Instagram Reels · Facebook Reels · LinkedIn · Threads · Bluesky · Pinterest ·
Snapchat Spotlight · Reddit · Tumblr

**Video platforms:** **Bilibili** · Vimeo · Dailymotion · Rumble · Odysee · Niconico

**Membership and community:** Patreon · Substack · Beehiiv · Ghost · Kit · Discord · Telegram

> **Bilibili is newly open to Western creators.** It relaunched its international app on 19 August
> 2026 and **dropped the identity-verification requirement** — an email address or phone number is now
> enough to register and publish, where a passport used to be required even for creators outside
> China. It has 772 million monthly users, is hiring creator staff in Los Angeles, London, Mexico
> City, São Paulo, Istanbul and Tokyo, and is building an English-language upload site. MrBeast has
> been posting there since 2024.

With a Grok Bot you sign in once and it posts from there, handing the wheel back only for a second
factor or a CAPTCHA.

### Roadmap

Native, scheduled publishing through first-party APIs — no browser — for TikTok · Instagram Reels ·
LinkedIn Video · Bluesky · Threads · X Threads · LinkedIn Article.

## What it costs

**Start free. Creating an account adds 200 credits, no card required, and they do not expire.** That
is roughly six weeks of publishing at three Shorts a day.

You pay **per Short that actually publishes** — nothing for a failed render, nothing for a clip you
decide not to post, and nothing to create a job.

| Action | Credits |
|---|---|
| Publish a Short | **1** |
| Publish a Short on autopilot | **1.5** |
| Publish to X through our shared app quota | **4** |
| Upload a full long-form episode | **5**, plus **1 per GB** |

Captions are included. Show notes (1.5), extended clip retention (0.5) and transcript export (0.5)
are optional extras.

**More credits, if you want them:** $10 → 70 · $25 → 185 · $50 → 400 · $100 → 2,500.

**An agent can never spend your money.** It holds no card, cannot top up, and cannot reach a
checkout. When the balance runs low a tool returns a top-up link; the agent's job is to hand it to
you and stop.

[Current pricing →](https://www.longwave.media/pricing)

## How your data is handled

- **Your YouTube credentials never leave Longwave's servers.** An agent receives an opaque Longwave
  token, never anything issued by Google.
- **Scopes are narrow and explicit.** Reading your channel and creating clips is one level.
  Publishing to a live channel, and changing a published thumbnail, are separate permissions you
  grant deliberately — because both change something public.
- **The agent never touches your money or your credentials** — see *What it costs* above.
- The plugin package itself collects and stores nothing.

[Terms](https://www.longwave.media/terms) · [Privacy](https://www.longwave.media/privacy)

## The plugin

`Longwave-Media/longwave-grok-plugin` — for Grok Build, Grok Bot, Cursor, Claude Code and Muse.

```
grok plugin install Longwave-Media/longwave-grok-plugin
```

## Talk to us

`support@longwave.media` · <https://www.longwave.media>

---

Longwave is a product of **Signal Group Limited** — New Zealand · NZBN 9429035771678 · Co. No 1396666.
