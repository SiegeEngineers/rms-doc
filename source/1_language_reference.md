Scripts are divided in 7 sections, each one managing a category of map features. Sections start with the following tags:

```rms
<PLAYER_SETUP>                  /* Basic setup */
<LAND_GENERATION>               /* Main lands or seas */
<ELEVATION_GENERATION>          /* Hills */
<CLIFF_GENERATION>              /* Rocky cliffs */
<TERRAIN_GENERATION>            /* Terrain patches */
<CONNECTION_GENERATION>         /* Terrain bridges/roads/passages */
<OBJECTS_GENERATION>            /* Units, buildings, resources, eye-candies */
```

- You don't need to write sections in that order, however that's the order the game uses them.
- You might notice that in the standard maps they are in a different order with cliffs and connections (and sometimes elevation) at the end. However, it might be helpful to write them in the order above, because it makes it easier for you to visualize the map generation process and understand why things will happen; like terrain water on hills, objects on connections, or terrain avoiding cliffs. Ultimately the order in which you write the sections has no effect though. 
- Not all the sections are necessary (e.g. you may make a map without cliffs).
- Each section contains some types of instructions. Most instructions look like this:

```rms
create_something WHAT
{
attribute TYPE
attribute N
set_attribute
(...)
}
```

- You can indent instructions however you want, just keep words separated by newlines or spaces.
- Scripts are case-sensitive, pay attention to capital letters.
- All "create" commands can be used multiple times in a RMS. Other commands can't.
- Most "attributes" (subcommands inside brackets) have a default and can be omitted. Some { } can be empty!
- Order of attributes inside brackets is not important.
- If an item can't be created for some reason, the game will simply ignore it and go on. If you see something is missing, try to relax some constraints on its placement.


## 1.1. Scheme of a RMS

Here's the skeleton of a script with all possible commands, useful for cutting & pasting. Everything is explained later.

