Scheme of a RMS
---------------

Here's the skeleton of a script with all possible commands, useful for cutting & pasting. Everything is explained later.

- N means an integer number, possibly within a range. Decimals and negatives are not allowed.
- % means a percentage (0-100). Decimals are not allowed. Do not type the "%"!
- TYPE means a constant identifier such as GRASS. Types are reported in "Terrains & Objects" chapter.
  Nothing happens if you use a non-valid name (a type that doesn't exist).
- Commands work in all versions of the game unless specifically stated otherwise.
- / means that you should use either one or the other of these attributes, but not both.

::
    
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
