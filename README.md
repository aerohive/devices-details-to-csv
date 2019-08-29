# NO LONGER MAINTAINED
As of August 30, 2019 this project is no longer maintained. It should still (probably) work, but I am no longer providing support, fixing issues, or adding new features.

# SYNOPSYS
This script is designed to help Aerohive Administrators to get the devices details to a CSV file. It can be used with Windows, Linux and MacOs.
The script will only save REAL devices (opposed to SIMULATED devices), and can save devices' information like the Hostname, the IP Address, the Location, CPU and memory load, ...

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

# USAGE

This script requires to have NodeJS installed. You can download it from the [NodeJS web site](https://nodejs.org/). 
Please note that only the LTS version was tested.

To run the script, you'll need to :
* Configure the script. All the parameters are listed at the beginning of the script
* Install Node.js from https://www.nodejs.org
* From your CLI or Windows CMD, go to the folder where you saved the script and run `node ./devices.js`. This will display you the result of the csv file, but it will not create it. If you want to execute the script and create the csv file at the save time, you can use the command `node devices.js > devices.csv`.

# RESULT EXAMPLE
```
#Start of Output
#serialId,model,osVersion,macAddress,hostName,ip,subnetMask,defaultGateway,dns,ntp,cpuUsage,memUsage,connected,policy
01301601000000,AP_130,8.1.1.0,885BDD000000,AP130-Test,172.16.227.23,255.255.255.0,172.16.227.1,192.168.0.1,0.aerohive.pool.ntp.org,2,47,true,Test-mesh
22081604000000,SR_2208P,1.0.1.22,B87CF2000000,SR2208P-Test,172.16.227.42,255.255.255.0,,,0.aerohive.pool.ntp.org,,,true,void
02501602000000,AP_250,8.1.1.0,C413E2000000,AP250-Test,172.16.227.17,255.255.255.0,172.16.227.1,208.67.222.222,0.aerohive.pool.ntp.org,1,33,true,Test

#Total # of Devices: 4
#Total # of Real Devices: 3
#End of Output
```
# PARAMETERS
## ACS Parameters
```javascript
var clientId = "xxxxxx";
var clientSecret = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx";
var redirectUrl = "https://127.0.0.1";
```
### IF YOU ARE USING NG CLOUD
You'll have to create an account at https://developer.aerohive.com and create a new "App" to get your own parameters:
### IF YOU ARE USING NG-VA
You don't need a developer account, and you can just use, for example:
  * var clientId = "12345";
  * var clientSecret = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx";
  * var redirectUrl = "https://127.0.0.1";
  

## HiveManager NG Parameters
```javascript
var serverFQDN = "cloud-ie.aerohive.com";
var accessToken = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx";
var ownerId = "xxxxxx";

```
### IF YOU ARE USING NG CLOUD
* serverFQDN: it's something like cloud-xxx.aerohive.com, where xxx can be "va", "va2", "ie" or "aus" (this list may change). You can find it in the "About" section of your HiveManager NG account.
* accessToken: In your HiveManagerNG account, go to "Global Settings > API Token Management" and create your token. **Be sure to generate the access token by using the same clientID as the one configured above!**.
* ownerId: The ownerId is the "VHM Id" value in the "About" section of your HiveManager NG account.
### IF YOU ARE USING NG-VA
* serverFQDN: it is the FADN of your HiveManager NG Virtual Appliance.
* accessToken: In your HiveManagerNG account, go to "Global Settings > API Token Management" and create your token. **Be sure to generate the access token by using the same clientID as the one configured above!**.
* ownerId: The ownerId is the "VHM Id" value in the "About" section of your HiveManager NG account.

## CSV Parameters
```javascript
var csvFields = [ "serialId", "hostName", "macAddress", "connected", "cpuUsage", "memUsage", "ip", "defaultGateway", "dns", "ntp", "subnetMask", "upTime", "deviceTemplate", "lastUpdated"];
```
This parameter will let you choose which fields will be saved in the CSV file.
### available fields: 
* alarmEvents (Array[AlarmEvent], optional): The alarm events associated with this client device. ,
* configType (string, optional): The type of configuration used for this device = ['STATIC_IP', 'DHCP_CLIENT_WITH_FALLBACK', 'DHCP_CLIENT_WITHOUT_FALLBACK'],
* connected (boolean, optional): Indicates whether or not a device is connected or disconnected. True indicates that the device is connected, False indicates that the device is not connected. ,
* cpuUsage (integer, optional): Percentage CPU Usage. ,
* defaultGateway (string, optional): The Default Gateway configuration associated with the device. ,
* deviceId (integer, optional): The unique device number of this Access Point/Device. ,
* deviceTemplate (string, optional): The name of the device template used to configure this device. ,
* dns (string, optional): The configured Domain Name System server to be used by the device. ,
* hostName (string, optional): The Hostname of the device. ,
* ip (string, optional): The IP Address of the device. ,
* lastUpdated (string, optional): The date the device was last updated in ISO-8601 format. ,
* latitude (number, optional): The latitude of the device. ,
* locationId (integer, optional): Location ID where the Device exists ,
* locations (Array[string], optional): (DEPRECATED) An array of Strings containing the hierarchical location information. ,
* longitude (number, optional): The longitude of the device. ,
* macAddress (string, optional): The MAC Address of the device. ,
* memUsage (integer, optional): Percentage memory usage. ,
* mgmtStatus (string, optional): The management status of the device. ,
* mode (string, optional): The operating mode of the device ,
* model (string, optional): The model information of the device. ,
* ntp (string, optional): The configured Network Time Protocol server used by the device. ,
* osVersion (string, optional): The device operating system version. ,
* ownerId (integer, optional): The id of the customer that owns this device. ,
* policy (string, optional): The name of the network policy used to configure this device. ,
* serialId (string, optional): The unique serial number of the device. ,
* simulatedDevice (boolean, optional): Is this a real or simulated device? ,
* subnetMask (string, optional): The Subnet Mask configuration associated with the device. ,
* upTime (string, optional): The time that the device was last booted.
