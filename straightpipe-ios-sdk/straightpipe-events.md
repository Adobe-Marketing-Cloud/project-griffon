# Sending events

The SDK enables the user to send data to the Straightpipe backend using the `sendEvent` API. This API  requires an SPIEvent instance to be passed in, which encapsulates the data in a format that the Straightpipe service expects.

## SPIEvent class

### initWithVendor:type:payload

Initializes the SPIEvent with the vendor, type, and payload.

#### Declaration

```objectivec
- (instancetype) initWithVendor: (NSString*) vendor type: (NSString*) type payload: (NSDictionary*) payload;
```

#### Parameters

Here are the parameters for this event:

**vendor**  
Identifies the event, and the string can be a reverse domain name format to uniquely identify the vendor.

**type**  
The type of the event.

**payload**  
The payload to be sent, which is wrapped in the event. This payload is serialized in JSON in the transport process.

#### Return

An SPIEvent instance.

#### Sample Code

```objectivec
id vendorId = @"com.myapp.vendor";
id eventType = @"type";
NSDictionary* payload_dict = @ {
@"key": @"value"
};

SPIEvent* event = [[SPIEvent alloc] initWithVendor:vendorId type:eventType payload:payload_dict];
```

### initWithJSONData:

Creates an SPIEvent instance with the required parameters specified in a JSON object.

#### Declaration

```objectivec
- (instancetype) initWithJSONData: (NSData*) json;
```

#### Parameters

**json**  
The JSON for the event.

#### Description 

The Json keys required are:

 eventID - Required - A unique UUID string to identify the event

 vendor - Required - A vendor string

 type - Required - A type string for the event

 payload - Optional - A JSON Object for the payload

 pairID - Optional - The eventID of the event this is a response for

#### Return

The SPIEvent instance. Returns `nil` if any of the required parameters are not present in the JSON file.

#### Sample Code

```objectivec
    NSDictionary* jsonObject = @ {
                                @"eventID" : @"eventidhash",
                                @"sessionID" : sessionId,
                                @"type" : eventType,
                                @"vendor" : vendorId,
                                @"payload" : payload_dict
                                };

    NSError* error = nil;
    NSData* data = [NSJSONSerialization dataWithJSONObject:jsonObject options:0 error:&error];

    if (error) {
        //Log error and bail!
    }

    SPIEvent* event = [[SPIEvent alloc] initWithJSONData:data];
```

#### 

