::: {.slide #slide-1}

::: {.center-title #rectangle}

SFT300 – FTTM

:::

::: {.subtitle #subtitle}

*FactoryTalk Transaction Manager Overview*

:::

::: {.notes #notes-1}

Course Name is 32 pt Trebuchet MS in Bold
Lesson Name is 28 pt Trebuchet MS in Bold & Italic
Technology Center is 28 pt Arial Narrow in Bold

:::

:::

::: {.slide #slide-2}

::: {.title #title}

Course Overview

:::

::: {.object #content-placeholder}

4 Day Class
    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project
Take breaks as needed and inform instructor of any absences needed
    - Lunch will be ~12:00PM-1PM each day
70% required for passing the test (and course)
    - Test will be completed in Microsoft Forms (online w/Office 365 Account)
Course and instructor evaluation
    - 
    - 

:::

::: {.notes #notes-2}

`content is empty`

:::

:::

::: {.slide #slide-3}

::: {.title #title}

Course Overview

:::

::: {.object #content-placeholder}

Monday
    - Transaction Manager Overview 
    - Factory Talk Services Platform (Lab 01)
    - Creating a FactoryTalk Application (Lab 02)
    - Installing Transaction Manager (Lab 03)
    - Installing and Configuring Microsoft SQL Server (Lab 04)
    - FTTM Setup and Configuration (Lab 05)
    - 
    - 

:::

::: {.notes #notes-3}

`content is empty`

:::

:::

::: {.slide #slide-4}

::: {.title #title}

Course Overview

:::

::: {.object #content-placeholder}

Tuesday
    - Q&A Session
    - Editing a running configuration (Lab 06)
    - Binding Transaction Results (Lab 07)
    - Data loss (Lab 08)
    - FTTM functions (Lab 09)
    - FTTM update data objects (Lab 10)
    - 
    - 

:::

::: {.notes #notes-4}

`content is empty`

:::

:::

::: {.slide #slide-5}

::: {.title #title}

Course Overview

:::

::: {.object #content-placeholder}

Wednesday
    - Q&A Session
    - Trigger and Storage options (Lab 11)
    - Select Stored Procedures (Lab 12)
    - Insert Stored Procedures (Lab 13)
    - Update Stored Procedures (Lab 14)
    - XML Import/Export (Lab 15)
    - Error Logging (Lab 16)
    - FTTM Security (Lab 17)
    - Mini project handout
    - 
    - 

:::

::: {.notes #notes-5}

`content is empty`

:::

:::

::: {.slide #slide-6}

::: {.title #title}

Course Overview

:::

::: {.object #content-placeholder}

Thursday
    - Finish any labs
    - Q&A Session
    - Mini project checkoffs
    - Test
    - Course Evaluations
    - 
    - 

:::

::: {.notes #notes-6}

`content is empty`

:::

:::

::: {.slide #slide-7}

::: {.title #title}

Transaction Manager Lab Setup

:::

::: {.object #content-placeholder}

Computer-A VM
    - PC Name: Computer-A
    - IP address: 192.168.1.100
    - Subnet: 255.255.255.0
    - No gateway
    - Windows Server 2008 R2
Software
    - MSSQL 2008 R2 Standard
    - FTSP v2.30.01 (CPR 9 SR 3)
    - FTTM v10.10
User info:
    - Username: Rockwell
    - Password: rockwell

:::

::: {.object #content-placeholder}

PLC-Image VM
    - PC Name: PLC-Image
    - IP address: 192.168.1.200
    - Subnet: 255.255.255.0
    - No gateway
    - Windows Server 2003 Standard
Software
    - SoftLogix 5800 v19.00.00
    - FTSP 2.50 (CPR 9 SR 5)
    - Oracle 10g
User info:
    - Username: Administrator
    - Password: rockwell

:::

::: {.notes #notes-7}

`content is empty`

:::

:::

::: {.slide #slide-8}

::: {.title #title}

What is Factory Talk Transaction Manager?

:::

::: {.object #content-placeholder}

Previously known as RSSQL (“Rascal”)
    - Last release (v7.5) was ~2005
Software engine that shares data between your control system and enterprise applications
Control systems
    - HMI
    - PLC
    - ControlLogix
    - DCS
Enterprise Applications
    - Corporate database, such as MSSQL
    - Custom applications

:::

::: {.notes #notes-8}

`content is empty`

:::

:::

::: {.slide #slide-9}

::: {.title #title}

Transaction Manager Uses

:::

::: {.object #content-placeholder}

Track Material Consumption or production
Download, upload, and manage recipes
Automate data logging
    - Track bar codes in real-time
    - Create rules for data logging
    - Different end-uses than a Historian software
Update real-time process information
    - Temperature, pressure, alarm states
Integration with RSBizWare Suite (Historian Classic and Metrics)

:::

::: {.notes #notes-9}

`content is empty`

:::

:::

::: {.slide #slide-10}

::: {.title #title}

Transaction Manager Architecture

:::

![image_21.png](media\image_21.png)

::: {.notes #notes-10}

FTTM consists of 6 components:

ICS system (external)
Control connectors (for connecting to ICS)
Transaction and Control Manager Service (this IS FTTM)
Enterprise connectors (for connecting to a database or custom application)
Enterprise systems (database or custom application)
User interface

:::

:::

::: {.slide #slide-11}

::: {.title #title}

FactoryTalk Services Platform

:::

![image_23.png](media\image_23.png)

::: {.notes #notes-11}

The FactoryTalk services platform is a suite of services that are installed in the background of all FactoryTalk-branded products. In version 10.10 that we are using, currently Alarms and Events are not supported. In future versions of FTTM, Alarms and Events are supported (v12).

FTSP enables Transaction Manager to talk to various FT components (PLC, HMI, activation manager, directory, etc).

:::

:::

::: {.slide #slide-12}

::: {.title #title}

Transaction Manager Versions

:::

::: {.object #content-placeholder}

Professional
    - Supports distributed operations and the ability to add multiple enterprise or control connectors on different computers
    - Includes a server license for Microsoft® SQL Server 2012 Standard Edition and a SQL Server Client Access License (CAL) as required by Microsoft
    - Up to 70k tags
Standard
    - Must have all services on the same computer, but it can connect to remote databases and/or OPC servers (if that option is supported by the OPC vendor)
    - Up to 5k tags
Both Professional and Standard are licensed by # of tags

:::

:::

::: {.slide #slide-13}

::: {.title #title}

Transaction Manager User Interface

:::

![image_27.png](media\image_27.png)

::: {.notes #notes-13}

The Transaction Manager “Configuration Tree” contains the configuration server and above it, the computer it is running on. 

The next item (in this case, “ProductionArea”), is the configuration name, which will be defined in detail by the user. If the configuration uses online edits, below the configuration is the Transaction Control Manager service. Otherwise, it will use the FTTM service. 

Lastly, There are either control connectors (for connecting to FactoryTalk Live Data, for instance) or Enterprise connectors (for connecting to a database).

Note that each configuration is defined by a traffic light. As with a normal traffic light, green is good, and red means that the configuration is not running for some reason (may simply be stopped by the user, but could be something more problematic).

:::

:::

::: {.slide #slide-14}

::: {.title #title}

Transaction Manager User Interface

:::

![image_29.png](media\image_29.png)

::: {.notes #notes-14}

Configuration checklist is the menu where the configuration, connectors, data points, data objects, and transactions will be defined. Once all of these have been defined, the configuration can be “run”. Users can expect to spend most of their setup time in this menu. 

:::

:::

::: {.slide #slide-15}

::: {.title #title}

Transaction Manager User Interface

:::

::: {.line}

:::

![image_32.png](media\image_32.png)

::: {.notes #notes-15}

So the first thing to look at is the configuration of our application. We will define our name, application location, and connections here. 

:::

:::

::: {.slide #slide-16}

::: {.title #title}

Transaction Manager User Interface

:::

![image_34.png](media\image_34.png)

::: {.notes #notes-16}

These “connectors” represent some sort of software that links up my data points to my enterprise applications.

Control connectors are the software that link Transaction Manager to my data points. This is a link between FTTM and a data server. In our case, we are going to utilize FactoryTalk Live Data, which is part of the FT Services Platform. Newer versions of FTTM do not support RSLinx Classic or RSView32. Generic OPC would be for 3rd party data servers (such as Kepware).

Enterprise connectors are the software that link Transaction Manager to my enterprise servers. In our case, we are going to link up to an ODBC database (Microsoft SQL Server) to send/receive data from a database. This can also be linked up to FT Metrics (part of the RSBizWare Suite) to send/receive KPI information about how our process is behaving from a quality perspective. Newer versions of FTTM do not support OLE-DB or COM+ as these are older types of database connections. 

The location of these connectors will be defined in the next step.

:::

:::

::: {.slide #slide-17}

::: {.title #title}

Transaction Manager User Interface

:::

![image_36.png](media\image_36.png)

::: {.line}

:::

::: {.notes #notes-17}

After we have defined the types of connections we want to make (i.e. FactoryTalk Live Data and an ODBC connection), we will need to specify where these connections are located. 

:::

:::

::: {.slide #slide-18}

::: {.title #title}

Creating a FTTM Configuration *Transaction Control Manager Service*

:::

::: {.body #rectangle}

**Transaction Control Manager Service** 
    - The Transaction Control Manager is a service that controls and executes transactions with the additional functionality of the FactoryTalk Live Data control connector embedded in it. 
    - The Transaction Control Manager service can connect to Rockwell Software products and all OPC servers; therefore, the use of this service is the preferred method for all new FactoryTalk Transaction Manager configurations.  
    - 


:::

![image_40.png](media\image_40.png)

::: {.notes #notes-18}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-19}

::: {.title #title}

Creating a FTTM Configuration *Transaction Manager Service*

:::

::: {.body #rectangle}

**FactoryTalk Transaction Manager Service **
    - The FactoryTalk Transaction Manager service is used to control and execute FactoryTalk Transaction Manager transactions contained in configurations created prior to CPR 7 or when you have a business reason to not run the Transaction Control Manager service. 
    - 


:::

![image_43.png](media\image_43.png)

::: {.notes #notes-19}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-20}

::: {.title #title}

Control Connector

:::

![image_45.png](media\image_45.png)

::: {.notes #notes-20}

Transaction/Control Manager connector is a service that controls and executes transactions with the additional functionality of the FT Live Data Control connector embedded inside it. We therefore do not have to define an additional connector for FTLD.

This is the preferred connector, as it can connect to Rockwell Software products and all OPC servers.

:::

:::

::: {.slide #slide-21}

::: {.title #title}

Creating a FTTM Configuration *Control Connectors*

:::

::: {.object #content-placeholder}

The FactoryTalk Transaction Manager service interfaces with the industrial control system device via a control connector. 
A control connector is a Microsoft Windows 2003/XP/Vista/2008 service that **collects data from a controller and sends it to the FactoryTalk Transaction Manager service** in the FactoryTalk Transaction Manager. You can use the following types of control connectors: 
    - FactoryTalk Live Data
    - DDE
    - RSLinx Classic OPC
    - RSView32
    - Generic OPC  

:::

::: {.notes #notes-21}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-22}

::: {.title #title}

Enterprise Connectors

:::

![image_49.png](media\image_49.png)

![image_50.png](media\image_50.png)

::: {.notes #notes-22}

After we have defined the types of connections we want to make (i.e. FactoryTalk Live Data and an ODBC connection), we will need to specify where these connections are located. These are called enterprise connectors, which can be set to the following types of connectors:
	ODBC (Open Database Connectivity)
	Oracle Call Interface (OCI)
	Microsoft OLE DB 
	Microsoft COM+
	Time-series Data Compression
	FactoryTalk Metrics

:::

:::

::: {.slide #slide-23}

::: {.title #title}

Creating a FTTM Configuration *Enterprise Connectors*

:::

::: {.object #content-placeholder}

The Transaction Control Manager service and the FactoryTalk Transaction Manager service interface with enterprise systems such as databases via an enterprise connector service. 
An enterprise connector is a Microsoft Windows 2003/XP/Vista/2008 service **that transfers data between the Transaction Control Manager service or the FactoryTalk Transaction Manager service and a database**. You can use the following types of enterprise connectors: 
    - Open Database Connectivity (ODBC)
    - Oracle Call Interface (OCI)
    - Microsoft OLE DB
    - Microsoft COM+
    - Time-series Data Compression
    - FactoryTalk Metrics

:::

::: {.notes #notes-23}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-24}

::: {.title #title}

Creating a FTTM Configuration *Configuration Server*

:::

::: {.object #content-placeholder}

The Configuration Server is a Microsoft Windows 2003/XP/Vista/2008 service that **runs continuously to provide a single interface to the configuration (.dat) files that make up the FactoryTalk Transaction Manager configuration**. 
The Configuration Server simplifies access to configuration files by filtering all changes to the files and interfacing with other FactoryTalk Transaction Manager services. A collection of all changes that affect a configuration are recorded in an audit trail (via either FactoryTalk Diagnostics or the Configuration Server *.log file). 

:::

::: {.notes #notes-24}

The user will interface with the configuration server to make changes to the system.

:::

:::

::: {.slide #slide-25}

::: {.title #title}

Transaction Manager User Interface

:::

![image_56.png](media\image_56.png)

::: {.line}

:::

::: {.notes #notes-25}

After the connections have been established, we can now add data points from our FTLD interface (or other connection). 

:::

:::

::: {.slide #slide-26}

::: {.title #title}

Transaction Manager User Interface

:::

![image_59.png](media\image_59.png)

::: {.notes #notes-26}

If I wanted to use data and/or tags from within a FT application (HMI Tags, Controller tags, FTAE tags, etc.), the data point editor is where I would add these. These data points can be renamed to a more desirable name, can be bound to a particular string, can be scanned at a different rate, and can also be “Scheduled” to be collected (either unconditionally or based on a pre-programmed condition)

:::

:::

::: {.slide #slide-27}

::: {.title #title}

Transaction Manager User Interface

:::

![image_61.png](media\image_61.png)

::: {.line}

:::

::: {.notes #notes-27}

We have defined what types of points we would like to collect from our control system. Now we would like to establish what tables/objects we would like to connect these data points to inside of our database or other type of enterprise connector. 

:::

:::

::: {.slide #slide-28}

::: {.title #title}

Transaction Manager User Interface

:::

![image_64.png](media\image_64.png)

::: {.notes #notes-28}

`content is empty`

:::

:::

::: {.slide #slide-29}

::: {.title #title}

Transaction Manager User Interface

:::

![image_66.png](media\image_66.png)

::: {.line}

:::

::: {.notes #notes-29}

Finally! We’ve connected all of our data together, but what should we do with it? Transactions define some sort of transfer of data—either into our DCS/control system, from a DCS/Control system, or to/from our enterprise connection (in our case a SQL database. This setup defines what triggers make a transaction occur, how a transaction stores data, and what type of information needs to be exchanged. 

:::

:::

::: {.slide #slide-30}

::: {.title #title}

Transaction Manager User Interface

:::

![image_69.png](media\image_69.png)

::: {.notes #notes-30}

The transaction definition will let me set up my data exchange. I definite what objects within my database I would like to act on, what values I should bind them to, add NULL values if desired, and what data type I want to use. I can validate the transaction, define a timeout, and either use a cache value or a real time thread. 

Cache transaction files would be useful if I have a unidirectional transaction happening (pure data logging)

Real time thread is needed for bi-directional transactions (real-time download or confirmation of data quality)

:::

:::

::: {.slide #slide-31}

::: {.title #title}

Transaction Manager User Interface

:::

![image_71.png](media\image_71.png)

::: {.notes #notes-31}

Our transactions can be seen in this menu. The green light on “RSSQLOnline” indicates that our configuration is happy, and there are a significant number of “Database passed” transactions, indicating that our transactions/data are being successfully sent to our SQL database. 

:::

:::

::: {.slide #slide-32}

::: {.title #title}

SQL Database Verification

:::

![image_73.png](media\image_73.png)

:::

::: {.slide #slide-33}

::: {.title #title}

Creating a FTTM Configuration *Configuration Checklist – Final Notes and Recap*

:::

::: {.object #content-placeholder}

A FactoryTalk Transaction Manager configuration consists of a set of transactions that use control and enterprise connector elements required to perform the transactions. 
You may create many configurations, but the Transaction Control Manager service or the FactoryTalk Transaction Manager service can run only one configuration at a time. Therefore, all the transactions required to implement an application must be contained in a single configuration. 

:::

::: {.notes #notes-33}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-34}

::: {.title #title}

Creating a FTTM Configuration *Configuration Checklist – Final Notes and Recap*

:::

::: {.object #content-placeholder}

Step 1 – Defining and Naming a new Configuration
Step 2 – Defining Connectors
Step 3 – Defining Data Points
Step 4 – Defining Data Objects
Step 5 – Defining Transactions
Step 6 – Verifying Transactions


:::

::: {.notes #notes-34}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-35}

::: {.title #title}

Creating a FTTM Configuration *Configuration Checklist – Final Notes and Recap*

:::

::: {.object #content-placeholder}

FactoryTalk Transaction Manager consists of several design-time and run-time components including: 
    - Transaction Control Manager service
    - FactoryTalk Transaction Manager service 
    - Control Connectors 
    - Enterprise Connectors
    - Configuration Server
    - Transactions 


:::

::: {.notes #notes-35}

Lesson Name is 28 pt Trebuchet MS in Bold
Slide Topic is 24 pt Trebuchet MS in Bold & Italic

:::

:::

::: {.slide #slide-36}

::: {.title #title}

Transaction Manager Resources

:::

::: {.object #content-placeholder}

[Transaction Manager User Manual](https://literature.rockwellautomation.com/idc/groups/literature/documents/um/rssql-um001_-en-p.pdf)
[RSBizWare](https://literature.rockwellautomation.com/idc/groups/literature/documents/in/bzware-in001_-en-p.pdf)[ Administration Guide](https://literature.rockwellautomation.com/idc/groups/literature/documents/in/bzware-in001_-en-p.pdf)
[FTTM Product Profile](https://literature.rockwellautomation.com/idc/groups/literature/documents/pp/ftalk-pp011_-en-p.pdf)
[Ordering Information](https://www.rockwellautomation.com/rockwellsoftware/products/factorytalk-transaction-manager.page?#ordering-information)


    - 

:::

::: {.notes #notes-36}

`content is empty`

:::

:::

::: {.slide #slide-37}

::: {.title #title}

Transaction Manager – Ordering Information

:::

![image_83.png](media\image_83.png)

::: {.object #content-placeholder}

`content is empty`
    - 

:::

::: {.notes #notes-37}

`content is empty`

:::

:::

::: {.slide #slide-38}

::: {.title #title}

Transaction Manager – Ordering Information

:::

::: {.object #content-placeholder}

`content is empty`
    - 

:::

![image_87.png](media\image_87.png)

::: {.notes #notes-38}

`content is empty`

:::

:::

::: {.slide #slide-39}

::: {.title #title}

Transaction Manager Pricing (July 2019)

:::

::: {.object #content-placeholder}

`content is empty`

:::

\[redacted\]

::: {.notes #notes-39}

`content is empty`

:::

:::

::: {.slide #slide-40}

::: {.center-title #rectangle}

FactoryTalk Transaction Manager Overview

:::

::: {.subtitle #subtitle}

*End of Presentation*

:::

::: {.notes #notes-40}

Course Name is 32 pt Trebuchet MS in Bold
Lesson Name is 28 pt Trebuchet MS in Bold & Italic
Technology Center is 28 pt Arial Narrow in Bold

:::

:::

