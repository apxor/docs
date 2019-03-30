### Web {docsify-ignore}

#### Initialize Apxor SDK 
- **Single Page Applications**: in root of your application
- **Server Rendering Applications**: inside `<head>` tag of every page you want to track.

```javascript
Apxor.init('YOUR_SITE_ID', {/*Config*/});
```

##### Configuration Options

- **debug**: _boolean_ [false],
- **honorDNT**: _boolean_ [false],
- **idle_time_out**: _number(seconds)_ [3600]


#### APIs:

To get started with any of the following APIs first import the Apxor Library using

```javascript
import Apxor from 'apxor';
```


##### Identifying Users

You can assign your own user IDs. This is particularly useful if you want to study a specific user with ease. To assign your own user ID, you can use

```javascript
Apxor.setUserId(String);
```
    
> Eg:
```javascript
Apxor.setUserId("user@example.com");
```
    
***

##### Track Screen View:

For SPA, use the following to log the page view for client side rendering applications, this notifies the SDK about the change in the page being currently viewed. This is strictly not for Server rendering applications.

```javascript
Apxor.logPageView(location.pathname); //String URL pathname
```

> Eg:
```javascript
Apxor.logPageView("/about.html");
```
    
***
    
##### App Events:

Events make it easier to analyze user behavior and optimize your product and marketing decisions around common business goals. You can also add additional information for that event that you feel is important to analyze later.

To track an event with the event name and properties.

```javascript
Apxor.logEvent(name, properties, [category]);
```
    
> Eg:
```javascript
Apxor.logEvent("ADD_TO_CART", {
    "userId": "user@example.com",
    "value": 1299,
    "item": "Sony Head Phone 1201" 
}, "PRODUCT_PURCHASE");
```
    
***
    
##### User Attributes:

There is often additional user identifying information, such as name and email address, connected with the external IDs.

To add some more attributes that are specific to a particular user,

```javascript
Apxor.setUserProperties({
    "property1": "value",
    "property2": "value2"
});
```
    
> Eg:
```javascript
Apxor.setUserProperties({
    "gender": "male",
    "age": "24"
});
```
    
***

##### Session Attributes:

A Session can be simply defined as user journey as he opens the site, until he closes it. There can be various pieces of information that be very impactful when accumulated in a session.

To add session attributes that are specific to a session,

```javascript
Apxor.setSessionProperties({
    "property1": "value",
    "property2": "value2"
});
```
    
> Eg:
```javascript
Apxor.setSessionProperties({
    "language": "en",
    "location": "Hyderabad"
});
```

***

##### App | Site Version:

A unique version to identify your particular release.

```javascript
Apxor.setAppVersion(version);
```
    
> Eg:
```javascript
Apxor.setAppVersion("1.2.3");
```