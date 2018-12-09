### Callback Events

The structure of the post object sent to this callback is consistant between all event types. Only the attributes contained in the <code>attr</code> field will change.

```json
{
  "jobid":"VE2018032518574086823ae0",
  "itemId":"2f8b2b67dd1b4353b3ddb889fbee39c1",
  "eventId": "06de4508-8337-4b21-b09e-6b1d87eba14e",
  "type":"Sent",
  "timestamp": "1457141619",
  "attr": { ... }
}
```

|Field  |Description  |
|--|--|
| jobId |The jobId with which this email is associated.  |
| itemId |The unique ID for this email.  |
| eventId |An internal ID that identifies this event specifically.  |
| type |The type of event that has been raised. |
| timestamp |The time the event was raised as a Unix timestamp.  |
| attr |A map containing details specific to the type of event that has been raised.  |


### Dropped Event

The Dropped Event is raised when the recipient is known to VFS as a non-deliverable target.  This can be due to one of the following reasons:

* The recipient is on a global suppression list.
* The recipient is on a local suppression list.
* The recipient has previously unsubscribed.

#### Dropped Event Attributes

```json
{
  "reason": "Global Suppression",
  "code": "100.0.0"
}
```

|Field   |Description   |
|---|---|
|reason   | A text explanation of the reason. Possible values are TBD  |
|code   | A VFS response code that identifies the failure reason. These codes are TBD  |

<hr>


### Failed Event

The Failed Event is raised when a job item could not be processed due to an error or impossible resolution. This can be due to bad content in user data or other issues in processing a request.

#### Failed Event Attributes

```json
{
  "reason": "Missing Token.",
  "code": "100.0.0"
}
```

|Field   |Description   |
|---|---|
|reason   | A text explanation of the reason. Possible values are TBD  |
|code   | A VFS response code that identifies the failure reason. These codes are TBD  |

<hr>


### Sent Event

The Sent event is raised when a job item has been placed on the SMTP network. Sent events have no event attributes.

<hr>


### Deferred Event

The deferred event is raised when an email has been delayed due to network or MTA issues. The message will be retried.


#### Deferred Event Attributes

```json
{
  "attempts": 2,
  "reason": "Network not available."
}
```

|Field   |Description   |
|---|---|
|attempts | An integer representing the number of times this message has been attempted. |
|reason   | The message received from MTA in the attempt. |

<hr>


### Hard Bounce Event

The Hard Bounce Event is raised when an email was not deliverable due to an invalid mailbox.

#### Hard Bounce Event Attributes

```json
{
  "reason": "Bad destination mailbox address.",
  "statusCode": "5.1.1"
}
```

|Field   |Description   |
|---|---|
|reason | The MTA Message that describes the reason. |
|statusCode | The EMSSC status code from or derived from the MTA message. |

<hr>

### Soft Bounce Event
The Soft Bounce Event is raised when an email was not deliverable due to issue with the destination or path to the destination mailbox.

#### Soft Bounce Event Attributes

```json
{
  "reason": "Mailbox disabled, not accepting messages.",
  "statusCode": "5.2.1"
}
```

|Field   |Description   |
|---|---|
|reason | The MTA Message that describes the reason. |
|statusCode | The EMSSC status code from or derived from the MTA message. |

<hr>

### Delivered Event
The Delivered Event is raised when the email has been accepted by the receiving mailbox.

#### Delivered Event Attributes

```json
{
  "response": "250 Requested mail action okay, completed."
}
```

|Field   |Description   |
|---|---|
|reason | The message received from the MTA. |

<hr>

### Opened Event
The Opened Event is raised when the recipient has opened the email.

#### Opened Event Attributes

```json
{
    "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.118 Safari/537.36",
    "ipAddr": "207.170.247.50",
}
```

|Field   |Description   |
|---|---|
|userAgent | The user-agent provided at the time of the reqeuset for the resource (tracking image). |
|ipAddr | The end-users IP Address are recorded by the server handling the resource request (tracking image). |

<hr>

### Clicked Event
The Clicked Event is raised when the recipient follows a link provided in the email content.

#### Clicked Event Attributes

```json
{
    "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.118 Safari/537.36",
    "ipAddr": "207.170.247.50",
    "url": "http://velma.com/foo/bar"
}
```

|Field   |Description   |
|---|---|
|userAgent | The user-agent provided at the time of the request for the resource (url). |
|ipAddr | The end-users IP Address are recorded by the server handling the resource request (url). |
|url | The resource requested by the user. |

<hr>

### Complaint Event
The Complaint event is raised when a recipient reports the given message as spam. There are no attributes for this event.

<hr>

### Unsubscribe Event
The Unsubscribe event is raised when a recipient follows the Unsubscribe link to opt-out of future emails from the sender. There are no attributes for this event.
