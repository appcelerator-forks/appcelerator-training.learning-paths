theme:appcelerator-training
tableclass:striped
progress:true

# Networking

Appcelerator SDK Fundamentals

---cover

# Networking

## Appcelerator SDK Fundamentals

--- 

# In this lesson, you will:

- Use the HTTPClient API to fetch remote data
- Explore how to upload and download files
- Work with JSON and XML data retrieved from the network
- Learn how to work with SOAP data

---section

# Making The Connection

---

# The XMLHTTPRequest Object
![img](/assets/images/slides/8/image6.png)

- In the web browser, Ajax requests rely on the XMLHTTPRequest object provided by the browser
- In Titanium the app is the client, everything else should be the same

---

# The HTTPClient Object
- ```Ti.Network.HTTPClient``` implements the XHR specification
- Low level HTTP client interface with support for most HTTP verbs
- Should be familiar to Ajax programmers

---

# A GET Network Request

```javascript
// index.jsvar xhr = Ti.Network.createHTTPClient(); 
xhr.onload = function() { 
  // do something with the response payload 
}; 
xhr.open('GET', 'http://example.com/endpoint'); 
xhr.send(); 
```

---

# A POST Network Request

```javascript
/network.jsvar xhr = Ti.Network.createHTTPClient(); 
xhr.onload = function() { 
     // do something with the response payload 
}; 
xhr.open('POST', 'http://example.com/endpoint'); 
// set HTTP headers here, if required 
xhr.send({myvariable: 'value'}); 
```

---

# Lifecycle Callbacks
- onload: function called when HTTP request returns (200 status code)
- onerror: function called when HTTP error received (404, 500, etc.)
- onreadystatechange:low-level handler for HTTP state
- onsendstream/ondatastream:file upload/download

---

# Return Data

```javascript
/network.jsvar xhr = Ti.Network.createHTTPClient(); 
xhr.onload = function() { 
     // this.responseText = returned data as text 
     // this.responseData = returned data as blob 
     // this.responseXML = returned data as XML object 
}; 
xhr.open('GET', 'http://example.com/endpoint'); 
xhr.send();
```

---

# Mobile Web Considerations
- Must consider cross-domain security issues — app is running in a browser
- Either set up CORS header support on your server
- Or, configure a proxy service

---section

# Data Transport Formats
---

# Working With JSON

- Recommended data transport format for Titanium Mobile - compact and efficient
- Super easy to serialize/rehydrate data
- JSON.parse() — convert string to JavaScript object
- JSON.stringify() - convert JavaScript object to string

```javascript
var character = { name: 'Thomas Anderson', nickname: 'Neo'}; 
var asJSON = JSON.stringify(character); 
var sameCharacter = JSON.parse(asJSON); 
```

---

# Working With XML

- XML DOM Level 2 API built in
- XML document by referring to this.responseXML
- XML related functions in the Ti.XML namespace
- More data over the wire, but still commonly used

---

# XML Example

```javascript
var RSS_URL = http://feeds.mashable.com/Mashable?format=xml
var xhr = Titanium.Network.createHTTPClient();
xhr.onload = function(e) {
    var xml = this.responseXML;
    var items = xml.documentElement.getElementsByTagName("item");
    var data=[];
    for (var i = 0; i < items.length; i++) {
        var item = items.item(i);
        data.push({
            title: getRssText(item, 'title'),
	 link: getRssText(item, 'link'),
	 pubDate: parseDate(getRssText(item, 'pubDate')),
        });
    }
}
xhr.open('GET', RSS_URL);
```

---

# A Few Words on SOAP
- 'Simple Object Access Protocol'- possibly the most ironic acronym in tech history
- At the end of the day, it is just a layer of abstraction over the top of XML and HTTP
- Plan A: Use a server-side proxy to return JSON
- Plan B: Use the Suds helper library (github.com/kwhinnery/Suds)
- Plan C: Manually construct SOAP envelopes

---

# Summary

In this lesson, you:

- Used the HTTPClient API to fetch remote data
- Explored how to upload and download files
- Worked with JSON and XML data retrieved from the network
- Learned how you could work with SOAP data

---section

# Questions?
