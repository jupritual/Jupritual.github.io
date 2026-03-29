<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-bot/main/assets/avatar.png" width="80" height="80"/><br/><h1>Jupritual</h1>

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

<summary><b>📸 Click to expand screenshots</b></summary>

---

<details>
<summary><b>🗳️ Vote-Based Moderation</b></summary>

## 🗳️ Vote-Based Moderation

> Let your mod team collectively decide — no single mod has to take the blame.

---

### Vote Ban — `j.voteban @user [duration] [mode] [reason]`

Starts a timed vote to ban a member. Requires majority upvotes from mods to execute.

<div align="center">

**Step 1 — Vote in progress**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/voteban-progress.png" width="350"/><br/><br/>

**Step 2 — Ban executed by community vote**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/voteban-success.png" width="350"/>

</div>

---

### Vote Unban — `j.voteunban @user [duration] [mode] [reason]`

Starts a vote to lift an existing ban. Same flow — mods vote, majority wins.

<div align="center">

**Step 1 — Vote in progress**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/voteunban-progress.jpeg" width="350"/><br/><br/>

**Step 2 — Unban executed by community vote**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/voteunban-success.jpeg" width="350"/>

</div>

---

### Vote Kick — `j.votekick @user [duration] [mode] [reason]`

Starts a vote to kick a member. If majority isn't reached — kick is cancelled automatically.

<div align="center">

**Step 1 — Vote in progress**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/votekick-progress.jpeg" width="350"/><br/><br/>

**Step 2 — Kick failed — not enough votes**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/votekick-failed.png" width="350"/>

</div>

</details>

---

<details>
<summary><b>🔧 Moderation Tools</b></summary>

## 🔧 Moderation Tools

> Full channel and member control — lock, inspect, and manage with interactive dropdowns.

---

### Timeout List — `j.timeoutlist`

View all currently timed out members in the server with time remaining — select any member from the dropdown to see full details and manage their timeout.

<div align="center">

**Step 1 — Overview of timed out members**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/timeoutlist-overview.png" width="350"/><br/><br/>

**Step 2 — Dropdown showing members with time remaining**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/timeoutlist-dropdown.png" width="350"/><br/><br/>

**Step 3 — Detailed timeout info with untimeout & back actions**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/timeoutlist-details.jpeg" width="350"/>

</div>

---

### Lock List — `j.locklist`

View all currently locked channels in the server — select any channel from the dropdown to see full details and unlock options.

<div align="center">

**Step 1 — Overview of locked channels**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/locklist-overview.png" width="350"/><br/><br/>

**Step 2 — Dropdown showing all locked channels**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/locklist-dropdown.png" width="350"/><br/><br/>

**Step 3 — Channel details with unlock & back actions**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/locklist-details.png" width="350"/>

</div>

---

### Purge — `j.purge [filter] [amount]`

Delete messages with powerful filters — by user, keyword, embeds, bots, and more. Shows a confirmation with full message preview before deleting anything.

<div align="center">

**Confirmation + live message preview before deletion**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/purge-confirm.jpeg" width="350"/>

</div>

---

### Snipe — `j.snipe [number]`

Recover recently deleted messages — shows message content, who sent it, and who deleted it. Specify a number to recover multiple messages at once.

<div align="center">

**Deleted messages recovered with full details**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/snipe.jpeg" width="350"/>

</div>

</details>

---

<details>
<summary><b>⚠️ Warning System</b></summary>

## ⚠️ Warning System

> A full infraction tracking system — warn members, set automated actions at point thresholds, and track everything with IDs.

---

### Warn — `j.warn @user [points] [reason]`

Warn a member with custom infraction points and reason. Each warn gets a unique infraction ID and shows current total active points.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/warn.jpeg" width="350"/>

</div>

---

### Set Warn Action — `j.setwarnaction`

Configure automatic actions that trigger when a member reaches a points threshold — timeout, kick, ban, add/remove role, or custom message.

<div align="center">

**Step 1 — Current auto-actions overview**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setwarnaction-overview.png" width="350"/><br/><br/>

**Step 2 — Action configuration guide with placeholders**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setwarnaction-guide.jpeg" width="350"/><br/><br/>

**Step 3 — Choose action type dropdown**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setwarnaction-dropdown.png" width="350"/><br/><br/>

**Step 4 — Modal to set points threshold and duration**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setwarnaction-modal.png" width="350"/><br/><br/>

