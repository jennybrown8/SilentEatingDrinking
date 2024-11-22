# Silent Eating and Drinking Mod for Ark: Survival Ascended

Silences player eating and drinking sounds and visual animations, especially for players 
with misophonia and similar sound sensitivities. Also changes drowning-suffocation 
sound and silences pooping and yawning during bed travel.

All players on the server are silenced. All consumables should be silenced (berries, meat, mushrooms, drinks, stews, mindwipes, iced canteens - 
everything that's edible). The buff is added at player spawn and should remain permanently unless the mod is uninstalled. You may still hear 
water containers being refilled if you use them within an irrigated area or lake, but the player drink sound is still silenced. This mod might 
result in changes to sounds that persist after the mod is uninstalled, since it modifies the sounds on the individual food items. Freshly 
generated food items should get their sounds back.

CurseForge mod project page will be more up to date than this readme: https://www.curseforge.com/ark-survival-ascended/mods/silent-eating-and-drink

Ark DevKit: https://store.epicgames.com/en-US/p/ark-devkit

## Dev Notes

Notes to myself next time I come back to this after a year and forget how to work on it, or tips for anyone who decides to fork/clone the repo and wants to work on it.

1. Run Epic Games Launcher, update the ark devkit install, or reinstall it if external drive failure happened.  Needs about 700 G for real.  This can take 3-4 days to download through the epic launcher due to complicated stupid network and DNS reasons even if you're on a good connection.
2. Restore the git repo from github to local; install location by default was `/e/DevKits/ARKDevkit/Projects/ShooterGame/Mods/SilentEatingDrinking`
3. Launch Unreal.  Wait forever (ok really about 20 minutes on first launch).
4. Open or reimport the project.  Check the UGC menu to checkbox activate the SilentEatingDrinking mod.
5. Double click the TestMapArea_SilentEatingDrinking to open the correct test level which activates the mod for Play in Editor (PIE).
6. Review the technical notes in the txt file in there, which explain how the blueprints and graphs fit together.
7. SaveGameActor_SilentEatingDrinking is the singleton that sets up event hooks and bootstraps the code.  It also modifies player-level sounds.
8. Buff_SilentEatingDrinking is the core business logic for silencing the food and drink items individually.
9. Remember to check both the graph view and the individual functions to review how it works.  Class Settings and Class Defaults are also important.
10. Some interesting class names from core Ark classes are: PrimalCharacter (all Ark dinos and players), ShooterCharacter (human players only), PDA_Voice_Collection with DA_Male_Legacy, DA_Male_A, etc. which are stored in ShooterCharacter.Player Voice Collection; and Character Status Component (status effect sounds).

To view the pathnames of currently playing sounds while playing the game, set `au.debug.sounds 1` from the Ark in-game console.

## Publishing

Once the mod is working and tested, Unreal's UGC menu has a "Share" option that automatically uploads to CurseForge provided you've linked your account login the way that it wants.  It's one click and even provides a convenience URL link directly to your CurseForge page.  Very easy.  Once the mod is on CurseForge, it takes about 20 minutes for it to "Cook" and reach "waiting for approval".  YOU are the one who approves it and publishes it, as the build is considered a private test build until you mark it Approved.  There's a complicated way to download a test mod to a private server for private testing, but I usually don't bother and just push the build public and test it "in production".  It can be rolled back if necessary.
