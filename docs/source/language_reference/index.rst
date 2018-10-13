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

.. include:: scheme_of_a_rms.rst
.. include:: commands.rst
.. include:: syntax.rst
