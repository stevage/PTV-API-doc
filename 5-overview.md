template: lucid.haml
title: Overview
---
---
#Overview
##Main features
####Stateless
Public transport timetable data is fast-changing, time-based data so our API is REST-like (and therefore stateless).
####Format
The API functions via a request and response format whereby parameters are passed in a request and a response with the relevant data received accordingly.
####Output
The responses you receive from the API will be represented in JSON. The format is that of a JSON object with a name for each attribute. 
For more information on JSON, see http://www.json.org/ 
####Authentication
A unique key and developer ID is used to calculate a signature for every request that you make.
For more information about how to get a key and developer ID and how to calculate a signature, check out the Getting Started section.
####DateTime and time zone
All DateTimes are stored and reported in UTC. The ISO8601 format (e.g. 2011-09-13T16:09:54Z) is used throughout the API. The DateTimes are returned as strings since JSON does not have a DateTime object in the specification.
####Versioning
The PTV Timetable API uses semantic versioning.
The current version of the API is 2.0.0 but the URL only includes the relevant part of the version number (in this case, the major part).
##Structure
The PTV Timetable API is structured to allow you to build information dynamically as you need it, based on the output of each API called.
For example, the Stops Nearby API requires inputs that are not specific to public transport (i.e. latitude and longitude coordinates). The output, however, includes stop_id and transport_type data. You can then pass that data through the Broad Next Departures API to obtain line_id, direction_id, run_id and timetable data. You can then use these outputs as inputs into other APIs.
The table <a href="#fig-inputsoutputs"></a> summarises the relevant subset of inputs and outputs of each API.
<div id="fig-inputsoutputs">
    <h4>Inputs and outputs</h4>
<table>
<tbody><tr>
<th>API</th>
<th>Inputs</th>
<th>Outputs include</th>
</tr>
<tr>
<td>Stops Nearby</td>
<td>lat / lon, signature</td>
<td>transport_type, stop_id, lat / lon</td>
</tr>
<tr>
<td>Transport POIs by Map</td>
<td>transport_type, lat / lon, grid depth, limit, signature</td>
<td>transport_type, stop_id, lat / lon</td>
</tr>
<tr>
<td>Search</td>
<td>search term, signature</td>
<td>transport_type, stop_id, lat / lon, line_id</td>
</tr>
<tr>
<td>Broad Next Departures</td>
<td>transport_type, stop_id, limit, signature</td>
<td>transport_type, stop_id, lat / lon, line_id, direction_id, run_id, timetable time</td>
</tr>
<tr>
<td>Specific Next Departures</td>
<td>transport_type, line_id, stop_id, direction_id, limit, for_utc, signature</td>
<td>transport_type, stop_id, lat / lon, line_id, direction_id, run_id, timetable time</td>
</tr>
<tr>
<td>Stopping Pattern</td>
<td>transport_type, run_id, stop_id, for_utc, signature</td>
<td>transport_type, stop_id, lat / lon, line_id, direction_id, run_id, timetable time</td>
</tr>
<tr>
<td>Stops on a Line</td>
<td>transport_type, line_id, signature</td>
<td>transport_type, stop_id, lat / lon</td>
</tr>
</tbody></table>    
</div>

> For a __full list__ of the relevant parameters and output data for each API, check out the section [?].

##Interface
You access the PTV Timetable API through an HTTP interface, as follows:

<code>base URL / version number / API name / query string</code>

The base URL is <code>http://timetableapi.ptv.vic.gov.au</code>

The version number, API name and query string are provided in the Reference section, under each API.

> <code>%@</code> in the request URL represents a parameter.
  

##Errors
####Error trapping through Health Check
Calling the Health Check API at the start of each sequence of APIs flushes out any system problems.
A return of true or false for the following attributes reveals their status (where "true" means the system is okay, and "false" reveals a problem):

* <code>securityTokenOK</code> &ndash; i.e. your key/signature is working
  (if it returns "false" check your logic and ensure you have a valid key)
* <code>clientClockOK</code> &ndash; i.e. your clock is synchronised with our clock within three minutes
(this is for your information only; if it returns "false" it may affect the way you present dates and times)
* <code>memcacheOK</code> &ndash; performance cache is working well
(if it returns "false" your queries will be slow)
* <code>databaseOK</code> &ndash; availability of the data
(if it returns "false" your queries won't work)

For more information on the Health Check API, check out the Quick start guide and the Reference section.
HTTP status codes

Since the PTV Timetable API uses a HTTP interface, any of the following standard HTTP status codes may be returned:

*   <code>200</code> &ndash; no error; system okay
*   <code>403</code> &ndash; access denied (will be returned when the wrong signature is used)
*   <code>404</code> &ndash; requested resource not found (check your URL, including parameters, is correct)
*   <code>500</code> &ndash; internal server error (check your URL, including parameters, is correct)

For more information, see <a href="http://en.wikipedia.org/wiki/List_of_HTTP_status_codes">Wikipedia</a>.

