template: lucid.haml
title: Introduction
sort_key: 1
---
---
# Introduction
## Important!
This document is a reformatted, somewhat edited, and __currently incomplete__ unofficial version of the PTV API. It is maintained by <a href="http://stevebennett.me">Steve Bennett</a>, who has no relationship with PTV.  You can access the official PTV Timetable API <a href="https://www.data.vic.gov.au/raw_data/ptv-timetable-api/6056">at data.vic.gov.au</a>, or view it in <a href="https://github.com/stevage/PTV-API-doc/blob/gh-pages/PTV_Timetable_API.pdf?raw=true">PDF format</a>. This web template is Embellish/<a href="https://github.com/boscoh/supplescroll">SuppleScroll</a> by Bosco Ho.

*Source: Licensed from Public Transport Victoria under a Creative Commons Attribution 3.0 Australia Licence.*

### Hello and welcome
Hi and welcome to the PTV Timetable API. The API has been created to provide public transport timetable data to the public in the most dynamic and efficient way.
By providing an API, rather than an enormous data file or database, PTV hopes to maximise both the opportunities for re-use of public transport data and the potential for innovation.
### Licence
Ownership of intellectual property rights in this publication
Unless otherwise noted, copyright (and any other intellectual property rights, if any) in this publication is owned by Public Transport Victoria (referred to below as PTV).
### Creative Commons licence
This publication is licensed under a Creative Commons Attribution 3.0 Australia Licence. 
Creative Commons Attribution 3.0 Australia Licence is a standard form licence agreement that allows you to copy, distribute, transmit and adapt this publication provided that you attribute the work. A summary of the licence terms is available from http://creativecommons.org/licenses/by/3.0/au/deed.en. The full licence terms are available from http://creativecommons.org/licenses/by/3.0/au/legalcode.
PTV requests that you attribute this publication (and any material sourced from it) using the following wording: Source: Licensed from Public Transport Victoria under a Creative Commons Attribution 3.0 Australia Licence. 
### Disclaimer
####Don't use our IP
You may use PTV's data as permitted by the above licence, but you are not permitted to use PTV's intellectual property (including copyright, registered and unregistered trade marks) for any other purpose. 
####Don't pretend to be us
When you use PTV's data, don't pretend to be PTV or claim that PTV has endorsed your product or service.

[Editor's note: A reminder that the version of the document you are reading is *not* from PTV, and this copy is not endorsed by PTV. You can access the official PTV Timetable API <a href="https://www.data.vic.gov.au/raw_data/ptv-timetable-api/6056">at data.vic.gov.au</a>.]

####Your use is your responsibility
The data provided to you by PTV is provided 'as is' and PTV is not liable for how you use this data, how third parties use or rely on this data or any errors contained within the data. You are responsible for determining whether the data is suitable for your particular usage and purposes.

###What you get with the PTV Timetable API
Our API gives you direct access to the PTV timetable data. The API allows you to query locations for timetable, line and stop data for all train, tram and bus, V/Line rail and coach, and NightRider services. It also includes access to myki ticket outlet data.

> In this document, "stop" means any train station, tram stop or bus stop. For more information, check out the [Ed: ?].



The data will be updated weekly to take into account any planned timetable changes, for example, due to holidays or planned disruptions. (Any changes to the timetable notified by public transport operators on the day of operation will not be picked up.)

> PTV timetable data consists of the scheduled timetable. It is __not__ real-time data nor service disruption information.


The PTV timetable API is the same API currently used by PTV for our website and smartphone apps. PTV enhances these products by integrating its timetable data with TramTracker data, the Google geocoding API (which allows for address searching) and PTV's own journey planner service.

> The following are __not included __ in the PTV Timetable API:

> * TramTracker data - this is available through [Ed: ?]

> * An address geocoding API - available through search providers such as [Ed: ?]

>  * The PTV journey planner - this is not raw data but rather a service PTV provides







###Do's and don'ts
Timetables, stops, lines and even ticket outlets change frequently so to get the most out of the PTV Timetable API, we recommend you use it dynamically. That's the only way to ensure you're accessing the most up-to-date data and providing it to your audience through the app or service you create.


> Do use the API dynamically to get the most up-to-date data for your audience.

> Do not cache the data. If you want a dump of timetable data for a specific point in time, [Ed: ?].

> Do not hammer our servers. Do not use the API to make multiple requests for large sets of data in short periods of time.




###Audience
The PTV Timetable API is for everyone. All members of the public, whether they are students, hobbyist app developers or companies, can access PTV timetable data using our API.
PTV assumes that you know how to use APIs and do not provide instructions on how to code in any specific programming languages.

> PTV __does not provide technical support__ for the API.> All information required to use the API is included in this document.
