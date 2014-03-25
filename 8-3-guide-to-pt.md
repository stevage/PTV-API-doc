template: lucid.haml
title: Guide to understanding PT data
---
---
##Guide to understanding public transport data
  

This part of the document is designed to give you a crash course in public transport data concepts and terms relevant to the API. It's not meant to be a comprehensive guide to all public transport data in the known universe.
We want to help you understand the data that is returned through the API so you can get the most out of it.
We've created a fictional town called Somewhere (diagram 1) to help illustrate some of the key concepts.


  



Public transport is easy to understand, right? There's trains, trams and buses, some routes, a timetable, some stations and stops...it's all pretty simple stuff, right?
Well, yes. And also no.
Public transport seems pretty simple on the surface, but the data that underpins it is a very complex beast. You see, there's public transport data, and then there's how it's presented to the public. A lot of effort goes into making public transport 'nice' for the public!
Let's start with the concept of a stop. In our data, a stop can be a tram stop, a bus stop, a bus bay at a shopping centre or junction, or a train station.
So all of the bus stops and the train stations in Somewhere (diagram 2) would be returned as stops.


  
 
You can identify what kind of stop it is through the transport_type attribute. These can be train, tram, bus, V/Line train and coach, or NightRider.
All stops have a unique identifier (stop_id attribute) and also a location name. Location names describe as concisely as possible the physical location of the stop.
For train stations, the location name is the name of the station &ndash; for example, "Somewhere Station".
For tram and bus stops, location names are determined by a hierarchy of available stop information. The hierarchy is:
Landmark > Cross Street > Travel Street
where Travel Street is the street the vehicle is travelling on, and Cross Street is a street that intersects, or crosses, it.
Depending on the content of those fields in our database, the location name can be Landmark_Travel Street, or Cross Street_Travel Street, or just Travel Street, together with the suburb. Tram stop location names also include a stop number at the start (which is the number that appears on the signage at the stop or in the timetable; not the same as the "stop_id").
Diagram 3 shows the bus stop location names in Somewhere.


  



On a map, a stop may appear to be a single point on a road (tram or bus) or building (train). When you zoom in, however, you will notice that it may in fact be made up of several separate stops, each with its own unique stop ID.


  



Stops and retail ticket outlets make up public transport points of interest (POIs). Ticket outlet POIs also have a location name, as well as a business name. The town of Somewhere has two ticket outlet POIs and 6 stop POIs (diagram 4).


  



Next let's look at routes. The public knows train services by the name of the line (for example, "Alamein line"), and tram and bus routes by a number, or a name. For example, the Route 112 tram or the Ballarat-Bendigo coach.
In public transport data, however, each route is made up of multiple route variations, which are the geographic paths that a vehicle takes under the name of a route. Each route variation or path is made up of a sequence of stops in a particular order (and a path may pass the same stop more than once).
There can be different paths at different times of day, in different directions or when a vehicle (usually a bus) deviates to a school or shopping centre.
A collection of route variations or paths make up a line. Mostly lines run in two directions, however they sometimes run in a loop. In our data a line can be any of the following transport type: train, tram, bus, V/Line rail and coach, or NightRider.
In Somewhere, the Route 007 bus is a line made up of two paths (diagram 5).


  



The sequence of stops that a vehicle actually stops at on a path for any particular trip (also known as a service or run) is known as a stopping pattern. For example, a vehicle may stop at all stops on a particular path, or it may travel express and skip some stops on the path.
A timetable overlays times onto the movement of a vehicle on a particular run. The times take into account the path that the vehicle takes, as well as the stopping pattern.
Variations are explained through the use of flags. A flag might indicate that a particular stopping pattern or path is taken on school days only, for example, or only on a particular day of the week. It can also indicate that reservations are required for a service or that the service is drop off or pick up only at a particular stop.
The Route 007 bus that runs from Somewhere Shopping Centre to Somewhere Station has two paths and three stopping patterns. These are indicated in the timetable for that route (diagram 6).


  



We hope you now understand the main timetable data concepts a little better, to help you get the most out of our API.