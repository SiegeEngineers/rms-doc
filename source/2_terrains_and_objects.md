Here are the lists of available item types, including:

- Predefined constant name, if any (otherwise use `#const`). 
- Constant number N, to be used for name definitions: `#const  name  N`
- Comments, if needed

I reported only items that look good enough to be useful in a RMS. For a complete list of constants, including defective stuff, see Links and Resources.


## 2.1. Terrains

|Type	|Predefined Name	|N	|Comments	|
|-------|-----------------------|-------|---------------|
|Beach	|BEACH	|2	|Automatically placed around coasts. Ships can sail on! No buildings except walls|
|Beach, icy	|	|37	|Automatically placed around snowy coasts, acts like BEACH|
|Dirt	|DIRT	|6	|Includes some cactus objects|
|Dirt, foundation	|	|27	|Like DIRT2, but has no beaches, still dockable, created by buildings|
|Dirt, grass mix	|DIRT2	|11	||
|Dirt, greenish	|DIRT3	|3	||
|Dirt, snowy	|DIRT_SNOW	|33	|Has ice beaches|
|Dirt, snowy, foundation	|	|36	|Like DIRT_SNOW, but has no beaches, still dockable, created by buildings placed on snowy terrain|
|Desert	|DESERT	|14	||
|Farms, ploughed	|	|29	|Terrain only, not cultivable!|
|Farms, growing	|	|30	|Terrain only, not cultivable!|
|Farms, growing more	|	|31	|Terrain only, not cultivable!|
|Farms, planted	|	|7	|Terrain only, no food!|
|Farms, expired	|	|8	|Terrain only, not replantable!|
|Forest, Bamboo	|BAMBOO	|18	||
|Forest	|FOREST	|10	|20 is same, but game thinks it's different (e.g. as base_terrain)|
|Forest, Oak	|	|20	|Like FOREST, but is called "Oak forest" when you click on a tree|
|Forest, Jungle	|JUNGLE	|17	||
|Forest, Leaves	|LEAVES	|5	|Terrain left when temperate or tropical forest is chopped|
|Forest, Palm	|PALM_DESERT	|13	|Leaves behind DESERT when chopped|
|Forest, Pine	|PINE_FOREST	|19	||
|Forest, Snowy	|SNOW_FOREST	|21	|Leaves behind GRASS_SNOW when chopped, gets a special "leaves, snow" texture in the HD Edition|
|Grass	|GRASS	|0	|Default terrain|
|Grass, cliffs	|	|16	|Like GRASS; automatically placed under all cliffs|
|Grass, other	|	|41	|Like GRASS, but black on the minimap.  DO NOT USE – unit pathing is broken on this terrain|
|Grass, brighter	|GRASS2	|12	||
|Grass, brownish	|GRASS3	|9	||
|Grass, snowy	|GRASS_SNOW	|34	|Terrain left when snowy forest is chopped|
|Ice	|ICE	|35	|Ships cannot sail through this|
|Ice, other	|	|26	|Like ICE, ships can sail through this, acts like SHALLOW|
|Road	|ROAD	|24	|You can't place gold, stone, berries on any type of road|
|Road, dirty	|ROAD2	|25	||
|Road, grassy	|	|39	||
|Road, other	|	|40	|Like ROAD, no buildings, used in King of the Hill|
|Road, snowy	|	|38	||
|Shallow	|SHALLOW	|4	|Swampy water; walkable and navigable|
|Snow	|SNOW	|32	||
|Water, deep	|DEEP_WATER	|22	|Not dockable|
|Water, medium	|MED_WATER	|23	|Not dockable|
|Water, shallow	|WATER	|1	||
|Water, shallow, no beach	|	|15	|Like WATER, but has no beaches, not dockable|
|Water, shallow, walkable!	|	|28	|Like WATER, no beaches, walkable, no ships|

### 2.1.1. DLC Terrains
These terrains were added by The Forgotten, African Kingdoms, and Rise of the Rajas. For the most part, they will cause the map to CRASH if you attempt to load a map that contains them in any version of the game that does not have the required expansions.

|Type	|Predefined Name	|N	|Comments	|
|-------|-----------------------|-------|---------------|
|Rock	|DLC_ROCK	|40	|No buildings, King of the hill, also in the basegame but looks like ROAD there|
|Savannah	|DLC_SAVANNAH	|41	||
|Dirt 4	|DLC_DIRT4	|42	|Blend of DIRT and GRASS|
|Road, Desert	|DLC_DRYROAD	|43	||
|Grass, muddy	|DLC_MOORLAND	|44	||
|Desert, cracked	|DLC_CRACKED	|45	|Buildings take 25% more damage on this terrain|
|Quicksand	|DLC_QUICKSAND	|46	|No buildings; no natural resources|
|Black	|DLC_BLACK	|47	|No buildings, completely black|
|Dragon Tree Forest	|DLC_DRAGONFOREST	|48	|Leaves behind DIRT when chopped|
|Baobab Forest	|DLC_BAOBAFOREST	|49	|200 wood per tree, many gaps between trees, leaves behind DLC_DIRT4 when chopped|
|Acacia Forest	|DLC_ACACIAFOREST	|50	|Some gaps between trees, leaves behind DLC_SAVANNAH when chopped|
|Beach, white, grassy	|DLC_BEACH2	|51	|Acts like BEACH|
|Beach, grassy	|DLC_BEACH3	|52	|Acts like BEACH|
|Beach, white	|DLC_BEACH4	|53	|Acts like BEACH|
|Shallows, Mangrove	|DLC_MANGROVESHALLOW	|54	|Building possible, ships can sail|
|Mangrove Forest	|DLC_MANGROVEFOREST	|55	|Some gaps between trees, leaves behind DLC_MANGROVESHALLOW when chopped|
|Rainforest	|DLC_RAINFOREST	|56	|Leaves behind DLC_JUNGLELEAVES when chopped|
|Water, Deep Ocean	|DLC_WATER4	|57	|Not dockable|
|Water, Azure	|DLC_WATER5	|58	|Dockable|
|Shallows, Azure	|DLC_NEWSHALLOW	|59	|Acts like SHALLOW|
|Grass, Jungle	|DLC_JUNGLEGRASS	|60	||
|Road, Jungle	|DLC_JUNGLEROAD	|61	||
|Leaves, Jungle	|DLC_JUNGLELEAVES	|62	||
|Rice Farm 	|	|63	|no food; building possible; navigable; not dockable|
|Rice Farm, Dead 	|	|64	|no food; building possible; navigable; not dockable|
|Rice Farm, 0%	|	|65	|no food; building possible; navigable; not dockable|
|Rice Farm, 33%	|	|66	|no food; building possible; navigable; not dockable|
|Rice Farm, 66%	|	|67	|no food; building possible; navigable; not dockable|

