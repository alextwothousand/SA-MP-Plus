SA-MP+
==========

A client modification that uses SA-MP's plugin SDK to interact with the server and add new features

Download
---------
  * [PAWN include](Build/sampp.inc?raw=true)
  * [SublimeText auto complete file](Build/Pawn.sublime-completions?raw=true)
  * [Source code](https://github.com/v01d-/SA-MP-Plus/archive/master.zip)

#### Windows:
  * [Server plugin](Build/Release/sampp_server.dll?raw=true)
  * [Client addon](Build/Release/sampp_client.asi?raw=true)

#### Linux:
  * [Server plugin](Build/Release/sampp_server.so?raw=true)

Installation (Client)
---------
 * Download and run the [Installer](https://github.com/KingHual/SA-MP-Plus/blob/master/Build/Release/sampp-installer.exe?raw=true)
 
 Alternatively:

  * Download and install an [ASI Loader for GTA San Andreas](http://www.gtagarage.com/mods/show.php?id=8321) if you don't have one,
  * Place the [sampp_client.asi](Build/Release/sampp_client.asi?raw=true) file in your GTA:SA's folder, along with *gta_sa.exe*.
  

Installation (Server)
---------
  * Download the [Windows](Build/Release/sampp_server.dll?raw=true) or [Linux](Build/Release/sampp_server.so?raw=true) server plugin.
  * Place the file in the *plugins* folder of your server.
  * Add the plugin to your server's *server.cfg*.

Scripting
---------

#### Defines
```Pawn
#define HUD_COMPONENT_ALL 0
#define HUD_COMPONENT_AMMO 1
#define HUD_COMPONENT_WEAPON 2
#define HUD_COMPONENT_HEALTH 3
#define HUD_COMPONENT_BREATH 4
#define HUD_COMPONENT_ARMOUR 5
#define HUD_COMPONENT_MINIMAP 6
#define HUD_COMPONENT_CROSSHAIR 7
#define HUD_COMPONENT_MONEY 8

#define HUD_COLOUR_MONEY_POSITIVE 0
#define HUD_COLOUR_MONEY_NEGATIVE 1
#define HUD_COLOUR_ARMOUR 2
#define HUD_COLOUR_HEALTH 3
#define HUD_COLOUR_BREATH 4
#define HUD_COLOUR_AMMO 5
#define HUD_COLOUR_WANTED_LEVEL 6
#define HUD_COLOUR_RADIO_TUNED 7
#define HUD_COLOUR_RADIO_UNTUNED 8

#define RADIO_PLAYBACKFM 1
#define RADIO_KROSE 2
#define RADIO_KDST 3
#define RADIO_BOUNCEFM 4
#define RADIO_SFUR 5
#define RADIO_LOSSANTOS 6
#define RADIO_RADIOX 7
#define RADIO_CSR 8
#define RADIO_KJAHWEST 9
#define RADIO_MASTERSOUNDS 10
#define RADIO_WCTR 11
#define RADIO_UTP 12
#define RADIO_OFF 13

#define PAUSE_ID_STATS 0
#define PAUSE_ID_STARTGAME 1
#define PAUSE_ID_BRIEF 2
#define PAUSE_ID_AUDIOSETTINGS 3
#define PAUSE_ID_DISPLAYSETTINGS 4
#define PAUSE_ID_MAP 5
#define PAUSE_ID_DEFAULTSETTINGS 23
#define PAUSE_ID_AUDIODEFAULTSETTINGS 24
#define PAUSE_ID_CONTROLLERDEFAULTSETTINGS 25
#define PAUSE_ID_USERTRACKOPTIONS 26
#define PAUSE_ID_LANGUAGE 28
#define PAUSE_ID_OPTIONS 33
#define PAUSE_ID_QUITGAME 35
#define PAUSE_ID_CONTROLLERSETUP 36
#define PAUSE_ID_REDEFINECONTROLS 37
#define PAUSE_ID_FOOTVEHICLECONTROLS 38
#define PAUSE_ID_MOUSESETTINGS 39
#define PAUSE_ID_JOYPADSETTINGS 40
#define PAUSE_ID_MAIN 41

#define PLAYER_ACTION_ALL 0
#define PLAYER_ACTION_SPRINT 1
#define PLAYER_ACTION_ENTER_CAR 2
#define PLAYER_ACTION_CROUCH 3
#define PLAYER_ACTION_FIRE_WEAPON 4
#define PLAYER_ACTION_UNKNOWN 5
#define PLAYER_ACTION_SWITCH_WEAPON 6
#define PLAYER_ACTION_JUMP 7

#define STUNT_TYPE_TWO_WHEELS 247
#define STUNT_TYPE_INSANE 173
#define STUNT_TYPE_WHEELIE 117
#define STUNT_TYPE_STOPPIE 233

#define DEFAULT_BLUR_INTENSITY 36
#define NO_BLUR_INTENSITY 0

#define DEFAULT_AIRCRAFT_HEIGHT 800
#define DEFAULT_JETPACK_HEIGHT 100

#define MOUSE_LEFT_CLICK 0
#define MOUSE_RIGHT_CLICK 1
#define MOUSE_MIDDLE_CLICK 2
```

#### Functions
```Pawn
ToggleHUDComponentForPlayer(playerid, componentid, bool:toggle);
SetRadioStationForPlayer(playerid, stationid);
SetWaveHeightForPlayer(playerid, Float:height);
SetWaveHeightForAll(Float:height);
TogglePauseMenuAbility(playerid, bool:toggle);
IsPlayerInPauseMenu(playerid);
SetPlayerHUDComponentColour(playerid, componentid, colour);
TogglePlayerAction(playerid, actionid, bool:toggle);
SetPlayerBlurIntensity(playerid, intensity);
SetPlayerGameSpeed(playerid, Float:speed);
TogglePlayerDriveOnWater(playerid, bool:toggle);
TogglePlayerFrozen(playerid, bool:toggle);
SetPlayerPedAnims(playerid, bool:toggle);
TogglePlayerSwitchReload(playerid, bool:toggle);
bool:IsUsingSAMPP(playerid);
GetPlayerResolution(playerid, &X, &Y);
SetPlayerNoReload(playerid, bool:toggle);
TogglePlayerInfiniteRun(playerid, bool:toggle);
SetPlayerAircraftHeight(playerid, Float:height);
Float:GetPlayerAircraftHeight(playerid);
SetPlayerJetpackHeight(playerid, Float:height);
Float:GetPlayerJetpackHeight(playerid);
TogglePlayerVehicleBlips(playerid, bool:toggle);
GetPlayerVehicleBlips(playerid);
GetPlayerRadioStation(playerid);
TogglePlayerInfiniteOxygen(playerid, bool:toggle);
ToggleWaterBuoyancy(playerid, bool:toggle);
ToggleUnderwaterEffect(playerid, bool:toggle);
ToggleNightVision(playerid, bool:toggle);
ToggleThermalVision(playerid, bool:toggle);
SAMPP_ExecuteCallback(type, {Float,_}:...);

// Experimental/Unstable
SetPlayerCheckpointEx(playerid, Float:x, Float:y, Float:z, Float:size, colour = 0xFF000020, period = 1024, Float:pulse = 0.1, rotation_rate = 0, bool:check_z = true);
SetPlayerCheckpointColour(playerid, colour);
SetPlayerRaceCheckpointEx(playerid, type, Float:x, Float:y, Float:z, Float:point_x, Float:point_y, Float:point_z, Float:size, colour = 0xFF000020, period = 1024, Float:pulse = 0.1, rotation_rate = 0);
SetPlayerRaceCheckpointColour(playerid, colour);
```

#### Callbacks
```Pawn
OnPlayerOpenPauseMenu(playerid);
OnPlayerClosePauseMenu(playerid);
OnPlayerEnterPauseSubmenu(playerid, from, to);
OnDriverDriveByShot(playerid);
OnPlayerStunt(playerid, stuntid, money, details[]);
OnPlayerResolutionChange(playerid, X, Y);
OnPlayerSAMPPConnect(address[], port);
OnPlayerSAMPPJoin(playerid, bool:has_plugin);
OnPlayerClick(playerid, type, X, Y);
OnPlayerChangeRadioStation(playerid, stationid, vehicleid);
OnPlayerDrinkSprunk(playerid);
```

Compilation
---------

#### Windows:
  * Open the provided solution file (.sln) in Visual Studio.
  * Make sure to change the target to *"Release"* unless you want a build with debug symbols.

#### Linux:
  * Open a terminal and use the following commands:
```sh
cd Build
mkdir Temp
cd Temp
cmake ../..
make
```
  * Pass the *-DSAMPP_DEBUG=1* parameter to CMake for generating a build with debug symbols.
