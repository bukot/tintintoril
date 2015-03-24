# tintintoril
tintin classes for the toril mud

I have a very detailed map, but its only by request in game.
it was alot of work and fun to make, so I don't want to spoil the fun for others.

do a who @justmefjs to find me.

this is still a beta build.  Many changes may happen sporadically,
and there are refrences to files and methods that don't exist yet.
As those files are made stable they will appear here.

recent changes

-	made all map functions start with m<command> for ease of tracking and use

-	fixed various bug in the the chat capture that was triggering on all lines with ansi
	seems to be stable now
	
-	broke the undo actions for the mapper out to their own file to prevent unwieldy growth
	of the main mapper file and make it easier to find them when looking.

-	rearanged the locations of some of mapping commands so that mapport.tt could be turned
	off and on to reduce mapper latency and errors when walking through port rooms.

-	added a cond tracker/caller to general.tt control through tracker (on/off).
	will only trig on ph and above