The HD Edition DLC also adds a bunch of so-called "moddable terrains" (70-99), which look exactly like the existing terrains, but could be used if you wanted to modify terrains and make a map using those modded terrains. For example, you could make a terrain mod that turns a moddable water into the appearance of lava and then make an RMS that specifically uses this terrain.
Warning! [Wololo Kingdoms](https://github.com/AoE2CommunityGitHub/WololoKingdoms) changes some of the constant numbers. Check their documentation for how to handle this. Predefined names are automatically transitioned, but when using `#const`, you must manually deal with this.


## 2.2. Player Objects

These units and buildings can be controlled by a player. With `set_gaia_object_only`, they become rescuable.
CAPITAL names are valid predefined labels; other names are only descriptive (use `#const` for such objects).

### 2.2.1. Barracks Units

|Unit|ID|
|---|---|
|CHAMPION	|567|
|EAGLE_WARRIOR	|751|
|ELITE_EAGLE_WARRIOR	|752|
|HALBERDIER	|359|
|LONG_SWORDSMAN	|77|
|MAN_AT_ARMS	|75|
|MILITIA	|74|
|PIKEMAN	|358|
|SPEARMAN	|93|
|TWO_HANDED_SWORDSMAN	|473|


### 2.2.2. Archery Range Units

|Unit|ID|
|---|---|
|ARBALEST	|492|
|ARCHER	|4|
|CAVALRY_ARCHER	|39|
|CROSSBOWMAN	|24|
|ELITE_SKIRMISHER	|6|
|HAND_CANNONEER	|5|
|HEAVY_CAVALRY_ARCHER	|474|
|SKIRMISHER	|7|

### 2.2.3. Stable Units

|Unit|ID||
|---|---|---|
|CAMEL	|329	||
|CAVALIER	|283	||
|HEAVY_CAMEL	|330	||
|HUSSAR	|441	||
|KNIGHT	|38	||
|LIGHT_CAVALRY	|546	||
|PALADIN	|569	||
|SCOUT, SCOUT_CAVALRY	|448	|Automatically places Eagle Warriors for Aztecs and Mayas.  I couldn't find a way to place cavalry Scouts for Aztecs and Mayas!|

### 2.2.4. Siege Engines

|Unit|ID|
|---|---|
|BATTERING_RAM	|35|
|BOMBARD_CANNON	|36|
|CAPPED_RAM	|422|
|HEAVY_SCORPION	|542|
|MANGONEL	|280|
|ONAGER	|550|
|SCORPION	|279|
|SIEGE_ONAGER	|588|
|SIEGE_RAM	|548|
|TREBUCHET (unpacked)	|42|
|TREBUCHET_PACKED	|331|

### 2.2.5. Ships

|Unit|ID|
|---|---|
|CANNON_GALLEON	|420|
|DEMOLITION_SHIP	|527|
|ELITE_CANNON_GALLEON	|691|
|FAST_FIRE_SHIP	|532|
|FIRE_SHIP	|529|
|FISHING_SHIP	|13|
|GALLEY	|539|
|GALLEON	|442|
|HEAVY_DEMOLITION_SHIP	|528|
|TRADE_COG	|17|
|TRANSPORT_SHIP	|545|
|WAR_GALLEY	|21|

### 2.2.6. Reserved Units

|Unit|ID|
|---|---|
|BERSERK	|692|
|CATAPHRACT	|40|
|CHU_KO_NU	|73|
|CONQUISTADOR	|771|
|HUSKARL	|41|
|JAGUAR_WARRIOR	|725|
|JANISSARY	|46|
|LONGBOAT	|250|
|LONGBOWMAN	|8|
|MAMELUKE	|282|
|MANGUDAI	|11|
|MISSIONARY	|775|
|PLUMED_ARCHER	|763|
|SAMURAI	|291|
|TARKAN	|755|
|TEUTONIC_KNIGHT	|25|
|THROWING_AXEMAN	|281|
|TURTLE_SHIP	|831|
|WAR_ELEPHANT	|239|
|WAR_WAGON	|827|
|WOAD_RAIDER	|232|
|ELITE_BERSERK	|694|
|ELITE_CATAPHRACT	|553|
|ELITE_CHU_KO_NU	|559|
|ELITE_CONQUISTADOR	|773|
|ELITE_HUSKARL	|555|
|ELITE_JAGUAR_WARRIOR	|726|
|ELITE_JANISSARY	|557|
|ELITE_LONGBOAT	|533|
|ELITE_LONGBOWMAN	|530|
|ELITE_MAMELUKE	|556|
|ELITE_MANGUDAI	|561|
|ELITE_PLUMED_ARCHER	|765|
|ELITE_SAMURAI	|560|
|ELITE_TARKAN	|757|
|ELITE_TEUTONIC_KNIGHT	|554|
|ELITE_THROWING_AXEMAN	|531|
|ELITE_TURTLE_SHIP	|832|
|ELITE_WAR_ELEPHANT	|558|
|ELITE_WAR_WAGON	|829|
|ELITE_WOAD_RAIDER	|534|

### 2.2.7. Other standard units

|Unit|ID||
|---|---|---|
|KING	|434	|Must be manually placed for regicide (use: `if REGICIDE...`)|
|MONK	|125	||
|PETARD	|440	||
|SHEEP	|594	|Can belong to a player at start|
|TRADE_CART	|128	||
|Trade cart, packed	|204	|Appears as packed, but it's not carrying gold|
|TURKEY	|833	|Can belong to a player at start|
|VILLAGER	|	|Randomly places man or woman. If you don't set `number_of_objects`, the game will automatically place 3 villagers (or 6 for Chinese, 4 for Mayas)|
|Villager	|293 woman, 83 man	||
|Villager, builder	|212 woman, 118 man	||
|Villager, farmer	|214 woman, 259 man	||
|Villager, fisher	|57 woman, 56 man	||
|Villager, gatherer	|354 woman, 120 man	||
|Villager, miner	|581 woman, 579 man	||
|Villager, hunter	|216 woman, 122 man	||
|Villager, chopper	|218 woman, 123 man	||
|Villager, sheperd	|590 woman, 592 man|

### 2.2.8. Heroes

|Unit|ID|Type|
|---|---|---|
|ADMIRAL_YI_SUN_SHIN	|844	|Turtle ship|
|AETHELFIRTH	|169	|Woad raider|
|Alexander Nevski	|197	|Cavalier. Predefined name is WILLIAM_THE_CONQUEROR2|
|ARCHBISHOP	|177	|Monk. Turns to a normal monk when he picks up a relic|
|ARCHERS_OF_THE_EYES	|686	|Arbalest, not so tough|
|ATTILA_THE_HUN	|777	|Cataphract|
|BAD_NEIGHBOR	|682	|Trebuchet, unpacked|
|BAD_NEIGHBOR_PACKED	|730	|Trebuchet, packed|
|BELISARIUS	|167	|Cataphract|
|CHARLEMAGNE	|165	|Throwing axeman|
|CHARLES_MARTEL	|424	|Throwing axeman|
|CONSTABLE_RICHEMONT	|646	|Knight with lance|
|DUKE_D_ALENCON	|638	|Knight with lance|
|EL_CID	|198	|Champion|
|EL_CID_CAMPEADOR	|824	|Knight with lance|
|EMPEROR_IN_A_BARREL	|733	|Trade cart. Appears as packed, but it's not carrying gold|
|ERIK_THE_RED	|171	|Berserk|
|FRANKISH_PALADIN	|632	|Knight with lance|
|FRIAR_TUCK	|163	|Monk. Turns to a normal monk when he picks up a relic|
|GAWAIN	|175	|Cavalier|
|GENGHIS_KHAN	|731	|Mangudai, very tough|
|GODS_OWN_SLING	|683	|Trebuchet, unpacked|
|GODS_OWN_SLING_PACKED	|729	|Trebuchet, packed|
|GUY_JOSSELYNE	|648	|Paladin|
|HENRY_V	|847	|Paladin|
|HROLF_THE_GANGER	|428	|Berserk|
|HUNTING_WOLF	|700	|Wolf. Only hero wolves can be controlled by players|
|IMAM	|842	|Monk. Turns to a normal monk when he picks up a relic|
|JEAN_BUREAU	|650	|Bombard cannon, not so tough|
|JEAN_DE_LORRAIN	|644	|Bombard cannon|
|JOAN_OF_ARC	|629	|Knight, woman (different graphics!)|
|JOAN_THE_MAID	|430	|Poor woman, not so tough|
|KING_ALFONSO	|840	|King. Hero kings don't work for regicide!|
|KING_ARTHUR	|173	|King. Hero kings don't work for regicide!|
|KING_SANCHO	|838	|King. Hero kings don't work for regicide!|
|KITABATAKE	|195	|Samurai|
|KUSHLUK	|702	|Cavalier|
|LA_HIRE	|640	|Champion|
|LANCELOT	|174	|Paladin|
|LORD_DE_GRAVILLE	|642	|Arbalest, not so tough|
|MASTER_OF_THE_TEMPLAR	|680	|Knight with lance|
|MINAMOTO	|196	|Samurai|
|MORDRED	|176	|Paladin|
|NOBUNAGA	|845	|Samurai|
|ORNLU_THE_WOLF	|707	|Wolf, very tough, towers can't target him|
|POPE_LEO_I	|781	|Monk. Turns to a normal monk when he picks up a relic|
|REYNALD_DE_CHATILLON	|678	|Knight with lance|
|RICHARD_THE_LIONHARTED	|160	|Paladin|
|ROBIN_HOOD	|200	|Longbowman|
|ROLAND	|166	|Knight|
|SCYTHIAN_SCOUT	|852	|Light cavalry, not so tough|
|SCYTHIAN_WILD_WOMAN	|783	|Poor woman (same as Joan the Maid), not so tough|
|SHAH	|704	|King. Hero kings don't work for regicide!|
|SHERIFF_OF_NOTTINGHAM	|164	|Man at arms, not so tough|
|SIEGFRIED	|170	|Champion|
|SIEUR_BERTRAND	|636	|Knight|
|SIEUR_DE_METZ	|634	|Knight|
|SIR_JOHN_FASTOLF	|652	|Knight with lance|
|SUBOTAI	|698	|Heavy cavalry archer|
|TAMERLANE	|172	|Mangudai|
|THE_BLACK_PRINCE	|161	|Cavalier|
|THEODORIC_THE_GOTH	|168	|Huskarl|
|WILLIAM_THE_CONQUEROR	|849	|Knight with lance|
|WILLIAM_WALLACE	|432	|Champion|

### 2.2.9. Other Units

|Unit|ID||
|---|---|---|
|Advanced heavy crossbowman	|493	|New ranged unit, with unique graphics!|
|Alternative Berserk 	|94	|New melee unit, with unique graphics!|
|Cobra Car	|748	|The one of the cheat|
|Converter Galley	|536	|A galley that converts enemies like a monk!|
|ES_FLAG	|851	|Ensemble Studios flag|
|FLAG_A	|600	|Tall flag|
|FLAG_B	|601	|Bifurcate flag|
|FLAG_C	|602	|Spotted flag|
|FLAG_D	|603	|Crossed flag|
|FLAG_E	|604	|Binged flag|
|	|	|All flags can be placed by default on water, and also on some other objects. If placed with set_gaia_object_only, they're not rescuable, only eye-candy. |
|Furious the monkey boy	|860	|The one of the cheat. VERY powerful! If gaia, attacks as a wolf|
|HORSE	|814	|Can explore, but short sight|
|Infiltrator	|299	|Looks exactly as a Militia, but he's stronger|
|Junk	|15	|New ship, with unique graphics! Can explore. Turns invisible when it attacks; auto responds if attacked.|
|MAP_REVEALER	|837	|Invisible and immobile; gives sight of 4 tiles radius area|
|SABOTEUR	|706	|The one of the cheat. Stronger than Petard|
|Shipwreck	|436	|Can't move unless in group. A nice eye-candy, but counts as 4 population!|
|Super armored Archer	|571	|Armor 1000, but attack only 1|
|Super armored Cavalry Archer	|577	|Armor 1000, but attack only 1|
|Super armored Light Cavalry	|575	|Armor 1000, but attack only 1|
|Super armored Militia	|573	|Armor 1000, but attack only 1|
|TORCH	|499	|Can be placed even on water and forests. Not rescuable if gaia|
|TORCH_CONVERTING	|854	|As TORCH, but joins human players that come by (like sheep)|


### 2.2.10. Standard Buildings

|Building|ID|
|---|---|
|ARCHERY_RANGE	|87|
|BARRACKS	|12|
|BLACKSMITH	|103|
|BOMBARD_TOWER	|236|
|CASTLE	|82|
|DOCK 	|45|
|FARM	|50|
|FISH_TRAP	|199|
|FORTIFIED_WALL	|155|
|GUARD_TOWER	|234|
|HOUSE	|70|
|KEEP	|235|
|LUMBER_CAMP	|562|
|MARKET	|84|
|MILL 	|68|
|MINING_CAMP	|584|
|MONASTERY	|104|
|OUTPOST	|598|
|PALISADE_WALL	|72|
|SIEGE_WORKSHOP	|49|
|STABLE	|86|
|TOWN_CENTER	|109|
|UNIVERSITY	|209|
|WALL, STONE_WALL	|117|
|WATCH_TOWER	|79|
|WONDER	|276|


### 2.2.11. Note on Walls

Standard walls (palisade, stone or fortified) are automatically placed in rings around player lands, including four gates (one per side), whenever you use `set_place_for_every_player`. If you use palisade walls, the stone gates will be placed in the original AoC, but HD will place palisade gates instead.
E.g. this command would create square walls with 15 tiles radius:

```rms
create_object WALL
{
set_place_for_every_player
min_distance_to_players 15
max_distance_to_players 15
}
```

- number_of_objects is ignored, so don't even type it
- `min_distance` and `max_distance` must be specified, or you get bad results
- If `max_distance` is greater than `min_distance`, you get a non-square ring, with varying radius
- You can't place more than one wall ring per player. Any further walls after the first one will end up on top of the original ring, regardless of the min and max distance specified.
- You can't place single pieces of wall (not rings) for players, and you can't place rings for gaia
- You must place the wall AFTER placing a town center for every player. If you place it before a TC is placed, or if no TCs are placed, the wall will form a ring around the center of the map instead
- Walls are not placed if the players are completely separated from each other by water
- Walls are not placed on lands created with `assign_to_player`


### 2.2.12. Other Buildings

Most of these buildings do nothing and are eye-candy only. "Not working" buildings generally can't train units, research, receive resources or fire arrows; they only have sight and potentially population support.

|Building|ID||
|---|---|---|
|Archery range, not working	|10	|Castle age style|
|Barracks, not working	|498	|Feudal age style|
|Barracks, not working	|20	|Castle age style|
|Blacksmith, not working	|105	|Feudal age style|
|Blacksmith, not working	|18	|Castle age style|
|Bridge A, bottom	|607	||
|Bridge A, mid	|606	||
|Bridge A, mid, mid broken	|738	||
|Bridge A, mid, top broken	|739	||
|Bridge A, mid, bottom broken	|740	||
|Bridge A, top	|605	||
|Bridge B, bottom	|610	||
|Bridge B, mid	|609	||
|Bridge B, mid, mid broken	|741	||
|Bridge B, mid, top broken	|742	||
|Bridge B, mid, bottom broken	|743	||
|Bridge B, top	|608	||
| | |Bridge A goes SW to NE. Bridge B goes NW to SE. They can't be attacked. They aren't rescuable if gaia. Middle parts always have some water underneath.|
|Castle, not working	|33	|Does nothing, but can garrison 75 units! (they don't shoot)|
|CATHEDRAL	|599	|Does nothing. Looks like British wonder, but bigger|
|Dock, not working	|133	|Feudal age style|
|Dock, not working	|47	|Castle age style|
|DOME_OF_THE_ROCK	|690	|Does nothing. Great mid-east temple|
|Fortified Gate	|/ 63,<br> \ 85,<br> — 660,<br> \| 668| Only central part actually looks like a fortified gate	|
|Fortified wall, corner	|80	|Has a fortified gate's HP and icon, but it's just a junction piece of wall.  It's placed as a normal object, not in rings as FORTIFIED_WALL|
|Gate	|/ 64,<br> \ 88,<br> — 659,<br> \| 667	||
|GREAT_PYRAMID	|696	|Does nothing.|
|House, feudal age	|463	|Works!|
|House, castle age	|464	|Works!|
|Lumber camp, not working	|563	||
|Market, not working	|116	|Castle age style|
|Market, not working	|137	|Imperial age style|
|Mill, not working	|129	|Feudal age style|
|Mill, not working	|130	|Castle age style|
|Mining camp, not working	|585	||
|Monastery, not working	|30	||
|MONUMENT	|826	|Same as a wonder, but doesn't let you win|
|MOSQUE	|655	|Does nothing. Looks exactly as the Turkish wonder|
|PAVILION	|624	|Big tent. Works as a house, but only 500 HP|
|PAVILION2	|626	|Small tent. Works as a house, but only 500 HP|
|PAVILION3	|625	|Small tent. Works as a house, but only 500 HP|
|Port, not working	|446	|A castle age style dock. Has special graphics for east-European and American civs. Slightly different for others|
|PYRAMID	|689	|Does nothing.|
|Sea Gate (Palisade Gate in HD DLC) (open)	|/ 790,<br> \ 794,<br>  — 798,<br>  \| 802	|A wooden gate on water! Friendly ships can pass thru. Palisade gate can be placed on land in AoF |
|Sea Gate (Palisade Gate in HD DLC) (closed)	|/ 789,<br> \ 793,<br> — 797,<br> \| 801	|A wooden gate on water! Friendly ships can pass thru. Palisade gate can be placed on land in AoF |
|Sea Tower	|785	|New water building! Graphics aren't perfect but can shoot arrows. Graphics fixed in the HD Edition|
|Sea Wall (part of palisade gate in HD DLC)	|791	|A wooden wall on water! But it's not automatically placed in rings. Part of the Palisade gate graphics in HD DLC|
|Siege workshop, not working	|150	||
|Stable, not working	|101	|Castle age style|
|THE_ACCURSED_TOWER	|684	|Powerful guard tower, similar to west-European ones. Great range|
|THE_TOWER_OF_FLIES	|685	|Powerful guard tower, similar to west-European ones.|
|Town center, not working	|71	|Can garrison, fire arrows, and support pop. Graphics aren't perfect.|
|TRADE_WORKSHOP	|110	|Does nothing. Has west-European and far-east versions|
|University, not working	|210	|Imperial age style|
|Wall, corner	|81	|Has a gate's HP and icon, but it's just a junction piece of wall.  It's placed as a normal object, not in rings as WALL|
|YURT	|712	|Big, wooden hut. Works as a house, but only 500 HP|
|YURT2	|713	|Small, wooden hut. Works as a house, but only 500 HP|
|YURT3	|714	|Small, wooden hut. Works as a house, but only 500 HP|
|YURT4	|715	|Small, wooden hut. Works as a house, but only 500 HP|
|YURT5	|716	|Small, leather hut. Works as a house, but only 500 HP|
|YURT6	|717	|Small, leather hut. Works as a house, but only 500 HP|
|YURT7	|718	|Small, leather hut. Works as a house, but only 500 HP|
|YURT8	|719	|Big, leather hut. Works as a house, but only 500 HP|


## 2.3. Gaia Objects

These objects can never belong to a player. `set_gaia_object_only` is required if `set_place_for_every_player` is used.
Again, capital letters names are predefined labels, while lower case names are just descriptive (you must use `#const`).
"Varies" means that the same type of object can actually have two or more different aspects (like the villagers, that can randomly be men or women), making a better eye-candy.


### 2.3.1. Animals

|Unit|ID||
|-----------------------------|-----|-----------------------------------------------------------------------------------------|
| BOAR                        | 48  |                                                                                         |
| DEER                        | 65  |                                                                                         |
| Deer, not huntable          | 333 |                                                                                         |
| DIRE_WOLF                   | 89  | A wolf with 100 HP, but low attack. Not so dire, but AIs have trouble with these wolves |
| DORADO, FISH_DORADO         | 455 |                                                                                         |
| FISH                        | 53  | Called Perch, 200 food like shore fish (normal fish have more)                          |
| HAWK                        | 96  |                                                                                         |
| IRON_BOAR                   | 810 | Very strong, attacks villagers at sight, can't be hunted.  Will cause AIs trouble       |
| JAGUAR                      | 812 |                                                                                         |
| JAVELINA                    | 822 | Just a boar with different name, isn't it? :)                                           |
| MACAW                       | 816 | Tropical bird, wandering like a hawk                                                    |
| MARLIN1, GREAT_FISH_MARLIN  | 450 |                                                                                         |
| MARLIN2, GREAT_FISH_MARLIN2 | 451 |                                                                                         |
| RABID_WOLF                  | 202 | Slightly stronger. Sees and pursues villagers from far away.                            |
| SALMON, FISH_SALMON         | 456 |                                                                                         |
| SNAPPER, FISH_SNAPPER       | 458 |                                                                                         |
| SHEEP                       | 594 | Can also be placed as a player object                                                   |
| SHORE_FISH                  | 69  |                                                                                         |
| TUNA, FISH_TUNA             | 457 |                                                                                         |
| TURKEY                      | 833 | Can also be placed as a player object                                                   |
| WILD_HORSE                  | 835 | Wanders like a deer. Use HORSE for a player-controlled horse                            |
| WOLF                        | 126 |                                                                                         |


### 2.3.2. Trees

Unlike forest terrains, tree objects aren't visible on mini-map. Normal trees have 100 wood each. The scenario editor trees (399-410) have 125 wood and cannot be cut down with siege onagers.  AIs sometimes may not recognize them as a wood source for the purpose of choosing initial lumber camp sites.

|Unit|ID||
|---------------------------------------|-----|---------------------------------------------|
| BAMBOO_TREE, BAMBOO_FOREST_TREE       | 348 | Varies. Same created by BAMBOO terrain      |
| JUNGLETREE, JUNGLE_TREE               | 414 | Varies. Same created by JUNGLE terrain      |
| OAKTREE, FOREST_TREE, OAK_FOREST_TREE | 349 | Varies. Same created by FOREST terrain      |
| PALMTREE, PALM_FOREST_TREE            | 351 | Varies. Same created by PALM_DESERT terrain |
| PINETREE, PINE_FOREST_TREE            | 350 | Varies. Same created by PINE_FOREST terrain |
| SNOWPINETREE, SNOW_PINE_TREE          | 413 | Varies. Same created by SNOW_FOREST terrain |
| TREE_A, TREE1, TREE_TD                | 399 | Oak forest                                  |
| TREE_B, TREE2                         | 400 | Oak forest                                  |
| TREE_C, TREE3                         | 401 | Oak forest                                  |
| TREE_D, TREE4                         | 402 | Oak forest                                  |
| TREE_E, TREE5                         | 403 | Oak forest                                  |
| TREE_F                                | 404 | Dry, no leaves                              |
| TREE_G                                | 405 | Brown leaves                                |
| TREE_H                                | 406 | Oak forest                                  |
| TREE_I                                | 407 | Dry, no leaves                              |
| TREE_J                                | 408 | Oak forest                                  |
| TREE_K                                | 409 | Oak forest                                  |
| TREE_L                                | 410 | Oak forest                                  |


### 2.3.3. Other 


|Unit|ID||
|-------------------------------|-----|----------------------------------------------------------------------------------------------------|
| Arrow                         | 315 | Lying on ground. Can be on water. Varies                                                           |
| Arrows                        | 54  | Lying on ground. Can be on water. Varies                                                           |
| BROKEN_CART                   | 858 |                                                                                                    |
| CACTUS                        | 709 | Varies                                                                                             |
| Car!                          | 749 | The one of the cheat, but eye-candy only                                                           |
| Cliff, alternative            | 273 | A small cliff, with new rock color                                                                 |
| CRACKS                        | 241 |                                                                                                    |
| CRATER                        | 723 | Quite small                                                                                        |
| EXPIRED_FISHTRAP              | 278 | Can be on land. Disappears quickly                                                                 |
| FLOWER_BED                    | 859 |                                                                                                    |
| FLOWERS_1                     | 334 | Can overlap water and other stuff                                                                  |
| FLOWERS_2                     | 335 | Can overlap water and other stuff                                                                  |
| FLOWERS_3                     | 336 | Can overlap water and other stuff                                                                  |
| FLOWERS_4                     | 337 | Can overlap water and other stuff                                                                  |
| FORAGE, FORAGE_BUSH           | 59  | Varies                                                                                             |
| GOLD                          | 66  | Varies                                                                                             |
| GRAVE                         | 820 | Varies                                                                                             |
| HAY_STACK                     | 857 |                                                                                                    |
| HEAD                          | 821 | Pole with human head                                                                               |
| MOUNTAIN_1, MOUNTAIN1         | 310 | Can't walk on. Grassy                                                                              |
| MOUNTAIN_2, MOUNTAIN2         | 311 | Can't walk on. Grassy                                                                              |
| MOUNTAIN_3                    | 744 | Can't walk on. Rocky                                                                               |
| MOUNTAIN_4                    | 745 | Can't walk on. Rocky                                                                               |
| NINE_BANDS                    | 720 | Pole with horn decorations                                                                         |
| OLD_STONE_HEAD                | 855 | Pre-Columbian sculpture. Varies                                                                    |
| Outlaw                        | 158 | Neutral archer. Attacks everyone he sees! Cool but only 15 HP                                      |
| PATH_1                        | 339 | Muddy trail. Can overlap water and other stuff                                                     |
| PATH_2                        | 340 | Muddy trail. Can overlap water and other stuff                                                     |
| PATH_3                        | 341 | Muddy trail. Can overlap water and other stuff                                                     |
| PATH_4                        | 338 | Two muddy trails crossing. Can overlap water and other stuff                                       |
| PIECE_OF_THE_TRUE_CROSS       | 688 | Black relic. Disappears when picked up...                                                          |
| PLANT, PLANTS                 | 818 | Small grass. Can be on water! Varies                                                               |
| RELIC                         | 285 |                                                                                                    |
| Relic, with civilization name | 287 British,<br>288 Byzantine,<br>289 Chinese,<br>290 Frankish,<br>292 Gothic,<br>294 Japanese,<br>295 Persian,<br> 296 Saracen,<br>297 Teutonic,<br>298 Turkish | Only name is different from a normal relic. They become normal relics when brought to a monastery. |
| ROCK                          | 623 | Can be on water, but looks good only on land. Varies.                                              |
| ROMAN_RUINS                   | 856 | Can be on water! Varies.                                                                           |
| RUBBLE_1_X_1                  | 863 | Like destroyed buildings, 1x1 tiles. Can be on water!                                              |
| Rubble 1x1, temporary         | 143 | Can be on water! Disappears quickly                                                                |
| RUBBLE_2_X_2                  | 864 | Can be on water!                                                                                   |
| Rubble 2x2, temporary         | 144 | Can be on water! Disappears quickly                                                                |
| Rubble 2x2, different         | 147 | Can be on water! Disappears quickly                                                                |
| RUBBLE_3_X_3                  | 865 | Can be on water!                                                                                   |
| Rubble 3x3, temporary         | 145 | Can be on water! Disappears quickly                                                                |
| Rubble 4x4, temporary         | 146 | Can be on water! Disappears quickly                                                                |
| Rubble 5x5, temporary         | 148 | Can be on water! Disappears quickly                                                                |
| RUGS                          | 711 | Can be on water! Varies                                                                            |
| RUINS                         | 345 | Quite big                                                                                          |
| SEA_ROCKS_1                   | 389 |                                                                                                    |
| SEA_ROCKS_2                   | 396 |                                                                                                    |
| SHIPWRECK                     | 721 |                                                                                                    |
| SHIPWRECK2                    | 722 |                                                                                                    |
| SIGN                          | 819 | Wooden road signal. Can be on water!                                                               |
| SKELETON                      | 710 | Varies                                                                                             |
| Small white stone             | 417 |                                                                                                    |
| STATUE                        | 817 | The one of European universities. Can be on water!                                                 |
| Stormy Dog                    | 862 | Flying dog! The one of the cheat... wanders like a hawk                                            |
| STONE                         | 102 | Varies                                                                                             |
| STUMP                         | 809 | What remains of a cut tree. Varies                                                                 |
| Stump, temporary              | 415 | Disappears after some time. Varies                                                                 |
| Stumps of bamboo              | 737 | Disappears after some time                                                                         |
| Trireme                       | 61  | Eye-candy only. Disappears after some time. Can be on land. Varies (rotates)                       |


### 2.3.4. Dead Units

These units, except for wild animals, can also be placed as player objects (with `set_place_for_every_player` and without `set_gaia_object_only`); of course they're not controllable, and only get owner's color.
All dead units decay and disappear after some time. They can be placed on water.

|Unit|ID|
|----------------------------------|-----|
| Dead Adv. Hv. Crossbowman        | 497 |
| Dead Arbalest                    | 687 |
| Dead Archer                      | 3   |
| Dead Battering Ram               | 23  |
| Dead Berserk                     | 693 |
| Dead Boar (no food)              | 356 |
| Dead Bombard Cannon              | 16  |
| Dead Camel                       | 494 |
| Dead Capped Ram                  | 423 |
| Dead Cataphract                  | 27  |
| Dead Cavalier                    | 139 |
| Dead Cavalry Archer              | 34  |
| Dead Champion                    | 151 |
| Dead Conquistador                | 772 |
| Dead Crossbowman                 | 26  |
| Dead Deer (no food)              | 43  |
| Dead Eagle Warrior               | 754 |
| Dead Heavy Camel                 | 113 |
| Dead Horse                       | 815 |
| Dead Huskarl                     | 62  |
| Dead Jaguar                      | 813 |
| Dead Joan of Arc                 | 630 |
| Dead Joan the Maid               | 431 |
| Dead King                        | 839 |
| Dead Knight                      | 111 |
| Dead Knight with Lance           | 633 |
| Dead Light Cavalry               | 547 |
| Dead Long Swordsman              | 180 |
| Dead Mameluke                    | 44  |
| Dead Man at Arms                 | 157 |
| Dead Mangonel                    | 675 |
| Dead Militia                     | 152 |
| Dead Missionary                  | 776 |
| Dead Monk                        | 134 |
| Dead Onager                      | 121 |
| Dead Paladin                     | 570 |
| Dead Plumed Archer               | 764 |
| Dead Pikeman                     | 501 |
| Dead Scorpion                    | 149 |
| Dead Sheep (no food)             | 595 |
| Dead Siege Onager                | 589 |
| Dead Siege Ram                   | 549 |
| Dead Skirmisher                  | 238 |
| Dead Spearman                    | 100 |
| Dead Tarkan                      | 480 |
| Dead Teutonic Knight             | 181 |
| Dead Throwing Axeman             | 154 |
| Dead Trade Cart, unpacked        | 178 |
| Dead Trade Cart, packed          | 205 |
| Dead Trebuchet, unpacked         | 194 |
| Dead Trebuchet, packed           | 735 |
| Dead Two Handed Swordsman        | 568 |
| Dead Unrecognized cavalry        | 135 |
| Dead Unrecognized infantry       | 98  |
| Dead Unrecognized infantry       | 750 |
| Dead Unrecognized infantry       | 22  |
| Dead Unrecognized infantry       | 99  |
| Dead Villager, woman             | 60  |
| Dead Villager, woman, builder    | 213 |
| Dead Villager, woman, farmer     | 215 |
| Dead Villager, woman, forager    | 355 |
| Dead Villager, woman, miner      | 582 |
| Dead Villager, woman, hunter     | 217 |
| Dead Villager, woman, lumberjack | 219 |
| Dead Villager, woman, shepherd   | 591 |
| Dead Villager, man               | 58  |
| Dead Villager, man, builder      | 230 |
| Dead Villager, man, farmer       | 228 |
| Dead Villager, man, forager      | 353 |
| Dead Villager, man, miner        | 229 |
| Dead Villager, man, hunter       | 227 |
| Dead Villager, man, shepherd     | 226 |
| Dead War Elephant                | 136 |
| Dead War Wagon                   | 828 |
| Dead Woad Raider                 | 233 |
| Dead Wolf                        | 237 |

## 2.4. DLC Objects

These objects were added with DLC expansions to the HD Edition on Steam. For the most part, they will cause the map to CRASH if you attempt to load a map that contains them in any version of the game that does not have the required expansions

### 2.4.1. Animals from all Expansions

|Unit|ID||
|------------------|------|-----------------------------------------|
| Dolphin          | 61   | AoF; like great fish                    |
| DLC_LLAMA        | 305  | AoF; like sheep                         |
| DLC_BEAR         | 486  | AoF; like wolf                          |
| DLC_COW          | 705  | AoF; like sheep, but 150 food and 14 hp |
| Wild Camel       | 884  | AoF; like wild horse, no food           |
| Camel            | 897  | AoF; like horse, converts               |
| DLC_VULTURE      | 917  | AoF; like hawk                          |
| DLC_ELEPHANT     | 936  | AoF; like boar, but 400 food            |
| DLC_ZEBRA        | 1019 | AK; like deer                           |
| DLC_OSTRICH      | 1026 | AK; like deer                           |
| DLC_STORK        | 1028 | AK; like hawk                           |
| DLC_LION         | 1029 | AK; like wolf                           |
| DLC_CROCODILE    | 1031 | AK; like wolf                           |
| Falcon           | 1056 | AK; like hawk                           |
| DLC_GOAT         | 1060 | AK; like sheep                          |
| DLC_KOMODO       | 1135 | RoR; like wolf                          |
| DLC_TIGER        | 1137 | RoR; like wolf                          |
| DLC_RHINO        | 1139 | RoR; like boar, but 400 food            |
| DLC_BOXTURTLE    | 1141 | RoR; like shore fish                    |
| DLC_WATERBUFFALO | 1142 | RoR; like sheep, but 150 food           |


### 2.4.2. Eye-candy from the Forgotten

|Unit|ID||
|-----------------|---------|---------------------------------------------------------|
| Rubble 2x2      | 191     |                                                         |
| Rubble 2x2      | 192     | temporary                                               |
| Grass Patch     | 301     | tall grass                                              |
| Bush            | 302     | 2 variations, from JUNGLE terrain                       |
| Seagulls        | 303     | in a small patch                                        |
| Bonfire         | 304     | can be placed as a player object to offer line of sight |
| Black Tile      | 306     | 1x1 square of pure black                                |
| Loot            | 472     | pile of golden treasure                                 |
| Burned Building | 635     | varies                                                  |
| Burned Building | 758     | varies                                                  |
| Rock (Stone)    | 839     | turns into mineable stone when attacked by villagers    |
| Rock (Gold)     | 841     | turns into mineable gold when attacked by villagers     |
| Waterfall       | 896     | 3 rotations                                             |
| Rain            | 900     | 1x1 patch                                               |
| Flag F          | 901     | with golden emblem                                      |
| Smoke           | 902     | from blacksmith                                         |
| Boardwalk       | 904-909 | narrow wooden bridge                                    |
| Impaled Corpse  | 910     | varies, can be player object                            |
| Boardwalk       | 911-913 | narrow wooden bridge                                    |
| Quarry          | 914     | pile of mined rocks, no stone                           |
| Lumber          | 915     | pile of logs, no wood                                   |
| Goods           | 916     | fruit market stall, no food                             |
| Rock 2          | 918     | varies, brown rocks                                     |
| Barrels         | 933     | varies                                                  |
| Flame 1         | 939     | small                                                   |
| Flame 2         | 940     | small                                                   |
| Flame 3         | 941     | large                                                   |
| Flame 4         | 942     | large                                                   |


### 2.4.3. Buildings from the Forgotten

|Unit|ID||
|------------------------|---------|-------------------------------------------------------------|
| Fortress               | 33      | castle with new graphics, cannot train units                |
| Fortifed Palisade Wall | 119     | 500 HP, can be placed like walls, comes with palisade gate  |
| Fire Tower             | 190     | looks like keep, shoots fire                                |
| Aquaduct               | 231     | 1600 HP, can be placed like walls, comes with palisade gate |
| Amphitheatre           | 251     | eye-candy only                                              |
| Colosseum              | 263     | eye-candy only                                              |
| Indestructible Outpost | 308     | not actually indestructible, but very heavily armored       |
| City Wall              | 370     | 3200 HP, can be placed like walls, comes with palisade gate |
| Temple of Heaven       | 637     | eye-candy only                                              |
| Palisade Gate          | 789-804 | automatically placed for non-standard walls                 |
| Quimter Cathederal     | 872     | eye-candy only                                              |
| Arch of Constantine    | 899     | eye-candy only                                              |


### 2.4.4. Units from the Forgotten

|Unit|ID||
|---------------------------|-----|-----------------------------------------------|
| Legionary                 | 1   |                                               |
| Royal Janissary           | 52  | stronger janissary with new graphics          |
| Spy                       | 138 | high attack, looks like man-at-arms           |
| Condottiero               | 184 |                                               |
| Slinger                   | 185 |                                               |
| Flamethrower              | 188 | Dragon in AoFE (the original free mod)        |
| Imperial Camel            | 207 |                                               |
| Centurion                 | 275 | can be placed with CARAVAN                    |
| Nordic Swordsman          | 361 | wields an axe, not a sword                    |
| Penguin                   | 639 | cheat unit; not so strong                     |
| Heavy Eagle Warrior       | 753 |                                               |
| Canoe                     | 778 | can attack                                    |
| Amazon Warrior            | 825 | wields a spear                                |
| Donkey                    | 846 | no food                                       |
| Amazon Archer             | 850 |                                               |
| Genoese Crowwbowman       | 866 |                                               |
| Elite Genoese Crossbowman | 868 |                                               |
| Magyar Huszar             | 869 |                                               |
| Elite Magyar Huszar       | 871 |                                               |
| Elephant Archer           | 873 |                                               |
| Elite Elephant Archer     | 875 |                                               |
| Boyar                     | 876 |                                               |
| Elite Boyar               | 878 |                                               |
| Kamayuk                   | 879 |                                               |
| Elite Kamayuk             | 881 |                                               |
| Condottiero               | 882 |                                               |
| Siege Tower               | 885 |                                               |
| Tarkan                    | 886 |                                               |
| Elite Tarkan              | 887 |                                               |
| Heavy Pikeman             | 892 |                                               |
| Eastern Swordsman         | 894 |                                               |
| Monk with Relic           | 922 |                                               |
| Queen                     | 923 | no attack, doesn't trigger defeat in regicide |
| Alfred the Alpaca         | 934 | cheat unit; 120 attack                        |
| Dragon Ship               | 938 | shoots fire                                   |
| Relic Cart                | 944 | converts, cannot be destroyed or garrisoned   |


### 2.4.5. Heroes from the Forgotten

|Unit|ID||
|-----------------------|-----|--------------------------|
| Vlad Dracula          | 193 | Boyar                    |
| Quauhtemoc            | 307 | Elite Eagle Warrior      |
| Francisco de Orellana | 425 | Elite Conquistador       |
| Gonzalo Pizarro       | 427 | Elite Conquistador       |
| Frederick Barbarossa  | 429 | Elite Teutonic Knight    |
| Prithviraj            | 437 | Heavy Cavalry Archer     |
| Francesco Sforza      | 439 | Samurai                  |
| Sanyogita             | 925 | Queen                    |
| Prithvi               | 926 | Crossbowman              |
| Chand Bhai            | 927 | Monk with unique graphic |
| Saladin               | 929 | Elite Mameluke           |
| Khosrau               | 930 | Elite Elephant Archer    |
| Jarl                  | 931 | Elite Tarkan             |
| Savaran               | 932 | Elite Cataphract         |
| Osman                 | 943 | Heavy Cavalry Archer     |


### 2.4.6. Dead Units from the Forgotten

|Unit|ID||
|--------------------------|-----|
| Dead Legionary           | 2   |
| Dead Slinger             | 186 |
| Dead Flamethrower        | 189 |
| Dead Centurion           | 277 |
| Dead Imperial Camel      | 300 |
| Dead Nordic Swordsman    | 362 |
| Dead Monk (?)            | 412 |
| Dead Bear                | 489 |
| Dead Penguin             | 641 |
| Dead Llama               | 780 |
| Dead Cow                 | 843 |
| Dead Donkey              | 848 |
| Dead Genoese Crossbowman | 867 |
| Dead Magyar Huszar       | 870 |
| Dead Elephant Archer     | 874 |
| Dead Boyar               | 877 |
| Dead Kamayuk             | 880 |
| Dead Condottiero         | 883 |
| Dead Siege Tower         | 891 |
| Dead Heavy Pikeman       | 893 |
| Dead Eastern Swordsman   | 895 |
| Dead Camel               | 898 |
| Dead Amazon Warrior      | 919 |
| Dead Amazon Archer       | 920 |
| Dead Imam                | 921 |
| Dead Queen               | 924 |
| Dead Chand Bhai          | 928 |
| Dead Alfred the Alpaca   | 935 |
| Dead Elephant            | 937 |
| Dead Shaw                | 945 |


### 2.4.7. Eye-candy from African Kingdoms

|Unit|ID||
|--------------------|------|----------------------------------|
| DLC_SAVANNAHPATCH  | 1033 | light brown grass                |
| DLC_MOUNTAIN_5     | 1041 | like AoC mountains               |
| DLC_MOUNTAIN_6     | 1042 | rocky                            |
| DLC_MOUNTAIN_7     | 1043 | rocky                            |
| DLC_MOUNTAIN_8     | 1044 | rocky                            |
| DLC_MOUNTAIN_9     | 1045 | snowy                            |
| DLC_MOUNTAIN_10    | 1046 | snowy                            |
| DLC_MOUNTAIN_11    | 1047 | snowy                            |
| DLC_BOULDER_A      | 1048 | varies; small 1x1 rock formation |
| DLC_BOULDER_B      | 1049 | varies; tall 1x1 rock formation  |
| DLC_BOULDER_C      | 1050 | 3x3 rock formation               |
| DLC_DRAGONTREE     | 1051 | varies, 100 wood                 |
| DLC_BAOBABTREE     | 1052 | varies, 200 wood                 |
| DLC_AFRICANBUSH    | 1053 | various green bushes; 100 wood   |
| DLC_AFRICANBUSH_2  | 1054 | various snowy bushes; 100 wood   |
| DLC_ORANGEBUSH     | 1059 | like forage bush                 |
| DLC_ACACIATREE     | 1063 | varies, 100 wood                 |
| wooden rubble      | 1065 | 1x1                              |
| DLC_ANIMALSKELETON | 1091 |                                  |
| DLC_STELAE_A       | 1092 | 2x2 pillar                       |
| DLC_STELAE_B       | 1093 | 1x1 pillar                       |
| DLC_STELAE_C       | 1094 | 1x1 pillar                       |
| DLC_GALLOW         | 1095 | tree with noose                  |


### 2.4.8. Buildings from African Kingdoms

|Unit|ID||
|-------------------|------|----------------------------------------------------------|
| DLC_FEITORIA      | 1021 | generates resources over time                            |
| DLC_FENCE         | 1062 | 1 HP, can be placed like walls, comes with palisade gate |
| DLC_STORAGE       | 1081 | 2x2 thatch structure                                     |
| DLC_AFRICANHUT_A  | 1082 | 3x3 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_B  | 1083 | 2x2 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_C  | 1084 | 2x2 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_D  | 1085 | 2x2 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_E  | 1086 | 2x2 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_F  | 1087 | 2x2 straw hut, provides 5 housing space                  |
| DLC_AFRICANHUT_G  | 1088 | 2x2 straw hut, provides 5 housing space                  |
| DLC_GRANARY       | 1089 | 1x1 structure                                            |
| DLC_BARRICADE     | 1090 | a pile of rubbish, 1000 HP                               |
| Palace            | 1096 | wonder from random civilization                          |
| Tent              | 1097 | 3x3 tent, provides 5 housing space                       |
| Tent              | 1098 | 3x3 tent, provides 5 housing space                       |
| Tent              | 1099 | 3x3 tent, provides 5 housing space                       |
| Tent              | 1100 | 3x3 tent, provides 5 housing space                       |
| Tent              | 1101 | 3x3 tent, provides 5 housing space                       |
| Sea Fortification | 1102 | tower, cannot be placed on water                         |


### 2.4.9. Projectiles from African Kingdoms

|Unit|ID||
|----------------------|------|------------------------|
| throwing knife       | 1055 | spins and makes sounds |
| heavy bolt           | 1057 | stationary and silent  |
| heavy bolt (flaming) | 1058 | stationary and silent  |
| bolt                 | 1111 | stationary and silent  |
| bolt (flaming)       | 1112 | stationary and silent  |
| bolt                 | 1113 | stationary and silent  |
| bolt (flaming)       | 1114 | stationary and silent  |
| organ gun bullet?    | 1119 | stationary and silent  |


### 2.4.10. Units from African Kingdoms

|Unit|ID|
|-------------------------------|------|
| DLC_ORGANGUN                  | 1001 |
| DLC_ELITEORGANGUN             | 1003 |
| DLC_CARAVEL                   | 1004 |
| DLC_ELITECARAVEL              | 1006 |
| DLC_CAMELARCHER               | 1007 |
| DLC_ELITECAMELARCHER          | 1009 |
| DLC_GENITOUR                  | 1010 |
| DLC_ELITEGENITOUR             | 1012 |
| DLC_GBETO                     | 1013 |
| DLC_ELITEGBETO                | 1015 |
| DLC_SHOTELWARRIOR             | 1016 |
| DLC_ELITESHOTELWARRIOR        | 1018 |
| Monkboat (converts units)     | 1022 |
| DLC_AOE1PRIEST                | 1023 |
| Genitour (placeholder, 60 HP) | 1079 |
| Preist with relic             | 1025 |
| DLC_FIREGALLEY                | 1103 |
| DLC_DEMOLITIONRAFT            | 1104 |
| DLC_SIEGETOWER                | 1105 |

### 2.4.11. Dead Units from African Kingdoms

|Unit|ID|
|--------------------------|------|
| Dead Organ Gun           | 1002 |
| Dead Organ Gun           | 1005 |
| Dead Camel Archer        | 1008 |
| Dead Genitour            | 1011 |
| Dead Gbeto               | 1014 |
| Dead Shotel Warrior      | 1017 |
| Dead Zebra               | 1020 |
| Dead Priest              | 1024 |
| Dead Ostrich             | 1027 |
| Dead Lion                | 1030 |
| Dead Crocodile           | 1032 |
| Dead Goat                | 1061 |
| Dead Siege Tower         | 1107 |
| Dead Dagnajan            | 1108 |
| Dead Gidajan             | 1110 |
| Dead Eagle Warrior       | 1116 |
| Dead Elite Eagle Warrior | 1117 |

### 2.4.12. Heroes from African Kingdoms

|Unit|ID||
|---------------------|------|--------------------------|
| DLC_MUSA            | 1034 | Camel Archer             |
| DLC_SUNDJATA        | 1035 | Light Cavalry            |
| DLC_TARIQ           | 1036 | Genitour                 |
| DLC_RICHARDDECLARE  | 1037 | Light Cavalry            |
| DLC_TRISTAN         | 1038 | Magyar Huszar            |
| DLC_YODIT           | 1039 | Queen, no attack         |
| DLC_HENRY2          | 1040 | Two-handed Swordsman     |
| DLC_YEKUNOAMLAK     | 1064 | Shotel Warrior           |
| DLC_WARRIORYODIT    | 1066 | Gbeto                    |
| DLC_ITZCOATL        | 1067 | Jaguar Warrior           |
| DLC_MUSTAFA         | 1068 | Janissary                |
| DLC_PACAL2          | 1069 | Plumed Archer            |
| DLC_BABUR           | 1070 | Imperial Camel           |
| DLC_ABRAHAELEPHANT  | 1071 | War Elephant             |
| DLC_GUGLIELMO       | 1072 | Genoese Crossbowman      |
| DLC_SU_DINGFANG     | 1073 | Chu-ko-nu                |
| DLC_PACHACUTI       | 1074 | Kamayuk                  |
| DLC_HUAYNA_CAPAC    | 1075 | Slinger                  |
| DLC_MIKLOSTOLDI     | 1076 | Magyar Huszar            |
| DLC_LITTLEJOHN      | 1077 | Spearman                 |
| DLC_ZAWISZATHEBLACK | 1078 | Hussar                   |
| DLC_SUMANGURU       | 1080 | Cataphract               |
| DLC_DAGNAJAN        | 1106 | Alephant Archer          |
| Gidajan             | 1109 | Carries sword and shield |

### 2.4.13. Eye-candy from Rise of the Rajas

|Unit|ID||
|---------------------|-----------|---------------------------------|
| DLC_MANGROVE_TREE   | 1144      | from DLC_MANGROVEFOREST terrain |
| DLC_RAINTREE        | 1146      | from DLC_RAINFOREST terrain     |
| DLC_ROCKBEACH       | 1148      | massive rocky outcropping       |
| DLC_ROCKJUNGLE      | 1149      | plant-covered rocks             |
| Flag G              | 1150      |                                 |
| Flag H              | 1151      |                                 |
| Flag I              | 1152      |                                 |
| Flag J              | 1153      |                                 |
| DLC_BUDDHA_STATUE_A | 1171      | 2x2                             |
| DLC_BUDDHA_STATUE_B | 1172      | 3x3                             |
| DLC_BUDDHA_STATUE_C | 1173      | 1x1 sitting Buddha              |
| DLC_BUDDHA_STATUE_D | 1174      | 1x1 standing Buddha             |
| DLC_FERN_PATCH      | 1175      | cluster of small plants         |
| DLC_TROWULAN_GATE   | 1176      | tall stone structure, varies    |
| DLC_VASES           | 1177      | clay vessels, varies            |
| Stupa               | 1191      | small structure                 |
| Pagoda, tall        | 1201      |                                 |
| Pagoda, medium      | 1202      |                                 |
| Pagoda, short       | 1203      |                                 |
| Bridge C and D      | 1204-1215 | wide beige stone bridge         |

### 2.4.14. Buildings from Rise of the Rajas

|Unit|ID||
|------------------|-----------|-------------------------------------|
| Rice Farm        | 1187      | contains food                       |
| Dead Rice Farm   | 1188      | can be reseeded                     |
| Harbor           | 1189      | fires arrows, cannot produce ships  |
| Army Tent, large | 1196      | opens to the left, supports 5 pop   |
| Army Tent, large | 1197      | opens to the right, supports 5 pop  |
| Army Tent, small | 1198      | opens to the right, supports 5 pop  |
| Army Tent, small | 1199      | opens to the left, supports 5 pop   |
| Army Tent, small | 1200      | opens to the bottom, supports 5 pop |
| Sanchi Stupa     | 1216      | Stupa monument                      |
| Gol Gumbaz       | 1217      | palace monument                     |
| Barricade        | 1218-1220 | rotated versions of DLC_BARRICADE   |

### 2.4.15. Projectiles from Rise of the Rajas

|Unit|ID|
|----------------------------------------|------|
| Ballista Elephant Projectile           | 1167 |
| Ballista Elephant Projectile (burning) | 1168 |
| Arrow                                  | 1169 |
| Arrow (burning)                        | 1170 |
| Cow projectile (fired by Sharkatzor)   | 1223 |

### 2.4.16. Units from Rise of the Rajas

|Unit|ID|
| DLC_BALLISTAELEPHANT           | 1120 |
|--------------------------------|------|
| DLC_ELITEBALLISTAELEPHANT      | 1122 |
| DLC_KARAMBIT                   | 1123 |
| DLC_ELITEKARAMBIT              | 1125 |
| DLC_ARAMBAI                    | 1126 |
| DLC_ELITEARAMBAI               | 1128 |
| DLC_RATTANARCHER               | 1129 |
| DLC_ELITERATTANARCHER          | 1131 |
| DLC_BATTLEELEPHANT             | 1132 |
| DLC_ELITEBATTLEELEPHANT        | 1134 |
| DLC_IMPERIALSKIRMISHER         | 1155 |
| Farmer (male villager)         | 1192 |
| Sharkatzor (flying cheat unit) | 1222 |

### 2.4.17. Dead Units from Rise of the Rajas

|Unit|ID|
|----------------------------|------|
| Dead Ballista Elephant     | 1121 |
| Dead Karambit Warrior      | 1124 |
| Dead Arambai               | 1127 |
| Dead Rattan Archer         | 1130 |
| Dead Battle Elephant       | 1133 |
| Dead Komodo Dragon         | 1136 |
| Dead Tiger                 | 1138 |
| Dead Rhinoceros            | 1140 |
| Dead Water Buffalo         | 1143 |
| Dead Elite Battle Elephant | 1154 |
| Dead Imperial Skirmisher   | 1156 |
| Dead Sunda Royal Fighter   | 1161 |
| Dead Gajah Mada            | 1190 |

### 2.4.18. Heroes from Rise of the Rajas

|Unit|ID||
|-------------------------|------|---------------------------|
| DLC_GADJAH_MADA         | 1157 | shirtless swordsman       |
| DLC_JAYANEGARA          | 1158 | no attack, reskinned King |
| DLC_RADEN_WIJAYA        | 1159 | Cavalier                  |
| DLC_SUNDA_ROYAL_FIGHTER | 1160 | wields spear and shield   |
| DLC_SURYAVARMAN_I       | 1162 | Elite Battle Elephant     |
| DLC_UDAYADITYAVARMAN_I  | 1163 | no attack, reskinned King |
| DLC_JAYAVIRAVARMAN      | 1164 | Karambit Warrior          |
| DLC_BAYINNAUNG          | 1165 | Elite Battle Elephant     |
| DLC_TABINSHWEHTI        | 1166 | Elephant Archer           |
| DLC_LELOI               | 1178 | Champion                  |
| DLC_LELAI1              | 1179 | Champion                  |
| DLC_LELAI2              | 1180 | Two-Handed Swordsman      |
| DLC_LETRIEN             | 1181 | Champion                  |
| DLC_LUUNHANCHU          | 1182 | Arbalest                  |
| DLC_BUIBI               | 1183 | Monk with unique graphic  |
| DLC_DINHLE              | 1184 | Paladin                   |
| DLC_WANGTONG            | 1185 | Cataphract                |
| DLC_ENVOY               | 1186 | Light Cavalry             |

