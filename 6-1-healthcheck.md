template: lucid.haml
title: Health Check
---
---
#Reference
##Health Check
###Version Number
2.0.0
###Description
A check on the timely availability, connectivity and reachability of the services that deliver security, caching and data to web clients.  A health status report is returned.
  
>It's good practice to call the Health Check API every time you make a sequence of calls to the API.


###Request URL
base URL
<code>/v2/healthcheck?timestamp=%@&devid=%@&signature=%@</code>

###Parameters

* timestamp        =        optional: the date and time of the request in ISO 8601 UTC format e.g. 2013-11-13T05:24:25Z
* devid        =        optional: the developer ID supplied in your email from PTV
* signature        =        optional: the customised message digest calculated using the method in the Quick start guide

>While all parameters for this API are optional, if you don't include them the <code>securityTokenOK</code> and <code>clientClockOK</code> response will return “false”.


###Response
The response is made up of the following JSON objects: 

* securityTokenOK        boolean &ndash; indicates whether your key is valid/signature is calculated correctly
* clientClockOK        boolean &ndash; indicates whether your clock is synchronised with our clock within 3 minutes
* memcacheOK        boolean &ndash; indicates status of the performance cache
* databaseOK        boolean &ndash; indicates availability of the data

>Refer to [?] for more information on using Health Check to trap errors.
  

Example request <a href="#fig-example-healthcheck"></a>
<div id="fig-example-healthcheck">
<h4>Example Health Check request</h4>
<code>http://timetableapi.ptv.vic.gov.au/v2/healthcheck?timestamp=2014-01-22T03:28:33Z</code>

<h4>Example Health Check response</h4>
<pre>
{
  "securityTokenOK": false,  
  "clientClockOK": false,   
  "memcacheOK": true,     
  "databaseOK": true,  
} 
</pre>
[Ed: Commentary on this response not included]
</div>