## What are Alignments?

The alignment of an element specifies its relative location on the menu screen. Several alignment [presets](#preset-alignments) are defined for your convenience, although you can [create a custom alignment](#specifying-a-custom-alignment), if desired.

***

### Preset Alignments

The following alignments are available by default:
`"bottom_left", "bottom_right", "top_left", "top_right", "button", "center", "top_center", "left_center", "bottom_center", "right_center"`

***

### Interaction with percent units

When a button uses `unit: "percent"` (see [Buttons](https://github.com/lumien231/Custom-Main-Menu/wiki/Buttons#adaptive-sizing--positioning)), `posX`/`posY` are first resolved to absolute pixels against the screen size, and the alignment's `factorX * screenWidth` / `factorY * screenHeight` offset is then added on top. This resolution order is fixed, and the alignment's anchor behavior is not affected by the percent unit.

For example, `"unit": "percent", "posX": -25, "posY": 10, "alignment": "center"` places the button's anchor at `screenWidth*0.5 + (-25/100)*screenWidth` on the X axis and `screenHeight*0.5 + (10/100)*screenHeight` on the Y axis.

***

### Specifying a custom alignment

If none of the provided alignments are suitable, you can create a custom alignment as demonstrated in the example JSON below:

```json
{
    "images":
    {
        "title":
        {
            "image" : "custommainmenu:textures/gui/minecraft.png",
            "posX" : -137,
            "posY" : 30,
            "width" : 512,
            "height" : 512,
            "alignment" : "top_center"
        }
    },
   
    "buttons":
    {
        "singleplayer":
        {
            "text" : "menu.singleplayer",
            "posX" : -100,
            "posY" : 48,
            "width" : 200,
            "height" : 20,
            "action" :
            {
                "type" : "openGui",
                "gui" : "singleplayer"
            }
        },
       
        "multiplayer":
        {
            "text" : "menu.multiplayer",
            "posX" : -100,
            "posY" : 72,
            "width" : 200,
            "height" : 20,
            "action" :
            {
                "type" : "openGui",
                "gui" : "multiplayer"
            }
        },
       
        "mods":
        {
            "text" : "fml.menu.mods",
            "posX" : -100,
            "posY" : 96,
            "width" : 200,
            "height" : 20,
            "action" :
            {
                "type" : "openGui",
                "gui" : "mods"
            }
        },
           
        "options":
        {
            "text" : "menu.options",
            "posX" : -100,
            "posY" : 132,
            "width" : 98,
            "height" : 20,
            "action" :
            {
                "type" : "openGui",
                "gui" : "options"
            }
        },
       
        "quit":
        {
            "text" : "menu.quit",
            "posX" : 2,
            "posY" : 132,
            "width" : 98,
            "height" : 20,
            "action" :
            {
                "type" : "quit"
            }
        },
       
        "language":
        {
            "text" : "",
            "posX" : -124,
            "posY" : 132,
            "width" : 20,
            "height" : 20,
            "action" :
            {
                "type" : "openGui",
                "gui" : "languages"
            }
        },
       
        "refresh":
        {
            "text" : "",
            "posX" : -154,
            "posY" : 132,
            "width" : 20,
            "height" : 20,
            "texture" : "custommainmenu:textures/gui/buttons.png",
            "action" :
            {
                "type" : "refresh"
            }
        }
    },
   
    "texts":
    {
        "mojang":
        {
            "text" : "Copyright Mojang AB. Do not distribute!",
            "posX" : -197,
            "posY" : -10,
            "color" : -1,
            "alignment" : "c1"
        },
       
        "fml":
        {
            "text" : "",
            "posX" : 2,
            "posY" : -50,
            "color" : -1,
            "alignment" : "c2"
        }
    },
 
    "alignments":
    {
        "c1":
        {
            "factorWidth" : 0.5,
            "factorHeight" : 0.7
        },
 
        "c2":
        {
            "factorWidth" : 0.2,
            "factorHeight" : 0.2
        }
    },
   
    "other":
    {
        "splash-text":
        {
            "posX" : 90,
            "posY" : 70,
            "color" : -256,
            "alignment" : "top_center",
            "file" : "texts/splashes.txt"
        },
       
        "panorama":
        {
            "images" : "minecraft:textures/gui/title/background/panorama_%c.png",
            "animate" : true,
            "animationSpeed" : 1,
            "blur" : true,
            "gradient" : true
        }
    }
}
```