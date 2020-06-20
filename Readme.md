**Check current BIOS Version**
* Check the current BIOS version by invoking the following request and expect to receive a JSON response with the BIOS version.

Method: [GET]
URL: 
https://$BMC_IP/redfish/v1/Systems/1

![](https://github.com/Solutions-Guy/BIOS-Update-Guide/blob/master/Check%20BIOS%20from%20Talend%20Chrome-based%20App.png)
Check BIOS from Talend Chrome-based app

Confirm BIOS Version from Response

**Enter BIOS Update Mode**

* Enter BIOS update mode by posting the following request and expect to receive a “Successfully Completed Request” response in Figure 2-4.

Method: [POST]
URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.EnterUpdateMode
JSON Payload: {}

Enter BIOS Update Mode

Confirm BIOS Mode from Response

**Upload BIOS Image**

* Upload the BIOS image by posting the following request and expect to receive a “Successfully Completed Request” response. The content type must be “multipart/form-data”. The body must be “Form”, and enter “bios” as name, select “File” and choose the BIOS image from your local drive. 

Method: [POST]
URL: https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.Upload

Upload BIOS Image

Uploading BIOS Image in progress

Confirm Uploaded BIOS Image successfully

* Update BIOS by invoking the following request with the following payload and expect to receive a “Successfully Completed Request” response as this action will invoke an ongoing task. In the response, you can find the task information in the response body and task monitor in the response header (see Figure 2-9.   

Method: [POST]
URL: 
https://$BMC_IP/redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/Actions/SmcFirmwareInventory.Update
JSON Payload:
{"PreserveME":true, 
 "PreserveNVRAM":true,
 "PreserveSMBIOS":true}

Note: Preserving the Management Engine, NVRAM, and SMBIOS will reset the BIOS to factory defaults.

* All three attributes in the payload may also take false as values. Below is the alternative JSON Payload.

JSON Payload:
{"PreserveME":false, 
 "PreserveNVRAM":false,
 "PreserveSMBIOS":false}

Update BIOS

Confirm Accepted Request

**2.5	Check BIOS Update Status**

*Check the BIOS Update progress by invoking the following request and expect a response with information about the update progress, such as the percentage of completion.

Method: [GET]
URL: Use one of types of URIs from the response body for the ongoing Task in section 2.4 
https://$BMC_IP/redfish/v1/TaskMonitor/[###########]
https://$BMC_IP/redfish/v1/TaskService/Tasks/#

Check Update Progress with Task Monitor to find ongoing task#

Get the task number from the response for Update Progress

Check Update Progress with Task Service

Check BIOS Update Progress (86%)

Check BIOS Update Progress (100%)

* Confirm the BIOS version by invoking the following request and expect a response with the BIOS version

Method: [GET]
URL: 
https://172.31.32.138//redfish/v1/UpdateService/SmcFirmwareInventory/BIOS/

Get BIOS Version

Confirm BIOS Status
