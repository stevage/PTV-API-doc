template: lucid.haml
title: Data Quality Statement
---
---
##Data Quality Statement
###Data Source: 
  PTV Timetable API


###Institutional Environment:
  Data Collector(s):  Data is created and collected by Victorian public transport train, tram and bus operators and by Public Transport Victoria.
###Collection authority:  
Public Transport Victoria
###Data Compiler(s):  
Public Transport Victoria (a government agency) compiles the data.
Additional information: Timetable data changes frequently (for example, over summer, or for planned works) and is updated on an as needs basis. Changes are advertised on the PTV website. As the data is accessed through an API, the data released is always up-to-date.

###Relevance:
####Data topic: 
The data collected is the public transport timetable for services in the state of Victoria (including Melbourne metropolitan services).
####Level of geography: 
The state of Victoria.
####Key Data Items: 
Timetable, station/stop locations, line/route paths, and myki ticket outlets.
####Additional information: 
The PTV Timetable API does not provide access to the PTV journey planner, the Yarra Trams TramTRACKER feed, nor the Google Geocoding API (used by PTV to search addresses).


###Timeliness:
####Data collected: 
The data is collected on an as needs basis and is compiled weekly for release.
Data available: The data is made accessible through the PTV Timetable API, its availability is current.
####Referenced Period: 
Approximately 14 days.
####Additional information: 
Public transport timetable, stop/station, route and line data changes frequently. In order to ensure you access the most up-to-date data, it is strongly recommended you use the API dynamically.


###Accuracy:
####Method of Collection: 
The data is collected both manually and through electronic file.
####Data Adjustments: 
The data contains interpolated times for stops on bus routes that are not timing points.
Collection size: All public transport services in the State of Victoria.
Additional information: The timetable data released is consistent with the data on the PTV website and through the PTV apps.


###Coherence
####Consistency over time: 
The data is consistent over time in that the same set of data (i.e. pertaining to services provided by public transport operators) is consistently collected and released.
####Consistency of jurisdictions: 
Unknown.
####Time series: 
There is not a consistent time series for this data. Timetable data changes frequently; PTV only keeps the current timetable data, it does not archive the old data once it has changed.


###Interpretability:
####Context: 
The PTV Timetable API gives the public access to raw public transport timetable data. It is not a journey planner service.


###Accessibility:
Additional information: PTV has also released other public transport data through the DataVic website: www.data.vic.gov.au.


  