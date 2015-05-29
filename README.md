#Superseded!

A newer version of this documentation, prepared in Swagger and supporting API version 2.1.0, is available at okfnau.github.io/PTV-API-Swagger/dist/index.html

#About
This is an unofficial mirror of the official PTV Timetable API documentation, which is distributed as a downloadable 
Word document. Hopefully, a more readable version will get more people using it.

The HTML and CSS files are generated from .md and .sass files respectively. To build them:

<pre>
sudo apt-get install -y python-pip unzip nginx vim curl git
sudo pip install embellish

cd PTV-API-doc
embellish .
</pre>
