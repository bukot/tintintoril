# tintintoril
tintin classes for the toril mud

I have a very detailed map, but its only by request in game.
it was alot of work and fun to make, so I don't want to spoil the fun for others.

do a who @justmefjs to find me.

this is still a beta build.  Many changes may happen sporadically,
and there are refrences to files and methods that don't exist yet.
As those files are made stable they will appear here.
<pre>
post release full refresh
               after creating a release I refreshed all the files in my git.
               I found that several files were not updating propperly, and felt
               this was the best way to make sure all files were up to date and
               as ready to be used as possible.
2015-08-27
               in mapping.tt
                    {mdrag set} now accepts only a comma seperated list of items
                    to be dragged.
                    
                    fixed bugs with drag and escape following
                    
                    added alias for .(speedwalkdirs)  it will only process simple
                    dirs newsud and numbers for counts.  the map will follow along
                    with the speedwalk. ie: .2nuses3d would send n;n;u;s;e;s;d;d;d


----------------------------------------------------------------------------------
2015-05-11
               in mapping.tt
                    added alias {mdrag} to allow the map to follow you when you
                    are dragging corpses.  released in a partial push
                    
                    changed {mdrag} to work with a stored string for easier drags
                    
                    added {mdrag set} to create the string used by mdrag.  for now
                    enter the string as drag targ for singles or 
                    drag targ drag targ... for chain dragging.


----------------------------------------------------------------------------------
2015-05-06
               in mapmistake.tt
                    adapted wall error triggers to not undo when map is in static
                    mode.
                    
               in mapping.tt
                    added alias {mmove} as shortcut to #map move
                    
                    added alias {mpath} as a shortcut to #map find to allow for
                    visible paths on the map easier
                    
                    added map updates to all functions that change the map 
                    in a visible way.
                    
                    mavoid will now accept an optional room num or name
               
               in general.tt
                    minor change to {logon &lt;string&gt;} to prevent erroneous sends to
                    the mud
                    
                    fixed chat trigger to catch a red shape messages correctly
                    
                    added alias {alpha} to facilitate some advanced features to
                    come.
                    
                    fixed infinite loop error with tloot alias
                    
               in combat.tt
                    documented it, and cleaned up the targeting features.
                    
               in classset.tt
                    now makes the name set to $me lowercase and tries to load
                    a file for that character incase we have character specific
                    info.


----------------------------------------------------------------------------------
2015-04-13
               in general.tt
                    rearranged the order that the chat grab trigger executes
                    to allow for easy removal of speech sequences by people
                    who don't want a mud reader.
               
                    fixed bug with {tloot} alias
               
                    converted various aliases in to regex for more predictable 
                    matching
                    
                    made map go to static mode on load by default
                    
                    added loottype &lt;word&gt; &lt;a&gt; to get all or coins, or what ever
                    you want to specify.  &lt;a&gt; is optional and will get all.&lt;word&gt;
                    if omitted will just get &lt;word&gt; or 1.&lt;word&gt;
                    
                    tloot now reports looter to mud and locally tells you what
                    you are looting
                    
                    added mapdir and ttdir variables to hold the path to file
                    locations and incorporated them into all save and read
                    aliases
                    
               in combat.tt
                    revamped alias t&lt;digit&gt; for targeting to work better and
                    report via local says

               in rogue.tt
                    changed app alias to app &lt;wep&gt; &lt;poison&gt; if poison is
                    omitted it will default to the last poison used.  if no other
                    poison was used previously throws an error.
                    
                    fixed poison blind action to be an action INSTEAD OF AN ALIAS
                    
                    fixed autogar alias so it will report status when param is
                    omitted.
               
               in mapping.tt (i know i thought i was done with it too)
                    changed mapunload to unloadmap and added the optional 
                    parameter n if n is specified the map WONT be saved before 
                    being destroyed. this will allow you to revert to a previous
                    version of the map easily.
                    
                    changed mapupdate to mupdate to normalize commands contained
                    in this file
                    
                    added mstatic &lt;on|off&gt; alias to prevent some mapping mishaps
                    have not worked on mapmistake.tt to take static mode into 
                    account yet.  use static mode with caution!
                    
                    added nn param to mfind to search both notes and name
                    
               in mapport.tt
                    changed portto to use portnoact instead of duplicating the
                    functionality


