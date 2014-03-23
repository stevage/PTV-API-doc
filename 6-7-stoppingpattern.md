template: lucid.haml
title: Broad Next Departures
---
---
##Stopping Pattern
###Version Number
2.0.0
###Description
The Stopping Pattern API returns the stopping pattern for a specific run (i.e. transport service) from a prescribed stop at a prescribed time. The stopping pattern is comprised of timetable values ordered by stopping order.
###Request URL

base URL
<code>/v2/mode/%@/run/%@/stop/%@/stopping-pattern?for_utc=%@&devid=%@&signature=%@</code>

###Parameters

* mode        =        a number representing the transport_type of the stop, defined as follows:

    * 0        Train (metropolitan)
    * 1        Tram
    * 2        Bus (metropolitan and regional, but not V/Line) 
    * 3        V/Line train and coach
    * 4        NightRider 

    e.g. "2"

* run        =        the run_id of the requested run

    e.g. "1464"

* stop        =        the stop_id of the stop

    e.g. "1108"

* for_utc        =        the date and time of the request in ISO 8601 UTC format e.g. 2013-11-13T05:24:25Z

* devid        =        the developer ID supplied in your email from PTV

* signature        =        the customised message digest calculated using the method in the Quick start guide

###Response
Returns a collection of JSON timetable "values" that have a "platform" and "run" object embedded within them.
The "platform" objects have a "stop" and "direction" object in them, and the "direction" object has a "line" object within it.
  

For more information on the data structures, check out the JSON object structure.


Timetable "values" have the following attributes<a href="#fig-timetable-values"></a>:

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


"Line" objects have the following attributes:
<a href="#fig-line-values"></a>

* transport_type
* line_id
* line_name
* line_number  


###Example use case
Next Janelle wants to enhance her tourist app so it can show a basic timetable for any of the departure times selected by tourists (i.e. returned through Broad Next Departures). She uses the Stopping Pattern API to do this.

* Example selection: 2:31pm service departing Jolimont-MCG Train Station on the Hurstbridge Line towards Eltham
* Example request
<code>http://timetableapi.ptv.vic.gov.au/v2/mode/0/run/21173/stop/1104/stopping-pattern?for_utc=2014-01-20T03:18:08Z&devid=4&signature=2CACC8A77A24452DEC110FD948906EBE4F10DC7B</code>
* Example response <a href="#fig-exampleresponse-stopping"></a>

<div id="fig-exampleresponse-stopping">
  <h4>Example Stopping Pattern response</h4>
  <pre>
{                            
  "values": [
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Melbourne City",
          "transport_type": "train",
          "stop_id": 1071,
          "location_name": "Flinders Street",
          "lat": -37.81831,
          "lon": 144.966965,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:19:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Melbourne City",
          "transport_type": "train",
          "stop_id": 1181,
          "location_name": "Southern Cross",
          "lat": -37.8183327,
          "lon": 144.95253,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:22:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Melbourne City",
          "transport_type": "train",
          "stop_id": 1068,
          "location_name": "Flagstaff",
          "lat": -37.8119774,
          "lon": 144.955658,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:24:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Melbourne City",
          "transport_type": "train",
          "stop_id": 1120,
          "location_name": "Melbourne Central",
          "lat": -37.8099365,
          "lon": 144.9626,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:26:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Melbourne City",
          "transport_type": "train",
          "stop_id": 1155,
          "location_name": "Parliament",
          "lat": -37.8110542,
          "lon": 144.9729,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:28:00Z",
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
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:31:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Richmond",
          "transport_type": "train",
          "stop_id": 1207,
          "location_name": "West Richmond",
          "lat": -37.8149452,
          "lon": 144.991425,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:32:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Richmond",
          "transport_type": "train",
          "stop_id": 1145,
          "location_name": "North Richmond",
          "lat": -37.8103943,
          "lon": 144.9925,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:34:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Abbotsford",
          "transport_type": "train",
          "stop_id": 1043,
          "location_name": "Collingwood",
          "lat": -37.8045235,
          "lon": 144.993744,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:35:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Abbotsford",
          "transport_type": "train",
          "stop_id": 1201,
          "location_name": "Victoria Park",
          "lat": -37.7991562,
          "lon": 144.994446,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:37:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Clifton Hill",
          "transport_type": "train",
          "stop_id": 1041,
          "location_name": "Clifton Hill",
          "lat": -37.7886543,
          "lon": 144.995422,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:39:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Northcote",
          "transport_type": "train",
          "stop_id": 1209,
          "location_name": "Westgarth",
          "lat": -37.7806168,
          "lon": 144.999237,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:41:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Northcote",
          "transport_type": "train",
          "stop_id": 1053,
          "location_name": "Dennis",
          "lat": -37.7791824,
          "lon": 145.00824,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:43:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Fairfield",
          "transport_type": "train",
          "stop_id": 1065,
          "location_name": "Fairfield",
          "lat": -37.7791748,
          "lon": 145.0169,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:44:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Alphington",
          "transport_type": "train",
          "stop_id": 1004,
          "location_name": "Alphington",
          "lat": -37.7783966,
          "lon": 145.03125,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:46:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Ivanhoe",
          "transport_type": "train",
          "stop_id": 1050,
          "location_name": "Darebin",
          "lat": -37.7749634,
          "lon": 145.038483,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:48:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Ivanhoe",
          "transport_type": "train",
          "stop_id": 1101,
          "location_name": "Ivanhoe",
          "lat": -37.768898,
          "lon": 145.045425,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:50:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Eaglemont",
          "transport_type": "train",
          "stop_id": 1056,
          "location_name": "Eaglemont",
          "lat": -37.7635841,
          "lon": 145.05394,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:51:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Heidelberg",
          "transport_type": "train",
          "stop_id": 1093,
          "location_name": "Heidelberg",
          "lat": -37.7570763,
          "lon": 145.060684,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:53:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Rosanna",
          "transport_type": "train",
          "stop_id": 1168,
          "location_name": "Rosanna",
          "lat": -37.7428741,
          "lon": 145.066147,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:56:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Macleod",
          "transport_type": "train",
          "stop_id": 1117,
          "location_name": "Macleod",
          "lat": -37.72601,
          "lon": 145.069153,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T03:59:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Watsonia",
          "transport_type": "train",
          "stop_id": 1203,
          "location_name": "Watsonia",
          "lat": -37.7109528,
          "lon": 145.0838,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T04:02:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Greensborough",
          "transport_type": "train",
          "stop_id": 1084,
          "location_name": "Greensborough",
          "lat": -37.70395,
          "lon": 145.108246,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T04:08:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Montmorency",
          "transport_type": "train",
          "stop_id": 1130,
          "location_name": "Montmorency",
          "lat": -37.7152977,
          "lon": 145.1215,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T04:11:00Z",
      "time_realtime_utc": null,
      "flags": ""
    },
    {
      "platform": {
        "realtime_id": 0,
        "stop": {
          "suburb": "Eltham",
          "transport_type": "train",
          "stop_id": 1062,
          "location_name": "Eltham",
          "lat": -37.71355,
          "lon": 145.147827,
          "distance": 0.0
        },
        "direction": {
          "linedir_id": 0,
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
        "destination_id": 0,
        "destination_name": ""
      },
      "time_timetable_utc": "2014-01-20T04:15:00Z",
      "time_realtime_utc": null,
      "flags": "E"
    }
  ]
}
</pre>
</div>