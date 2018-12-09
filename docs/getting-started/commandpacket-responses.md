The ***jobid*** is created for the command packet and will be used for tracking
- **jobid**: This is in following format.
  - **type**: VE: (Email job) :  VP  (Print Job - currently In development)
  -  **date**: 20160711 - YYYY MM DD
  - **guid**: 164624cf4caafd - Unique for VFS
- **code**: From the Response code table below
- **status**: success, failure
- **message**: Details of the issue

There are three types of responses that can be returned from a job post request.

1. A Successful Submission Response (If validateOnly is set to false)
2. A Submission Failure Response (If a request failed to validate or otherwise failed)


### Successful Submission Response
Here is the response you will receive from a successful command packet submission:
```json
 {
     "jobid":"VE20160711164624cf4caafd",
     "code":"100.0.0",
     "status":"success",
     "message":"Successful Submission"
  }
```

### Submission Failure Response
Here is the response you will receive from a failure occurs while processing the command packet:
```json
{
    "code": "[CODE]",
    "status": "failure",
    "message": "[DETAIL]"
}
```
