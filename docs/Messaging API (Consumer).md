
# LGS Messaging API (Consumer)  
Version: 1.0.0  
________________________________________  
  
## Overview  
The Consumer Service API allows subsystems to register as   consumers of LGS Messaging topics and retrieve messages   published to those topics.  
Each subsystem is identified by a numeric ID, which maps to a   subsystem type based on predefined ID ranges.  
Subsystem ID Mapping  
Each numeric subsystem ID corresponds to a subsystem type..    This should be an enumerated type.  
  
|ID Range | Subsystem | 
|---------| --------- |
|0 – 332  |	Germinator | 
|333 – 666|	Gardener  |
|667 – 999|	Pavillion | 
|1000 – 1999|	Inspector | 
|2000 – 2999|	Barn      |
|3000 – 3999|	Director  |
|4000 – 4999|	Assembly  |
|5000 – 5999|	Network   |
|6000 – 6999|	Farmer    |  
  
  
## Package  
The API endpoints will be wrapped around in a package.  The   package will hide the endpoints from the end user and instead   expose the following methods:  
________________________________________  

## Register() 
   Registers the subsystem to the messaging system consumer.  

ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
}   
ConsumerToken – a token that uniquely identifies the consumer.  
  
Data – the alert data  
  
errorCode - an enum value representing the HTTP status 
            code  returned by the underlying   endpoint.  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}

Call getErrorDescription() to get the error description.  
  
Additional Methods  
  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   
     HTTP error code.  
  
________________________________________  
  
## ConsumeEquipmentAlert()  

|Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  
  
ReturnType {  
        ConsumerToken: …  
        EquipmentAlert_Data: ….  
        errorCode: ….  
}
  
ConsumerToken – a token that uniquely identifies the consumer.  
  
EquipmentAlert_Data – the Equipment alert data  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}

Call getErrorDescription() to get the error description.  
  
Additional Methods  
  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   HTTP error code.  
________________________________________  
  
  
## ConsumeVerticalAcreAlert()  
  
|Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |
  
ReturnType {  
        ConsumerToken: …  
        VerticalAcreAlert_Data: ….  
        errorCode: ….  
}   
  
ConsumerToken – a token that uniquely identifies the consumer.  
  
VerticalAcreAlert_Data – the Vertical Acre alert data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description. 
   
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified  
      HTTP error code.  
  
  
## ConsumeHVACAlert()  

|Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |
  
ReturnType {  
        ConsumerToken: …  
        HVACAlert_Data: ….  
        errorCode: ….  
}  

ConsumerToken – a token that uniquely identifies the consumer.  
  
HVACAlert_Data – the HVAC alert data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}  
  
Call getErrorDescription() to get the error description.  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified HTTP error code.  
________________________________________  
  
## ConsumeTemperatureOutofSyncAlert()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |

ReturnType {  
        ConsumerToken: …  
        TemperatureOutOfSyncAlert_Data: ….  
        errorCode: ….  
}   
  
ConsumerToken – a token that uniquely identifies the consumer.  
  
TemperatureOutOfSyncAlert_Data – the Temperature Out-of-Sync alert data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"   500}  
  
Call getErrorDescription() to get the error description.  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   
     HTTP error code.  
________________________________________  
  
## ConsumeSubsystemAlert()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |

ReturnType {  
        ConsumerToken: …  
        SubsystemAlert_Data: ….  
        errorCode: ….  
}   
  
ConsumerToken – a token that uniquely identifies the consumer.  
  
SubsystemAlert_Data – the Subsystem alert data  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods    
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified HTTP error code.  
________________________________________  
## ConsumeGrowerRoomAlert()  
  
|Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |

ReturnType {  
        ConsumerToken: …  
        GrowerRoomAlert_Data: ….  
        errorCode: ….  
}  
     
ConsumerToken – a token that uniquely identifies the consumer.  
  
GrowerRoomAlert_Data – the Grower Room alert data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
    
Call getErrorDescription() to get the error description.  
  
Additional Methods  
  
String getErrorDescription(int errorCode)    
	 Returns the description associated with the specified     
     HTTP error code.  
  
________________________________________  
  
## ConsumeIncubatorAlert()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  
  
ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
}   
  
ConsumerToken – a token that uniquely identifies the consumer.  

