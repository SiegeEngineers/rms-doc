<div align="center">
<h1>UPDATED NEW RANDOM MAP SCRIPTING GUIDE<br>
(Age of Empires II: the Conquerors Expansion)</h1>
<h5>by Bultro</h5>

<p>
Updated for:<br>
Age of Empires II HD [HD] and all its DLC expansions and the UserPatch 1.4 [UP]<br>
by Zetnus<br>
<i>most recent revision 19 June 2019</i>
</p>
</div>


### 0.1. Versions of the Game

This guide was originally written for Age of Empires II: The Conquerors [AoC], which was released on CD in 1999.  The CD version of the game has received fan-made updates in the form of the UserPatch [UP]. This guide has been updated to cover functionality added by UserPatch 1.4. UserPatch 1.5 adds many additional features (such as direct placement and modifying object attributes), which are NOT yet covered in this guide. The Conquerors was re-released on Steam as the HD Edition in 2013, where it implemented almost all of the UP 1.4 features as well. It then received three official DLC expansions: The Forgotten, African Kingdoms, and Rise of the Rajas, which all provided additional civilizations and content in the form of terrains and objects. This guide has been updated to cover the HD Edition and its expansions.

### 0.2. Random Map Scripting

Random Map Scripts define new general types of map, such as the standard Arabia or Baltic. DON'T confuse a random map with a scenario: random maps look different at every game, and CAN'T be designed with the "Editor" button.
The standard RMS guide is in the `DOCS` subdirectory of the game if you have the CD version of the game, or in `docs\All` if you have the HD Edition on Steam. It's detailed, but is full of omissions and mistakes, so DON'T rely on things written there! 

Random maps must be plain text files with `.RMS` or `.rms` extension and names of no more than 20 characters. Longer names no longer cause crashes in the HD edition or the UserPatch. However, if it is too long, only the first part of the name will be visible in the ingame menus. You can edit them with any text editor, such as Notepad (or Notepad++) or Word, just remember to set plain text type in the "Save As" dialog. Getting community-made RMS syntax highlighting for your text editor will help you spot errors (see Links and Resources).

Scripts must be placed in the "Random" subdirectory of the game if you have the CD version. As of patch 4.0 in the HD Edition, the directory is now located at `resources\_common\random-map-scripts` instead.  For custom mods (such as Forgotten Empires or Wololo Kingdoms) running on the UserPatch, the subdirectory is `Games\modname\Script.Rm`.  Scrips are automatically transferred to other players in multiplayer, but if you have a newer version with exactly the same name, other players must manually delete the old one.

You should let people know if your map is suitable or not for single-player, because the game won't make distinctions.
Computer players usually can play well on custom maps, if they're not too tricky. Remember that computers:

- Need large building space
- Need easy access to all resources
- Can't ferry villagers
- Can't rescue neutral units

