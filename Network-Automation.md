# Network Automation
any process that is self-driven, that reduces and potentially eliminates, the need for human intervention.

## Data Formats
Hypertext Markup Language (HTML)
JavaScript Object Notation (JSON)
eXtensible Markup Language (XML)
YAML Ain’t Markup Language (YAML)

JSON Format
{
	"message": "success",
	"timestamp": 1560789260,
	"iss_position": {
		"latitude": "25.9990",
		"longitude": "-132.6992"
	}
}
YAML Format
message: success
timestamp: 1560789260
iss_position:
    latitude: '25.9990'
    longitude: '-132.6992'
XML Format

<-?xml version="1.0" encoding="UTF-8" ?>
<-root>
  <message>success</message>
  <timestamp>1560789260</timestamp>
  <iss_position>
    <latitude>25.9990</latitude>
    <longitude>-132.6992</longitude>
  </iss_position>
</-root>

## JSON Syntax Rules
These are some of the characteristics of JSON:

It uses a hierarchical structure and contains nested values.
It uses braces { } to hold objects and square brackets [ ] hold arrays.
Its data is written as key/value pairs.
In JSON, the data known as an object is one or more key/value pairs enclosed in braces { }. The syntax for a JSON object includes:

Keys must be strings within double quotation marks " ".
Values must be a valid JSON data type (string, number, array, Boolean, null, or another object).
Keys and values are separated by a colon.
Multiple key/value pairs within an object are separated by commas.
Whitespace is not significant.
At times a key may contain more than one value. This is known as an array. An array in JSON is an ordered list of values. Characteristics of arrays in JSON include:

The key followed by a colon and a list of values enclosed in square brackets [ ].
The array is an ordered list of values.
The array can contain multiple value types including a string, number, Boolean, object or another array inside the array.
Each value in the array is separated by a comma.
For example, a list of IPv4 addresses might look like the following output. The key is “addresses”. Each item in the list is a separate object, separated by braces { }. The objects are two key/value pairs: an IPv4 address (“ip”) and a subnet mask (“netmask”) separated by a comma. The array of objects in the list is also separated by a comma following the closing brace for each object.


***the characteristic of YAML include:***

It is like JSON and is considered a superset of JSON.
It has a minimalist format making it easy to both read and write.
It uses indentation to define its structure, without the use of brackets or commas.

***characteristics of XML include:***

It is like HTML , which is the standardized markup language for creating web pages and web applications.
It is self-descriptive. It encloses data within a related set of tags: <-tag>data</-tag>
Unlike HTML, XML uses no predefined tags or document structure.


## API
An API is software that allows other applications to access its data or services. It is a set of rules describing how one application can interact with another, and the instructions to allow the interaction to occur.

### Types
- Open APIs or Public APIs - These APIs are publicly available and can be used with no restrictions.
- Internal or Private APIs - These are APIs that are used by an organization or company to access data and services for internal use only.
- Partner APIs - These are APIs that are used between a company and its business partners or contractors to facilitate business between them.

### Web Service APIs
- Simple Object Access Protocol (SOAP)
- Representational State Transfer (REST)
- eXtensible Markup Language-Remote Procedure Call (XML-RPC)
- JavaScript Object Notation-Remote Procedure Call (JSON-RPC)

## REST and RESTful APIs
