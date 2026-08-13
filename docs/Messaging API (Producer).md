# LGS Messaging API (Producer)

## Overview

The Messaging API provides wrapper methods for publishing  
 different types of operational messages including:  

•	EquipmentAlerts (SourceSubsystem_webhook object)  
•	Vertical-Acre Alerts  
•	HVAC Alerts  
•	Temperature Out-of-sync alerts  
•	Seed cartridge recall messages (SourceSubsystem_webhook object)  
•	Lot recall messages  
•	Box/Carton recall messages  
•	Palette recall messages  
•	Sensor data  
•	Harvest data  
•	Feedback  
•	QR scan data  
•	Food safety data  



## Package
The API endpoints will be wrapped around in a package.  The   package will hide the endpoints from the end user and instead   expose the following methods:  
________________________________________  
  
## SendEquipmentAlert()  
Parameters  
  
|Field	| Type	| Required	| Description|  
|-------|-------|-----------|------------|
|alert_component|	string	| Yes	| Component that generated the alert | 
|alert_component_id	| string	| Yes	| Entity associated with the alert|  
|Message_id	|uuid string	| Yes	| Unique alert identifier|  
|EquipmentAlert_data	|String | Yes  |	Detailed alert information | 
|alert_urgency_level | integer.  4 levels of alert.  Document   what the four levels of alert are here).	string	| Yes	| Alert urgency level  |
| SourceSubsystem_webhook	| object	| Yes	|Takes the user straight to the alert details | 
  
Return value – a data structure containing the consumer token, the data and any error codes  
    enum LGS_MSG_ERROR = {
        "LGS_MSG_SUCCESS" = 200, 
        "LGS_MSG_BAD_REQUEST" = 400, 
        "LGS_MSG_NOT_FOUND" = 404, 
        "LGS_MSG_METHOD_NOT_ALLOWED" = 405, 
        "LGS_MSG_INTERNAL_SERVER_ERROR" = 500
    }  
  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}  
  
getErrorDescription()  
Parameter: error code  
Return value: the error description.  
________________________________________  

## SendHVACAlert()  
Parameters  
  
|Field	Type	| Required	| Description |
|-------------|-----------|-------------|
|alert_component|	string	|Yes	|Component that generated the alert | 
|alert_component_id|	string	|Yes	|Entity associated with the alert | 
|Message_id|	uuid string|	Yes|	Unique alert identifier | 
|HVACAlert_data|	String |	Yes | 	Detailed alert information  
alert_urgency_level (integer) – 4 levels of alert.  Document   what the four levels of alert are here).	| string	|Yes	|Alert  urgency level  |
|SourceSubsystem_webhook	|object	| Yes	|Takes the user straight to the alert details    
  
Return value 

enum LGS_MSG_ERROR = {
        "LGS_MSG_SUCCESS" = 200, 
        "LGS_MSG_BAD_REQUEST" = 400, 
        "LGS_MSG_NOT_FOUND" = 404, 
        "LGS_MSG_METHOD_NOT_ALLOWED" = 405, 
        "LGS_MSG_INTERNAL_SERVER_ERROR" = 500
    }
  
getErrorDescription()  
Paremeter – error code  
Return value - get the error description.  
  
  
## Shared Error Responses  
HTTP Code	Condition	Example Response  
400 Bad Request	The request body is malformed or required fields are missing.	{  
"error": "Invalid request body."   
}  

404 Not Found	The requested endpoint does not exist	{  
"error": "Endpoint not found."  
}  

405 Method Not Allowed	Request uses a method other than POST	{
"error": "Method Not Allowed. Use POST."
}

500 Internal Server Error	The server encountered an unexpected error while processing the request.	{
"error": "Internal server error."
}
 
500 {Messaging system} Connection Error	{Messaging system} connection refused	{
"error": "{Messaging system}Error: connection refused."
}

500 {Messaging system} Publish Timeout	{Messaging system} broker request timed out	{
"error": "{Messaging system}Error:  connection timed out."
}

500 {Messaging system} Serialization Error	Failed to serialize {Messaging system} message payload	{
"error": "{Messaging system}Error: failed to serialize message."
}
________________________________________




## SendVerticalAcreAlert()  
Parameters  

|Field|Type|Required|Description|  
|-----|----|--------|-----------|  
|alert_component|string|Yes|Component that generated the alert|  
|alert_component_id|string|Yes|Entity associated with the alert|  
|Message_id|uuid string|Yes|Unique alert identifier|  
|VerticalAcreAlert_data|String|Yes|Detailed alert information|  
|alert_urgency_level|integer – 4 levels of alert.  Document   what the four levels of alert are here).|Yes|Alert urgency level|  
|SourceSubsystem_webhook|object|Yes|Takes the user straight to the alert details|  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
Call getErrorDescription() to get the error description.  
  
## SendTemperatureOutOfSyncAlert()  
Parameters  
  
