# Art of the Rail (AotR) Dedicated Server Guide

This guide is how to run an Art of the Rail dedicated server. Currently only deployed for Windows, but Linux support is being tested and is planned. All commands will work the same within the executable.

## Running the Client as a Dedicated Server

By adding ```-batchmode``` as a startup parameter and the client will run as a dedicated server.

## Installation

> :warning: **If using prior to release**: You will need to use a steam key and authenticate, or download from the Itch Store, as steam does not make the application available for anonymous download prior to a game being marked as release.

1. Download from the Itch.Io Store Page
2. Install via Steam Client, under Tools, as ```Art of the Rail Dedicated Server```
3. Install via [SteamCMD](https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip)](https://developer.valvesoftware.com/wiki/SteamCMD)
   1. Run SteamCMD
   2. Set the desired install directory 
      ```force_install_dir C:\aotrserver```
   3. Login as anonymous client 
      ```login anonymous```
   4. Download the files 
      ```app_update 1699670 validate```

## Startup Parameters

You can use startup parameters in a batch file or shortcut to control how the server executes, note these also apply to both the game client and the server.

> :information_source: **Wrap text in quote marks**: text containing spaces should be wrapped in ```"``` quote marks to allow parsing, but quote marks are not required for content not containing spaces. So ```-load mysave``` will work just as well as ```-load "mysave"```

| Parameter | Build | Description |
| ------------------------------ |:-----------------:|-----------------------------------------------------------------------------------|
| ```-batchmode``` | Client | Forces game client to run as a dedicated server |
| ```-nosplash``` | Client | Disables startup logo screens |
| ```-new {x} {y}``` | Client, Server | Generates a new world of dimensions ```{x}``` and ```{y}``` |
| ```-load {filename}``` | Client, Server | Loads the given filename ```{filename}``` |
| ```-editor``` | Client | Enters the ingame prefab editor immediately on startup, bypassing the main menu |
| ```-host``` | Client, Server | Attempts to start as host immediately after starting, will be executed after any load parameters regardless of order |
| ```-join "{address}" "{port}"``` | Client, Server | Attempts to join a game at the given ```{address}``` and ```{port}``` |
| ```-noauth``` | Client | Disables any authentication methods, such as steam authentication |
| ```-localfolder "{path}"``` | Client, Server | Executes using the provided ```{path}``` for all local files such as saves, mods, and settings files |
| ```-name "{name}"``` | Client, Server | Forces the host name to be the provided name, regardless of what is set in the settings file |
| ```-mods "{modid}" ...``` | Client, Server | Disables all mods and then lods on the names of the provided mods. Mod names should be wrapped in quote marks if containing spaces, and each mod name separated by spaces. Such as ```-mods "myfirstmod" "my second mod"``` |
| ```-nosound``` | Client | Disables all sounds, useful mainly for testing. Sounds will not be loaded into memory or executed |
| ```-noimagegen``` | Client | Disables all image generation. UI images will be empty instead |
| ```-debug``` | Client, Server | Full logs during game execution, useful for testing and debugging but not recommended during normal game execution as can have an impact on performance |
| ```-info``` | Client, Server | Logs system information automatically into console during startup |
| ```-nomenuscene``` | Client | Menu scene will not be loaded. The menu itself will be loaded, but background will be blank. Speeds up loading times slightly |
| ```-developer``` | Client | Enables developer systems such as the ingame prefab editor. Note that these may contain bugs and don't always have a lot of documentation |

## Console Commands

You can use a varity of commands using either the ingame console in the game client, or the console when running the game as a dedicated server.

> :information_source: **Question Marks Indicate Optional Variables**: if you see a quotation mark before a command variable it designates that variable as being optional, and does not need to be included for the command to work

| Command | Description |
| ------------------------------ | ---------------------------------------------------------------------- |
| ```addcargo {id} {cargotype} {quantity}``` | adds the provided cargo to the object specified in the id |
| ```addfunds {?companyid} {quantity}``` | adds funds to the provided company, or current company if no id provided |
| ```audiopool {?begin} {?limit}``` | prints all 'audiopool' to the console |
| ```audiosources {?begin} {?limit}``` | prints all 'audiosources' to the console |
| ```cargotypes {?begin} {?limit}``` | prints all 'cargotypes' to the console |
| ```checksum ``` | returns the game data checksum allowing the comparison of game data between clients |
| ```cities {?sortby} {?count}``` | lists all cities in current game; sort by id', name', area' |
| ```clear ``` | clears all console text |
| ```clearcargo {id} {cargotype}``` | clears the provided cargo type |
| ```clearreports ``` | clears all financial reports |
| ```clients {?begin} {?limit}``` | prints all 'clients' to the console |
| ```companies {?begin} {?limit} {?sortby}``` | lists all companies in current game; sort by id', name', funds', founded' |
| ```connect {address} {?port}``` | attempts to connect to the provided address; no port entered will use default port |
| ```date {?date}``` | if provided, sets game date to that provided, if none then displays the current game date |
| ```debug {?scope}``` | sets debug mode to scope: none', audio', signal', block', vehicle', line', node', segment', structure', terrain', fps', report', city' |
| ```delete {id} {?force}``` | deletes object with given Id |
| ```disconnect ``` | closes the current network connection to a host, if any |
| ```enablecheats {?true/false}``` | sets cheats on or off |
| ```files {?begin} {?limit}``` | prints all 'files' to the console |
| ```find {id}``` | centers the camera on the found thing |
| ```follow {id}``` | sets the camera to follow the found thing |
| ```generatelanguage {locale}``` | creates a blank language file for provided locale |
| ```help {?begin} {?limit}``` | prints all 'help' to the console |
| ```helpfile ``` | generates a help file in markdown format |
| ```kick {clientId}``` | disconnects the client from the game |
| ```load {?savename}``` | loads the world with the provided save name; if none uses quick or last save name |
| ```loadsettings ``` | loads the current settings to file |
| ```logtoclipboard ``` | copies the content of the console buffer to the system clipboard buffer |
| ```logtofile {?logname}``` | exports the content of the console buffer to a log file, using the filename if specified |
| ```materials {?begin} {?limit}``` | prints all 'materials' to the console |
| ```meshes {?begin} {?limit}``` | prints all 'meshes' to the console |
| ```mods {?begin} {?limit}``` | returns the currently loaded mods, including core game data |
| ```movetodepot {vehicleid} {depotid}``` | moves vehicle and its children to depot |
| ```network ``` | returns the current network status |
| ```new {x} {y}``` | creates a new world of x and y chunks |
| ```nextmusic ``` | plays the next music track |
| ```pause ``` | will pause the game (including for clients) |
| ```previousmusic ``` | plays the previous music track |
| ```quit ``` | immediately quits the game without any prompts |
| ```resetaudiopool ``` | resets state of audio pool |
| ```restart ``` | restarts the game completely |
| ```save {?savename}``` | saves the current game using the provided save name; if none uses quick or last save name |
| ```savesettings ``` | saves the current settings to file |
| ```say {message}``` | sends a message to all connected players |
| ```set {setting} {value}``` | sets a game setting and applies it |
| ```setcargo {id} {cargotype} {quantity}``` | set the provided cargo to the object specified in the id |
| ```setfilter {true/false}``` | sets audio filter state |
| ```setfunds {?companyid} {quantity}``` | set funds for the provided company, or current company if no id provided |
| ```showfps {?true/false}``` | sets frames per second display |
| ```showgrid {?true/false}``` | sets game grid state |
| ```showprofiler {?true/false}``` | sets render info state |
| ```splineclasses {?begin} {?limit}``` | prints all 'splineclasses' to the console |
| ```starthost {?port}``` | begins hosting the game on the provided port, or the default if none entered |
| ```stations {?sortby} {?count}``` | lists all stations in current game; sort by id', name', company', revenue' |
| ```stophost ``` | stops hosting |
| ```systeminfo ``` | prints system information to console |
| ```threads {?begin} {?limit}``` | prints all 'threads' to the console |
| ```timescale {?value}``` | sets the game speed scale; no entered value returns current speed |
| ```unpause ``` | will unpause the game (including for clients) |
| ```upnp ``` | returns universal plug and play (upnp) state |
| ```vehicles {?sortby} {?count}``` | lists all vehicles in current game; sort by id', name', company', revenue' |
| ```version ``` | returns the game version |

