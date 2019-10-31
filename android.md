### Android {docsify-ignore}

#### Initializing the Apxor SDK

To start tracking with the Apxor Android SDK, you must first initialize it with your project token. To initialize the SDK,

```java
ApxorSDK.initialize(<APXOR_ID> , this.getApplicationContext());
```

#### Identifying Users

The Apxor SDK automatically captures device IDs which the Apxor backend uses to uniquely identify users.

If you want to, you can assign your own user IDs. This is particularly useful if you want to study a specific user with ease. To assign your own user ID, you can use

```java
ApxorSDK.setUserIdentifier(<SOME_USER_ID>);
```

#### User Attributes

There is often additional user identifying information, such as name and email address, connected with the external IDs.

To add some more attributes that are specific to a particular user,

```java
Attributes userInfo = new Attributes();
userInfo.putAttribute("age", 27);
userInfo.putAttribute("gender", "Male");
ApxorSDK.setUserCustomInfo(userInfo);
```

#### Session Attributes

A Session can be simply defined as user journey as he opens the app, until he closes the app. There can be various pieces of information that be very impactful when accumulated in a session. For example, location in a session can be useful to know exactly where, the user is utilizing the app most.

To add session attributes that are specific to a session,

```java
ApxorSDK.setSessionCustomInfo("network", "4G");
```

Or if you have multiple key value pairs that need to be logged, you can simply put them in a hashmap like,

```java
Attributes sessionInfo = new Attributes();
sessionInfo.putAttribute("network", "4G");
sessionInfo.putAttribute("city", "GAJ");
ApxorSDK.setSessionCustomInfo(sessionInfo);
```

#### Reporting Custom Errors

Custom errors describe situations like LOGIN_FAILED, NETWORK_CALL_FAILED and are to be treated differently compared to app events. So these are treated as errors and are shown on the issues page to let you know their impact.

A custom error takes the exception itself and some context (what? OR which?) to make it easy for you identify. To report a custom error,

```java
Exception e = new Exception("LOGIN FAILED EXCEPTION");
HashMap<String, String> additionalInfo = new HashMap<>();
additionalInfo.put("email", "spock@vulcan.com");
additionalInfo.put("cause", "network failure");
ApxorSDK.reportCustomError("Null Value", additionalInfo, e);
```

#### App Events

App events make it easier to analyze user behavior and optimize your product and marketing around common business goals such as improving user retention or app usage. You can also add additional information for any event.

To track an event with the event name and properties.

```java
Attributes additionalInfo = new Attributes();
additionalInfo.putAttribute("type", "Google");
additionalInfo.putAttribute("language", "Valyrian");
ApxorSDK.logAppEvent("Login", additionalInfo);
```

#### Aggregate Events

<!-- Description about Aggregate Event -->

```java
Attributes additionalInfo = new Attributes();
additionalInfo.putAttribute("card_type", "Text");
additionalInfo.putAttribute("id", "46Juzcyx");
ApxorSDK.logAppEvent("Impression", additionalInfo, true);
```

#### Client Events

<!-- Description about Client Event -->

```java
Attributes additionalInfo = new Attributes();
additionalInfo.putAttribute("type", "Google");
additionalInfo.putAttribute("language", "Valyrian");
ApxorSDK.logClientEvent("Login", additionalInfo);
```