----------------------------------------------------------------------------------


2015-04-06     fixed matching in res alias cleric.tt var %1 to %2.  Was
               preventing res alias from working at all.  Usage stayed the same
               internal fix only
               
               fixed issue with asst alias in combat.tt logic was not set
               correctly when last update was done.  Usage stayed the same
               internal fix only.
               
               made mset second param testing more stringent to prevent triggering
               on malformed entries.  Sligtly more complex matcthing, but more
               predictible actions when used.  Usage stayed the same internal fix
               only.
               
               renamed savemap to msave in mapping.tt
               
               moved #event &#123;session disconnect&#125; from mapping.tt to general.tt
               and made it save the map contingent on $mapping being true
               
               other structural and processing changes to mapping.tt to prevent
               unintended usage or activation, but no other changes to commands.

----------------------------------------------------------------------------------


2015-04-03     in the process of adding a comment to the begining of each file,
               and making sure any persistant vars are declared in the class file
               that declares them.  this will make resetting classes easier as
               all values will be reset with the class instead of having to hunt
               them down individually or restarting tintin.

               reorganized mapping.tt
                    combined msetname and msetnote into one alias mset that takes
                    an arguement mset &#60;command&#62; &#60;value&#62; it uses regex so the
                    space between mset and the command is optional for backwards
                    compatability also it will match the abreviated arguement or 
                    the whole word mset no, msetno, msetnote, and msetnote are
                    all the same thing this will make it easier to add other map
                    features as needed
                    
                    mmakeport now more robust
                         mmakeport &#60;en|open|jump|...&#62; &#60;portalname&#62; &#60;room to link&#62;
                         this will add a non standard exit to a room as a one way
                         link.
                         it also has to be used at both ends of the portal for
                         two way links.
                         remember that common portal types (portal, well, hole)
                         will need to have both endpoints added to mapport to
                         avoid breaking the mapper.
                    
                    added mportloc to allow for fast port locations to the file
                    for now this does a simple location add and more complex locs
                    will still require direct file addition.  it expects the full
                    room name as the arguement.
                    
                    mapunload now correctly removes the map name from the variable
                    
                    added bank as an option in mcolor and made setting a room to
                    default white easier by allowing mcolor to be called with out
                    arguements
                    
               working on striping general.tt down as far as possible to make 
               branching this project as easy as possible.  more files, but more
               flexibility too.

----------------------------------------------------------------------------------

2015-03-29     streamlined some actions in mapping to reduce the number of match
               attempts.
					
               removed comma fix in spellout.tt and replaced with a per class					
               match that will only rep the spells you can't cast with that class					
               see the alias's at the end of that file for more information
						
               added var class &#60;classname&#62; to each class file and included the					
               class files here.

----------------------------------------------------------------------------------

2015-03-27     reduced the number of tokens in chat capture.  no real functional					
               change, just faster response times for parsing.
										
               fixed prompt line matcher to work with psi and other classes 					
               correctly.  YMMV if you use custom prompt setups.
					
               refined mapport.tt to match on right rooms, and made the mapping.tt					
               load and unload it correctly only as needed.
					
               added spellout.tt to announce or not announce when effects expire					
               putting a comma after the spell type will cause it to display but					
               not be announced by the character in mud.

----------------------------------------------------------------------------------

2015-03-26     refined regex for chat capture again.  should not cap room or other					
               info where the com type isn't the second word on the line.  also					
               got rid of lag in certain circumstances when ansi was involved.					
               hopefully this is the last time I will have to visit this line of					
               script.

-	made all map functions start with m&#60;command&#62; for ease of tracking and use

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