- `N` means an integer number, possibly within a range. Decimals and negatives are usually not allowed.
- `%` means a percentage (0-100). Decimals are not allowed. Do not type the "%"!
- TYPE means a constant identifier such as GRASS. Types are reported in Terrains & Objects chapter.
Nothing happens if you use a non-valid name (a type that doesn't exist).
- Commands work in all versions of the game unless specifically stated otherwise in the descriptions below.
- / means that you should use either one or the other of these attributes, but not both.

```rms
<PLAYER_SETUP>
random_placement  /  grouped_by_team
nomad_resources
ai_info_map_type TYPE N(0-1) N(0-1) N(0-1)

<LAND_GENERATION>

base_terrain TYPE

create_player_lands
{ 
terrain_type TYPE
land_percent %  /  number_of_tiles N
base_size N  
base_elevation N(1-7) 
left_border %,  right_border %,  top_border %,  bottom_border %
border_fuzziness %
clumping_factor %
zone N  /  set_zone_randomly  /  set_zone_by_team  
other_zone_avoidance_distance N
}

create_land
{
terrain_type  TYPE
land_percent %  /  number_of_tiles N
base_size N
base_elevation N(1-7)
left_border %,  right_border %,  top_border %,  bottom_border %
land_position % %
border_fuzziness %
clumping_factor %
zone N  /  set_zone_randomly 
other_zone_avoidance_distance N
min_placement_distance N
land_id N
assign_to_player N(1-8)
}

<ELEVATION_GENERATION>

create_elevation  N(1-7)
{
base_terrain TYPE
number_of_tiles N
number_of_clumps N
set_scale_by_size
set_scale_by_groups
spacing N 
}

<CLIFF_GENERATION>

min_number_of_cliffs N
max_number_of_cliffs N
min_length_of_cliff N
max_length_of_cliff N
cliff_curliness %
min_distance_cliffs N
min_terrain_distance N 

<TERRAIN_GENERATION>

create_terrain TYPE
{
base_terrain TYPE
land_percent %  /  number_of_tiles N
number_of_clumps N
set_scale_by_size
set_scale_by_groups
spacing_to_other_terrain_types N
set_avoid_player_start_areas
height_limits N(0-7) N(0-7)
set_flat_terrain_only
clumping_factor %
}

<CONNECTION_GENERATION>

create_connect_all_players_land  /  create_connect_teams_lands  /  
create_connect_all_lands  /  create_connect_same_land_zones
{
	default_terrain_replacement  TYPE 
replace_terrain 	TYPE 	TYPE
terrain_cost 	TYPE 	N(1-15)
terrain_size    	TYPE	N N
}

<OBJECTS_GENERATION>

create_object TYPE
{
number_of_objects N
number_of_groups N
group_variance N
set_scaling_to_map_size  /  set_scaling_to_player_number
set_place_for_every_player
set_gaia_object_only
terrain_to_place_on TYPE
min_distance_to_players N,  max_distance_to_players N
max_distance_to_other_zones N
min_distance_group_placement N
temp_min_distance_group_placement N
group_placement_radius N
set_tight_grouping  /  set_loose_grouping
place_on_specific_land_id N
resource_delta N
}
```


## 1.2. Command Descriptions

### 1.2.1. &lt;PLAYER_SETUP>

default is `random_placement`

#### Commands

`random_placement`  
Players are positioned in circle/oval around the map. Even if you don’t type it, it still applies because it is the default.

`grouped_by_team`  
Position team members in close proximity on the map. This command and random_placement are mutually exclusive. The base_size specified in create_player_lands determines the distance between players on a team. Requires UP/HD.

`nomad_resources`  
Modify starting resources to match the built-in nomad map. This means that the cost of a town center (275W, 100S) is added to the stockpile. Can be used even if your map is not a nomad map. Requires UP/HD.

`ai_info_map_type TYPE  N(0-1)  N(0-1)  N(0-1)`  
This is an optional line to help the AI (computer player) detect the type of map. 
Map types are reported in section 2.5.
The N values are for map styles. 1 is used if the style applies, 0 if it does not apply. They require UP/HD.

- The 1st number is 1 if nomad, else 0
- The 2nd number is 1 if michi, else 0 
- The 3rd number is 1 if you want to display the map type in the objectives window, if not 0 
- Nomad is any map where you start without a town center
- Michi is a type of map where teams are completely separated from each other by forest and have to cut through.

Example – a map that is similar to Arabia, but has a nomad start, and you want the objectives screen to say Arabia:
`ai_info_map_type ARABIA 1 0 1`




### 1.2.2. &lt;LAND_GENERATION>

Here basic territories are created, especially player starting lands; e.g. you may place grass continents on a water base. Land origins (square bases) are placed in order. After that, all lands "grow" at the same time from their origins outwards to fill the amount of space specified for each land.

#### Commands
`base_terrain TYPE`  
Initially, the map is filled with this terrain type. Default is GRASS.

`create_player_lands { ... }`  
Creates starting lands for ALL players. Usually there's one and only one create_player_lands statement.
- If you use create_player_lands more than once, each player will have multiple starting towns!
- Instead of create_player_lands you can use assign_to_player (see below)
- If you create no player lands at all, you can't place starting units and resources (only a Town Center and Villagers will be placed somewhere at random – not evenly spaced – so this is generally not recommended)

`create_land { ... }`  
Creates a generic land. It's called "land" but it can also be a lake (or any terrain type)! 

######  Attributes
`terrain_type TYPE`  
Type of terrain... Default is GRASS.

`land_percent %  /  number_of_tiles N`  
Size of land. Use either land_percent or number_of_tiles. Default is 100%.
If total size of all lands exceeds the size of whole map, the game will try to reduce them fairly.

`land_percent %`  

- Percent on whole map; scales with map size 
- For Player Lands, it's total size (shared among ALL players), so you better set a high %


`number_of_tiles N `

- It's a fixed size
- For Player Lands, it means the size of each player's land; about 1000 tiles should be ok.

`base_size N`  
Minimum square radius of the land. Default is 3 (7x7 square). Placed sequentially, so if land bases are large and overlap, the ones placed later will be visible. This command can force land size to be bigger than that specified with `land_percent` / `number_of_tiles`. If base_size is high in comparison with land size, the land becomes square-like (or even a perfect square!). Land origins will be placed at least this far from the edge of the map.  If base_size for non-player lands  is too large, the land will fail to find a valid position and will be placed at the center of the map.

`base_elevation N(1-7)`  
Modify the base elevation for player and standard lands. Default is 0 (not elevated). &lt;ELEVATION_GENERATION> must exist if used. Requires UP/HD. Values over 7 are possible, but there are rendering issues with terrain and objects. Setting it to -1 results in maximally elevated lands, and causes those same issues.  It is best to stay in the range 1-7. 

`left_border %,  right_border %,  top_border %,  bottom_border %`  
Make the land stay away from map edges, at least by specified distance (defined by % of map width).
You can specify one or more of these attributes. Default is 0 (lands can touch any edge).

- Top border refers to the upper left edge.
- You can use these attributes to create a land near the centre of the map, but also to create a land near a particular edge: e.g. bottom_border 90 would create a strip of land very close to top border.

Using asymmetric borders for player lands can cause crashes in some cases.  To avoid this, follow these steps:

- Never use top_border in isolation when creating player lands.
- Using any one of right/left/bottom along with top will prevent crashes, as long as it has at least the magnitude of the top_border.

Negative borders can be used, with caution. If a land has it's randomly placed origin "outside" of the map, then game will crash. Therefore you should not use not use negative borders for a land unless you have specified a land_position for that land, to ensure the origin is not oustide the map.



`land_position %(0-100) %(0-99) `  
Defines the origin of a given land using X% and Y% coordinates. For example, `land_position 50 50` would place the land at the map center. Ignores borders and any other restrictions. Default is random. Disabled for player lands and lands with assign_to_player. Setting the second number to 100 will crash the map. If land_position specifies an origin that lies outside the area specified by `left_border %`,  `right_border %`,  `top_border %`,  `bottom_border %`, the land will only be the size of its base_size and will not grow.

`border_fuzziness %`  
Border regularity: lower values (5-20) tend to make land edges more ragged and natural when land growth is constrained by borders. Default is 20. Lower values allow land growth to exceed the boundaries set by top/bottom/left/right borders. At border_fuzziness 0, the land ignores borders entirely. At 100 (or any negative value), borders are not exceeded at all.

`clumping_factor %(-100-99)`  
Shape regularity: higher values tend to form roundish lands; lower values tend to form weird, snaky lands. Default is 8.
If you want to guarantee that a land is wide enough, you better use base_size. Negative values will create extremely patchy and snaky lands and is generally not recommended.

`zone N   /  set_zone_randomly  /  set_zone_by_team`  
Setting a zone is useful if combined with other_zone_avoidance_distance (see below). Zone number is just a label, its value is not important. By default, every Player Land has a different zone (as in Islands map), but non-player lands all have same zone. 

- `set_zone_randomly` assigns a random zone. In `create_player_lands` it works separately for each player, so that some players share the same zone, some others don't (as in Archipelago map)
- `set_zone_by_team` works only for Player Lands, makes allies share the same zone (as in Team Islands map)
- zone 99 will crash the game; values greater than 99 work again though.

`other_zone_avoidance_distance N`  
Minimum distance, in tiles, from lands of other zones (see above) to stop land growth. Default is 0 (lands can touch each other). Keeps isles separated. Useful also for creating rivers: even if the lands cover the whole map, with this attribute they will still be separated by strips of base terrain of constant width N.

- If you want to be sure that two lands are separated, BOTH land definitions must contain this attribute!
- If you give two lands different values, the smaller avoidance distance will be the one that applies
- When used for player lands (and lands with assign_to_player), it only applies to the distance to other player lands and NOT to non-player lands
- This attribute only applies to land growth – land origins/bases may end up closer together or even touching if base_size is large or many players are on a small map.

`min_placement_distance N`  
Specifies the minimum distance that a land's origin must be placed away from the origins of other lands. Has no effect on Player Lands. Specifiying too high of a number means that the land will find no valid position, and will be placed in the center. This attribute was previously undocumented and is basically never used.  Best to leave it out of your script.

`land_id N`  
Assigns a numeric label to the land (it has nothing to do with zone labels). Its value is not important.
This allows objects (see below) to be placed only on this land, using place_on_specific_land_id.

- Does not work with Player Lands
- Land must be separated from others by water (or shallow / ice / beach for objects not allowed there)
- Multiple lands can be given the same id – in this case the objects will be placed on all lands with this id

`assign_to_player N(1-8)`  
To be used only in create_land, makes this land player N's starting land. An alternative to create_player_lands.
You should assign 8 different lands to 8 players, if you want your RMS to support up to 8 players. 

- Player number refers to order, not color (player 1 is first name on list, not necessarily blue)
- If some players are not playing, their lands won't be created at all
- You can't assign the same land to more players
- This attribute, along with terrain_to_place_on can be used to create unequal starts. For example, to make a computer-player-friendly single player version of a map that computer players normally have trouble with. However, you cannot control the position of individual lands that are made using this attribute - all lands belonging to players will still be in a circle or oval shape and `land_position` is ignored.


### 1.2.3. &lt;ELEVATION_GENERATION>

Elevations are the smooth and walkable hills. They automatically avoid players' start areas.

#### Commands
`create_elevation N(1-7) { ... }`  
Creates one or more hills with random height, up to N. Generally, hills with larger base reach greater height.

##### Attributes
`base_terrain TYPE`  
Hills grow on this type of terrain. Default is `GRASS`.

`number_of_tiles N`  
Total base size of ALL hills. Default is about 152 tiles.

`number_of_clumps N`  
Maximum number of distinct hills to create. Default is one hill.

`set_scale_by_size`  
Total base size is scaled to map size. Unscaled value refers to a 100x100 map.

`set_scale_by_groups`  
Number of hills is scaled to map size. Unscaled value refers to a 100x100 map.

`Spacing N`  
Specifies the spacing between each height level on each clump of elevation. Default is 1. Larger numbers produce hills with rings of flat areas on each level. This can be used to increase buildable land and prevent long sloped areas. 

### 1.2.4. &lt;CLIFF_GENERATION>
Cliffs are the rocky, not walkable canyons. You can't create single cliffs, but you can define general cliff statistics.
All commands have a reasonable default; typing just `<CLIFF_GENERATION>` is enough to create cliffs.  If you don’t want your map to have cliffs, then don’t put in a `<CLIFF_GENERATION>` section at all.  Cliffs automatically avoid player start areas as well as the origins of non-player lands and also avoid all sources of water.

#### Commands
`min_number_of_cliffs N`  
`max_number_of_cliffs N`  
Limits of total number of cliffs on map. They don't scale with map size (so you need to manually scale with "if" statements - see conditionals).  Default is min 3 and max 8.

`min_length_of_cliff N`  
`max_length_of_cliff N`  
Length limits of each cliff (each one can have different length). Default is min 5 and max 9. Usually, min must be at least 3 for individual cliffs to appear at all. Note that cliff length is not equivalent to the number of tiles the cliff occupies, because cliff objects are larger than one tile. Length 3 is 12 tiles, 4 is 15 tiles, 5 is 18 tiles and so on.  Cliffs may end up shorter than expected if restricted by other nearby cliffs.

`cliff_curliness %`  
Chance of turning at each cliff tile. Low % makes straighter cliffs, high % makes curlier cliffs. Default is 36.

`min_distance_cliffs N`  
Minimum distance between cliffs, in tiles. Default is 2.  A distance of 2 is 6 tiles between cliffs, 1 is 3 tiles, 0 is 0 tiles.

`min_terrain_distance N`  
Minimum distance to the nearest body of water (including ice). Does not apply to water created in `<TERRAIN_GENERATION>` because that is created afterwards. Default is 2. A distance of 2 is 6 tiles, 1 is 3 tiles, 0 is 0 tiles.





### 1.2.5. &lt;TERRAIN_GENERATION>
Here you can create a variety of terrain patches on the main lands. Sometimes you may achieve the same result by creating a Land or by creating a Terrain, but they can have different attributes. Also remember:

- Terrain order is important: if you want to place palm forest on desert, first you must declare desert.
- Terrain is placed AFTER elevations, so be careful e.g. when placing water... or you may get water on hills!

#### Commands
`create_terrain TYPE { ... }`  
Creates one or more patches of TYPE terrain.

##### Attributes
`base_terrain TYPE`  
What terrain type the new terrain will be placed on. Default is GRASS.

`land_percent %  /  number_of_tiles N`  
Total size of terrain patches. Use either land_percent or number_of_tiles. Default is about 150 tiles.

- `land_percent %`  
    Percent on whole map; scales with map size 

- `number_of_tiles N `  
    It's a fixed size

`number_of_clumps N`  
Maximum number of distinct terrain patches to create. Default is one.

`set_scale_by_size`  
To be used with number_of_tiles; total terrain size is scaled to map size. Unscaled value refers to a 100x100 map.

`set_scale_by_groups`  
Number of patches is scaled to map size. Unscaled value refers to a 100x100 map.

`spacing_to_other_terrain_types N`  
Minimum distance, in tiles, from different types of terrains. Default is none.
Recommended for keeping forests away from shores, otherwise they can obstruct the way. 

- It doesn't force terrains placed later to stay away, only checks terrains placed before; so you better include this attribute for all terrains that must be separated
- It also affects the minimum distance, in tiles, from cliffs

`set_avoid_player_start_areas`  
Makes terrain stay away from the center of Player Lands. Without it, forests and lakes may swallow town centers!

`height_limits N(0-7) N(0-7)`  
Forces terrain to be placed within certain elevations. First number is minimum height, second is maximum.
For example, it lets you place snow only on hill tops.

`set_flat_terrain_only`  
Avoid elevation changes. Useful to prevent lakes form lying on slopes.
If it doesn't work, try using height_limits 0 0

`clumping_factor %(-100-99)`  
Shape regularity: higher values tend to form roundish patches, lower values tend to form weird, snaky patches. 
Default is 20 (different than in Land generation). Negative values will create extremely patchy and snaky clumps.

### 1.2.6. &lt;CONNECTION_GENERATION>
Connections are lines of terrain that link Lands. Usually their job is to ensure that units can walk to other lands.
You can't create single connections, only general systems of connections. If possible, connections reach origins of lands (town centers, if placed with max_distance_to_players 0).

#### Commands
`create_connect_all_lands { ... }`  
All Lands are connected. In general this doesn't include isles created with &lt;TERRAIN_GENERATION>.

`create_connect_all_players_land { ... }`  
All Player Lands are connected. Connections may pass thru nobody's lands too, if that's the easiest way.

`create_connect_teams_lands { ... }`  
Allied Player Lands are connected. Connections may pass thru enemy and nobody's lands too, if that's the easiest way.

`create_connect_same_land_zones { ... }`  
Appears to behave the exactly same way as create_connect_all_lands. Previously undocumented and is not therefore not typically used.

##### Attributes
`default_terrain_replacement TYPE `  
Creates connections by replacing ALL intervening terrain with the specified terrain.  Previously undocumented, and therefore not typically used. If used, make sure to use before any replace_terrain attributes. Those replace_terrain attributes can then be used to specify a different terrain for parts of the connection.  For example, to replace all terrain with road, but water with shallows. When used after a replace_terrain attribute it overrides it and re-replaces terrain along the connection.

`replace_terrain  TYPE  TYPE`  
Defines what base terrain should be replaced by what connection terrain. 
Typically shallow replaces water, by typing `replace_terrain WATER SHALLOW`
By default, connections CAN pass through not specified terrain; however, they are not visible if you do not have a replace_terrain for a given terrain. If you want to make sure a connection doesn’t pass through a terrain, give that terrain a relatively high terrain_cost.

- You can replace a terrain with itself.

`terrain_cost TYPE  N(1-15)`  
"Cost" of passing thru that terrain (can be set even if you don’t have a corresponding replace_terrain). Connections are more likely to pass thru terrains with lower cost, and tend to avoid terrains with higher cost (or take shorter ways). Default is 1.

`terrain_size  TYPE  N  N`  
Connections width on that terrain (requires respective replace_terrain). 

- First number is mean width in tiles
- Second number is maximum random variation of connections width in every point

E.g. terrain_size WATER 5 2 creates paths 3 to 7 tiles wide (5 ± 2). Default is 1 0. 
Specifying a variance greater or equal to mean width CAN reduce width to 0 (broken connections!).
If a connection looks wider than it should, actually it's two or more parallel connections; try changing terrain cost.

### 1.2.7. &lt;OBJECTS_GENERATION>
Objects include units, buildings, resources and decorations such as hawks. 

#### Commands
`create_object TYPE { ... }`  
Creates one or more objects of TYPE, for players or for nature.   
WARNING: I experienced crashes and bad results when using more than 99 distinct create_object commands! 

##### Attributes
`number_of_objects N`  
How many to place. Default is 1.

`number_of_groups N`  
Creates N groups, each of specified number_of_objects. Total objects  =  number_of_objects  X  number_of_groups.  
Default is no groups: objects are independent and completely scattered.

`group_variance N`  
Works only with number_of_groups: randomizes number of objects in every group. It changes by a random amount ranging from -N to N (a group of deer with number_of_objects 5 and group_variance 2 can have 3 to 7 deer: 5 ± 2). Default is 0.

- Each group can have a different amount
- Groups always have at least one element

`set_scaling_to_map_size  /  set_scaling_to_player_number`  
Use one or other. Scales number of groups; if number_of_groups isn't defined, scales number_of_objects.

- set_scaling_to_map_size: unscaled value refers to a 100x100 map
- set_scaling_to_player_number: Total groups  =  number_of_groups  X  number of players		

(it has only effect on number, don't get confused with set_place_for_every_player)

`set_place_for_every_player`  
Places objects as "personal" objects for every player, such as the starting villagers. Also works for non-player objects, e.g. everyone can start with a personal gold mine nearby (but set_gaia_object_only is needed).

- Places objects even if player doesn't have the ability to build them; e.g. you can create a stable also at Dark Age or for Aztecs, though it won't produce any horsemen
- Works only if Player Lands are defined
- You can't place units on lands that are separated by water from own Player Land (or shallow / ice / beach for buildings and other objects not allowed there)
- Usually it doesn't work for water objects, so you CAN'T place starting ships, docks and so on, BUT...
    - It works if Player Lands are made of dirt (`DIRT`, `DIRT2`, `DIRT3`, `DIRT_SNOW`)
    - It works for computer players
    - It may work if water is part of the player land itself
    - It does not work if land_id is used

I made a lot of experiments but still I can't find logic in this!!

`set_gaia_object_only`  
Makes objects belong to NO player. By default, all objects are "gaia" if you don't use `set_place_for_every_player`.

- It MUST be used, together with `set_place_for_every_player`, for personal non-controllable objects.
- If used with controllable objects (units and buildings), makes them neutral (rescuable). Rescuable objects permanently join the first human player who passes by, but not computer players. They're west-European style.

`terrain_to_place_on TYPE`  
Only places on this type of terrain. By default, most common objects are automatically placed on reasonable terrains (no fish on land, no relics on water, no gold on road, etc...), and you can't put them on weird terrain anyway.
But some types of eye-candies may be put on weird terrain (you can use terrain_to_place_on to avoid this).

`min_distance_to_players N,  max_distance_to_players N`  
Minimum and maximum distance, in tiles, from the centers of Player Lands. You can specify one or both attributes.
By default, there are no distance limits. Usually the town center is placed at `max_distance_to_players 0`.

- With `set_place_for_every_player`, distance refers only to respective player
- Without `set_place_for_every_player`, `max_distance_to_players` has NO effect, and `min_distance_to_players` ensures a minimum distance from the centers of ALL LANDS. If you have many non-player lands this can restrict the placement of objects.
- With `place_on_specific_land_id`, distance refers to that land's center
- If `number_of_groups` is defined, distance refers to centers of groups.
- If these distance limits are very strict (e.g. min = max), objects tend to appear mostly on the left.

`max_distance_to_other_zones N`  
Minimum (NOT maximum!!) distance in tiles from borders of zones; useful to keep objects away from shores.
If `number_of_groups` is defined, distance refers to centers of groups.

`min_distance_group_placement N`  
Scatters objects, keeping them at least N tiles away from any other current or future object of any type.
Keeps away only objects created by the same create_object command, or placed later; does not affect objects placed earlier. To be sure that two series of objects aren't close, add this attribute to both creation statements.
If `number_of_groups` is defined, distance applies among centers of groups, not among objects of same group.
WARNING: This attribute will affect ALL objects placed after this command. If you want to scatter objects created in the same create_object command without restricting future object placement, it is best to use `temp_min_distance_group_placement` (see blow) to do so. Use `min_distance_group_placement` with smaller values to prevent objects created in future commands from ending up directly next to the current ones.  Both attributes can be used together in the same `create_object` command.  Inappropriate use of `min_distance_group_placement` may result in objects towards the end of your script not being placed at all!



`temp_min_distance_group_placement N`  
Scatters objects created by current create_object command, keeping them at least N tiles away from each other. Does not apply to objects placed earlier or later. If number_of_groups is defined, distance applies among centers of groups, not among objects of same group. Only used for relics in the standard maps; however is often a good idea to use this attribute for any objects that need to be scattered far apart from each other (like wolves, or extra map resources).

`group_placement_radius N`  
Force objects in every group to stay within N tiles from center of group. Default is 3 tiles (7x7 square area).

- group_placement_radius overrides other attributes, including number_of_objects. For large groups, you need a large group_placement_radius; by default, groups can contain no more than 7x7=49 objects

`set_tight_grouping  /  set_loose_grouping`  
Use one or other. Tight groups have no space among objects (like gold and stone in standard maps).  
Loose groups can have 1 or 2 tiles among objects; `set_loose_grouping` is default and can be omitted.

- `set_tight_grouping` doesn't place objects that are larger than 1 tile and can't overlap (like most buildings)

`place_on_specific_land_id N`  
Places objects only on the Land marked by `land_id N`.
- Personal objects are assigned to players without needing to use `set_place_for_every_player` (and won't appear if you do use it)
- Land must be separated from others by water (or shallow / ice / beach for objects not allowed there)
- If there are multiple lands with the same id, the set number of objects is placed on each of them

`resource_delta -N`  
Modify the resources of a specific instance of an object. (only works with UP, not in the HD Edition)
This allows you to, for example, produce a gold mine with only 300 gold in it.  Does not work in the scenario editor.

### 1.2.8. Map Sizes
(the values provided in the original RMSG are not correct)  
Scaling refers to map area, that is total number of tiles, not side length.
`set_scale_by_size` and `set_scale_by_groups` (for terrain and elevation) use a 100x100 = 10000 tiles reference map.
`set_scaling_to_map_size` (for objects) uses a 100x100 map as a reference. So that is number of objects x area ratio from the table below:

| Size    | Tiles on Sides | Total Tiles | Area ratio to 100x100 map |
|---------|----------------|-------------|---------------------------|
|Tiny     |120x120         |14400        |1.4                        |
|Small    |144x144         |20736        |2.1                        |
|Medium   |168x168         |28224        |2.8                        |
|Large    |200x200         |40000        |4.0                        |
|Huge     |220x220         |48400        |4.8                        |
|Gigantic |240x240         |57600        |5.8                        |
|LudiKRIS |480x480         |230400       |23.0                       |


## 1.3 General Syntax

These structures can be used anywhere in an RMS. Most of them allow a RMS to change at every game.

### 1.3.1. Comments
```rms
/* This is a comment. It's ignored by the game, but useful to people who read the RMS, especially yourself! */
```

- Comments can span on multiple lines
- Comments can be nested
- There must be space or new line between the asterisks and the words, otherwise the whole rest of your script may be ignored!
- WARNING: there is a bug where comments are NOT ignored, if they are within logical branches of conditionals and random code (see below) that aren't chosen. This may get fixed in future versions of the UserPatch, but it is best to avoid comments within conditionals and random code. Be especially careful about this when creating map packs!

### 1.3.2. Conditionals
```rms
if LABEL_1
(...)	/* commands executed only if LABEL_1 is defined */
elseif LABEL_2 	
(...)	/* commands executed only if LABEL_2 is defined */	  
elseif LABEL_3 	
(...)	/* commands executed only if LABEL_3 is defined */ 
else
(...)	/* commands executed only if none of the previous labels is defined */  
endif
```

Commands following an `if` statement (until next `elseif`/`else`/`endif`) are executed ONLY if respective `LABEL` is true.
E.g. Kings should be created only if game mode is Regicide.

- `elseif`s and `else` are optional:
    - `elseif` checks another condition, if previously checked conditions fail
    - `else` executes by default if none of the other conditions apply
- An if structure can control whole commands, but can also be used inside any { } brackets, to control attributes
- Whole if structures can be nested
- A "NOT" can be implemented this way:
```rms
if LABEL
else
(...)	/* this code is executed if LABEL is NOT true! */
endif
```

Here are the possible condition labels defined by the game.

- Game type:
    - `REGICIDE`
    - `DEATH_MATCH`
- Map dimension:
    - `TINY_MAP`
    - `SMALL_MAP`
    - `MEDIUM_MAP`
    - `LARGE_MAP`
    - `HUGE_MAP`
    - `GIGANTIC_MAP`
    - `LUDIKRIS_MAP`
- Starting resources:
    - `HIGH_RESOURCES`
    - `MEDIUM_RESOURCES`
    - `LOW_RESOURCES`
    - `DEFAULT_RESOURCES`
- Player positioning:
    - `FIXED_POSITIONS`: defined if the "Team Together" box is checked
- UP-only Definitions:
    - `RANDOM_MAP`: defined for Random Map games
    - `TURBO_RANDOM_MAP` defined for Turbo Random Map games
    - `KING_OT_HILL`: defined for King of the Hill games
    - `WONDER_RACE`: defined for Wonder Race games
    - `DEFEND_WONDER`: defined for Defend the Wonder games
    - `CAPTURE_RELICS`: defined for the Relics victory condition
    - `[1-8]_PLAYER_GAME`: defined as the total number of players (2_PLAYER_GAME, etc.)
    - `UP_AVAILABLE`: defined for v1.4 and later; used to detect the patch
- HD-only Definitions:
    - `CAPTURE_THE_RELIC`: defined for the new "capture the relic" mode

In addition, it is possible to use any of the Item Constants in conditionals. They will always be true if that constant is available in the game.  This can be used to implement conditional checks for mods or game versions. For example:

```rms
if BEGUINE /* this is a pre-defined constant in the Age of Chivalry mod */
create_object JAGUAR /* creates a Jaguar when you are using Age of Chivalry */
else
create_object WOLF /* otherwise creates a wolf */
endif
```

This technique CAN be used to distinguish between the basegame in the HD Edition and the DLC expansions, by checking for a predefined name from Rise of the Rajas only (not AoF or AK); for example:
```rms
if DLC_MANGROVEFOREST #define DLC_AVAILABLE endif
```

```rms
#define LABEL
```

Defines whatever label you want, to be used as an if condition. It will evaluate as true.

- Condition names can contain ANY character ("$%&òà" is a valid condition!!)
- Be careful when choosing a name that is already defined as a constant.  For example `#define DESERT` caused me problems; probably because `DESERT` is a preexisting terrain name.

### 1.3.3. Random Code
```rms
start_random
percent_chance %
(...)
percent_chance % 
(...)
end_random
```

Blocks of code following each percent_chance instruction have that percent probability at each game to be executed.
If percents don't add up to 100, the remaining percent is the chance that nothing happens.

- Random structures can control whole commands, but can also be used inside { } brackets, to control attributes
- Whole random structures can be nested
- You cannot use decimals (percent_chance 12.5 is NOT valid)

Example:

```rms
start_random
  percent_chance 30
      #define ARABIAN_MAP      /* map will be Arabian in 30% of games */
  percent_chance 20
      #define NORTHERN_MAP     /* map will be northern in 20% of games */
end_random                     /* map will be default (e.g. temperate) in remaining 50% of games */
```


## 1.4. Item Constants

`#const   NAME   N`  
Creates a constant name for a terrain or object type, suitable for commands such as create_terrain. 
Items are identified by a number inside the game, but by a name (such as `GRASS`) in a RMS; this command ties a practical name to an item number. Numbers are reported in Terrains & Objects chapter.

- Constant names can contain ANY character ("$%&kòà" is a valid name!!)
- Every item can have many names; original names remain valid
- You can't redefine an existing name to a different number

Many items already have a predefined name, but `#const` can be very useful because: 

- Some items, e.g. snowy road, don't have a predefined name
- You may want an alias for your convenience, e.g. in your language
- You can define variable items with a single if structure, instead of checking every time an item is used. 

In this example you would use only `GROUND` and `TREE` from now on:

```rms
If ARABIAN_MAP
	#const GROUND 14	/* desert */
	#const TREE 351	/* palm */
elseif NORTHERN_MAP
	#const GROUND 32	/* snow */
	#const TREE 413	/* snowy pine */
else
	#const GROUND 0	/* grass */
	#const TREE 411	/* oak */
endif

#const works only for terrain and object identifiers, not generic numbers. You CAN'T do this:
#const NUM 10
(...)
number_of_objects NUM
```
