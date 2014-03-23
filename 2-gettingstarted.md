template: lucid.haml
title: Getting started
---
---
#Getting started
###First steps: getting your security key and developer ID
You'll need to pass along a signature and a developer ID &ndash; or "devid" - with every request using HTTP GET.
To calculate the signature, you'll need the request, which includes your developer ID, and a key.
The key consists of a 128bit GUID.
  
The __key__ and the __request (including developer ID)__ are used to calculate a __signature__ for every request.





###How to register for a key and developer ID
* Send an email to APIKeyRequest@ptv.vic.gov.au with the following information in the subject line of the email:

> "PTV Timetable API &ndash; request for key"

* Once we've got your email request, we'll send you a key and a developer ID by return email.
  
> A high volume of requests may result in a delay in providing you with your key and developer ID. We'll try to get it to you as soon as we can.


* We'll also add your email address to our API mailing list so we can keep you informed about the API.
  
>The “APIKeyRequest” email address is only used to send you the key and developer ID and any relevant notifications. To provide feedback on the API check out our [Ed: ?].

>PTV does not provide technical support on the API.




###Privacy
Your email address is the only bit of information about you that PTV will hold in its register. You can view PTV's privacy policy at http://www.ptv.vic.gov.au/privacy.
