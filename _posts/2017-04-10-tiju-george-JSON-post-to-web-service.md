---
layout: post
title: "Tiju George, Post JSON data to Web Service"
date: 2017-04-10
---


##Python-Post JSON data to the endpoint that is expecting a JSON

Recently I had to send an application to a company and they were expecting to submit the applition through API. I was wondering how to send it through Python. After few searches, found an article<sup>1</sup> 

The code to post JSON data using urllib2 in python
```python
import json
import urllib
import urllib2

url = "http://company_server/welcome"
values = {'name' : 'Tiju George',
'email' : 'tiju.m.george@gmail.com'}

req = urllib2.Request(url, json.dumps(values), headers={'Content-type': 'application/json', 'Accept': 'application/json'})
response = urllib2.urlopen(req)
the_page = response.read()
print the_page
```

1: Reference:
https://varunver.wordpress.com/2013/05/20/python-post-json-data-curl-equivalent-in-python-using-urllib2/
