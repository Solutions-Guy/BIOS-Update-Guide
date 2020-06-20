**Check current BIOS Version**
* Check the current BIOS version by invoking the following request and expect to receive a JSON response with the BIOS version.
* Method: [GET]
* URL: https://$BMC_IP/redfish/v1/Systems/1
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20from%20Talend%20Chrome-based%20App.png)
<p align="center">Check BIOS from Talend Chrome-based app</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Version%20from%20Response.PNG)
<p align="center">Confirm BIOS Version from Response</p>

**Enter BIOS Update Mode**
* Enter BIOS update mode by posting the following request and expect to receive a “Successfully Completed Request” response.
* Method: [POST]
* URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.EnterUpdateMode

```JSON Payload
{}
```

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Enter%20BIOS%20Update%20Mode.PNG)
<p align="center">Enter BIOS Update Mode</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Mode%20from%20Response.PNG)
<p align="center">Confirm BIOS Mode from Response</p>

**Upload BIOS Image**
* Upload the BIOS image by posting the following request and expect to receive a “Successfully Completed Request” response. The content type must be “multipart/form-data”. The body must be “Form”, and enter “bios” as name, select “File” and choose the BIOS image from your local drive. 
* Method: [POST]
* URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.Upload
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Upload%20BIOS%20Image.PNG)
<p align="center">Upload BIOS Image</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Uploading%20BIOS%20Image%20in%20Progress.PNG)
<p align="center">Uploading BIOS Image in progress</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20Uploaded%20BIOS%20Imae%20Succesfully.PNG)
<p align="center">Confirm Uploaded BIOS Image successfully</p>

* Update BIOS by invoking the following request with the following payload and expect to receive a “Successfully Completed Request” response as this action will invoke an ongoing task. In the response, you can find the task information in the response body and task monitor in the response header

**Optional JSON Payloads**

* Method: [POST]
* URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.Update
* JSON Payload:
{"PreserveME":true, 
 "PreserveNVRAM":true,
 "PreserveSMBIOS":true}
 
 Note: Preserving the Management Engine, NVRAM, and SMBIOS will reset the BIOS to factory defaults.

* All three attributes in the payload may also take false as values. Below is the alternative JSON Payload.

JSON Payload:
{"PreserveME":false, 
 "PreserveNVRAM":false,
 "PreserveSMBIOS":false}
 
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Update%20BIOS.PNG)
<p align="center">Update BIOS</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20Accepted%20Request.PNG)
<p align="center">Confirm Accepted Request</p>

**2.5	Check BIOS Update Status**

* Check the BIOS Update progress by invoking the following request and expect a response with information about the update progress, such as the percentage of completion.
* Method: [GET]
* URL: Use one of types of URIs from the response body for the ongoing Task
* https://$BMC_IP/redfish/v1/TaskMonitor/[###########]
* https://$BMC_IP/redfish/v1/TaskService/Tasks/#

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20Update%20Progress%20with%20Task%20Monitor%20to%20Find%20Ongoing%20Task%23.PNG)
<p align="center">Check Update Progress with Task Monitor to find ongoing task#</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Get%20Task%20Number%20From%20Response%20for%20Update%20Progress.PNG)
<p align="center">Get the task number from the response for Update Progress</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20Update%20Progress%20with%20Tast%20Service.PNG)
<p align="center">Check Update Progress with Task Service</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20Update%20Progress%20(86%25).PNG)
<p align="center">Check BIOS Update Progress (86%)</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20Update%20Progress%20(100%25).PNG)
<p align="center">Check BIOS Update Progress (100%)</p>

* Confirm the BIOS version by invoking the following request and expect a response with the BIOS version
* Method: [GET]
* URL: https://172.31.32.138//redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Get%20BIOS%20Version.PNG)
<p align="center">Get BIOS Version</p>

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Status.PNG)
<p align="center">Confirm BIOS Status</p>
