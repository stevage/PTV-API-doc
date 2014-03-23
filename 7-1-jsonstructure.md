template: lucid.haml
title: JSON object structure
---
---
##JSON object structure
The diagrams below show the structure of the JSON objects returned from the API calls.

Stop data is returned through three different pathways: as a stop object, as part of a “locations” object, and as a type of “result” object.

Line data is returned through two pathways: as a “line” object and as a type of “result” object.

Timetable data is returned through “value” objects.

  
###"result" objects
These are returned through the Stops Nearby and Search APIs. The data structure looks like this:


"result" object
  

#### "stop" object:
suburb
transport_type
stop_id
location_name
lat
lon
distance
type = "stop"
  
####"line" object:
transport_type
line_id
line_name
line_number
type = "line"

### "locations" objects
These are returned through the Transport POIs by Map API. The data structure looks like this:

"locations" object

* suburb
* location_name
* lat
* lon
* distance
  
"stop" object

* transport_type
* stop_id
  
"outlet" object

* outlet_type
* business_name
  

####"values" objects
These are returned via the three APIs which return timetable data: Broad Next Departures, Stopping Pattern and Specific Next Departures. The data structure looks like this:


* "values" object
* "platform"
* "run"
* time_timetable_utc
* time_realtime_utc
* flags
    
  

"run" object
  "platform" object
  transport_type
run_id
num_skipped
destination_id
destination_name
  

  realtime_id
"stop"
"direction"
    
  

"stop" object
  

  "direction" object
  suburb
transport_type
stop_id
location_name
lat
lon
distance
  

  linedir_id
direction_id
direction_name
"line"
    

"line" object
  transport_type  
line_id
line_name
line_number