IncubatorAlert_Data – the Incubator alert data  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not  Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)    
	 Returns the description associated with the specified   
     HTTP error code.  
________________________________________  
  
## ConsumeSeedCartridgeRecall()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |

	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: …  
}   
  
ConsumerToken – a token that uniquely identifies the consumer.  
  
SeedCartridgeRecall_Data – the Seed Catridge Recall data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}    
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   
     HTTP error code.  
  
________________________________________  
  
## ConsumeLotRecall()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |
  
	ReturnType {  
        ConsumerToken: …  
        LotRecall_Data: ….  
        errorCode: ….  
} 
    
ConsumerToken – a token that uniquely identifies the consumer.  
  
LotRecall_Data – the Lot Recall data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  

Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified     HTTP error code.   
       
________________________________________  
## ConsumeBoxRecall()  
  
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  


	ReturnType {  
        ConsumerToken: …  
        BoxRecall_Data: ….  
        errorCode: ….  
}  
    
ConsumerToken – a token that uniquely identifies the consumer.  
  
BoxRecall_Data – the Box Recall data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not  Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   HTTP error code.  
  
________________________________________  
## ConsumePaletteRecall()  

  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  


	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
}   
ConsumerToken – a token that uniquely identifies the consumer.  
  
PaletteRecall_Data – the Palette Recall data  
    
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified  
     HTTP error code.  
  
________________________________________  
  
## ConsumeSensorData()  
	
  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  


	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
} 
    
ConsumerToken – a token that uniquely identifies the consumer.  
  
Data – the Sensor data
    
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not Found=404, "Method Not Allowed" = 405, "Internal Server error" 500}
    
Call getErrorDescription() to get the error description.    
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified  
      HTTP error code.  
  
________________________________________  
## ConsumeHarvestData()  

  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  


	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
} 
    
ConsumerToken – a token that uniquely identifies the consumer.  
  
Harvest_Data – the Harvest Data  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   
     HTTP error code.  
  
________________________________________  
## ConsumeFeedback()  
  
|Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  


	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
}  

ConsumerToken – a token that uniquely identifies the consumer.  
  
Feedback_Data – the Feedback data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.
    
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified  
    HTTP error code.  

________________________________________  
## ConsumeQRScanCode()  

  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  

	ReturnType {  
        ConsumerToken: …  
        Data: ….  
        errorCode: ….  
}  

ConsumerToken – a token that uniquely identifies the consumer.  
  
QRScan_Data – the QR Scan data  
  
enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}  
  
Call getErrorDescription() to get the error description.  
  
Additional Methods  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   
     HTTP error code.  
  
________________________________________  
## ConsumeFoodSafetyData()  

  |Parameter	| Type| Required| Description|  
|-----------|-----|---------|------------|
|subsystem_id	|string 	|Yes	|Numeric subsystem ID |  

	ReturnType {  
        ConsumerToken: …  
        FoodSafety_Data: ….  
        errorCode: ….  
}   
ConsumerToken – the consumer token.  
  
FoodSafety_Data – the Food Safety data  

enum errorCode = {"Success" = 200, "Bad request" = 400, "Not   Found=404, "Method Not Allowed" = 405, "Internal Server error"  500}
  
Call getErrorDescription() to get the error description.  
  
### Additional Method  
String getErrorDescription(int errorCode)  
	 Returns the description associated with the specified   error code.  

       
         ## Shared Error codes legend
| Error code |	Condition | 
| ---------- | ---------- | 
|    400     | Bad Request	Missing subsystem_id |  
|    400     | Bad Request	Invalid subsystem_id(non-numeric) |  
|    400     | Bad Request	Malformed request |  
|    405     | Method Not Allowed Request uses a method other than GET  |
|   404        | Not Found Consumer not registered for alerts | 
|   422        | Unprocessable Entity The harvest_data topic   
                   is  invalid   for subsystem_id  |
|   422      | Unprocessable Entity	subsystem_id outside of    
                        valid   ranges  |
|   500      | Internal Server Error {Messaging system  
                      connection  refused |  
|   500      | Internal Server Error	{Messaging system} 
               broker request   timed out |  
|   500      | Internal Server Error Failed to deserialize  
                    {Messaging   system} message payload |  
  

________________________________________  