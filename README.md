Adventure Prompt
================


Adventure Prompt is an interactive fiction authoring system with a twist. Two or three, even.

For players
-----------

Games come in files with the `.json` extension. (Beware, not all are made for Adventure Prompt!) You can open them with an interpreter called `promptrun.html` -- a single-page web app. It's also possible to find a game pre-bundled, but you can still use the top toolbar to open any other. In fact, the only difference between a save file and a brand-new game is that the former has a non-zero turn count and possibly score.

You play through a book-like interface with buttons you can click or tap. Most of the information you need is always visible on the screen.

For authors
-----------

To make your own adventures, you literally just have to fill in the blanks of a configuration file. Here's a small sample:

	[study]
	name = Wizard's study
	type = room
	description = Curtains dyed a leafy brown adorn the stone walls, 
	otherwise bare but for the furniture leaning against them: a large, 
	ornate writing desk near the window, a bed on the opposite side and, 
	facing the door, a little bookshelf. Peeking between two clouds, the 
	sun casts a patch of light on the fading carpet.
	success = Distant birdsong is more often than not covered by the 
	wind whistling outside the window, only to bring in the smell of 
	pine needles.

	[desk]
	name = writing desk
	type = scenery
	location = study
	description = It's all rickety now, and the lacquered wood has shed 
	its luster, but the chair is still comfy, and the many drawers open 
	easily. Curios from lands you've only heard of perch precariously 
	around the edges.

	[note]
	name = penned note
	type = thing
	location = desk
	description = A note penned with flowery letters on paper that's 
	only slightly yellow says, "I've been called away again. Hold the 
	fort until my return. Seriously, don't go anywhere! Read a book or 
	something if you get bored."

Most systems that promise not to require coding still have you juggle a myriad dropdowns and checkboxes that change depending on what you selected. It's coding in all but name. Adventure Prompt is more limited, but never looks more complicated than the above. And there's a surprising amount that can be done even so. As of March 2018, it supports rooms, exits, scenery/portals, inscriptions, portable items, vehicles, spells and actions, all of them able to appear and disappear, and constrain each other's behavior in various ways. All objects support the same properties, so there's less to remember. It's just that the meaning of a property depends on context.

Moreover, if you ever used a [MUSH][] or [MUCK][], and are acquainted with the online building commands, you can also use an interactive command-line editor that works in the same way. It's good for quickly inspecting and tweaking a game compiled from configuration files, or even a save file.

[MUSH]: https://en.wikipedia.org/wiki/MUSH
[MUCK]: https://en.wikipedia.org/wiki/TinyMUCK

Both the `advc.py` compiler and the editor, `advprompt.py`, are command-line programs written and tested in Python (3.3, though 2.7 should work). The editor contains most of the documentation, available through a live help system. It can also run in IDLE: open the file with Ctrl-O, then press F5 to run it as a module.

Bundling a game with the runner only possible with the compiler for now, or else manually.

For developers
--------------

Between the editor and runner sits the story file format, a simple and uniform database currently serialized as JSON, that encodes a variety of game behaviors implicitly. It should be possible to implement an undo function -- at least the back-and-forth kind -- in the same way restarting works.

Currently there are no provisions for localizations, but few messages are hardcoded, and most of them can be overridden in-game.
