template: lucid.haml
title: FAQs
---
---
##FAQs
####Q.  What does the PTV Timetable API do?

A.  The PTV Timetable API provides a way to directly and dynamically access the most up-to-date stop, line and timetable data held by PTV. By creating an API we are increasing the opportunities for developers to take our data and re-use it in innovative way.

####Q.  Who is the PTV Timetable API for?
A.  Our API is for everyone who wants to take our data and re-use it in a web or smartphone app.

####Q.  Can I use the API to download all the timetable data?

A.  The API is not designed to download all the timetable data at once. It works most effectively when used dynamically within an app as that is the way to guarantee you're always accessing &ndash; and providing &ndash; the most up-to-date data. If you want to use the API to get a dump of all of the data, please contact us.

####Q.  Some of the timetable results I get using the API are different to those the PTV journey planner provides &ndash; why?

A.  The PTV journey planner is coded with a number of business rules that reflect public transport operational requirements. This can include noting which multi-modal services are guaranteed connections, for example, or requiring passengers to board a regional train half an hour before it is due to leave.
The API accesses raw timetable data, not journey planner results. Your timetable results will reflect the actual timetable.

####Q.  Is the timetable data available in a GTFS format?

A.  Timetable data is not available in GTFS format. The operational needs of our business dictate the format of our data and the methods to access it. This is why the API we're releasing is the same as the API that we use for our own online products.

####Q.  What programming languages can I use with the API?

A.  The PTV Timetable API can work with all programming languages. Because it is a programming language agnostic interface, as long as the language you are using supports HTTP protocols, you can use our API.

####Q.  Is real-time data available?
A.  PTV gets real-time data for trams through Yarra Trams' TramTRACKER system. Contact Yarra Trams to find out more.
There are currently no real-time data feeds for trains and buses.