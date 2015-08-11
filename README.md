[[TOP]]
= Roads, Nodes and Automobiles =
:neo4j-version: 2.0.0
:author: Jacqui Read
:twitter: @tekiegirl
:tags: domain:community, model:transport:navigation:satnav

== or 'How a sat-nav could use a graph database'

'''

=== My talk on this gist is available to watch online at SkillsMatter http://bit.ly/neo4jrna

*Coming Up*

* <<L1, Inspiration>>
* <<L2, Data>>
** <<L2-1, Sources>>
* <<L3, Model>>
** <<L3-1, Graph Population>>
** <<L3-2, Graph Visualisation>>
* <<L4, Applications>>
** <<L4-1, Simple Navigation>>
** <<L4-2, Complex Navigation>>
* <<L6, Console>>

'''

[[L1]]
== Inspiration
Navigation has nothing to do with my day job, but I regularly use satellite navigation. This gist has been inspired by Waze, a satellite navigation system, which allows users to edit the maps. It is easy to see a graph in the structure of the map, but how could it work?

I decided to create a gist that could model a map and possible ways in which the data stored could be queried to allow someone to navigate that map. The area to be mapped will be restricted for the purposes of simplicity and the capabilities of the gist processing.

To this end, this gist will create a representation of part of the M3 and M25 motorways (in the UK) and some of the connected towns.

[[L2]]
== Data
There are many sources of data on the internet for a range of gist applications. It is worth looking at various sources to see which fits your requirements the best, or combine different sources. It is possible to import data from sources such as csv files with various available tools. Rik Van Bruggen's blog (http://blog.bruggen.com/) is a good source for tutorials on how to do this.

[[L2-1]]
=== Sources <<TOP, ^Top^>>
I originally started out using Wikipedia and Google Maps as my data sources, but then discovered that the editable Waze map had the distance information I needed, which I had previously been guestimating from Wikipedia and Google Maps combined.

With regard to speed data it seems that Waze do not store this, or do not make it available to users. I have used a combination of informed guesses (M roads are typically 3 lanes and 70mph) and Google Maps Streetview, to look at speed signs, and enter the data into my road relationships.

Waze may also calculate the speed by using users' covered distance and time, or they may not use it and just estimate time from past data collected from users.

* Google Maps https://goo.gl/maps/5Kmhx
* Waze https://www.waze.com/editor/
* M3 data on Wikipedia http://en.wikipedia.org/wiki/M3_motorway_(Great_Britain)

[[L3]]
== Model
++++
<div class="paragraph">
<p><span class="image"><img src="https://dl.dropboxusercontent.com/u/2900504/model%201.png" alt="Navigation Graph Model"></span></p>
</div>
++++

To begin with the model was fairly simple, with Locations and Junctions represented as nodes and the roads as relationships, but this evolved over time into Junctions being represented as a series of Exits and Entrances connected by roads.
