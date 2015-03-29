# tintintoril
tintin classes for the toril mud

I have a very detailed map, but its only by request in game.
it was alot of work and fun to make, so I don't want to spoil the fun for others.

do a who @justmefjs to find me.

this is still a beta build.  Many changes may happen sporadically,
and there are refrences to files and methods that don't exist yet.
As those files are made stable they will appear here.
<pre>
recent changes

2015-03-29		streamlined some actions in mapping to reduce the number of match
					attempts.
					
					removed comma fix in spellout.tt and replaced with a per class
					match that will only rep the spells you can't cast with that class
					see the alias's at the end of that file for more information
					
					added var class <classname> to each class file and included the
					class files here.

----------------------------------------------------------------------------------

2015-03-27 		reduced the number of tokens in chat capture.  no real functional
					change, just faster response times for parsing.
					
					fixed prompt line matcher to work with psi and other classes 
					correctly.  YMMV if you use custom prompt setups.
					
					refined mapport.tt to match on right rooms, and made the mapping.tt
					load and unload it correctly only as needed.
					
					added spellout.tt to announce or not announce when effects expire
					putting a comma after the spell type will cause it to display but
					not be announced by the character in mud.

----------------------------------------------------------------------------------

2015-03-26 		refined regex for chat capture again.  should not cap room or other
					info where the com type isn't the second word on the line.  also
					got rid of lag in certain circumstances when ansi was involved.
					hopefully this is the last time I will have to visit this line of
					script.

-	made all map functions start with m<command> for ease of tracking and use

-	fixed various bug in the the chat capture that was triggering on all lines with
	ansi seems to be stable now
	
-	broke the undo actions for the mapper out to their own file to prevent unwieldy
	growth of the main mapper file and make it easier to find them when looking.

-	rearanged the locations of some of mapping commands so that mapport.tt could be
	turned off and on to reduce mapper latency and errors when walking through port
	rooms.

-	added a cond tracker/caller to general.tt control through tracker (on/off).
	will only trig on ph and above
</pre>