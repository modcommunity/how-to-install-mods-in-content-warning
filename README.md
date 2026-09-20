A guide on how to **download** and **install mods** in [Content Warning](https://store.steampowered.com/app/2881650/Content_Warning/) on PC.

Content Warning is a Unity game, so its mods are [BepInEx](https://github.com/BepInEx/BepInEx) plugins and they all live on [Thunderstore](https://thunderstore.io/c/content-warning/). If you have modded Lethal Company before, everything here will feel familiar.

Because Content Warning is co-op first and almost nothing about it is worth doing alone, this guide leans hard on the part most guides skip: getting everybody in your lobby onto the same mod list. Our example is [Virality](https://thunderstore.io/c/content-warning/p/MaxWasUnavailable/Virality/), which raises the lobby player cap and adds late joining.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-content-warning/)

## Table Of Contents
* [Requirements](#requirements)
* [Before You Start](#before-you-start)
* [How Mods Load](#how-mods-load)
* [Choosing A Mod Manager](#choosing-a-mod-manager)
* [Installing With Gale](#installing-with-gale)
* [Installing With Thunderstore Mod Manager Or r2modman](#installing-with-thunderstore-mod-manager-or-r2modman)
* [Installing Manually](#installing-manually)
    * [Step 1 - BepInEx](#step-1---bepinex)
    * [Step 2 - The Mod](#step-2---the-mod)
* [Installing With The TMC App](#installing-with-the-tmc-app)
* [Getting Your Friends On The Same Mods](#getting-your-friends-on-the-same-mods)
* [Confirming It Worked](#confirming-it-worked)
* [Removing Mods](#removing-mods)
* [Common Problems](#common-problems)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
* A PC running **Windows 10** or later. Content Warning also runs on **Linux** through Proton, with one extra step covered below.
* **Content Warning** on Steam.
* A few hundred MB of free space.
* [7-Zip](https://www.7-zip.org/) or any other archive tool, if you are installing by hand.

## Before You Start
Two things worth doing before you touch anything.

**Make a note of where your game folder is.** Right-click **Content Warning** in your Steam library, then **Manage** followed by **Browse local files**. On a default install:

```
C:\Program Files (x86)\Steam\steamapps\common\Content Warning
```

**Know how to get back to vanilla.** Every file you add in this guide is a file you added, which means going back is a matter of deleting three things: the `BepInEx` folder, `doorstop_config.ini` and `winhttp.dll`. Steam's file verification will not clean these up for you because Steam has no idea they are there. Knowing that up front makes the rest of this a lot less nerve-wracking.

## How Mods Load
Content Warning does not load mods on its own. [BepInExPack](https://thunderstore.io/c/content-warning/p/BepInEx/BepInExPack/) sits in the game folder, hooks the game as it starts, and loads every plugin it finds in `BepInEx/plugins`.

So the order is always BepInEx first, mods second. A mod dropped into a game folder without BepInEx does nothing at all, with no error and no warning.

Some mods also depend on other mods. Virality only needs BepInEx itself. Something like [MoreColors](https://thunderstore.io/c/content-warning/p/ViViKo/MoreColors/) additionally needs [ContentSettings](https://thunderstore.io/c/content-warning/p/CommanderCat101/ContentSettings/), a shared settings library. Mod managers read those dependency lists and fetch everything for you, which is the main argument for using one.

## Choosing A Mod Manager
| Manager | Platforms | Why you might pick it |
| ------- | --------- | --------------------- |
| [Gale](https://thunderstore.io/c/content-warning/p/Kesomannen/GaleModManager/) | Windows, Linux | Small, fast, no Overwolf. Our default recommendation for this game. |
| [Thunderstore Mod Manager](https://www.overwolf.com/app/Thunderstore-Thunderstore_Mod_Manager) | Windows | Official and the one most mod pages link to. Requires Overwolf. |
| [r2modman](https://thunderstore.io/c/content-warning/p/ebkr/r2modman/) | Windows, Linux, macOS | The original, and still the option with the widest platform support. |

All three read and write the same profile format, so you and your friends do not all have to use the same one.

## Installing With Gale
1. Download Gale from [Thunderstore](https://thunderstore.io/c/content-warning/p/Kesomannen/GaleModManager/) or from [GitHub releases](https://github.com/Kesomannen/gale/releases).
2. Open it and select **Content Warning** from the game list.
3. Gale should find your Steam install automatically. If it does not, point it at the game folder manually.
4. Open the **Browse mods** tab and search for **Virality**.
5. Click **Install**. BepInExPack comes along as a dependency.
6. Click **Launch game (modded)**.

That is the whole process. The single most important part is step 6, because launching Content Warning from Steam starts it unmodded no matter what your manager has installed.

## Installing With Thunderstore Mod Manager Or r2modman
These two behave the same way as each other.

1. Install the manager and pick **Content Warning**.
2. Select or create a profile. A named profile per friend group is worth the ten seconds it takes.
3. Open **Get mods** (Thunderstore Mod Manager) or **Online** (r2modman).
4. Search for **Virality** and click **Download with dependencies**.
5. Click **Start modded**.

## Installing Manually
### Step 1 - BepInEx
1. Open the [BepInExPack page](https://thunderstore.io/c/content-warning/p/BepInEx/BepInExPack/) and click **Manual Download**.
2. Extract the zip somewhere outside your game folder.
3. Open the extracted folder, then open `BepInExPack` inside it.
4. Copy the **contents** of `BepInExPack` into your Content Warning folder, so that `BepInEx`, `doorstop_config.ini` and `winhttp.dll` end up next to `Content Warning.exe`.
5. Start the game once, then close it. This makes BepInEx create the folders it needs, including `BepInEx/plugins`.

**WARNING** - It is the contents of `BepInExPack` you copy, not the folder. Ending up with a path like `Content Warning\BepInExPack\BepInEx\` means nothing will load.

### Step 2 - The Mod
1. Open the [Virality page](https://thunderstore.io/c/content-warning/p/MaxWasUnavailable/Virality/) and click **Manual Download**.
2. Extract the zip.
3. Copy the `.dll` into `Content Warning\BepInEx\plugins`.

If the mod ships a folder with assets or a config alongside the `.dll`, copy the whole folder into `plugins` instead. BepInEx looks in subfolders, so both layouts work.

The other files in a Thunderstore zip (`manifest.json`, `icon.png`, `README.md`) are for the website and can be ignored.

**NOTE** - If you install by hand, dependencies are your job. Read the **Dependencies** section on the mod's Thunderstore page and install each one at the version listed, plus anything those depend on in turn.

## Installing With The TMC App
A fourth option, and ours: [the TMC App](https://moddingcommunity.com/tmc-app), a mod manager and server browser we build. It handles one-click installs and **sandboxes**, which are named mod profiles per game with their own load order and deployment method, switchable instantly without re-downloading.

**Content Warning is not in its supported games list yet.** Adding a game needs four JSON files and no code, so it is a small job and it is on the list.

That said, **the app is in very early development**, and we would rather tell you that here than have you find out the hard way. Its own README describes it as partially tested. Treat it as something to try alongside Gale rather than as a replacement, and if you do try it, please tell us what happened. That kind of feedback is the most useful thing anyone can give us right now.

It is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). [The issue tracker](https://github.com/modcommunity/tmc-app/issues) is open for bugs and requests, pull requests are welcome, and the repository documents how games are added if you want to contribute Content Warning support.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Getting Your Friends On The Same Mods
Content Warning's lobbies are peer to peer and most gameplay mods need to be installed by everyone, not just the host. Virality is a clear case: it raises the player cap, and somebody without it cannot join a lobby using the extra slots.

Rather than reading out a list of mod names, export a profile:

* **Gale**: **Profile**, then **Export**, which gives you a file or a shareable code.
* **Thunderstore Mod Manager / r2modman**: the profile menu, then **Export as code** or **Export as file**.

Whoever you send it to imports it and lands on an identical list, at identical versions. Versions are the part manual comparison always gets wrong.

**TIP** - Purely cosmetic mods are client-side and do not need to match. When a mod page does not say either way, assume everyone needs it.

## Confirming It Worked
BepInEx opens a console window next to the game. As the game boots, you should see it load the plugins one by one:

```
[Info   :   BepInEx] Loading [Virality 1.6.0]
```

No console at all means BepInEx itself is not loading, which is nearly always a wrong folder or a launch from Steam rather than the manager.

For Virality specifically, host a lobby and look at the player limit. Vanilla Content Warning caps at four.

## Removing Mods
Through a manager, uninstall the mod in the **Installed** list and it is gone. Disabling instead of uninstalling keeps the files around for later.

By hand, delete the `.dll` or folder from `BepInEx/plugins`.

To strip everything, delete `BepInEx`, `doorstop_config.ini` and `winhttp.dll` from the game folder, as mentioned earlier.

## Common Problems
**Nothing loaded and there is no console.** BepInEx is missing or in the wrong place, or you launched from Steam.

**One mod does not load and the rest do.** Check the console output. A missing dependency or a version mismatch is by far the most likely cause.

**The game crashes at startup after a game update.** Content Warning updates break BepInEx mods fairly often. Move your mods out of `plugins` to confirm, then wait for authors to update.

**Friends cannot join.** Mod lists differ. Export and import a profile.

**Linux.** Content Warning runs through Proton and BepInEx needs a DLL override to get loaded. Set the game's Steam launch options to `WINEDLLOVERRIDES="winhttp=n,b" %command%`. If you launch through Gale or r2modman, they set this up themselves.

## Conclusion
The short version: Gale, search for the mod, install, launch modded, then export the profile and send it to the people you play with. BepInEx comes along for the ride and you never have to think about it.

Manual installs are worth doing once so you know what the files look like, and worth avoiding after that for anything with a real dependency list.

If you want to help out with something, the [TMC App](https://github.com/modcommunity/tmc-app) is open source and early in development, and feedback on it would mean a lot.

## See Also
* [Content Warning on Thunderstore](https://thunderstore.io/c/content-warning/)
* [Content Warning Modding Discord](https://discord.gg/E9ustG9Drx)
* [Content Warning Wiki](https://contentwarning.wiki.gg/)
* [BepInEx documentation](https://docs.bepinex.dev/)
* [TMC App](https://github.com/modcommunity/tmc-app)

We keep this guide as current as we can, but the game and its mod loader both change over time. If an instruction here no longer matches what you are seeing, please tell us or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-content-warning/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or need a hand with anything modding related!
