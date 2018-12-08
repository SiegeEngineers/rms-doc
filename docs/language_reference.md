Language Reference
==================

Scripts are divided in 7 sections, each one managing a category of map features. Sections start with the following tags::

	<PLAYER_SETUP>			Basic setup
	<LAND_GENERATION>		Main lands or seas
	<ELEVATION_GENERATION>		Hills
	<CLIFF_GENERATION>		Rocky cliffs
	<TERRAIN_GENERATION>		Terrain patches
	<CONNECTION_GENERATION>		Terrain bridges/roads
	<OBJECTS_GENERATION>		Units, buildings, resources, eye-candies

- You don't need to write sections in that order, however that's the order the game uses them.
- You might notice that in the standard maps they are in a different order with cliffs and connections (and sometimes elevation) at the end. However, it might be helpful to write them in the order above, because it makes it easier for you to visualize the map generation process and understand why things will happen; like terrain water on hills, objects on connections, or terrain avoiding cliffs. Ultimately the order in which you write the sections has no effect though. 
- Not all the sections are necessary (e.g. you may make a map without cliffs).
- Each section contains some types of instructions. Most instructions look like this::

	create_something WHAT
	{
	attribute TYPE
	attribute N
	set_attribute
	(...)
	}

- You can indent instructions however you want, just keep words separated by newlines or spaces.
- Scripts are case-sensitive, pay attention to capital letters.
- All "create" commands can be used multiple times in a RMS. Other commands can't.
- Most "attributes" (subcommands inside brackets) have a default and can be omitted. Some { } can be empty!
- Order of attributes inside brackets is not important.
- If an item can't be created for some reason, the game will simply ignore it and go on. If you see something is missing, try to relax some constraints on its placement.


Scheme of a RMS
---------------

Here's the skeleton of a script with all possible commands, useful for cutting & pasting. Everything is explained later.

- N means an integer number, possibly within a range. Decimals and negatives are not allowed.
- % means a percentage (0-100). Decimals are not allowed. Do not type the "%"!
- TYPE means a constant identifier such as GRASS. Types are reported in "Terrains & Objects" chapter.
  Nothing happens if you use a non-valid name (a type that doesn't exist).
- Commands work in all versions of the game unless specifically stated otherwise.
- / means that you should use either one or the other of these attributes, but not both.

```rms
<PLAYER_SETUP>
random_placement  /  grouped_by_team (requires UP/HD)
nomad_resources (requires UP/HD)

<LAND_GENERATION>

base_terrain TYPE

create_player_lands
{ 
	terrain_type TYPE
	land_percent %  /  number_of_tiles N
	base_size N  
	base_elevation N(1-7) (requires UP/HD)
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
	base_elevation N(1-7) (requires UP/HD) 
	left_border %,  right_border %,  top_border %,  bottom_border %
	land_position %(0-100) %(0-99) 
	border_fuzziness %
	clumping_factor %
	zone N  /  set_zone_randomly 
	other_zone_avoidance_distance N
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
	resource_delta -N (UP only; not HD)
}
```

Command Descriptions
--------------------

### create_player_lands {…}

Creates starting lands for ALL players. Usually there's one and only one create_player_lands statement.

- If you use create_player_lands more than once, each player will have multiple starting towns!
- Instead of create_player_lands you can use assign_to_player (see below)
- If you create no player lands at all, you can't place starting units and resources (only a Town Center and Villagers will be placed somewhere at random – not evenly spaced – so this is generally not recommended)

####    terrain_type TYPE


Type of terrain... Default is GRASS.

####    land_percent %  /  number_of_tiles N

Size of land. Use either land_percent or number_of_tiles. Default is 100%.
If total size of all lands exceeds the size of whole map, the game will try to reduce them fairly.

land_percent %
- Percent on whole map; scales with map size 
- For Player Lands, it's total size (shared among ALL players), so you better set a high % 

number_of_tiles N 
- It's a fixed size
- For Player Lands, it means the size of each player's land; about 1000 tiles should be ok.

####    base_size N  
####    base_elevation N(1-7) (requires UP/HD)
####    left_border %,  right_border %,  top_border %,  bottom_border %
####    border_fuzziness %
####    clumping_factor %
####    zone N  /  set_zone_randomly  /  set_zone_by_team  
####    other_zone_avoidance_distance N

General Syntax
--------------

These structures can be used anywhere in an RMS. Most of them allow a RMS to change at every game.
