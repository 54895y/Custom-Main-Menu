# Custom Main Menu Reload

![logo](https://i.imgur.com/MgNdWTc.png)

Custom Main Menu Reload is a fork of [lumien231/Custom-Main-Menu](https://github.com/lumien231/Custom-Main-Menu) that adds new features on top of the original mod. It supports **Minecraft 1.12.2**.

Custom Main Menu is a mod that allows you to edit the minecraft main menu using json files. It allows you to add or remove elements like buttons and labels and also adds some new stuff that you can add to your menu like slideshows or whole custom guis. However if you just wanna do simple things like adding or changing some text you don't even have to get into all of this, the mod comes with a json file that replicates the vanilla menu where you can easily change simple things like text.

## What's new in Reload (3.0.0)

### Button adaptive sizing & positioning (percent unit)

Buttons now support a `unit` field (`"px"` or `"percent"`) plus optional per-field overrides (`posXUnit`/`posYUnit`/`widthUnit`/`heightUnit`). When `unit` is `"percent"`, `posX`/`width` resolve relative to the screen width, and `posY`/`height` resolve relative to the screen height, so the layout adapts automatically as the window size or `guiScale` changes.

Example:

```json
"myButton": {
    "text": "menu.singleplayer",
    "posX": -15,
    "posY": 0,
    "width": 30,
    "height": 8,
    "unit": "percent",
    "alignment": "center",
    "action": { "type": "openGui", "gui": "singleplayer" }
}
```

See [Buttons](https://github.com/54895y/Custom-Main-Menu-Reload/wiki/Buttons#adaptive-sizing--positioning) for details.

### Bug fixes

- Fixed button positions/sizes using stale screen dimensions on first menu entry (buttons were aligned to the previous, e.g. fullscreen, size and not rebuilt).
- Fixed textured buttons rendering smaller than their click hitbox when `width`/`height` used `percent` unit.

## Getting started

1. Download `CustomMainMenuReload-MC1.12.2-3.0.0.jar` from the [Releases](https://github.com/54895y/Custom-Main-Menu-Reload/releases) page.
2. Drop the jar into your Minecraft `mods/` folder.
3. Launch Minecraft 1.12.2 with Forge.
4. The mod ships a default config that replicates the vanilla main menu; edit `config/custommainmenu/mainmenu.json` (or the per-GUI json) to customize.