|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|alert_component|	string |Yes |Component that generated the alert | 
|alert_component_id| string	|Yes |Entity associated with the  
alert |
|Message_id| uuid string | Yes |Unique alert identifier | 
|TemperatureOutOfSyncAlert_data| String |	Yes | Detailed alert information |  
|alert_urgency_level | integer – 4 levels of alert.  Document   what the four levels of alert are here).|	string | Yes | Alert  urgency level |  
|SourceSubsystem_webhook|	object | Yes | Takes the user straight to the alert details|
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}

Call getErrorDescription() to get the error description.  
  
  
## SendIncubatorAlert()  
Parameters  
   
|Field|	Type|	Required|	Description|  
|-----|-----|---------|------------|
|alert_component|string|Yes|Component that generated the alert|  
|alert_component_id|string|Yes|Entity associated with the   alert|  
|Message_id|uuid string|Yes|Unique alert identifier|  
|IncubatorAlert_data|String (should be an alert specific object).|Yes|Detailed alert information|  
|alert_urgency_level|integer – 4 levels of alert.  Document   what the four levels of alert are here).|Yes|Alert  urgency level|  
|SourceSubsystem_webhook|object|Yes|Takes the user straight  
to the alert details|

Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  

## SendGrowerRoomAlert()  
Parameters  

|Field|Type|Required|Description| 
|-----|----|--------|-----------| 
|alert_component|string|Yes|Component that generated the alert|  
|alert_component_id|string|Yes|Entity associated with the   alert|  
|Message_id|uuid|string|Yes|Unique alert identifier|  
|GrowerRoomAlert_data|String (should be an alert specific object).|Yes|Detailed alert information|  
|alert_urgency_level (integer)|4 levels of alert.  Document   what the four levels of alert are here).	string|Yes|Alert  urgency level|  
|SourceSubsystem_webhook|object|Yes|Takes the user straight to  the alert details|
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  
  
## SendSubsystemAlerts()  
  
|Field|Type|Required|Description|
|-----|----|--------|-----------|  
|alert_component|string|Yes|Component that generated the alert|  
|alert_component_id|string|Yes|Entity associated with the   alert|  
|alert_id|uuid string|Yes|Unique alert identifier|  
|alert_data|String|Yes|Detailed alert information|  
|alert_type|(integer)	string|Yes|Type/category of alert
|alert_urgency_level|(integer) – 4 levels of alert.  Document   what the four levels of alert are here).	string|Yes|Alert  urgency level|  
|SourceSubsystem_webhook|object|Yes|Takes the user straight   to the alert details|
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  
  
________________________________________  
## SendSeedCartridgeRecall()  
Parameters  

