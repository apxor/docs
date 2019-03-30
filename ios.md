### iOS {docsify-ignore}

#### Initializing the library
To start tracking with the Apxor iOS SDK, you must first initialize it with your Apxor ID. To initialize the SDK,

```objc
[ApxorSDK initialize:@"<YOUR_APXOR_ID>"];
```

#### Identifying Users

The Apxor SDK automatically captures device IDs which the Apxor backend uses to uniquely identify users.

If you want to, you can assign your own user IDs. This is particularly useful if you want to study a specific user with ease. To assign your own user ID, you can use

```objc
[ApxorSDK setUserIdentifier:@"1729"];
```

#### User Attributes

There is often additional user identifying information, such as name and email address, connected with the external IDs.

To add some more attributes that are specific to a particular user,

```objc
NSDictionary *info = [[NSDictionary alloc] init];
[info setValue:@"email" forKey:@"spock@vulcan.com"];
[info setValue:@"location" forKey:@"In a galaxy far far away"];
[ApxorSDK setUserCustomInfo:info];
```

#### Session Attributes

A Session can be simply defined as user journey as he opens the app, until he closes the app. There can be various pieces of information that be very impactful when accumulated in a session. For example, location in a session can be useful to know exactly where, the user is utilizing the app most.

To add session attributes that are specific to a session,

```objc
NSDictionary *info = [[NSDictionary alloc] init];
[info setValue:@"email" forKey:@"spock@vulcan.com"];
[info setValue:@"location" forKey:@"In a galaxy far far away"];
[ApxorSDK setSessionCustomInfo:info];
```

#### Reporting Custom Errors

Custom errors describe situations like LOGIN_FAILED, NETWORK_CALL_FAILED and are to be treated differently compared to app events. So these are treated as errors and are shown on the issues page to let you know their impact.

A custom error takes the exception itself and some context (what? OR which?) to make it easy for you identify. To report a custom error,

```objc
NSError *error = [NSError errorWithDomain:NSURLErrorDomain code:-1007 userInfo:nil];
NSDictionary *userInfo = @{@"Error_function":@"getImages"};
[ApxorSDK reportCustomError:error withInfo:userInfo];
```

#### App Events

App events make it easier to analyze user behavior and optimize your product and marketing around common business goals such as improving user retention or app usage. You can also add additional information for any event.

Currently, we are supporting NSString, NSNumber, NSArray objects only to be passed as additional Info (without nesting)

To track an event with the event name and properties.

```objc
NSDictionary *info = [[NSDictionary alloc] init];
[info setValue:@"event_type" forKey:@"SelectLanguage"];
[info setValue:@"language" forKey:@"Valyrian"];
[ApxorSDK logAppEventWithName:@"LANG_SELECT" info:info];
```