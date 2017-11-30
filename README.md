# SourceMod for Insurgency
This repository has a complete installation of SourceMod, including all my plugins and source files. It's updated regularly, kept in sync with upstream, and includes a ton of stuff. It's still very much a development branch, so be aware that almost all the plugins I am working on are still pretty new and could be buggy.
##Plugin list
These plugins are all provided as-is, I do my best to document and describe them but they are all potentially broken, so be aware. Please send me feedback and bug reports to help keep these working.

 * <a href='#ammocheck'>Ammo Check 1.0.4</a>
 * <a href='#botcount'>Bot Counter 1.0.0</a>
 * <a href='#botnames'>Bot Names 1.0.5</a>
 * <a href='#botspawns'>Bot Spawns 1.0.0</a>
 * <a href='#cooplobby'>Coop Lobby Override 1.0.0</a>
 * <a href='#damagemod'>Damage Modifier 1.0.0</a>
 * <a href='#events'>Event Logger 1.0.0</a>
 * <a href='#hlstatsx'>HLStatsX CE Ingame Plugin 1.6.19</a>
 * <a href='#insurgency'>Insurgency Support Library 1.5.0</a>
 * <a href='#nofog'>No Fog 1.0.1</a>
 * <a href='#respawn'>Player Respawn 1.9.0</a>
 * <a href='#restrictedarea'>Restricted Area Removal 1.0.0</a>
 * <a href='#rpgdrift'>RPG Adjustments 1.0.0</a>
 * <a href='#suicide_bomb'>Suicide Bombers 0.0.7</a>
 * <a href='#updater'>Updater 1.3.0</a>
 * <a href='#votelog'>Vote Logging 1.0.0</a>
 * <a href='#weapon_pickup'>Weapon Pickup 1.0.0</a>

<a name="ammocheck">
### Ammo Check 1.0.4

