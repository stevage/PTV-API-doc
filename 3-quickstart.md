template: lucid.haml
title: Quick start guide
---
---
## Quick start guide
Once you have obtained your key and developer ID you can get started. The first thing you need to do is to calculate a signature.
###How to calculate a signature
* The signature value is a HMAC-SHA1 hash of the completed request (minus the base URL but including your developer ID, known as "devid") and the key:
   
    * signature        =        <code>crypto.HMACSHA1(request,key)</code>

> NOTE [Editor's addition]: "request" here is the URL from "/v2" onwards, and the signature must be converted to upper case.

* The calculation of a signature is based on a case-sensitive reading of the request message. This means that the request message used to calculate the signature must not be modified later on in your code or the signature will not work. If you do modify the case of the request message, you will need to calculate a new signature.

For example, "<code>http://timetableapi.ptv.vic.gov.au/v2/healthcheck?devid=ABCXYZ</code>" and "<code>http://timetableapi.ptv.vic.gov.au/v2/HealthCheck?devid=ABCXYZ</code>" require different signatures to be calculated; the same signature will not work for both requests.
* The signature itself is also case-sensitive

>Example of a request message for signature calculation:

> The request URL for the  API is:

><code>base URL/v2/nearme/latitude/%@/longitude/%@?devid=%@&signature=%@</code>

> A sample request message used to calculate a signature would be:
> <code>http://timetableapi.ptv.vic.gov.au/v2/nearme/latitude/-37.82392124423254/longitude/144.9462017431463?devid=0000001</code>



Refer to the Appendix for some sample code for calculating a signature.
### Performing the Health Check
The first API you need to call is the Health Check.
The Health Check will test a number of the key services that deliver the PTV Timetable API and let you know if there are any problems with connectivity, availability or reachability.
It will also test the time on your system to make sure that your clock is in sync with our clock.

The output is in the JSON format. <a href="#fig-healthcheck"></a>

Health Check request URL:
<code>http://timetableapi.ptv.vic.gov.au/v2/healthcheck?timestamp=%@&devid=%@&signature=%@</code>

><code>%@</code> in the request URL represents a parameter



<div id="fig-healthcheck">
<h4>Performing health check</h4>


<table>
<tr>
<th>Parameters</th></tr>
<tr>
<td>timestamp</td><td>optional: the date and time of the request in ISO 8601 UTC format e.g. 2014-02-28T05:24:25Z</td>
</tr><tr>
<td>devid</td><td>optional: the developer ID supplied in your email from PTV</td>
</tr><tr>
<td>signature</td><td>optional: the customised message digest calculated using the method in the Quick start guide</td>
</tr>
</table>  
<pre>

Response output:
{
  "securityTokenOK": boolean,
  "clientClockOK": boolean,
  "memcacheOK": boolean,
  "databaseOK": boolean,
}
</pre>
where a "true" value indicates service connectivity and availability, and "false" indicates a problem. For more information on this API, check out Errors and the Reference.
</div>
###Congratulations
Once you've calculated a signature and performed the health check successfully you are ready to access the timetable, line and stop data available through the PTV Timetable API.
All systems are go!