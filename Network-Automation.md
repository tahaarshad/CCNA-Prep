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
Conforming to the constraints of the REST architecture is generally referred to as being “RESTful”. An API can be considered “RESTful” if it has the following features:

Client-Server - The client handles the front end and the server handles the back end. Either can be replaced independently of the other.
Stateless - No client data is stored on the server between requests. The session state is stored on the client.
Cacheable - Clients can cache responses to improve performance.

A RESTful web service is implemented using HTTP. It is a collection of resources with four defined aspects:

The base Uniform Resource Identifier (URI) for the web service, such as http://example.com/resources.
The data format supported by the web service. This is often JSON, YAML, or XML but could be any other data format that is a valid hypertext standard.
The set of operations supported by the web service using HTTP methods.
The API must be hypertext driven.
RESTful APIs use common HTTP methods including POST, GET, PUT, PATCH and DELETE. As shown in the following table, these correspond to RESTful operations: Create, Read, Update, and Delete (or CRUD).


### URI
A URI is a string of characters that identifies a specific network resource. As shown in the figure, a URI has two specializations:

Uniform Resource Name (URN) - identifies only the namespace of the resource (web page, document, image, etc.) without reference to the protocol.
Uniform Resource Locator (URL) - defines the network location of a specific resource on the network. HTTP or HTTPS URLs are typically used with web browsers. Other protocols such as FTP, SFTP, SSH, and others can use a URL. A URL using SFTP might look like: sftp://sftp.example.com.
These are the parts of a URI, as shown in the figure:

Protocol/scheme – HTTPS or other protocols such as FTP, SFTP, mailto, and NNTP
Hostname - www.example.com
Path and file name - /author/book.html
Fragment - #page155


These are the different parts of the API request:

API Server - This is the URL for the server that answers REST requests. In this example it is the MapQuest API server.
Resources - Specifies the API that is being requested. In this example it is the MapQuest directions API.
Query - Specifies the data format and information the client is requesting from the API service. Queries can include:
Format – This is usually JSON but can be YAML or XML. In this example JSON is requested.
Key - The key is for authorization, if required. MapQuest requires a key for their directions API. In the above URI, you would need to replace “KEY” with a valid key to submit a valid request.
Parameters - Parameters are used to send information pertaining to the request. In this example, the query parameters include information about the directions that the API needs so it knows what directions to return: "from=San+Jose,Ca" and "to=Monterey,Ca".



***API applications***
- Developer Web Site
- Postman
- Python
- Network Operating Systems - NETCONF (NET CONFiguration), RESTCONF


## COnfiguration Management Tools
Simple Network Management Protocol (SNMP) was developed to allow administrators to manage nodes such as servers, workstations, routers, switches, and security appliances, on an IP network. Using a network management station (NMS), shown in the following figure, SNMP enables network administrators to monitor and manage network performance, find and solve network problems, and perform queries for statistics. SNMP works reasonably well for device monitoring. However, it is not typically used for configuration due to security concerns and difficulty in implementation. Although SNMP is widely available, it cannot serve as an automation tool for today’s networks.

You can also use APIs to automate the deployment and management of network resources. Instead of the network administrator manually configuring ports, access lists, quality of service (QoS), and load balancing policies, they can use tools to automate configurations. These tools hook into network APIs to automate routine network provisioning tasks, enabling the administrator to select and deploy the network services they need. This can significantly reduce many repetitive and mundane tasks to free up time for network administrators to work on more important things.


Configuration management tools make use of RESTful API requests to automate tasks and can scale across thousands of devices. Configuration management tools maintain the characteristics of a system, or network, for consistency. These are some characteristics of the network that administrators benefit from automating:

Software and version control
Device attributes such as names, addressing, and security
Protocol configurations
ACL configurations

Configuration management tools typically include automation and orchestration. Automation is when a tool automatically performs a task on a system. This might be configuring an interface or deploying a VLAN. Orchestration is the process of how all these automated activities need to happen, such as the order in which they must be done, what must be completed before another task is begun, etc. Orchestration is the arranging of the automated tasks that results in a coordinate process or workflow.

There are several tools available to make configuration management easier:

Ansible
Chef
Puppet
SaltStack


| Characteristic            | Ansible            | Chef         | Puppet        | SaltStack     |
|---------------------------|--------------------|--------------|---------------|---------------|
| What programming language?| Python + YAML      | Ruby         | Ruby          | Python        |
| Agent-based or agentless? | Agentless          | Agent-based  | Supports both | Supports both |
| How are devices managed?  | Any device can be “controller” | Chef Master | Puppet Master | Salt Master   |
| What is created by the tool? | Playbook         | Cookbook     | Manifest      | Pillar        |

Agent-based or agentless? - Configuration management is either agent-based or agentless. Agent-based configuration management is “pull-based”, meaning the agent on the managed device periodically connects with the master for its configuration information. Changes are done on the master and pulled down and executed by the device. Agentless configuration management is “push-based.” A configuration script is run on the master. The master connects to the device and executes the tasks in the script. Of the four configuration tools in the table, only Ansible is agentless.
How are devices managed? - This lies with a device called the Master in Puppet, Chef, and SaltStack. However, because Ansible is agentless, any computer can be the controller.
What is created by the tool? - Network administrators use configuration management tools to create a set of instructions to be executed. Each tool has its own name for these instructions: Playbook, Cookbook, Manifest, and Pillar. Common to each of this is specification of a policy or a configuration that is to be applied to devices. Each device type might have its own policy. For example, all Linux servers might get the same basic configuration and security policy

