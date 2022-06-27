# Art of the Rail (AotR) Dedicated Server Guide

This guide is how to run an Art of the Rail dedicated server. Currently only deployed for Windows, but Linux support is being tested and is planned. All commands will work the same within the executable.

## Running the Client as a Dedicated Server

By adding ```-batchmode``` as a startup parameter and the client will run as a dedicated server.

## Installation

> :warning: **If using prior to release**: You will need to use a steam key and authenticate, or download from the Itch Store, as steam does not make the application available for anonymous download prior to a game being marked as release.

1. Download from the Itch.Io Store Page
2. Install via Steam Client, under Tools, as ```Art of the Rail Dedicated Server```
3. Install via [SteamCMD](https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip)
   1. Run SteamCMD
   2. Set the desired install directory 
      ```force_install_dir C:\aotrserver```
   3. Login as anonymous client 
      ```login anonymous```
   4. Download the files 
      ```app_update 1699670 validate```

## Startup Parameters

You can use startup parameters in a batch file or shortcut to control how the server executes, note these also apply to both the game client and the server.

> :information_source: text containing spaces should be wrapped in ```"``` quote marks to allow parsing, but quote marks are not required for content not containing spaces. So ```-load mysave``` will work just as well as ```-load "mysave"```

> :information_source: the order of parameters does not matter. Their order of action is queued according to their required action

| Tables | Build | Description |
| ------------------------------ |:-----------------:|-----------------------------------------------------------------------------------|
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