Adds a check_ammo command for clients to get approximate ammo left in magazine, and display the same message when loading a new magazine
#### Plugin
[plugins/ammocheck.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/ammocheck.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/ammocheck.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/ammocheck.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_ammocheck_attack_delay" "1" // Delay in seconds until next attack when checking ammo
"sm_ammocheck_enabled" "1" // Allow clients to use check_ammo and post-reload ammo checks
```

#### Command List
```
"check_ammo" // Check ammo of the current weapon
```


<a name="botcount">
### Bot Counter 1.0.0

Shows Bots Left Alive
#### Plugin
[plugins/botcount.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/botcount.smx?raw=true)<br>
#### Source
[scripting/botcount.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/botcount.sp?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>

#### CVAR List
```
"sm_botcount_timer" "60" // Frequency to show count
"sm_botcount_enabled" "0" // sets whether bot naming is enabled
```


<a name="botnames">
### Bot Names 1.0.5

Gives automatic names to bots on creation.
#### Plugin
[plugins/botnames.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/botnames.smx?raw=true)<br>
#### Source
[scripting/botnames.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/botnames.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>

#### CVAR List
```
"sm_botnames_list" "default" // Set list to use for bots
"sm_botnames_enabled" "1" // sets whether bot naming is enabled
"sm_botnames_suppress" "1" // sets whether to supress join/team change/name change bot messages
"sm_botnames_random" "1" // sets whether to randomize names used
"sm_botnames_prefix" "" // sets a prefix for bot names (include a trailing space, if needed!)
"sm_botnames_announce" "0" // sets whether to announce bots when added
```

#### Command List
```
"sm_botnames_reload"
"sm_botnames_rename_all"
```


<a name="botspawns">
### Bot Spawns 1.0.0

Adds a number of options and ways to handle bot spawns
#### Plugin
[gamedata/insurgency.games.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/gamedata/insurgency.games.txt?raw=true)<br>
[plugins/botspawns.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/botspawns.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/botspawns.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/botspawns.sp?raw=true)<br>
[scripting/include/smlib.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/smlib.inc?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_botspawns_min_player_distance" "1200" // Min distance from players to spawn
"sm_botspawns_spawn_mode" "0" // Only normal spawnpoints at the objective, the old way (0), spawn in hiding spots following rules (1), spawnpoints that meet rules (2)
"sm_botspawns_counterattack_finale_infinite" "0" // Obey sm_botspawns_counterattack_respawn_mode (0), use rules and do infinite respawns (1)
"sm_botspawns_spawn_attack_delay" "10" // Delay in seconds for spawning bots to wait before firing.
"sm_botspawns_remove_unseen_when_capping" "1" // Silently kill off all unseen bots when capping next point (1, default)
"sm_botspawns_counterattack_mode" "0" // Do not alter default game spawning during counterattacks (0), Respawn using new rules during counterattack by following sm_botspawns_respawn_mode (1)
"sm_botspawns_total_spawn_frac" "1.75" // Total number of bots to spawn as multiple of number of bots in game to simulate larger numbers. 1 is standard, values less than 1 are not supported.
"sm_botspawns_spawn_snipers_alone" "1" // Spawn snipers alone, can be 50% further from the objective than normal bots if this is enabled?
"sm_botspawns_min_spawn_delay" "1" // Min delay in seconds for spawning. Set to 0 for instant.
"sm_botspawns_max_fireteam_size" "5" // Max number of bots to spawn per fireteam. Default 5
"sm_botspawns_min_objective_distance" "1" // Min distance from next objective to spawn
"sm_botspawns_counterattack_frac" "0.5" // Multiplier to total bots for spawning in counterattack wave
"sm_botspawns_max_objective_distance" "12000" // Max distance from next objective to spawn
"sm_botspawns_max_player_distance" "16000" // Max distance from players to spawn
"sm_botspawns_max_spawn_delay" "30" // Max delay in seconds for spawning. Set to 0 for instant.
"sm_botspawns_min_counterattack_distance" "3600" // Min distance from counterattack objective to spawn
"sm_botspawns_enabled" "0" // Enable enhanced bot spawning features
"sm_botspawns_max_frac_in_game" "1" // Max multiplier of bot quota to have alive at any time. Set to 1 to emulate standard spawning.
"sm_botspawns_min_frac_in_game" "0.75" // Min multiplier of bot quota to have alive at any time. Set to 1 to emulate standard spawning.
"sm_botspawns_stop_spawning_at_objective" "1" // Stop spawning new bots when near next objective (1, default)
"sm_botspawns_min_fireteam_size" "3" // Min number of bots to spawn per fireteam. Default 3
```


<a name="cooplobby">
### Coop Lobby Override 1.0.0

Plugin for overriding Insurgency Coop to 32 players
#### Plugin
[plugins/cooplobby.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/cooplobby.smx?raw=true)<br>
#### Source
[scripting/cooplobby.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/cooplobby.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>


<a name="damagemod">
### Damage Modifier 1.0.0

Modifies damage before applying to players
#### Plugin
[plugins/damagemod.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/damagemod.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/damagemod.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/damagemod.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_damagemod_ff_min_distance" "120" // Minimum distance between players for Friendly Fire to register
"sm_damagemod_enabled" "1" // Enable Damage Mod plugin
```


<a name="events">
### Event Logger 1.0.0

Log events to client or server
#### Plugin
[plugins/events.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/events.smx?raw=true)<br>
#### Source
[scripting/events.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/events.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_events_prefix" "sPrefix" // What to prefix on event messages
```

#### Command List
```
"sm_events_keylistentoall" // Start listening to all event keys
"sm_events_stoplisten" // Stop listening to all events and keys
"sm_events_listkeys" // List all keys for an event
"sm_events_listevents" // List all hooked events
"sm_events_searchevents" // Search for events
"sm_events_keylisten" // Start or stop listening to an event's keys
"sm_events_listentoall" // Start listening to all events
"sm_events_listen" // Start or stop listening to an event
```


<a name="hlstatsx">
### HLStatsX CE Ingame Plugin 1.6.19

Provides ingame functionality for interaction from an HLstatsX CE installation
#### Plugin
[plugins/hlstatsx.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/hlstatsx.smx?raw=true)<br>
#### Source
[scripting/hlstatsx.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/hlstatsx.sp?raw=true)<br>
[scripting/include/loghelper.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/loghelper.inc?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>

#### CVAR List
```
"hlx_block_commands" "1" // If activated HLstatsX commands are blocked from the chat area
"hlx_protect_address" "" // Address to be protected for logging/forwarding
"hlxce_webpage" "http://www.hlxcommunity.com" // http://www.hlxcommunity.com
"hlx_server_tag" "1" // If enabled, adds "HLstatsX:CE" to server tags on supported games. 1 = Enabled (default), 0 = Disabled
"hlx_message_prefix" "" // Define the prefix displayed on every HLstatsX ingame message
```

#### Command List
```
"hlx_sm_bulkpsay"
"hlx_sm_team_action"
"hlx_sm_world_action"
"log"
"hlx_sm_psay"
"hlx_sm_swap"
"hlx_sm_browse"
"hlx_sm_hint"
"hlx_sm_redirect"
"hlx_sm_csay"
"hlx_sm_msay"
"hlx_sm_tsay"
"logaddress_del"
"hlx_sm_psay2"
"hlx_message_prefix_clear"
"logaddress_delall"
"hlx_sm_player_action"
```


<a name="insurgency">
### Insurgency Support Library 1.5.0

Provides functions to support Insurgency. Includes logging, round statistics, weapon names, player class names, and more.
#### Plugin
[translations/insurgency.phrases.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/translations/insurgency.phrases.txt?raw=true)<br>
[gamedata/insurgency.games.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/gamedata/insurgency.games.txt?raw=true)<br>
[plugins/insurgency.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/insurgency.smx?raw=true)<br>
#### Source
[scripting/insurgency.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/insurgency.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/loghelper.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/loghelper.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_insurgency_class_strip_words" "template training coop security insurgent survival" // Strings to strip out of player class (squad slot) names
"sm_insurgency_checkpoint_capture_player_ratio" "0.5" // Fraction of living players required to capture in Checkpoint
"sm_insurgency_infinite_magazine" "0" // Infinite magazine, will never need reloading.
"sm_insurgency_enabled" "1" // sets whether log fixing is enabled
"sm_insurgency_disable_sliding" "0" // 0: do nothing, 1: disable for everyone, 2: disable for Security, 3: disable for Insurgents
"sm_insurgency_log_level" "error" // Logging level, values can be: all, trace, debug, info, warn, error
"sm_insurgency_infinite_ammo" "0" // Infinite ammo, still uses magazines and needs to reload
"sm_insurgency_checkpoint_counterattack_capture" "0" // Enable counterattack by bots to capture points in Checkpoint
```


<a name="nofog">
### No Fog 1.0.1

Removes fog
#### Plugin
[plugins/nofog.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/nofog.smx?raw=true)<br>
#### Source
[scripting/nofog.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/nofog.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_nofog_enabled" "1" // sets whether fog is enabled
```


<a name="respawn">
### Player Respawn 1.9.0

Respawn players
#### Plugin
[translations/common.phrases.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/translations/common.phrases.txt?raw=true)<br>
[translations/respawn.phrases.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/translations/respawn.phrases.txt?raw=true)<br>
[gamedata/plugin.respawn.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/gamedata/plugin.respawn.txt?raw=true)<br>
[plugins/respawn.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/respawn.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/respawn.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/respawn.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>

#### CVAR List
```
"sm_respawn_enabled" "1" // Enable respawn plugin
"sm_respawn_reset_each_round" "1" // Reset player respawn counts each round
"sm_respawn_final_counterattack" "0" // Respawn during final counterattack? (0: no, 1: yes, 2: infinite)
"sm_respawn_auto" "0" // Automatically respawn players when they die; 0 - disabled, 1 - enabled
"sm_respawn_delay" "1.0" // How many seconds to delay the respawn
"sm_respawn_counterattack" "0" // Respawn during counterattack? (0: no, 1: yes, 2: infinite)
"sm_respawn_count_team2" "-1" // Respawn all Team 2 players this many times
"sm_respawn_count_team3" "-1" // Respawn all Team 3 players this many times
"sm_respawn_count" "0" // Respawn all players this many times
"sm_respawn_reset_each_objective" "1" // Reset player respawn counts each objective
```

#### Command List
```
"sm_respawn" // sm_respawn <#userid|name>
```


<a name="restrictedarea">
### Restricted Area Removal 1.0.0

Plugin for removing Restricted Areas
#### Plugin
[plugins/restrictedarea.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/restrictedarea.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/restrictedarea.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/restrictedarea.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_restrictedarea_enabled" "1" // sets whether bot naming is enabled
```


<a name="rpgdrift">
### RPG Adjustments 1.0.0

Adjusts behavior of RPG rounds
#### Plugin
[plugins/rpgdrift.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/rpgdrift.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/rpgdrift.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/rpgdrift.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>
[scripting/include/smlib/entities.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/smlib/entities.inc?raw=true)<br>

#### CVAR List
```
"sm_rpgdrift_enabled" "1" // Sets whether RPG drifting is enabled
"sm_rpgdrift_always_bots" "1" // Always affect bot-fired rockets
"sm_rpgdrift_chance" "0.25" // Chance as a fraction of 1 that a player-fired rocket will be affected
"sm_rpgdrift_amount" "2.0" // Sets RPG drift max change per tick
```


<a name="suicide_bomb">
### Suicide Bombers 0.0.7

Adds suicide bomb for bots
#### Plugin
[plugins/suicide_bomb.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/suicide_bomb.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/suicide_bomb.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/suicide_bomb.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_suicidebomb_auto_detonate_range" "0" // Range at which to automatically set off the bomb (0 is disabled)
"sm_suicidebomb_player_classes" "sapper bomber suicide" // Player classes to apply suicide bomber changes to
"sm_suicidebomb_enabled" "0" // sets whether suicide bombs are enabled
"sm_suicidebomb_spawn_delay" "30" // Do not detonate if player has been alive less than this many seconds
"sm_suicidebomb_auto_detonate_count" "2" // Do not detonate until this many enemies are in range
"sm_suicidebomb_explode_armed" "0" // Explode when killed if C4 or IED is in hand
"sm_suicidebomb_strip_weapons" "1" // Remove all weapons from suicide bombers except the bomb
"sm_suicidebomb_death_chance" "0.1" // Chance as a fraction of 1 that a bomber will explode when killed
"sm_suicidebomb_bots_only" "1" // Only apply suicide bomber code to bots
```


<a name="updater">
### Updater 1.3.0

Automatically updates SourceMod plugins and files
#### Plugin
[translations/common.phrases.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/translations/common.phrases.txt?raw=true)<br>
[plugins/updater.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/updater.smx?raw=true)<br>
#### Source
[scripting/updater.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/updater.sp?raw=true)<br>
[scripting/include/cURL.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/cURL.inc?raw=true)<br>
[scripting/include/socket.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/socket.inc?raw=true)<br>
[scripting/include/steamtools.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/steamtools.inc?raw=true)<br>

#### CVAR List
```
"sm_updater" "2" // Determines update functionality. (1 = Notify, 2 = Download, 3 = Include source code),0
```

#### Command List
```
"sm_updater_status" // View the status of Updater.
"sm_updater_check" // Forces Updater to check for updates.
```


<a name="votelog">
### Vote Logging 1.0.0

Logs voting events
#### Plugin
[plugins/votelog.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/votelog.smx?raw=true)<br>
#### Source
[scripting/votelog.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/votelog.sp?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/loghelper.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/loghelper.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_votelog_enabled" "1" // Enable vote logging
```


<a name="weapon_pickup">
### Weapon Pickup 1.0.0

Weapon Pickup logic for manipulating player inventory
#### Plugin
[gamedata/insurgency.games.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/gamedata/insurgency.games.txt?raw=true)<br>
[gamedata/sdkhooks.games/engine.insurgency.txt](https://github.com/jaredballou/insurgency-sourcemod/blob/master/gamedata/sdkhooks.games/engine.insurgency.txt?raw=true)<br>
[plugins/weapon_pickup.smx](https://github.com/jaredballou/insurgency-sourcemod/blob/master/plugins/weapon_pickup.smx?raw=true)<br>
#### Dependencies
<a href='#insurgency'>insurgency</a><br>
#### Source
[scripting/weapon_pickup.sp](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/weapon_pickup.sp?raw=true)<br>
[scripting/include/smlib.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/smlib.inc?raw=true)<br>
[scripting/include/insurgency.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/insurgency.inc?raw=true)<br>
[scripting/include/updater.inc](https://github.com/jaredballou/insurgency-sourcemod/blob/master/scripting/include/updater.inc?raw=true)<br>

#### CVAR List
```
"sm_weapon_pickup_ammo" "1" // sets whether picking up a weapon the player already has will add to the player's ammo count
"sm_weapon_pickup_max_explosive" "3" // Maximum number of ammo that can be carried for explosives
"sm_weapon_pickup_enabled" "1" // sets whether weapon pickup manipulation is enabled
"sm_weapon_pickup_max_magazine" "12" // Maximum number of magazines that can be carried
```

#### Command List
```
"wp_weaponlist" // Lists all weapons. Usage: wp_weaponlist [target]
"wp_weaponslots" // Lists weapon slots. Usage: wp_weaponslots [target]
"wp_removeweapons" // Removes all weapons. Usage: wp_removeweapons [target]
```




## Ideas to develop
This is a sort of scratchpad and todo list for things that I think of or people ask for me to work on.
* [X] Remove counterattack capture ability in checkpoint coop mode via a cvar. Having to capture a building and then stand inside it while it gets assaulted instead of choosing good firing positions outside makes the game switch from tight, careful action to Call of Duty twitch shooter.
* [X] Review bot CVARs and changes from last two patches to see if there are any new options to try or setting changes that can help get the bots to behave like mildly well trained, scared teenagers instead of a guy on a sunday stroll who can hipshoot you at a hundred meters.
* [ ] IR strobe on the back of US helmets for IFF. Possible to do with a particle effect or alpha/color mask, Source engine precompiled lighting makes actual strobes unlikely.
* [ ] IR laser? Is there a variable I can check to see if a player has NV enabled, and then how to control visibility of the beam per-client.
* [ ] Artillery, mortar, or air support SM plugin to give delayed but devastating damage on an area? How to balance and offset the massive power for the Insurgent side?
* [ ] Wounded/disabled players, can talk for very short time but no ability to move or shoot? Implement contact shots?
* [ ] Look at ability to modify game rules via tricky Sourcemod magic, like passing off spawning additional waves, spawning in staggered groups, and other fun things we need to do.
* [ ] Ability to loot ammo from dead bodies and have them added to the player's inventory properly. Needs to be sorted out how player inventory is handled, with the array method where each magazine's capacity is tracked and retained, and make sure we only pick up the right ammo for the primary weapon. The system needs to inform player "picked up one full AK74 magazine" or "picked up one nearly empty M16 magazine". Should loot from most full to least full, loot one mag per run of the command, and say how many mags still available to be looted. Add cvar-controlled timer to delay next loot/shoot/reload/switch for half a second or so to balance it. Add support for shared magazines, namely AKS74U/AK74 and M16/M4A1/MK18.
* [ ] Decouple flashbang visual impairment and audio impairment. The goal is to slightly increase flashed vision loss time, but greatly increase efefct and duration of audio impairment.
* [X] Add controls to disable bot shooting while sliding or jumping.
* [X] Add controls to disable firing for slight delay after jumping or falling.
* [ ] Add slot for "ear protection", can be Peltors, plugs, or nothing. Costs points, affects shots/frags/flashes impact on hearing
* [ ] Add slot for radio, allow Prox, Squad, or Team as options to select how widely they want to communicate. maybe some team-level abilities via radio?
* [ ] Add tripwires, timers, and daisy chains to IEDs for Insurgents, give them multiple IEDs and have a defuse mission
* [X] Add fragmentation effect to grenades, slightly reduce damage blast radius but shoots 60+ fragments (bullets) out in a random pattern to really clear a room
* [ ] Create config-driven rules-based tutorial mod to tell players about their chosen kits and loadout. Have events hooked to firing, killing, getting killed, etc. to use in tips.
* [ ] Add ability to place explosives (grenades with mechanical switches) as booby traps
* [ ] Add 100 round magazine for SAR that adds weight/recoil to promote bipod use in intermediate machinegun role
* [ ] Add deployable supply point to Squad Leader. Destructible cache point that can be deployed and packed. One per round so it needs to be protected.