|Field|	Type|	Required|	Description|  
|-----|-----|---------|------------|
|Message_id|	string|	Yes|	Unique recall identifier|  
|Recall_source|	String| 	Yes|	What LGS sub-system the recall   originated from (for instance, Assembly, Farmer, LGS Retailer   etc|  
|Recall_reason|	string|	Yes|The reason for the recall.  For  example, problems found in seed cartridges or nutrient   packages or someone who does packaging is sick etc|  
|SourceSubsystem_webhook|	object|	Yes|	Takes the user straight to the recall details|  
|Recalled_lot_id|	string|	Yes	Lot Id where the recall occurred.|  
|Recalled_Palette_id|	string|	Yes|	Palette Id where the recall  occurred.|  
|Recalled_Carton_id|	string|	Yes|	Carton Id where the recall   occurred.|  

Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  
## SendLotRecall()  
Parameters  

|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|Message_id|	string|	Yes|	Unique recall identifier|  
|Recall_source|	String| 	Yes|	What LGS sub-system the recall   originated from (for instance, Assembly, Farmer, LGS Retailer   etc| 
|Recall_reason|	string|	Yes|	The reason for the recall.  For   example, problems found in seed cartridges or nutrient   packages or someone who does packaging is sick etc|
|SourceSubsystem_webhook|	object|	Yes|	Takes the user straight to the recall details|
|Recalled_lot_id|	string|	Yes|	Lot Id where the recall occurred.|  
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  

## SendBoxRecall()  
Parameters  
  
|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|Message_id|	string|	Yes|	Unique recall identifier|  
|Recall_source|	String| 	Yes|	What LGS sub-system the recall   originated from (for instance, Assembly, Farmer, LGS Retailer   etc  |
|Recall_reason|	string|	Yes|	The reason for the recall.  For   example, problems found in seed cartridges or nutrient   packages or someone who does packaging is sick etc|
|SourceSubsystem_webhook|	object||Yes|	Takes the user straight  to  the recall details |
|Recalled_Carton_id	|string|	Yes|	Carton Id where the recall   occurred. | 
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  

## SendPaletteRecall()  
Parameters  

|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|Message_id|	string|	Yes|	Unique recall identifier|  
|Recall_source|	String| 	Yes|	What LGS sub-system the recall   originated from (for instance, Assembly, Farmer, LGS Retailer   etc  |
|Recall_reason	|string|	Yes|	The reason for the recall.  For   example, problems found in seed cartridges or nutrient  packages or someone who does packaging is sick etc|  
|SourceSubsystem_webhook	|object|	Yes|	Takes the user straight to   the recall details  |
|Recalled_Palette_id	|string|	Yes|	Palette Id where the recall   occurred.  |
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  

  
  
## SendGerminatorSensorData()  
Parameters  
  
|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|sensor_id|	String (uuid)	|Yes|	Unique sensor message identifier  |
|Sensor_Data|	SensorJSON Object| 	No|	Additional sensor   
specific information|  
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  

 
  
## SendHarvestData()  
Parameters  
  
|Field|	Type|	Required|	Description| 
|-----|-----|---------|------------|
|harvest_id|	String (uuid)	|Yes|	Unique harvest identifier|  
|grow_unit_id|	String (uuid)| 	No|	Unique grow unit identifier|  
|grow_room_id| String (uuid)| No | Unique grow room identifier|
|grow_formula_id| String (uuid)| No | Unique grow formula identifier|  
|microgreen_tray_formula_id| String (uuid) | No | Unique microgreen Tray Formula Id|  
|expected_harvested_duration| number | No | Expected Harvest Duration in days|  
|farm_id| String (uuid) | No | Unique farm id |  
|Harvest_Lot_id | String (uuid) | No | Unique Harvest lot identifier|  
|Yield| number | No | The Yield|  
|Grade| string | No | The grade quality of the harvest|
|Color| string | No | THe color of the harvest|  
|width| number | No | The width of the harvest|  
|height | number | No | The height of the harvest|
|Brix_level|Number|No|The water solubility of the growing formula|  
|Vertical_Acre_Id| String (uuid) | No | The unique Vertical Acre Id|  
|Quarant_Id| string (uuid) | No | The unique quadrant Id|  




Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  


________________________________________  
## SendFeedback()  
Parameters  
  
|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|feedback_id|	String (uuid)|	Yes|	Unique feedback identifier|  
|Feedback_Data	|FeedbackJSON Object| 	No|	Additional sensor  specific information|  
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
  
    The method signature is:  

getErrorDescription  
	Parameter	error code (int)  
	Return value	error description (string)  
The error codes are described in the table below:  
    
________________________________________  
## SendQRScanCode()  
Parameters  

  |Field|	Type|	Required|	Description| 
|-----|-----|---------|------------|
|QRScan_id|	String (uuid)	|Yes|	Unique feedback identifier|  
|QRScan_Data|	QRScanJSON Object| 	No|	The QR Scan data| 


Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  
      
  
    The method signature is:  
  
getErrorDescription  
	Parameter	error code (int)  
	Return value	error description (string)  
The error codes are described in the table below:  
    
  
________________________________________  
## SendFoodSafetyData()  
Parameters  
   
|Field|	Type|	Required|	Description|
|-----|-----|---------|------------|  
|Product_id|	uuid string|	Yes|	Unique product identifier|  
|Hazard_id|	uuid_string	|No|	Unique hazard Id|  
|CAS_number|	uuid string|	No|	Unique numeric identifier  assigned by the Chemical Abstracts Service to every  
chemical substance described in scientific literature 
(First part contains 2-7 digits, second part contains 2   digits, third part contains a single check digit used to  verify accuracy.  |
|CS_Distribution_ID|	uuid string|	No|	A distribution ID|  
|Hairnet	|Bool|	No|	Did staff wear hairnet during food   
handling  |
|Gloves|	Bool|	No|	Did staff wear gloves during  
food handling|  
|Handwashing|	Bool|	No|	Did staff wash hands frequently  |
|Facility_Maintenance_Data|	String	|No|	Does the facility  
have non-absorbent, easy-to-clean walls and floors with   proper drainage and ventilation to stop condensation|  
|Equipment_Sanitation_data|	string|	No|	Does the equipment   utilize food-grade, non-corrosive metals that allow complete   disassembly for deep cleaning and testing.  |
  
Return value  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}   
  
Call getErrorDescription() to get the error description.  

    The method signature is:  
  
### getErrorDescription  
	Parameter	error code (int)  
	Return value	error description (string)  
  
The returned status  codes from each Send...method is   represented as an enum struct with each response code tied to a specific message.  

## Shared Error Responses  
  
|Return value	|  Condition  | Description |
| ------------| ----------- |-------------|  
| 400         | Bad Request	|The request body is malformed or required   fields are missing.|  
| 404         |  Not Found	| The requested endpoint does not exist | 
| 405         | Method Not Allowed|	Request uses a method other than POST | 
| 500         | Internal Server Error	| The server encountered an   unexpected error while processing the request.|  
| 500         | {Messaging system} Connection Error	| {Messaging system} connection refused | 
| 500         | {Messaging system} Publish Timeout	| {Messaging system}   broker request timed out|  
| 500         | {Messaging system} Serialization Error	| Failed to   serialize {Messaging system} message payload|  
 