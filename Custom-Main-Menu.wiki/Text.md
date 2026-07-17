### Generally all text that is visible on the gui (Labels, Buttons, Splash Text) can be defined using 3 different ways:
1. Loaded from a resource: 

`"splash-text": {
  "posX": 90,
  "posY": 70,
  "color": -256,
  "alignment": "top_center",
  "texts": "file:minecraft:texts/splashes.txt"
}`

Start the text with "file:" followed by the resource location of the file the text i supposed to be loaded from.

2. Loaded from a URL:

`"changelog": {
  "text": "web:http://pastebin.com/raw.php?i=MmSCr6zV",
  "posX": 2,
  "posY": 0,
  "color": -1,
  "alignment": "left_center"
}`

Start the text with "web:" followed by the URL the text is supposed to be loaded from.

3. Static text:

`"mojang": {
  "text": "Copyright Mojang AB. Do not distribute!",
  "posX": -197,
  "posY": -10,
  "color": -1,
  "alignment": "bottom_right"
}`

4. New Way
If you want to specify additional properties for the type of text you are using (like a refresh interval for web text)

`"label": {
  "text": {
    "type": "web",
    "url": "URL",
    "refreshInterval": 60
  },
  "posX": 0,
  "posY": 80,
  ...
}`

The refresh interval for text is in ticks and has to be >= 60 (3 Seconds).

### Placeholders
| placeholder | replacer | possible output |
|-------------|----------|---------|
| #date# | Local date | Dec 22, 2019 |
| #time# | Local time in HH:mm format | 14:09 |
| #mcversion# | Minecraft version | 1.12.2 |
| #fmlversion# | Forge Mod Loader version | 8.0.99.99 |
| #mcpversion# | Minecraft Coder Pack version | 9.42 |
| #modsloaded# | Number of loaded mods | 231 |
| #modsactive# | Number of active mods | 224 |
| #forgeversion# | Forge version | 14.23.5.2847 |
| #username# | Username | dimaxiton5 |

Placeholders can be used not only in "text" fields:
```
{
  ...
  "text": "web:https://example.com/logPlayer.php?playerName=#username#",
  "action": {
    "type": "openLink",
    "link": "https://example.com/viewProfile?username=#username#"
  }
}