**Step 5 — Action added successfully**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setwarnaction-success.png" width="350"/>

</div>

---

### Warn Leaderboard — `j.warnleaderboard`

Shows the most warned members in the server ranked by active infraction points.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/warnleaderboard.png" width="350"/>

</div>

---

### Remove Warn — `j.removewarn [infraction ID]`

Remove a specific warning by its infraction ID. Points are deducted and the infraction is cleared from the member's record.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/removewarn.png" width="350"/>

</div>

---

### Check Warns — `j.checkwarns @user`

View full warning history for a member — all infractions with IDs, points, reason, moderator, date, and active/expired status.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/checkwarns.png" width="350"/>

</div>

---

### Remove Points — `j.removepoints @user [points]`

Remove a specific number of infraction points from a member. Automatically adjusts or clears infractions accordingly.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/removepoints.png" width="350"/>

</div>

</details>

---

<details>
<summary><b>🎉 Welcome System</b></summary>

## 🎉 Welcome System — `j.welcomesystem`

> Fully configurable join/leave messages and welcome DMs — with embed designer, dynamic placeholders, auto-reactions, interactive buttons, and live preview.

---

**Dashboard — overview of all configured embeds**<br/>

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-dashboard.png" width="350"/>

</div>

---

### Setting Up a Join Embed — Step by Step

<div align="center">

**Step 1 — Select channels to send join messages**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step1-channel.png" width="350"/><br/><br/>

**Step 2 — Embed designer with dynamic placeholders**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step2-designer.jpeg" width="350"/><br/><br/>

**Step 3 — Auto-reactions on welcome messages**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step3-reactions.jpeg" width="350"/><br/><br/>

**Step 4 — Add interactive buttons and dropdowns**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step4-buttons.jpeg" width="350"/><br/><br/>

**Step 4 — Components overview with live preview**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step4-components.jpeg" width="350"/><br/><br/>

**Step 5 — Final review before saving + full live preview**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-step5-review.jpeg" width="350"/>

</div>

---

### Manage Embeds

<div align="center">

**Edit, toggle, enable/disable all embeds from one panel**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-manage-embeds.png" width="350"/>

</div>

---

### Dynamic Placeholders Guide

<div align="center">

**30+ placeholders for user, server, inviter, role, and more**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-placeholders.jpeg" width="350"/>

</div>

---

### Greet System Statistics

<div align="center">

**Full analytics — active embeds, triggers, components, recent activity**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/welcome-stats.jpeg" width="350"/>

</div>

> Leave embed and Welcome DM setup follow the same step-by-step flow.

</details>

---

<details>
<summary><b>📋 Logging System</b></summary>

## 📋 Logging System

> Route every moderation action to its own dedicated log channel — full audit trail with per-moderator activity summaries.

---

### Set Logging — `j.setlogging`

Configure which channel each moderation action logs to. Every action type routes independently.

<div align="center">

**Step 1 — Full logging configuration overview**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setlogging-config.png" width="350"/><br/><br/>

**Step 2 — Select channel for each action type**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/setlogging-channel.png" width="350"/>

</div>

---

### Mod Logs — `j.modlogs @moderator`

View complete moderation history for any moderator — broken down by action type with full entry details and pagination.

<div align="center">

**Step 1 — Activity summary with action counts per type**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/modlogs-overview.jpeg" width="350"/><br/><br/>

**Step 2 — Dropdown to select action type**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/modlogs-dropdown.png" width="350"/><br/><br/>

**Step 3 — Detailed log entries with target, action, and timestamp**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/modlogs-detail.jpeg" width="350"/>

</div>

</details>

---

<details>
<summary><b>💤 AFK System</b></summary>

## 💤 AFK System

> One of the most feature-complete AFK systems available — global or local mode, drop notes, notify on return, full stats tracking.

---

### AFK — `j.afk [reason]`

Set your AFK status with a reason. Choose local (this server only) or global (all servers). When someone pings you, they see your AFK status. Others can drop notes or subscribe to get notified when you return.

<div align="center">

**Step 1 — Choose local or global AFK mode**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/afk-settings.png" width="350"/><br/><br/>

**Step 2 — AFK set confirmation with Notify & Drop Note options**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/afk-set.png" width="350"/><br/><br/>

**Step 3 — Welcome back summary with pings received and notes left**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/afk-welcomeback.jpeg" width="350"/>

