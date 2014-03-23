template: lucid.haml
title: Search
---
---
## Search
###Version Number
2.0.0
###Description
The Search API returns all stops and lines that match the input search text.
###Request URL

<code>base URL
/v2/search/%@?&devid=%@&signature=%@</code>

###Parameters

* search        =        search text
e.g. "Alamein"
* devid        =        the developer ID supplied in your email from PTV
* signature        =        the customised message digest calculated using the method in the Quick start guide

###Response
Returns an array of JSON "result" objects for which the "type" equals either "stop" or "line".
A "stop" object or "line" object is embedded within each "result" depending on its type.
For more information on the data structures, check out the JSON object structure.

"stop" objects have these attributes: 
<a href="#fig-stop-values"></a>

* suburb
* transport_type
* stop_id
* location_name
* lat
* lon
* distance


"Line" objects have the following attributes:
<a href="#fig-line-values"></a>

* transport_type
* line_id
* line_name
* line_number
  

###Example use case
Janelle's next development for the tourist app is to add a search function that allows tourists to find any stations or stops, as well as any train lines, tram routes or bus routes, by inputting some text. She uses the Search API.

* Example search term: "Hoddle St"
* Example request <code>http://timetableapi.ptv.vic.gov.au/v2/search/Hoddle%20St?&devid=4&signature=93121A8B16A7158DB8169DBC405CF7405A05F2C0 </code>
* Example response <a href="#fig-exampleresponse-search"></a>

<div id="fig-exampleresponse-search">
  <h4>Example Search response</h4>
<pre>[
  {  
    "result": {  
      "suburb": "Richmond",  
      "transport_type": "bus",
      "stop_id": 12373,  
      "location_name": "Bridge Rd/Hoddle St ",
      "lat": -37.81719,
      "lon": 144.9902,
      "distance": 0.0
    },  
    "type": "stop"  
  },
  {
    "result": {
      "suburb": "Clifton Hill",
      "transport_type": "bus",
      "stop_id": 10285,
      "location_name": "Clifton Hill Railway Station/Hoddle St ",
      "lat": -37.7886963,
      "lon": 144.995071,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 12427,
      "location_name": "Gipps St/Hoddle St ",
      "lat": -37.80475,
      "lon": 144.992355,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "East Melbourne",
      "transport_type": "bus",
      "stop_id": 25376,
      "location_name": "Grey St/Hoddle St ",
      "lat": -37.81243,
      "lon": 144.990723,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Richmond",
      "transport_type": "nightrider",
      "stop_id": 24271,
      "location_name": "Hoddle St/Bridge Rd ",
      "lat": -37.81766,
      "lon": 144.990509,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Essendon",
      "transport_type": "bus",
      "stop_id": 24972,
      "location_name": "Hoddle St/Fletcher St ",
      "lat": -37.7557068,
      "lon": 144.923187,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Essendon",
      "transport_type": "tram",
      "stop_id": 2676,
      "location_name": "Hoddle St/Fletcher St #39 ",
      "lat": -37.7554665,
      "lon": 144.92276,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 12841,
      "location_name": "Hoddle St/Johnston St ",
      "lat": -37.7999763,
      "lon": 144.993561,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Collingwood",
      "transport_type": "bus",
      "stop_id": 13002,
      "location_name": "Hoddle St/Johnston St ",
      "lat": -37.79976,
      "lon": 144.992477,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Warrnambool",
      "transport_type": "bus",
      "stop_id": 31224,
      "location_name": "Hoddle St/Morriss Rd ",
      "lat": -38.36617,
      "lon": 142.46698,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Clifton Hill",
      "transport_type": "bus",
      "stop_id": 10869,
      "location_name": "Hoddle St/North Tce ",
      "lat": -37.79012,
      "lon": 144.994385,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Collingwood",
      "transport_type": "tram",
      "stop_id": 2472,
      "location_name": "Hoddle St/Victoria Pde #18 ",
      "lat": -37.8097343,
      "lon": 144.990967,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Richmond",
      "transport_type": "tram",
      "stop_id": 2471,
      "location_name": "Hoddle St/Victoria St #18 ",
      "lat": -37.80977,
      "lon": 144.991074,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 13952,
      "location_name": "Johnston St/Hoddle St ",
      "lat": -37.800415,
      "lon": 144.993057,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Collingwood",
      "transport_type": "bus",
      "stop_id": 25429,
      "location_name": "Johnston St/Hoddle St ",
      "lat": -37.7994537,
      "lon": 144.992889,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Collingwood",
      "transport_type": "bus",
      "stop_id": 20219,
      "location_name": "Keele St/Hoddle St ",
      "lat": -37.79744,
      "lon": 144.993317,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 12415,
      "location_name": "Langridge St/Hoddle St ",
      "lat": -37.8069649,
      "lon": 144.992,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Clifton Hill",
      "transport_type": "bus",
      "stop_id": 12460,
      "location_name": "Noone St/Hoddle St ",
      "lat": -37.79351,
      "lon": 144.994141,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Clifton Hill",
      "transport_type": "bus",
      "stop_id": 12471,
      "location_name": "North Tce/Hoddle St ",
      "lat": -37.79044,
      "lon": 144.994675,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Clifton Hill",
      "transport_type": "bus",
      "stop_id": 25440,
      "location_name": "Parslow St/Hoddle St ",
      "lat": -37.7932968,
      "lon": 144.99411,
      "distance": 0.0
    },
    "type": "stop"
  },
  {      
    "result": {
      "transport_type": "tram",
      "line_id": 5313,  
      "line_name": "Route 31 - Hoddle Street - Victoria Harbour Docklands",
      "line_number": "Route 31"
    },  
    "type": "line"  
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 12449,
      "location_name": "Truro St/Hoddle St ",
      "lat": -37.79768,
      "lon": 144993561,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Abbotsford",
      "transport_type": "bus",
      "stop_id": 12438,
      "location_name": "Vere St/Hoddle St ",
      "lat": -37.8028221,
      "lon": 144.9927,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Collingwood",
      "transport_type": "bus",
      "stop_id": 25418,
      "location_name": "Vere St/Hoddle St ",
      "lat": -37.80218,
      "lon": 144.992462,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "East Melbourne",
      "transport_type": "bus",
      "stop_id": 25387,
      "location_name": "Victoria Pde/Hoddle St ",
      "lat": -37.8105965,
      "lon": 144.9911,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Richmond",
      "transport_type": "bus",
      "stop_id": 12405,
      "location_name": "Victoria Pde/Hoddle St ",
      "lat": -37.8103256,
      "lon": 144.991333,
      "distance": 00
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "East Melbourne",
      "transport_type": "bus",
      "stop_id": 25361,
      "location_name": "Wellington Pde/Hoddle St ",
      "lat": -37.8172722,
      "lon": 144.989822,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Richmond",
      "transport_type": "bus",
      "stop_id": 12384,
      "location_name": "West Richmond Railway Station/Hoddle St ",
      "lat": -37.81497,
      "lon": 144.9905,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "East Melbourne",
      "transport_type": "bus",
      "stop_id": 25365,
      "location_name": "West Richmond Railway Station/Hoddle St ",
      "lat": -37.8149567,
      "lon": 144.990265,
      "distance": 0.0
    },
    "type": "stop"
  },
  {
    "result": {
      "suburb": "Richmond",
      "transport_type": "bus",
      "stop_id": 12394,
      "location_name": "York St/Hoddle St ",
      "lat": -37.8127022,
      "lon": 144.990967,
      "distance": 0.0
    },
    "type": "stop"
  }
]</pre></div>