template: lucid.haml
title: Broad Next Departures
---
---
##Specific Next Departures
###Version Number
2.0.0
###Description
Specific Next Departures returns the times for the next departures at a prescribed stop for a specific mode, line and direction.
For example, if the stop is Camberwell Station, Specific Next Departures returns only the times for one line running in one direction (for example, the Belgrave line running towards the city).
  
###Request URL

base URL
<code>/v2/mode/%@/line/%@/stop/%@/directionid/%@/departures/all/limit/%@?for_utc=%@
&devid=%@&signature=%@</code>

###Parameters

*mode        =        a number representing the transport_type of the stop, defined as follows:
* 0        Train (metropolitan)
* 1        Tram
* 2        Bus (metropolitan and regional, but not V/Line) 
* 3        V/Line train and coach
* 4        NightRider 

e.g. "0"
line        =        the line_id of the requested services
e.g. "3"
stop        =        the stop_id of the stop
e.g. "1108"
directionid        =        the direction_id of the requested services
e.g. "0"
limit        =        the number of next departure times to be returned, i.e. "5" will return the next five departure times (notes: "0" will return departures for the entire day; "1" will limit it to the very next departure, even if this is a few days away)
e.g. 2
for_utc        =        optional: the date and time of the request in ISO 8601 UTC format
e.g. 2013-11-13T07:08:03Z
devid        =        the developer ID supplied in your email from PTV
signature        =        the customised message digest calculated using the method in the Quick start guide

###Response
Returns a collection of JSON timetable "values" that have a "platform" and "run" object embedded within them.
The "platform" objects have a "stop" and "direction" object in them, and the "direction" object has a "line" object within it.
For more information on the data structures, check out the JSON object structure.


####Timetable "values" have the following attributes:
<a href="#fig-timetable-values"></a>:

* time_table_utc
* time_realtime_utc
* flags

"run" objects have the following attributes:
<a href="#fig-run-values"></a>

* transport_type
* run_id
* num_skipped
* destination_id
* destination_name


"platform" objects have the following attributes:
<a href="#fig-platform-values"></a>

* realtime_id


"stop" objects have these attributes: 
<a href="#fig-stop-values"></a>

* suburb
* transport_type
* stop_id
* location_name
* lat
* lon
* distance


"direction" objects have the following attributes:
<a href="#fig-direction-values"></a>

* linedir_id
* direction_id
* direction_name


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
Janelle's next enhancement for the tourist app is to let tourists choose which departure times they see for any given stop, by selecting the line and direction.
This will mean that if a stop or station has multiple routes or lines stopping there (for example, Flinders Street Station), the tourist won't be bombarded with a confusing list of departure times for multiple lines.
Building on the other APIs, Janelle uses the Specific Next Departures API to do this.

* Example selection: Jolimont-MCG Train Station towards Hurstbridge
* Example request
<code>http://timetableapi.ptv.vic.gov.au/v2/mode/0/line/8/stop/1104/directionid/8/departures/all/limit/5?for_utc=2014-01-20T03:18:08Z&devid=4&signature=2BEBB8A77A24452FAF110FD849906EBE4F10DC7B</code>
* Example response <a href="#fig-exampleresponsespecific"></a>
<div id="fig-exampleresponsespecific">
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
        "run_id": 21173,
        "num_skipped": 0,
        "destination_id": 1062,
        "destination_name": "Eltham"
      },
      "time_timetable_utc": "2014-01-20T03:31:00Z",
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
        "run_id": 21174,
        "num_skipped": 0,
        "destination_id": 1041,
        "destination_name": "Clifton Hill"
      },
      "time_timetable_utc": "2014-01-20T03:41:00Z",
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
        "run_id": 21175,
        "num_skipped": 0,
        "destination_id": 1100,
        "destination_name": "Hurstbridge"
      },
      "time_timetable_utc": "2014-01-20T03:51:00Z",
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
        "run_id": 21176,
        "num_skipped": 0,
        "destination_id": 1041,
        "destination_name": "Clifton Hill"
      },
      "time_timetable_utc": "2014-01-20T04:01:00Z",
      "time_realtime_utc": null,
      "flags": ""
    }
  ]
}
</pre>
</div>