OO, AI/ML Python Challenge
==========================

If I have the travel connection network:

![Connection Network][graph1]

The numbers against each link represent the effort it takes to move between the locations at each end of the link. You can think of this as a distance or a time, or just as a number that indicates some combination of such factors which affects the journey between two places. The exact values are nor particularly important for this exercise, but have been chosen to give slightly differing total lengths for the routes between Fleet and Basingstoke.  
(The links are shown going in one direction, but (for now, at least) assume that you can move along them in either direction. That is, the connection between Fleet and Hook is shown, but it is also allowed to travel from Hook to Fleet)

<!--
strict digraph {
	Fleet
	Hook
	Basingstoke
	Guildford

	Fleet -> Hook [length=2]
	Fleet -> Guildford [length=3]
	Hook -> Basingstoke [length=1]
	Guildford -> Basingstoke [length=1]
}
-->

How could I represent this data as Objects in Python?

Hint: There are _locations_ which are _linked_ to each other. What information does a location have? What does a link have?  

What functions might I need to determine a route from one place to another (even if not directly connected?)

The Drunkard's Walk
-------------------

One simplistic method for determining a route between two places (such as Fleet and Basingstoke - where we need to go via either Hook or Guildford) is called the Drunkard's Walk.

We can imagine a party-goer sitting in a bar in Fleet, hearing of a not-to-be-missed party going on in Basingstoke. He's already had a few beers, and is having difficulty making out the destinations on the train platforms, so just hops onto the next available train. He gets off at the next platform, checks if it's Basingstoke. If it's not, he hops onto the next available train, and repeats until he finally arrives at the party - or is so exhausted he decides to lie down on the station bench and go to sleep.

To translate this into something we might be able to code: start at the origin location, choose a route to another location at random. Traverse that route (so now the 'current' location becomes the end of the link between the two locations). If that is the target location, then record the trip from start to end as a valid route and exit. If not, choose another link from the current location at random, and repeat until we find our destination (It may even be a good idea to code the termination of the search by exhaustion by selecting a suitable number of hops to attempt before exiting with no valid route found.)

Once you've coded this, run it a few times on the network above, and see how wildly the path length varies (when successful), and how often it just gives up. 

Then, add a third in-between node. e.g.:

![Third node added][graph2]

<!--
strict digraph {
	Fleet
	Hook
	Basingstoke
	Guildford
	Reading

	Fleet -> Hook [length=2]
	Fleet -> Guildford [length=3]
	Hook -> Basingstoke [length=1]
	Guildford -> Basingstoke [length=1]
	Fleet -> Reading [length=4]
	Basingstoke -> Reading [length=1]
}
-->

Does your code cope with this? If not, why not - is it because you need a better way to represent the data, or have you made assumptions in your code about the "shape" of the data, perhaps?

[graph1]: graph1.png
[graph2]: graph2.png
