**Check current BIOS Version**
* Check the current BIOS version by invoking the following request and expect to receive a JSON response with the BIOS version.
* Method: [GET]
* URL: https://$BMC_IP/redfish/v1/Systems/1
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20from%20Talend%20Chrome-based%20App.png)
<p align="center">Check BIOS from Talend Chrome-based app</p>
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Version%20from%20Response.PNG)
Confirm BIOS Version from Response

**Enter BIOS Update Mode**

* Enter BIOS update mode by posting the following request and expect to receive a “Successfully Completed Request” response.
* Method: [POST]
*URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.EnterUpdateMode
* JSON Payload: {}
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Enter%20BIOS%20Update%20Mode.PNG)
Enter BIOS Update Mode
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Mode%20from%20Response.PNG)
Confirm BIOS Mode from Response

**Upload BIOS Image**

* Upload the BIOS image by posting the following request and expect to receive a “Successfully Completed Request” response. The content type must be “multipart/form-data”. The body must be “Form”, and enter “bios” as name, select “File” and choose the BIOS image from your local drive. 
* Method: [POST]
* URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.Upload
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Upload%20BIOS%20Image.PNG)
Upload BIOS Image
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Uploading%20BIOS%20Image%20in%20Progress.PNG)
Uploading BIOS Image in progress
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20Uploaded%20BIOS%20Imae%20Succesfully.PNG)
Confirm Uploaded BIOS Image successfully

* Update BIOS by invoking the following request with the following payload and expect to receive a “Successfully Completed Request” response as this action will invoke an ongoing task. In the response, you can find the task information in the response body and task monitor in the response header
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
Update BIOS
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20Accepted%20Request.PNG)
Confirm Accepted Request

**2.5	Check BIOS Update Status**

*Check the BIOS Update progress by invoking the following request and expect a response with information about the update progress, such as the percentage of completion.
* Method: [GET]
* URL: Use one of types of URIs from the response body for the ongoing Task
* https://$BMC_IP/redfish/v1/TaskMonitor/[###########]
* https://$BMC_IP/redfish/v1/TaskService/Tasks/#

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20Update%20Progress%20with%20Task%20Monitor%20to%20Find%20Ongoing%20Task%23.PNG)
Check Update Progress with Task Monitor to find ongoing task#
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Get%20Task%20Number%20From%20Response%20for%20Update%20Progress.PNG)
Get the task number from the response for Update Progress
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20Update%20Progress%20with%20Tast%20Service.PNG)
Check Update Progress with Task Service
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20Update%20Progress%20(86%25).PNG)
Check BIOS Update Progress (86%)
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20Update%20Progress%20(100%25).PNG)
Check BIOS Update Progress (100%)

* Confirm the BIOS version by invoking the following request and expect a response with the BIOS version
* Method: [GET]
* URL: https://172.31.32.138//redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Get%20BIOS%20Version.PNG)
Get BIOS Version
![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Confirm%20BIOS%20Status.PNG)
Confirm BIOS Status
