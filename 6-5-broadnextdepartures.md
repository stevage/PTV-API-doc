template: lucid.haml
title: Broad Next Departures
---
---
##Broad Next Departures
###Version Number
2.0.0
###Description
Broad Next Departures returns the next departure times at a prescribed stop irrespective of the line and direction of the service.
For example, if the stop is Camberwell Station, Broad Next Departures will return the times for all three lines (Belgrave, Lilydale and Alamein) running in both directions (towards the city and away from the city). 

###Request URL

base URL
<code>/v2/mode/%@/stop/%@/departures/by-destination/limit/%@?devid=%@&signature=%@</code>

###Parameters

* mode        =        a number representing the transport_type of the stop, defined as follows:
  * 0        Train (metropolitan)
  * 1        Tram
  * 2        Bus (metropolitan and regional, but not V/Line) 
  * 3        V/Line train and coach
  * 4        NightRider 

e.g. "2"
stop        =        the stop_id of the stop
e.g. "1108"
limit        =        the number of next departure times to be returned, i.e. "5" will return the next five departure times (notes: "0" will return departures for the entire day; "1" will limit it to the very next departure, even if this is a few days away)
e.g. 2
devid        =        the developer ID supplied in your email from PTV
signature        =        the customised message digest calculated using the method in the Quick start guide
Response
Returns a collection of JSON timetable "values" that have a "platform" and "run" object embedded within them.
The "platform" objects have a "stop" and "direction" object in them, and the "direction" object has a "line" object within it.
For more information on the data structures, check out the JSON object structure.


Timetable "values" have the following attributes:

* time_timetable_utc        date and time expressed in ISO 8601 UTC format &ndash; the scheduled time of the service at the stop &ndash; e.g. "2013-11-18T03:21:00Z"
* time_realtime_utc        date and time expressed in ISO 8601 UTC format &ndash; a place holder for the real-time of the service at the stop (for potential future implementation; as no real-time feeds are provided at this time, this returns "null") &ndash; e.g. "null"
* flags        Character &ndash; a stop may have zero or more flags associated with it,  delimited by a "-" character; examples include:

* RR = Reservations Required
* GC = Guaranteed Connection
* DOO = Drop Off Only
* PUO = Pick Up Only
* MO = Mondays only
* TU = Tuesdays only
* WE = Wednesdays only
* TH = Thursdays only
* FR = Fridays only
* SS = School days only

note: ignore "E" flag

&ndash; e.g. "RR-PUO"


"run" objects have the following attributes:
transport_type        string
&ndash; the mode of transport serviced by the stop
&ndash; e.g. can be either "train", "tram", "bus", "vline" or "nightrider"
run_id        numeric string
&ndash; the unique identifier of each run
&ndash; e.g. "1464"
num_skipped        integer
&ndash; the number of stops skipped for the run, applicable to train; a number greater than zero indicates either a limited express or express service
&ndash; e.g. 0
destination_id        numeric string
&ndash; the stop_id of the destination, i.e. the last stop for the run
&ndash; e.g. "1044"
destination_name        string
&ndash; the location_name of the destination, i.e. the last stop for the run
&ndash; e.g. "Craigieburn"


"platform" objects have the following attributes:
realtime_id        string
&ndash; a place holder for the stop's real-time feed system ID (for potential future implementation; as no real-time feeds are provided at this time, this returns "0")
&ndash; e.g. "0"


"stop" objects have these attributes: 
suburb        string
&ndash; the suburb name
&ndash; e.g. "Belgrave"
transport_type        string
&ndash; the mode of transport serviced by the stop
&ndash; e.g. can be either "train", "tram", "bus", "V/Line" or "NightRider"
stop_id        numeric string
&ndash; the unique identifier of each stop
&ndash; e.g. "1234"
location_name        string
&ndash; the name of the stop based on a concise geographic description
&ndash; e.g. "20-Barkly Square/115 Sydney Rd (Brunswick)"
lat        decimal number
&ndash; geographic coordinate of latitude
&ndash; e.g. -37.82005
lon        decimal number
&ndash; geographic coordinate of longitude
&ndash; e.g. 144.95047
distance        decimal number
&ndash;returns zero in the context of this API


