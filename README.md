# OC2 Cartographer

Custom kitchens for **Overcooked! 2** — build and play your own levels, authored as small JSON
files. No Unity, no game assets shipped, no other mods required.

> ⚠️ **Not ready to publish. Not authorized for distribution.**
>
> This is an **unfinished private test build**. You do **not** have consent to forward, share,
> re-upload, or post it to any platform (GitHub, Discord, Nexus Mods, GameBanana, Thunderstore,
> or anywhere else).
>
> - Nothing circulating came from me. I take **no responsibility for third-party or modified
>   copies**, or for anything they do to your game.
> - **Nobody is authorized** to distribute, promote, or speak for the project. Statements about
>   its scope, roadmap, or release timing aren't from me unless I post them myself.
> - This is built on top of the official game — **please support it.** The maps use official DLC
>   content; nothing here substitutes for buying Overcooked! 2, and nothing here should ever be
>   used to work around that. Full respect to Team17 and Ghost Town Games.
>
> 🍴 Glad people are excited — that's the best part of this.

## What it is

Cartographer adds its own **"Provisions & Co."** entry to the game's DLC menu. Pick it, choose a
custom kitchen, and play — solo or in co-op.

It's **self-contained** (a single DLL). At load it borrows a stock game scene as a base kitchen,
clears its layout, and rebuilds the kitchen from your level file — counters, dispensers, cookers,
sinks, the serving pass, recipes and all. Every object is materialized from the game's *own* asset
bundles by name, so a level is just a few kilobytes of JSON and no copyrighted content is ever
redistributed.

Levels are authored in a companion **web editor** (a grid-based kitchen designer) and shared
through an **invite-only registry** where friends sign in with Steam and pull maps into the game.

## Features

- **Custom kitchens from JSON** — stations, ingredients, and recipes placed on a grid.
- **Reference floorplans** — the editor snaps to each stock scene's real footprint so your
  layout fits the kitchen it loads into.
- **Recipe-driven design** — pick dishes and the editor derives the crates, prep, cookers, and
  serving stations you need, with live checks.
- **Co-op** — plays in multiplayer when every player has the mod and the same level.
- **Map Plaza ("Provisions & Co. Emporium")** — browse others' public maps and copy them into
  your own collection.
- **No asset duplication** — objects are discovered from the player's own game install.

## Install (players)

Distribution is **invitation only**. Full guide: **[INSTALL.md](INSTALL.md)**.

1. **Register** — open your invite link → read and accept the Terms → sign in with Steam. You
   land on the editor site, **[provisionsco.pages.dev](https://provisionsco.pages.dev/)**.
2. **Get your files** — on the site, click **Get mod** (`OC2Cartographer.dll`) and **Mod token**
   (`cartographer.token`).
3. **Install** — remove or disable any other BepInEx mods (in `BepInEx/plugins` and
   `BepInEx/scripts`) — should conflicts were later identified. Put **both** files into
   `Overcooked! 2/BepInEx/plugins/OC2Cartographer/`.
4. **First run** — start the game, go to the main menu (this sets up your account), then quit and
   restart. Your custom kitchens are now available.

Requires **BepInEx 5.4.21 (x86)**. Keep `cartographer.token` private — it's tied to your Steam
account and is traceable. This is a beta; use at your own discretion and risk.

## Build (developers)

Reference DLLs (game + BepInEx + Harmony) are bundled in [`lib/`](lib/), so it compiles with no
setup (targets `net35`):

```sh
dotnet build -c Release            # -> bin/Release/net35/OC2Cartographer.dll
dotnet build -c Install            # build + copy into <game>/BepInEx/plugins/OC2Cartographer/
dotnet build -c Install -p:OC2GameDir="D:\Games\Overcooked! 2"   # custom path
```

`Reload` deploys to `BepInEx/scripts/` for the ScriptEngine hot-reload plugin.

## Links

- **Cartographers' Portal** — https://provisionsco.pages.dev/
- **Cartographers' Cabin (Discord)** — https://discord.gg/ntxMtHwcn

## Credits & disclaimer

Authored by **tango_windsor**. This is an **unofficial fan project**, not affiliated with or
endorsed by Team17, Ghost Town Games, or Valve. You must own Overcooked! 2 to use it.
Contact: tango.windsor@outlook.com
