![](https://i.imgur.com/v4i8JR6.png)
### Buttons execute actions when pressed. They can open guis (custom ones as well) or for example connect to a server, open a link or load a specific world.

## Properties:
* posX : x-coordinate of the button
* posY : y-coordinate of the button
* width : width of the button
* height : height of the button,
* imageWidth : width of the button in the image (default: height),
* imageHeight : height of the button in the image (default: width),
* texture : (optional) a resource location that will be used as a custom texture for this button. The image has to contain a normal and a hover version of the button. [This](https://imgur.com/jjyvjrd) is an example for a 200x20 button.
* text : the [Text](https://github.com/lumien231/Custom-Main-Menu/wiki/Text) that is displayed on the button (A language key or just normal text)
hoverText : the [Text](https://github.com/lumien231/Custom-Main-Menu/wiki/Text) that is displayed on the button when the user hovers over it  (A language key or just normal text)
* normalTextColor : (optional) a rgb color integer for the normal text color of the button
* hoverTextColor : (optional) a rgb color integer for the text color of the button when the mouse is above it
* pressSound : (optional) a resource location that points towards the sound this button makes when pressed
* hoverSound : (optional) a resource location that points towards the sound this button makes when hovered
* tooltip : (optional) The Tooltip [Text](https://github.com/lumien231/Custom-Main-Menu/wiki/Text) that will be displayed when the user hovers over this button. 
* action : (optional) what the button will do when its clicked, see [Actions](https://github.com/lumien231/Custom-Main-Menu/wiki/Actions) for more information.
* wrappedButton : (optional) The Button ID, see [Wrapped Buttons](https://github.com/lumien231/Custom-Main-Menu/wiki/Wrapped-buttons) for more information.
* alignment : (optional) see Alignment for information
* textOffsetX/Y (optional): The Button text will be offset by this amount.
* unit : (optional) the unit used for posX/posY/width/height of this button. Either "px" (default, absolute pixels) or "percent" (percentage of the screen size, where 0–100 means 0%–100%, decimals allowed).
* posXUnit / posYUnit / widthUnit / heightUnit : (optional) per-field unit override. When omitted, the field falls back to unit. Same value range as unit.

## Adaptive Sizing & Positioning

By default, `posX`, `posY`, `width`, and `height` are interpreted as absolute pixels. Setting `unit: "percent"` makes these values resolve relative to the current screen size, so a button's layout adapts automatically as the window or `guiScale` changes.

Resolution formulas:

* `posX` and `width`: `resolved = value / 100 * screenWidth`
* `posY` and `height`: `resolved = value / 100 * screenHeight`

### Interaction with alignment

Unit resolution always happens first. The resolved absolute-pixel `posX`/`posY` are then passed to the alignment anchor, which adds its own offset (`factorX * screenWidth` / `factorY * screenHeight`). The alignment behavior is unchanged — see [Alignments](https://github.com/lumien231/Custom-Main-Menu/wiki/Alignments) for details.

### Minimal example

A button centered on screen, 30% of the screen wide and 8% of the screen tall:

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

### Per-field unit override

You can mix units on a single button. For example, `"unit": "px", "widthUnit": "percent", "width": 30` keeps `posX`/`posY`/`height` in absolute pixels while making the width equal to 30% of the screen width. Any field without an explicit `*Unit` falls back to the value of `unit`.