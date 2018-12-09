API Status Call

**Call**:  [https://api.vfs.velma.com/v1/system/status](https://api.vfs.velma.com/v1/system/status)  **Method Type:**  GET

```json
{
  "status": "Available",
  "code": "900.0.0",
  "message": "All VFS subsystems are in working order"   
}
```
**Statuses**

Status Codes

**Description**

900.0.0

**Available** - VFS is currently accepting requests and all subsystems are in good working order

900.1.0

**Not Available** - VFS is currently not accepting requests

900.2.0

**Limited Availability** - VFS is accepting requests but has limited availability

900.3.0

**Maintenance** - VFS is currently in maintenance mode and not accepting requests

**Available**

-   VFS is currently accepting requests and all subsystems are in good working order

**Not Available**

-   VFS is currently not accepting requests Possible causes: VFS encountered an emergency situation and had to be temporarily shut down

**Notifications**:

-   A notification will be sent to VFS sponsors if this is necessary

**Sponsor actions:**

-   All VFS command package submissions should be halted

**Limited Availability**

-   VFS is accepting requests but has limited availability This could potentially affect the following:

    -   Email disposition responses
    -   Email submissions
    -   In Process Failure responses

    **Sponsor actions:**

    -   All VFS command package submissions can continue but email disposition responses, in process failure responses and email submissions will potentially be delayed

**Maintenance**

-   VFS is currently in maintenance mode and not accepting requests
    -   **Possible causes**:
        -   The system has been set for an upgrade
        -   There was an issue and the system is scheduled for a hot fix  **_Note:_**  All scheduled maintenance will be performed outside of normal business operating hours
    -   **Notifications**:
        -   A Notification will be sent to VFS sponsors when scheduled maintenance is planned
