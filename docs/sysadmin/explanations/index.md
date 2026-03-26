# Architecture

Simple directory service consisting of a set of Channels (unique PV names).
Each Channel has an arbitrary number of Properties (name/value pairs) and Tags (names).
Each Channel, Property, or Tag has an Owner (group) to allow basic access control.
All names and values are strings.

Channel definition example: 
```
      "name": "XF:31IDA-OP{Tbl-Ax:X1}Mtr",
     "owner": "train",
"properties": [
			  	"handle":"Setpoint“,
				"axis":"1",
				"hostname":"training.org.epics",
				"iocName":"motorsim",
	    		"time":"2016-03-21”
				]
      "tags": ["motor", "sys.XF:31"]
```

## recSync

The record synchronizer. Service built of:
*A client (RecCaster) which running as part of an EPICS IOC (EPICS support module)
*A server (RecCeiver) which is a stand alone daemon. 
Together they work to ensure the the server(s) have a complete list of all records currently provided by the client IOCs. You can find out more on (recSync Github)[https://github.com/ChannelFinder/recsync]

![RecSync dataflow diagram](PIC/DataFlowDiagram.png)

## RecCeiver Features

cleanOnStart, cleanOnStop: Removes any channels recceiver created on start or stop

Timezone: Add timezone information to the timestamps of Active/Inactive

## Recsync : cfStore 

The properties currently managed with cfStore:
```
hostName
iocName
pvStatus : Active or InActive
time : The last time the above properties were updated
recordType
recordDesc
aliases
ip address
pvAccess and ChannelAccess ports
specified env variables
specified info tags
```