</div>

---

### AFK List — `j.afklist`

View all currently AFK members in the server — shows scope (local/global) and AFK info for each member.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/afk-list.jpeg" width="350"/>

</div>

---

### AFK Stats — `j.afkstats [@user]`

View detailed AFK statistics — server AFK time, weekly AFK time, global AFK time, and total sessions.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/afk-stats.png" width="350"/>

</div>

</details>

---

<details>
<summary><b>🤖 Auto-Reaction System</b></summary>

## 🤖 Auto-Reaction System — `j.autoreaction`

> Rule-based automatic emoji reactions — trigger on any text, match type, channel, user, or role. Up to 20 active rules per server.

---

**Dashboard — server status and quick actions**<br/>

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/autoreaction-dashboard.png" width="350"/>

</div>

</details>

---

<details>
<summary><b>🎭 Custom Role System</b></summary>

## 🎭 Custom Role System

> Create trigger-based role commands, manage them from a central control panel, and fully customize the assign/remove embeds per trigger.

---

### Manage Custom Role — `j.managecustomrole`

**Aliases:** `j.customrolemanage`, `j.cr` — **Permission:** Administrator

Opens the Custom Role Control Panel — your central hub for viewing, adding, and deleting role triggers.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-panel.png" width="350"/>

</div>

---

#### View Triggers

Browse all existing triggers with a paginated dropdown. Select any trigger to see its linked role, creator, creation date, usage count, and available actions.

<div align="center">

**Step 1 — Trigger list with paginated dropdown**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-viewtriggers.png" width="350"/><br/><br/>

**Step 2 — Full trigger info with actions**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-triggerdetail.png" width="350"/>

</div>

---

#### Edit Embed

Customize the embed shown when a role is assigned or removed. Supports dynamic placeholders like `{user.name}`, `{guild.icon}`, `{role.mention}`, `{timestamp}`, and more — with a live preview toggle.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-editembed.png" width="350"/>

</div>

---

#### Delete Trigger

Select a trigger from the dropdown to delete it. Shows full trigger details and an irreversibility warning before you confirm.

<div align="center">

**Step 1 — Select a trigger to delete**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-deletepanel.png" width="350"/><br/><br/>

**Step 2 — Trigger details + warning before confirm**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-deleteconfirm.png" width="350"/>

</div>

---

#### Add Trigger

Select a role from the paginated dropdown, set a trigger name via modal — done. The command `j.<triggername> @user` is immediately usable.

<div align="center">

**Step 1 — Select a role**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-addrole.png" width="350"/><br/><br/>

**Step 2 — Enter trigger name**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-settrigger.png" width="350"/><br/><br/>

**Step 3 — Trigger created**<br/>
<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/managecustomrole-created.png" width="350"/>

</div>

---

### Custom Role Panel — `j.customrolepanel @member`

**Permission:** Manage Roles

Assign or remove any configured role trigger for a member — no need to know the trigger name. The bot auto-detects whether to assign or remove based on the member's current roles.

<div align="center">

<img src="https://raw.githubusercontent.com/jupritual/Jupritual-Bot/main/assets/customrolepanel.png" width="350"/>

</div>

</details>


---

## ✦ Add to Your Server

<div align="center">

[![Invite Jupritual](https://img.shields.io/badge/%F0%9F%AA%90%20Invite%20Jupritual-5865F2?style=for-the-badge)](https://discord.com/oauth2/authorize?client_id=1245248139699556394)
[![Top.gg](https://img.shields.io/badge/View%20on%20Top.gg-ff3366?style=for-the-badge&logo=discord&logoColor=white)](https://top.gg/bot/1245248139699556394?s=071b865a14137)
[![Support Server](https://img.shields.io/badge/Support%20Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/fB42jHFHKB)

</div>

---

## ✦ About

Jupritual is independently developed and maintained by a solo developer
with a focus on production-quality architecture, real-world deployment,
and continuously expanding features.

This bot is not a fork. Not a tutorial project. Every system was designed, built, debugged, and deployed independently.

---

<div align="center">
<sub>
Built with Python · discord.py · MongoDB Atlas · Oracle Cloud · 
<a href="https://discord.gg/fB42jHFHKB">Support Server</a> · 
<a href="https://jupritual.github.io/tos">Terms of Service</a> · 
<a href="https://jupritual.github.io/privacy">Privacy Policy</a>
</sub>
</div>