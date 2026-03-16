<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-bot/main/assets/banner.png" width="100%"/>

<br/>

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-bot/main/assets/avatar.png" width="40" height="40" style="border-radius:50%; vertical-align:middle"/> **Jupritual**

**A production-grade Discord moderation & automation bot — built solo from scratch.**

[![Top.gg](https://img.shields.io/badge/Listed%20on-Top.gg-ff3366?style=for-the-badge&logo=discord&logoColor=white)](https://top.gg/bot/1245248139699556394?s=071b865a14137)
[![Invite](https://img.shields.io/badge/Invite%20Jupritual-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/oauth2/authorize?client_id=1245248139699556394)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![discord.py](https://img.shields.io/badge/discord.py-2.x-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discordpy.readthedocs.io)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com)
[![Oracle Cloud](https://img.shields.io/badge/Deployed-Oracle%20Cloud-F80000?style=for-the-badge&logo=oracle&logoColor=white)](https://oracle.com/cloud)

> *146+ commands. Modular architecture. Cloud-deployed. Built by divyam.*

</div>

---

## ✦ What is Jupritual?

Jupritual is not a template bot. It is a **fully custom Discord bot** built from the ground up using Python and discord.py — every system, every embed, every interaction flow designed and coded by hand.

It combines advanced moderation tooling, server automation, a dynamic role system, and a structured help registry into a single production-ready bot — deployed 24/7 on Oracle Cloud infrastructure.

---

## ✦ Feature Overview

### 🛡️ Moderation Suite
> Complete moderation toolkit with confirmation flows, silent variants, and vote-based actions.

| Command | Description |
|---|---|
| `j.ban` / `j.silentban` | Ban with or without public notice |
| `j.voteban` / `j.votekick` | Democratic moderation — mods vote to take action |
| `j.timeout` / `j.untimeout` | Timed mutes with reason tracking |
| `j.warn` | Warning system with infraction points, decay, and leaderboard |
| `j.purge [filter]` | Filtered message deletion — by user, embeds, bots, and more |

**Every action includes:** confirmation buttons, mod log integration, DM notification toggle, and audit trail.

---

### 🔧 Moderation Tools

| Command | Description |
|---|---|
| `j.lock` / `j.unlock` | Channel lock using correct `manage_roles` permission overwrite |
| `j.slock` / `j.sunlock` | Silent lock/unlock with reaction confirmation |
| `j.slowmode` | Set channel slowmode |
| `j.locklist` | View all currently locked channels via dropdown |
| `j.nickname` | Manage member nicknames |
| `j.snipe` | Recover recently deleted messages |

---

### 💤 AFK System
> One of the most feature-complete AFK systems available in a self-built bot.

- **Global & Local modes** — AFK across all servers or just the current one
- **Notify & Drop Note** — people who ping you while AFK can drop notes or subscribe to notify
- **Welcome Back summary** — pings received + notes waiting when you return
- **Privacy settings** — control who can see your AFK status
- **AFK leaderboard & stats**

---

### 🎭 Custom Role System
> A full role assignment engine with trigger-based custom embeds.

- Create named **role triggers** mapped to Discord roles
- Fully **customizable assign/remove embeds** per trigger
- **Dynamic placeholders**: `{user.name}`, `{guild.name}`, `{role.mention}`, `{timestamp}`, and more
- **Live embed preview** before saving
- Trigger management panel: edit, delete, rename — all via interactive buttons

---

### 🤖 Automation

- **Auto-Reaction Manager** — rule-based emoji reactions, up to 20 active rules per server
- **Welcome/Leave System** — configurable join/leave embeds + welcome DMs with dynamic placeholders
- **DM Toggle** — admins control whether the bot sends DMs for moderation actions

---

### 📋 Logging System
> Per-action log routing — each moderation action logs to its own configured channel.

- Per-event channel assignment (ban, kick, warn, lock, role changes, etc.)
- Mod logs overview with dropdown navigation
- Activity summary with action counts per moderator
- Auto-deletes logs older than 90 days

---

### 🎮 Roleplay System
> 50+ roleplay commands in two categories.

- **User actions** (34): hug, kiss, slap, pat, poke, wave, and more
- **Solo actions** (16): cry, smile, blush, think, and more

---

### ⚙️ Server Configuration

- **Dynamic prefix** per server — stored in MongoDB, changeable anytime
- **Command toggle system** — enable/disable any command per-channel or server-wide
- **Logging setup** — route any mod action to any channel
- **Welcome system** — fully configurable with 30+ dynamic placeholders

---

### 📖 Help System
> A structured help registry with dropdown navigation across 12 categories.

```
Bot Help Dashboard
├── Moderation         (ban, silentban, voteban, kick, timeout, warn...)
├── Moderation Tools   (lock, unlock, slowmode, purge, snipe...)
├── Warnings           (warn, setwarnaction, warnleaderboard, setdecay...)
├── User Info          (avatar, banner, userinfo, badges)
├── Server Info        (serverinfo, membercount, setroleicon, welcomesystem)
├── Roleplay           (50+ commands)
├── Logging            (setlogging, modlogs)
├── Automation         (afk, autoreaction)
├── Toggles            (disable, enable, svdisable, svenable, dmtoggle...)
├── Custom Roles       (setroleform, managecustomrole, giverole, removerole)
└── Configuration      (prefix)
```

Each command entry includes: usage, aliases, arguments, permissions required, notes, and examples.

---

## ✦ Architecture

```
jupritual/
├── main.py                  # Bot entry point, cog loader, event hooks
├── cogs/
│   ├── moderation.py        # ban, kick, timeout, warn system
│   ├── mod_tools.py         # lock, unlock, slowmode, purge
│   ├── afk.py               # AFK system with global/local mode
│   ├── autoreaction.py      # Auto-reaction rule engine
│   ├── custom_roles.py      # Role trigger + embed system
│   ├── welcome.py           # Join/leave/DM welcome system
│   ├── logging.py           # Per-action mod log routing
│   ├── roleplay.py          # 50+ roleplay commands
│   ├── info.py              # User/server info commands
│   ├── toggles.py           # Command enable/disable system
│   └── help.py              # Structured help registry
├── mongo_prefix.py          # Dynamic per-guild prefix handler
└── utils/
    └── set_logging.py       # Guild config helper
```

**Key technical decisions:**
- `motor` async driver for non-blocking MongoDB operations
- Per-guild config documents — no shared state between servers
- Cog-based architecture — each system is isolated and independently loadable
- Interactive UI built entirely with `discord.ui.View`, `discord.ui.Button`, `discord.ui.Select`

---

## ✦ Infrastructure

| Layer | Technology |
|---|---|
| Language | Python 3.10+ |
| Discord Library | discord.py 2.x (prefix commands) |
| Database | MongoDB Atlas + motor async |
| Hosting | Oracle Cloud Always Free (Ubuntu VM) |
| Process | systemd service with auto-restart |
| Version Control | GitHub (private) + git pull deploy |
| Bot Listing | Top.gg ✅ Approved |

---

## ✦ Screenshots

<details>
<summary><b>📸 Click to expand screenshots</b></summary>

### Bot Info
> Ping response showing uptime, latency, and 146 available commands

### Help Dashboard
> Category dropdown with all 12 command groups

### AFK System
> Local/Global mode selection → AFK set confirmation → Welcome back summary with notes & pings

### Vote Ban
> Live voting embed with upvote/downvote/abort — timer, mode, and real-time results

### Auto-Reaction Manager
> Rule overview panel with create/list/settings/stats actions

### Custom Role System
> Trigger management panel → Embed customization with 10+ dynamic placeholders

### Purge with Preview
> Confirmation → preview of messages to be deleted → ephemeral result

### Logging Configuration
> Per-action channel routing across moderation, channels, and roles

### Welcome System
> Guild Greet control panel with join/leave embeds + DM configuration

### DM Toggle
> Admin toggle for moderation DMs with last-toggled tracking

</details>

---

## ✦ Add to Your Server

<div align="center">

[![Invite Jupritual](https://img.shields.io/badge/%F0%9F%AA%90%20Invite%20Jupritual%20to%20your%20server-5865F2?style=for-the-badge)](https://discord.com/oauth2/authorize?client_id=1245248139699556394)

[![Top.gg Page](https://img.shields.io/badge/View%20on%20Top.gg-ff3366?style=for-the-badge&logo=discord&logoColor=white)](https://top.gg/bot/1245248139699556394?s=071b865a14137)

</div>

---

## ✦ About

Jupritual is independently developed and maintained by a solo developer
with a focus on production-quality architecture, real-world deployment,
and continuously expanding features.

This bot is not a fork. Not a tutorial project. Every system was designed, built, debugged, and deployed independently.

---

<div align="center">
<sub>Built with Python · discord.py · MongoDB Atlas · Oracle Cloud</sub>
</div>