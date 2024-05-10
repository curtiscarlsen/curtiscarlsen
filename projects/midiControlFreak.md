Turning my old midi controller (Behringer BCR2000) into a macro-pad for controlling computer

desc::a custom midiMacroPad

Use python and [[amidi]] (alsa command line midi interface) to handle midi commands from BCR2000 and use them to control browser and execute scripts

controls: 8 knobs with push functions, 16 push-buttons, 32(?) regular knobs

uses preset 3 configuration

python edited in pycharm: project name midiControlFreak

#project/software/ubuntu/general

#reference/software/python 
#reference/software/bash

[[managingBookmarksFromCommandLineinChrome 1]]


# use cases
* [[movie watching]]
	* show watchlist
	* open playlist bookmark folder
		* user can then drag and drop url to bookmark folder
	* trash current movie and move on to next
	* reserve current movie for watching with Lorri
		* add current movie to playlist bookmark folder
		* create new playlist bookmark folder
		* select existing playlist bookmark folder
* [[reference/Story Writing]]
* [[Research]]
	* open Obsidian
	* create Obsidian folder for new research/design project (different template/folder setup for each project type (pure research, software, electronics, cosplay,  physics, mechanical design?)
		* remember this as current project
		* set tags for the project?
	* Make existing project the current project (select from list)
	* start new note with title/filename for current project and set as focus in obsidian
		* set tags for the note

# code sequences


## to open bookmarks folder
* send win-left to current window (move to left side)
* send keys to chrome using [[xdotool]] :
	* ctrl+n 'chrome://bookmarks/...' \n  (customized for the actual bookmarks subfolder you want)

[[MOC - Software Projects]]