"direction" objects have the following attributes:
linedir_id        numeric string
&ndash; unique identifier of a particular line and direction
&ndash; e.g. "21"
direction_id        numeric string
&ndash; unique identifier of a direction (e.g. "0" signifies "city")
&ndash; e.g. "0"
direction_name        string
&ndash; name of the direction of the service
&ndash; e.g. "City (Flinders Street)"


"line" objects have these attributes: 
transport_type        string
&ndash; the mode of transport serviced by the line
&ndash; e.g. can be either "train", "tram", "bus", "V/Line" or "NightRider"
line_id        numeric string
&ndash; the unique identifier of each line
&ndash; e.g. "1818"
line_name        string
&ndash; the name of the line
&ndash; e.g. "970 - City - Frankston - Mornington - Rosebud via Nepean Highway & Frankston Station "
line_number        string
&ndash; the line number that is presented to the public (i.e. not the "line_id")
&ndash; e.g. "970"
 

###Example use case
Janelle has decided to add some timetable information to the tourist app. The next development lets tourists see the next departure times for any of the stations or stops that the tourist selects from a map or list.
Janelle uses the Broad Next Departures API to show the departure times for stops found via any of the three methods available (Stops Nearby, Transport POIs by Map or Search).

* Example stop selected: Jolimont - MCG Train Station (stop_id: 1104)
* Example request
<code>http://timetableapi.ptv.vic.gov.au/v2/mode/0/stop/1104/departures/by-destination/limit/1?devid=4&signature=2BEBBA8A77A24452DEC040F849906EBE4F10DA7D</code>
* Example response <a href="#fig-exampleresponse-broad"></a>

<div id="fig-exampleresponse-broad">
  <pre>
{    
  "values": [  
    {
      "platform": {  
        "realtime_id": 0,
        "stop": {  
          "suburb": "East Melbourne",
          "transport_type": "train",
          "stop_id": 1104,
          "location_name": "Jolimont-MCG",
          "lat": -37.81653,
          "lon": 144.9841,
          "distance": 0.0  
        },
        "direction": {  
          "linedir_id": 41,   
          "direction_id": 8,
          "direction_name": "Hurstbridge",  
          "line": {  
            "transport_type": "train",  
            "line_id": 8,
            "line_name": "Hurstbridge",
            "line_number": "Hurstbridge"
          }
        }
      },
      "run": {  
        "transport_type": "train",  
        "run_id": 21172,
        "num_skipped": 0,
        "destination_id": 1041,
        "destination_name": "Clifton Hill"
      },
      "time_timetable_utc": "2014-01-20T03:21:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "East Melbourne",
          "transport_type": "train",
          "stop_id": 1104,
          "location_name": "Jolimont-MCG",
          "lat": -37.81653,
          "lon": 144.9841,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 38,
          "direction_id": 5,
          "direction_name": "South Morang",
          "line": {
            "transport_type": "train",
            "line_id": 5,
            "line_name": "South Morang",
            "line_number": "South Morang"
          }
        }
      },
      "run": {
        "transport_type": "train",
        "run_id": 13975,
        "num_skipped": 0,
        "destination_id": 1224,
        "destination_name": "South Morang"
      },
      "time_timetable_utc": "2014-01-20T03:21:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "East Melbourne",
          "transport_type": "train",
          "stop_id": 1104,
          "location_name": "Jolimont-MCG",
          "lat": -37.81653,
          "lon": 144.9841,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 26,
          "direction_id": 0,
          "direction_name": "City (Flinders Street)",
          "line": {
            "transport_type": "train",
            "line_id": 8,
            "line_name": "Hurstbridge",
            "line_number": "Hurstbridge"
          }
        }
      },
      "run": {
        "transport_type": "train",
        "run_id": 21045,
        "num_skipped": 0,
        "destination_id": 1155,
        "destination_name": "Parliament"
      },
      "time_timetable_utc": "2014-01-20T03:23:00Z",
      "time_realtime_utc": null,
      "flags": ""
    }
  ]
}
</pre>
</div>