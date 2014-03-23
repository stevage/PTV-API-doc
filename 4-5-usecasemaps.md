template: lucid.haml
title: Use case maps
---
---
##Use case maps
To give you a taste of what you can do with the PTV Timetable API, we've created a small list of use case maps that show the sequence of APIs required to obtain particular information.

[Editor: The following is a text representation of the diagrams which were included in the <a href="https://www.data.vic.gov.au/raw_data/ptv-timetable-api/6056">Word version of this document</a>.]

###I want to...

#### see all bus stops near me on a map or list

1. __Health Check__
2. __Stops Nearby__

#### ...get the next three departure times for a specific service from a selected stop

1. __Health Check__
2. __Search__ or __Stops Nearby__ or __Transport POIs by Map__ => transport_type
3. __Broad Next Departures__ => transport_type, stop_id, line_id
4. __Specific Next Departures__

#### ...find out what lines travel through a stop near me and where they go

1. __Health Check__ 
2. __Stops Nearby__ => transport_type, stop_id
3. __Broad Next Departures__ => transport_type
4. __Stops on a Line__

#### ...get the next ten departures from my local stop

1. __Health Check__
2. __Search__ or __Stops Nearby__ or __Transport POIs by Map__ => transport_type
3. __Broad Next Departures__

#### ...find myki ticket outlets in my area

1. __Health Check__
2. Transport POIs by Map

#### ...see on a map which bus stops are near my local train station

1. __Health Check__
2. Transport POIs by Map    