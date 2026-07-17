### Actions are executed when a user clicks on a button or a text. There are various ones that can simply open GUIs, connect to servers, or load a world.

## Properties: 
* type: The type of action, valid values are: openLink, openGui, quit, refresh, connectToServer, loadWorld, openFolder

#### The rest of the action properties are determined by the type of action:

openLink:
* link: The link that's supposed to open

openGui:
* gui: The GUI (interface) that's supposed to open. This can be a custom GUI (`custom.CUSTOM_GUI_NAME`), or a Vanilla one. The following GUIs are available in Vanilla:

  `mainmenu`, `mods`, `singleplayer`, `singleplayer.createworld`, `multiplayer`, `credits`, `languages`, `realms`, `options`, `options.ressourcepacks`, `options.skinsettings`,  `options.snooper`, `options.sounds`, `options.video`, `options.controls`, `options.multiplayer`


connectToServer:
* ip: The ip of the server to connect to
 

loadWorld:
* dirName: The name of the directory the save is saved in (in the saves folder).
* saveName: Not really necessary, might appear as the name of the save in certain dialogs while loading the world.
 

openFolder:
* folderName : Then name of the folder that should be opened. (Uses the .minecraft folder as the root folder)
 

quit and refresh do not require any additional properties.