## IBN and Cisco DNA
Intent-Based Networking (IBN) and Cisco Digital Network Architecture (DNA) Center can help you bring it all together to create an automated network.

IBN is the emerging industry model for the next generation of networking. IBN builds on Software-Defined Networking (SDN), transforming a hardware-centric and manual approach to designing and operating networks to one that is software-centric and fully automated.

Business objectives for the network are expressed as intent. IBN captures business intent and uses analytics, machine learning, and automation to align the network continuously and dynamically as business needs change.

IBN captures and translates business intent into network policies that can be automated and applied consistently across the network.

Cisco views IBN as having three essential functions: translation, activation, and assurance. These functions interact with the underlying physical and virtual infrastructure, as shown in the figure.

The figure shows Intent-based networks (IBN) three essential functions and how they interact with the underlying physical and virtual infrastructure. The three functions are translation, activation and assurance. The figure is a flow chart. At the bottom is the Physical and Virtual network infrastructure. These are all devices in the network such as routers, switches, servers, access points, and virtual machines. An arrow is pointed from the Physical and Virtual network infrastructure to Assurance. Assurance provides continuous insights to management and perform corrective actions. Another arrow points from Assurance to Translation. Translation captures business intent and translate to policies. Another arrow points from Translation to Activation. Activation orchestrates policies and configure systems. The final arrow points from Activation to Physical and Virtual network infrastructure.

### Network Infrastructure as Fabric
From the perspective of IBN, the physical and virtual network infrastructure is a fabric. Fabric is a term used to describe an overlay that represents the logical topology used to virtually connect to devices, as shown in the figure. The overlay limits the number of devices the network administrator must program. It also provides services and alternative forwarding methods not controlled by the underlying physical devices. For example, the overlay is where encapsulation protocols like IP security (IPsec) and Control and Provisioning of Wireless Access Points (CAPWAP) occur. Using an IBN solution, the network administrator can specify through policies exactly what happens in the overlay control plane. Notice that how the switches are physically connected is not a concern of the overlay.
The underlay network is the physical topology that includes all hardware required to meet business objectives. The underlay reveals additional devices and specifies how these devices are connected, as shown in the figure. End points, such as the servers in the figure, access the network through the Layer 2 devices. The underlay control plane is responsible for simple forwarding tasks.

### Cisco Digital Network Architecture (DNA)
Cisco implements the IBN fabric using Cisco DNA. As displayed in the figure, the business intent is securely deployed into the network infrastructure (the fabric). Cisco DNA then continuously gathers data from a multitude of sources (devices and applications) to provide a rich context of information. This information can then be analyzed to make sure the network is performing securely at its optimal level and in accordance with business intent and network policies.

| Cisco DNA Solution  | Description                                                                                                                                                                                                                                                                                                                                 | Benefits                                                                                                                                                                                                                                           |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SD-Access           | First intent-based enterprise networking solution built using Cisco DNA. It uses a single network fabric across LAN and WLAN to create a consistent, highly secure user experience. It segments user, device, and application traffic and automates user-access policies to establish the right policy for any user or device, with any application, across a network.  |           Enables network access in minutes for any user or device to any application without compromising security.                                                                                                                                                                                                                                         |
| SD-WAN              | It uses a secure cloud-delivered architecture to centrally manage WAN connections. It simplifies and accelerates delivery of secure, flexible and rich WAN services to connect data centers, branches, campuses, and colocation facilities.  | Delivers better user experiences for applications residing on-premise or in the cloud. Achieve greater agility and cost savings through easier deployments and transport independence.                                                                                                                                                      |
| Cisco DNA Assurance | Used to troubleshoot and increase IT productivity. It applies advanced analytics and machine learning to improve performance and issue resolution, and predict to assure network performance. It provides real-time notification for network conditions that require attention.  |                   Allows you to identify root causes and provides suggested remediation for faster troubleshooting. The Cisco DNA Center provides an easy-to-use single dashboard with insights and drill-down capabilities. Machine learning continually improves network intelligence to predict problems before they occur.                                                                                                                                                                                                                                 |
| Cisco DNA Security  | Used to provide visibility by using the network as a sensor for real-time analysis and intelligence. It provides increased granular control to enforce policy and contain threats across the network. | Reduce risk and protect your organization against threats - even in encrypted traffic. Gain 360-degree visibility through real-time analytics for deep intelligence across the network. Lower complexity with end-to-end security. |


Many of these solutions are implemented using the Cisco DNA Center which provides a software dashboard for managing an enterprise network.

Cisco DNA Center
Cisco DNA Center is the foundational controller and analytics platform at the heart of Cisco DNA. It supports the expression of intent for multiple use cases, including basic automation capabilities, fabric provisioning, and policy-based segmentation in the enterprise network. Cisco DNA Center is a network management and command center for provisioning and configuring network devices. It is a hardware and software platform providing a ‘single-pane-of-glass’ (single interface) that focuses on assurance, analytics, and automation.

The DNA Center interface launch page gives you an overall health summary and network snapshot, as shown in the figure. From here, the network administrator can quickly drill down into areas of interest.

