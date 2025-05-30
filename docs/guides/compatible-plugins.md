Compatible Plugins
======

## Economy / Vault

Parkour natively supports Economy plugins using [Vault](https://dev.bukkit.org/projects/vault/files).

To enable, set `Plugin.Vault.Enabled` to `true` in the `config.yml` and use an Economy plugin that support Vault to successfully link the plugins.

You are able to reward players with an amount of currency, as well as charge them for joining a Course.

To set a Joining Fee: `/pa econ setfee (course) (amount)`.  
To set a Prize Amount: `/pa econ setprize (course) (amount)`.

## PlaceholderAPI

Parkour natively supports [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) which allows you to use Parkour values within other plugins.

To enable, set `Plugin.PlaceholderAPI.Enabled` to `true` in the `config.yml`.

**Please note that Parkour Expansion is no longer needed, as it has been implemented within the Parkour plugin.**

The `Plugin.PlaceholderAPI.CacheTime` value can be set to an interval in minutes for when to clear the cache. This is a performance improvement which caches the placeholder output until the time interval is reached.

[All the Parkour Placeholders are available here](/essential/placeholders.md).

## Decent Holograms

Parkour doesn't directly support [Decent Holograms](https://www.spigotmc.org/resources/decentholograms.96927/), however it can use PlaceholderAPI to create dynamic and nice looking Parkour holograms.

### Example usages

We can create a few examples of what is now possible. For demonstration purposes, I will be using a Course named "tutorial".

<details><summary>Parkour Leaderboards (Click to expand)</summary>

First we create a new Parkour leaderboard Hologram using the command and giving it a title.
`/dh create Leaderboard_tutorial Parkour Leaderboard - Tutorial`

Add a line for each position you want on the leaderboard (up to 10):

`/dh line add Leaderboard_tutorial 1 %parkour_topten_tutorial_1%`
`/dh line add Leaderboard_tutorial 1 %parkour_topten_tutorial_2%`
`/dh line add Leaderboard_tutorial 1 %parkour_topten_tutorial_3%`

Above we are using the Parkour placeholder `%parkour_topten_(course)_(position)%`.
There is an entry in the `strings.yml` named `PlaceholderAPI.TopTenResult` which will allow you to customise the appearance and colours used.

</details>

<details><summary>Parkour Course Best Player (Click to expand)</summary>

First we create a new Parkour leader Hologram using the command and giving it a title.
`/dh create Leader_tutorial Parkour Leader - Tutorial`

Add a line for each detail you want to display:

`/dh line add Leader_tutorial 1 Best Player: %parkour_leaderboard_tutorial_1_player%`
`/dh line add Leader_tutorial 1 Time: %parkour_leaderboard_tutorial_1_time%`
`/dh line add Leader_tutorial 1 Deaths: %parkour_leaderboard_tutorial_1_deaths%`

</details>

<details><summary>Next Checkpoint (Click to expand)</summary>

Display the next checkpoint for the Player to achieve, which displays a hologram above the pressure plate / action required to achieve the checkpoint.

For example, when checkpoint 2 is achieved only the hologram for checkpoint 3 will be visible.

![Next Checkpoint Example](https://i.imgur.com/JcnQsz6.png "Next Checkpoint Example")

Stand over the place where you want the pressure plate to be and enter

`/dh create (course)_checkpoint_(checkpoint) %parkour_current_checkpoint_hologram_(course)_(checkpoint)%`

For example:

`/dh create tutorial_checkpoint_3 %parkour_current_checkpoint_hologram_tutorial_3%`

</details>

## Holographic Displays (v3.0.0+)

Parkour doesn't directly support [Holographic Displays](https://dev.bukkit.org/projects/holographic-displays/files), however it can use PlaceholderAPI to create dynamic and nice looking Parkour holograms.  
_Holographic Displays now natively supports PlaceholderAPI, so no other plugins are required._

### Example Usages

We can create a few examples of what is now possible. For demonstration purposes, I will be using a Course named "tutorial".

<details><summary>Parkour Leaderboards (Click to expand)</summary>

First we create a new Parkour leaderboard Hologram using the command and giving it a title.  
`/hd create Leaderboard_tutorial Parkour Leaderboard - Tutorial`

Add a line for each position you want on the leaderboard (up to 10):

`/hd addline Leaderboard_tutorial {papi: parkour_topten_tutorial_1}`  
`/hd addline Leaderboard_tutorial {papi: parkour_topten_tutorial_2}`  
`/hd addline Leaderboard_tutorial {papi: parkour_topten_tutorial_3}`

Above we are using the Parkour placeholder `%parkour_topten_(course)_(position)%`.
There is an entry in the `strings.yml` named `PlaceholderAPI.TopTenResult` which will allow you to customise the appearance and colours used.

</details>

<details><summary>Parkour Course Best Player (Click to expand)</summary>

First we create a new Parkour leader Hologram using the command and giving it a title.  
`/hd create Leader_tutorial Parkour Leader - Tutorial`

Add a line for each detail you want to display:

`/hd addline Leader_tutorial Best Player: {papi: parkour_leaderboard_tutorial_1_player}`  
`/hd addline Leader_tutorial Time: {papi: parkour_leaderboard_tutorial_1_time}`  
`/hd addline Leader_tutorial Deaths: {papi: parkour_leaderboard_tutorial_1_deaths}`

</details>

<details><summary>Next Checkpoint (Click to expand)</summary>

Display the next checkpoint for the Player to achieve, which displays a hologram above the pressure plate / action required to achieve the checkpoint.

For example, when checkpoint 2 is achieved only the hologram for checkpoint 3 will be visible. 

![Next Checkpoint Example](https://i.imgur.com/JcnQsz6.png "Next Checkpoint Example")

Stand over the place where you want the pressure plate to be and enter

`/hd create (course)_checkpoint_(checkpoint) {papi:parkour_current_checkpoint_hologram_(course)_(checkpoint)}`

For example:

`/hd create tutorial_checkpoint_3 {papi:parkour_current_checkpoint_hologram_tutorial_3}`

</details>

## PlateCommands

[PlateCommands](https://www.spigotmc.org/resources/platecommands.90578/) was originally created as an extension to Parkour to allow for more powerful functionality. A pressure plate can perform command(s) that can be executed by the server or player.

### Example Usages

<details><summary>Multiple action Checkpoints (Click to expand)</summary>

Multiple pressure plates can achieve the same Checkpoint, instead of the limitation of a single pressure plate in Parkour:

`/pc create pac setcheckpoint %player% (checkpoint)`

</details>

<details><summary>Teleport the Player (Click to expand)</summary>

Whilst on a Course you may want the Player to be teleported to a different location, this can be done using:

`/pc create tp %player% (x) (y) (z)`

</details>

<details><summary>Player actions (Click to expand)</summary>

You can let the Player enter pre-determined commands using the "player:" prefix in the command which will execute the command as if the Player entered it.
An example could be walking on a pressure plate to leave the Course:

`/pc create player:pac leave %player%`

</details>

## ParkourGhost

[ParkourGhost](https://www.spigotmc.org/resources/parkourghost.122928/) was created by LOUDO that allows you race against a ghost of your best run, challenging yourself to beat your own record.

![Parkour Top Ten](https://i.imgur.com/117kzs5.png "ParkourGhost example")

<details><summary>Default setup (Click to expand)</summary>

Once you've finished a Course for the first time, you will be able to challenge your ghost by typing `/pg play (course)`.
This will join you to the Course automatically and display your ghost running the Course.
</details>

<details><summary>Integrated setup (Click to expand)</summary>

For a more seamless experience, in ParkourGhost's config.yml set the following:

```
playback.countdown: false
join_parkour_on_playback: false
```

Then in the Parkour config.yml add the following:

```
CourseDefault.Command.Join: 
  - player:pg play %COURSE_NAME% 
```

This will automatically spawn the Ghost when you join the Course, and the countdown will be disabled.
</details>

## Parkour Top Ten

[Parkour Top Ten](https://www.spigotmc.org/resources/parkour-top-ten.46268/) was created by steve4744 to allow for the Player's Head to be proudly displayed next to their best times, great for a competitive Parkour server.

![Parkour Top Ten](https://i.imgur.com/OGBAYkr.png "Parkour Top Ten")

## ConditionalEvents

[ConditionalEvents](https://www.spigotmc.org/resources/conditionalevents-custom-actions-for-certain-events-1-8-1-18.82271/) is a plugin that lets you execute actions when listening to different events.  
_Please note that most actions can be achieved using the [Courses' event command system](/tutorials/parkour-courses?id=command)._

Parkour provides the following custom events for you to listen to:

* io.github.a5h73y.parkour.event.ParkourCheckpointAllEvent
* io.github.a5h73y.parkour.event.ParkourCheckpointEvent
* io.github.a5h73y.parkour.event.ParkourDeathEvent
* io.github.a5h73y.parkour.event.ParkourFinishEvent
* io.github.a5h73y.parkour.event.ParkourTimeResultEvent
* io.github.a5h73y.parkour.event.ParkourJoinEvent
* io.github.a5h73y.parkour.event.ParkourLeaveEvent
* io.github.a5h73y.parkour.event.ParkourPlayerNewLevelEvent
* io.github.a5h73y.parkour.event.ParkourPlayerNewRankEvent
* io.github.a5h73y.parkour.event.ParkourPrizeEvent
* io.github.a5h73y.parkour.event.ParkourResetCourseEvent
* io.github.a5h73y.parkour.event.ParkourResetLeaderboardEvent
* io.github.a5h73y.parkour.event.ParkourResetPlayerEvent

### Example Usages

<details><summary>Replace Me (Click to expand)</summary>

[//]: # (Come up with a decent example.)

```
 event2:
    type: custom
    custom_event_data:
      event: io.github.a5h73y.parkour.event.ParkourFinishEvent
      player_variable: getPlayer()
    conditions:
      - '%player% equals %parkour_leaderboard_lett_1_player%'
    actions:
      default:
      - 'console_command: say congratulations %player%!'
```

</details>

## LeaderHeads

[LeaderHeads](https://www.spigotmc.org/resources/leaderheads.2079/) is a plugin that allows you to create all-time, daily, weekly, and monthly leaderboards from placeholders that return a numeric value.

When used with Parkour, course leaderboards can be created using placeholder `%parkour_player_personal_best_(course)_milliseconds%`

<details><summary>Creating a LeaderHeads Sign (Click to expand)</summary>

First place a sign, and then while looking at the sign, type:

`/leaderheads setsign %parkour_player_personal_best_tutorial_milliseconds% 1 weekly`

In this example the sign will update to show the number 1 ranked player on course 'tutorial' for the week with the time displayed as milliseconds.

![LeaderHeads Example 1](https://i.imgur.com/LTJ9Dw3.png "LeaderHeads Example 1")

In the file `statistics/parkour_player_personal_best_tutorial_milliseconds.yml`, set the statistic type to `time-milliseconds` and the order to `ascending`:

```
statistic-type: time-milliseconds
order-mode: ascending
```

Reload LeaderHeads, and the sign will update to display a formatted time.

![LeaderHeads Example 2](https://i.imgur.com/swbtPkt.png "LeaderHeads Example 2")

The time format can be changed in LeaderHeads' `config.yml`, for example:

`time-format: "{hours}:{minutes}:{seconds}"`

![LeaderHeads Example 3](https://i.imgur.com/XzwLLSL.png "LeaderHeads Example 3")

Currently, LeaderHeads does not appear to support displaying milliseconds as part of the formatted time on the sign.

</details>

## AdvancedReplay

Parkour doesn't directly support [AdvancedReplay](https://www.spigotmc.org/resources/advancedreplay-1-8-1-19.52849/), however you can use PlaceholderAPI which allows you to record and play back each Player's best time.

You will need to install the following plugins to achieve this:

* [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)

To achieve seamless integration with the plugin, Parkour's event command system will be used.

To apply to every single Course, set the `CourseDefault.Command.Join` to:

`replay start %PLAYER%-%COURSE_NAME% %PLAYER%`  

This means only the Player which joined the Course is recorded, the recording name will be a combination of the Player's name and the Course name.

To avoid complications, the recording will only be saved if they complete the Course with either their best time ever, or the Course's best time ever. All other events will discard the recording.

Set the `Leave`, `Finish` commands to `replay stop %PLAYER%-%COURSE_NAME% -nosave`

Set the `PlayerCourseRecord` and `GlobalCourseRecord` commands to `replay stop %PLAYER%-%COURSE_NAME% -force`

Now you can use `/replay play (player)-(course)` to see that Player's best time on the Course. Also, if you have PlaceholderAPI integration you could evaluate the best player's name using `%parkour_course_record_(course)_player%` when wanting to watch the best player's run for the given Course.
