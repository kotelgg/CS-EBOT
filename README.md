# CS 1.6 E-BOT !
AI Bot for Counter-Strike based on SyPB, this bot is only for zombie plague/escape and biohazard gamemodes.

### Try bots on public Counter-Strike 1.6 servers

- `csko.cz:27017` — custom zombie based on Zombie Plague (maps are in fog or partial darkness)
- `csko.cz:27031` — Zombie Plague 4.3 (complete darkness)  
- `csko.cz:27070` — zombie escape

  
<br>

[Click HERE To Join E-BOT Discord Community](http://discord.gg/v7PesBamXt)

<br>

### Features
- included semiclip
- auto wp generator
- API bridge for amxx
- zombie bots can destroy custom breakables
- hp multiplier for zombie bots
- damage multiplier to func_breakables
- human bots can use double jump
- radio commands
- support for parachute plugin (plugin example is in this pack: https://github.com/kotelgg/zp_ebot_pack/releases/tag/ZP-PACK-1.0)

### **Semiclip features**
- team filter
- filter for bots, players
- duck boost support for zombie boost + team filter
- players marked as ducking for boost are highlighted with an orange glow
- unstuck handling for players who end up stuck inside another player after spawning, teleporting, or changing teams
- knife trace correction for zombie attacks during semiclip
- human bots can shoot or knife breakable entities even while inside teammates due to semiclip
- optional semiclip handling for registered non-player entities
- this feature was implemented to keep CPU usage as low as possible

<br>

# How to install
1. Download & install metamod if you dont have.
2. Download latest ebot release.
3. Put ebot folder to "cstrike\addons"
4. Open "cstrike\addons\metamod\plugins.ini"
5. (For Windows) Add that line "win32 addons\ebot\dlls\ebot.dll" and save it.
6. (For Linux) Add that line "linux addons/ebot/dlls/ebot.so" and save it.

Or download this pack for Windows:
https://github.com/kotelgg/zp_ebot_pack/releases/tag/ZP-PACK-1.0

Add this to the config(amxx.cfg or server.cfg, etc.) if you're using ReHLDS (it fixes helicopter and elevator movement when using semiclip):
```
sv_force_ent_intersection 1
```



##  **System Requirements (Linux)**

> **Required glibc: 2.19+**
glibc 2.19 is already included in **Debian 8 (Jessie)**, so the Linux build should work on Debian 8 or newer.

---

### Tested on

Linux Debian 8, Linux Debian 13, Windows 7, Windows 10

**Linux dedicated server (rehlds + metamod-r + AMX Mod X 1.10.0.5474):**
```
ReHLDS-3.14.0.857
Metamod-r v1.3.0.149, API (5:13)
Metamod-r build: 11:31:17 Apr 23 2024
```

**Windows listen server (cs 1.6 steam + metamod-p + AMX Mod X 1.10.0.5474):**
```
Metamod v1.21p37  2013/05/30 (5:13)
```


# How to use - local listen server (cs client)
1. Write this to client console: `bind k "ebot menu"`
2. Write this to client console: `bind j "ebot wp menu"`

Press `j` or `k` and you can manage waypoints and bots. 


# How to use - dedicated server
1. Set password in ebot.cfg, for example: `ebot_password_key "39532"`
2. Write this to client console: `setinfo ebot_pass "39532"`
3. Restart server
3. Write this to client console: `bind k "ebot menu"`
4. Write this to client console: `bind j "ebot wp menu"`
5. Write this to client console: `ebot wp on`

Now on `k` you have main menu and on `j` wp editing menu.


### Other usefull commands:
- `bind "KP_MINUS"             "ebot kickall"`
- `bind "KP_PLUS"              "ebot_add"`
- `bind "*"                    "ebot killbots"`


## E-Bot Commands (Console)
Main command entry:
- `ebot <command> [args...]`

Standalone commands:
- `ebot_about` - print version/about info.
- `ebot_add` - add one random bot.
- `ebot_add_t` / `ebot_add_tr` - add one random Terrorist bot.
- `ebot_add_ct` - add one random Counter-Terrorist bot.

Core commands (`ebot ...`):
- `help` / `?` - show help (`ebot help full` for extended output).
- `version` / `ver` - show version.
- `about` / `about_bot` - show about block.
- `time` / `ctime` - print current server time.
- `menu` / `botmenu` - open main menu.
- `cmenu` / `cmdmenu` - open command menu.
- `list` / `listbots` - list active bots.
- `fill` / `fillserver` - fill server with bots.
- `kickall` / `kickbots` - remove all bots.
- `killall` / `killbots` - kill all bots.
- `kick` / `kickone` - remove one random bot.
- `kick_t` / `kickbot_t` - remove one random T bot.
- `kick_ct` / `kickbot_ct` - remove one random CT bot.
- `kill_t` / `killbots_t` - kill all T bots.
- `kill_ct` / `killbots_ct` - kill all CT bots.
- `swap` / `swaptteams` - swap teams.
- `order` / `sendcmd` - execute command on selected bot.
- `health <value>` / `sethealth <value>` - set bot health.
- `gravity <value>` / `setgravity <value>` - set bot gravity.

`ebot fill` syntax:
- `ebot fill [team] [personality] [skill] [count]`
- `team`: `1` = T, `2` = CT, `5` = random/default.
- omitted args use default/random behavior.

`ebot order` syntax:
- `ebot order <client_index> <bot_command>`
- example: `ebot order 3 radio1`

Waypoint commands (`ebot wp`, aliases: `ebot waypoint`, `ebot wpt`):
- `ebot wp` - print waypoint mode status.
- `ebot wp on` / `ebot wp off` - enable/disable waypoint editing mode.
- `ebot wp noclip` - toggle waypoint noclip helper.
- `ebot wp mdl on` / `ebot wp mdl off` - show/hide spawn models.
- `ebot wp menu` - open waypoint menu.
- `ebot wp add` - open add-waypoint menu.
- `ebot wp flags` - open waypoint flags menu.
- `ebot wp addbasic` - create base waypoints.
- `ebot wp analyze` / `ebot wp analyzeoff` / `ebot wp analyzefix` - analyze workflow.
- `ebot wp find <index>` - set/find waypoint index.
- `ebot wp cache` - cache nearest waypoint.
- `ebot wp teleport <index>` - teleport to waypoint.
- `ebot wp setradius <value>` - set nearest waypoint radius.
- `ebot wp autodelete <value>` - auto-delete waypoints within value units around the editor; `0` disables it.
- `ebot wp setmesh <value>` - set nearest waypoint mesh id.
- `ebot wp setgravity <value>` - set nearest waypoint gravity.
- `ebot wp delete` - delete nearest waypoint.
- `ebot wp save` / `ebot wp save nocheck` - save waypoint file.
- `ebot wp load` - load waypoint file.
- `ebot wp check` - validate waypoint graph.

Path commands (`ebot path`, aliases: `ebot pathwaypoint`, `ebot pwp`):
- `ebot path create` - open create-path menu.
- `ebot path delete` - delete path between selected points.
- `ebot path autodistance` - open auto-path distance menu.
- `ebot path create_out` - create outgoing path.
- `ebot path create_in` - create incoming path.
- `ebot path create_both` - create both-way path.
- `ebot path create_jump` - create jump path.
- `ebot path create_boost` - create zombie boost path.
- `ebot path create_visible` - create visible-only path.

Autowaypoint commands:
- `ebot autowp on` / `ebot autowp off` (alias: `ebot autowaypoint`) - toggle auto waypointing.
