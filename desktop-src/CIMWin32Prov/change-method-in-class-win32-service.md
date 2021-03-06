---
Description: Modifies a Win32\_Service.
ms.assetid: b32753c5-8fcf-44ee-a95f-e4f6076e0f28
ms.tgt_platform: multiple
title: Change method of the Win32_Service class (Mbnapi.h)
ms.topic: reference
ms.date: 05/31/2018
topic_type: 
- APIRef
- kbSyntax
api_name: 
- Win32_Service.Change
api_type: 
- COM
api_location: 
- CIMWin32.dll
---

# Change method of the Win32\_Service class

The **Change** [WMI class](https://docs.microsoft.com/windows/desktop/WmiSdk/retrieving-a-class) method modifies a [**Win32\_Service**](win32-service.md).

This topic uses Managed Object Format (MOF) syntax. For more information about using this method, see [Calling a Method](https://docs.microsoft.com/windows/desktop/WmiSdk/calling-a-method).

## Syntax


```mof
uint32 Change(
  [in] string  DisplayName,
  [in] string  PathName,
  [in] uint32  ServiceType,
  [in] uint32  ErrorControl,
  [in] string  StartMode,
  [in] boolean DesktopInteract,
  [in] string  StartName,
  [in] string  StartPassword,
  [in] string  LoadOrderGroup,
  [in] string  LoadOrderGroupDependencies[],
  [in] string  ServiceDependencies[]
);
```



## Parameters

<dl> <dt>

*DisplayName* \[in\]
</dt> <dd>

The display name of the service. This string has a maximum length of 256 characters. The name is case- preserved in the service control manager. *DisplayName* comparisons are always case-insensitive.

Constraints: Accepts the same value as the **Name** property.

Example, "Atdisk".

</dd> <dt>

*PathName* \[in\]
</dt> <dd>

The fully qualified path to the executable file that implements the service, for example, "\\SystemRoot\\System32\\drivers\\afd.sys".

</dd> <dt>

*ServiceType* \[in\]
</dt> <dd>

The type of services provided to processes that call them.

<dt>

1 (0x1)
</dt> <dd>

Kernel Driver

</dd> <dt>

2 (0x2)
</dt> <dd>

File System Driver

</dd> <dt>

4 (0x4)
</dt> <dd>

Adapter

</dd> <dt>

8 (0x8)
</dt> <dd>

Recognizer Driver

</dd> <dt>

16 (0x10)
</dt> <dd>

Own Process

</dd> <dt>

32 (0x20)
</dt> <dd>

Share Process

</dd> <dt>

256 (0x100)
</dt> <dd>

Interactive Process

</dd> </dl> </dd> <dt>

*ErrorControl* \[in\]
</dt> <dd>

Severity of the error if this service fails to start during startup. The value indicates the action taken by the startup program if failure occurs. All errors are logged by the system.

<dt>

<span id="Ignore"></span><span id="ignore"></span><span id="IGNORE"></span>

<span id="Ignore"></span><span id="ignore"></span><span id="IGNORE"></span>**Ignore** (0)


</dt> <dd>

User is not notified.

</dd> <dt>

<span id="Normal"></span><span id="normal"></span><span id="NORMAL"></span>

<span id="Normal"></span><span id="normal"></span><span id="NORMAL"></span>**Normal** (1)


</dt> <dd>

Normal. User is notified.

</dd> <dt>

<span id="Severe"></span><span id="severe"></span><span id="SEVERE"></span>

<span id="Severe"></span><span id="severe"></span><span id="SEVERE"></span>**Severe** (2)


</dt> <dd>

System is restarted with the last good configuration.

</dd> <dt>

<span id="Critical"></span><span id="critical"></span><span id="CRITICAL"></span>

<span id="Critical"></span><span id="critical"></span><span id="CRITICAL"></span>**Critical** (3)


</dt> <dd>

System attempts to restart with a good configuration.

</dd> </dl> </dd> <dt>

*StartMode* \[in\]
</dt> <dd>

Start mode of the Windows base service. For more information, see the Remarks section.

<dt>

Boot
</dt> <dd>

Device driver started by the operating system loader. This value is valid only for driver services.

</dd> <dt>

System
</dt> <dd>

Device driver started by the operating system initialization process. This value is valid only for driver services.

</dd> <dt>

Automatic
</dt> <dd>

Service to be started automatically by the Service Control Manager during system startup.

</dd> <dt>

Manual
</dt> <dd>

Service to be started by the Service Control Manager when a process calls the [**StartService**](startservice-method-in-class-win32-service.md) method.

</dd> <dt>

Disabled
</dt> <dd>

Service that can no longer be started.

</dd> </dl> </dd> <dt>

*DesktopInteract* \[in\]
</dt> <dd>

If **True**, the service can create or communicate with a window on the desktop.

</dd> <dt>

*StartName* \[in\]
</dt> <dd>

Account name the service runs under. Depending on the service type, the account name may be in the form of DomainName\\Username or .\\Username. The service process will be logged using one of these two forms when it runs. If the account belongs to the built-in domain, .\\Username can be specified. If **NULL** is specified, the service will be logged on as the LocalSystem account. For kernel or system-level drivers, *StartName* contains the driver object name (that is, \\FileSystem\\Rdr or \\Driver\\Xns) that the input and output (I/O) system uses to load the device driver. If **NULL** is specified, the driver runs with a default object name created by the I/O system based on the service name, for example, "DWDOM\\Admin".

You also can use the User Principal Name (UPN) format to specify the **StartName**, for example, *Username@DomainName*.

</dd> <dt>

*StartPassword* \[in\]
</dt> <dd>

Password to the account name specified by the *StartName* parameter. Specify **NULL** if you are not changing the password. Specify an empty string if the service has no password.

> [!Note]  
> When changing a service from a local system to a network, or from a network to a local system, *StartPassword* must be an empty string ("") and not **NULL**.

 

</dd> <dt>

*LoadOrderGroup* \[in\]
</dt> <dd>

Group name that it is associated with. Load order groups are contained in the system registry, and determine the sequence in which services are loaded into the operating system. If the pointer is **NULL**, or if it points to an empty string, the service does not belong to a group. For more information, see the Remarks section.

Dependencies between groups should be listed in the *LoadOrderGroupDependencies* parameter. Services in the load-ordering group list are started first, followed by services in groups not in the load-ordering group list, followed by services that do not belong to a group. The system registry has a list of load ordering groups located at:

**HKEY\_LOCAL\_MACHINE**\\**System**\\**CurrentControlSet**\\**Control**\\**ServiceGroupOrder**

</dd> <dt>

*LoadOrderGroupDependencies* \[in\]
</dt> <dd>

List of load-ordering groups that must start before this service starts. The array is doubly **null**-terminated. If the pointer is **NULL**, or if it points to an empty string, the service has no dependencies. Group names must be prefixed by the **SC\_GROUP\_IDENTIFIER** (defined in the Winsvc.h file) character to differentiate them from service names because services and service groups share the same namespace. Dependency on a group means that this service can run if at least one member of the group is running after an attempt to start all of the members of the group.

</dd> <dt>

*ServiceDependencies* \[in\]
</dt> <dd>

List that contains the names of services that must start before this service starts. The array is doubly **NULL**-terminated. If the pointer is **NULL**, or if it points to an empty string, the service has no dependencies. Dependency on a service indicates that this service can run only if the service it depends on is running.

</dd> </dl>

## Return value

Returns one of the values listed in the following list, or any other value to indicate an error. For additional error codes, see [**WMI Error Constants**](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-error-constants) or [**WbemErrorEnum**](https://docs.microsoft.com/windows/desktop/api/wbemdisp/ne-wbemdisp-wbemerrorenum). For general **HRESULT** values, see [System Error Codes](https://docs.microsoft.com/windows/desktop/Debug/system-error-codes).

<dl> <dt>

**Success**
</dt> <dd>

0

The request was accepted.

</dd> <dt>

**Not Supported**
</dt> <dd>

1

The request is not supported.

</dd> <dt>

**Access Denied**
</dt> <dd>

2

The user did not have the necessary access.

</dd> <dt>

**Dependent Services Running**
</dt> <dd>

3

The service cannot be stopped because other services that are running are dependent on it.

</dd> <dt>

**Invalid Service Control**
</dt> <dd>

4

The requested control code is not valid, or it is unacceptable to the service.

</dd> <dt>

**Service Cannot Accept Control**
</dt> <dd>

5

The requested control code cannot be sent to the service because the state of the service ([**Win32\_BaseService**](win32-baseservice.md).**State** property) is equal to 0, 1, or 2.

</dd> <dt>

**Service Not Active**
</dt> <dd>

6

The service has not been started.

</dd> <dt>

**Service Request Timeout**
</dt> <dd>

7

The service did not respond to the start request in a timely fashion.

</dd> <dt>

**Unknown Failure**
</dt> <dd>

8

Unknown failure when starting the service.

</dd> <dt>

**Path Not Found**
</dt> <dd>

9

The directory path to the service executable file was not found.

</dd> <dt>

**Service Already Running**
</dt> <dd>

10

The service is already running.

</dd> <dt>

**Service Database Locked**
</dt> <dd>

11

The database to add a new service is locked.

</dd> <dt>

**Service Dependency Deleted**
</dt> <dd>

12

A dependency this service relies on has been removed from the system.

</dd> <dt>

**Service Dependency Failure**
</dt> <dd>

13

The service failed to find the service needed from a dependent service.

</dd> <dt>

**Service Disabled**
</dt> <dd>

14

The service has been disabled from the system.

</dd> <dt>

**Service Logon Failed**
</dt> <dd>

15

The service does not have the correct authentication to run on the system.

</dd> <dt>

**Service Marked For Deletion**
</dt> <dd>

16

This service is being removed from the system.

</dd> <dt>

**Service No Thread**
</dt> <dd>

17

The service has no execution thread.

</dd> <dt>

**Status Circular Dependency**
</dt> <dd>

18

The service has circular dependencies when it starts.

</dd> <dt>

**Status Duplicate Name**
</dt> <dd>

19

A service is running under the same name.

</dd> <dt>

**Status Invalid Name**
</dt> <dd>

20

The service name has invalid characters.

</dd> <dt>

**Status Invalid Parameter**
</dt> <dd>

21

Invalid parameters have been passed to the service.

</dd> <dt>

**Status Invalid Service Account**
</dt> <dd>

22

The account under which this service runs is either invalid or lacks the permissions to run the service.

</dd> <dt>

**Status Service Exists**
</dt> <dd>

23

The service exists in the database of services available from the system.

</dd> <dt>

**Service Already Paused**
</dt> <dd>

24

The service is currently paused in the system.

</dd> <dt>

**Other**
</dt> <dd>

25 4294967295

</dd> </dl>

## Remarks

When a computer starts, all the autostart services also start. On occasion, one of these services might fail to start along with the computer. When a service fails during system startup, the computer takes action based on the value of the service error control code.

most services are installed using the Normal error control code. A few of the exceptions, which are installed using the Ignore error code, include:

-   File Replication Service
-   Smart Card
-   Secondary Logon
-   WMI

For the services installed using the Ignore error code, no notification is given to the user that the service has failed. If you prefer on-screen notification that a service could not start, you can use WMI to change the error control code. Error control codes apply only to computer startup; error control codes are not used if you stop and then attempt to restart a service after the computer is running.

On occasion, you might need to change the account under which a given service runs. For example, you might run a service under an administrative account. Because this can create a security vulnerability, you might switch the service to an account with fewer privileges. Alternatively, you might have services running under an account that is about to be deleted, or you might want to ensure that, on all your servers, certain services run under certain accounts. You can use the **Change** method of the [**Win32\_Service**](win32-service.md) class to configure services to run under a specified user account. When selecting an account, keep in mind the following:

-   The account being used as a service account must have the right to log on as a service. This right can be granted by using Group Policy.
-   The account being used as a service account should not be a member of a local, domain, or enterprise Administrators group.
-   Each instance of a service should run under a unique user account. This provides additional security, and enables the auditing of individual service instances.
-   If the service is interactive, then the service must run under the LocalSystem account.

    LocalSystem is required because only one window station (WinSta0) can be visible and interactive at a time. If a service runs under an account other than LocalSystem, it runs in the Service-0x03e7$\\Default window station, which is an invisible window. Services running in this window station cannot receive input or display output.

When you assign an account to a service, the SCM requires the correct password for that account before it makes the assignment. If you supply an incorrect password, the SCM rejects the account. If you configure a service account using the LocalSystem, LocalService, or NetworkService account, you do not need to supply an account password because these accounts do not have passwords.

The SCM stores the account password in the services database. After the password is assigned, however, the SCM does not ensure that the password stored in the services database and the password assigned to the user account in Active Directory continue to match. Consequently, a situation similar to the following could occur:

-   You configure a service to run under a particular user account.
-   The service starts up under that account by using the current account password.
-   You change the password for the user account.
-   The service continues to run. However, if the service stops, you cannot restart it because the SCM continues to use the old, invalid password. Changing the password in Active Directory does not change the password stored in the services database.

If you run services under regular user accounts, you need to update those service passwords each time the user account password changes. This can be particularly time-consuming if you are not sure which services are running under that account or which computers have services running under that account. Fortunately, you can use WMI to check the service accounts on all your computers and, if necessary, change the service account password.

The [**Win32\_LoadOrderGroup**](win32-loadordergroup.md) parameter represents a group of system services that define execution dependencies. The services must be initiated in the order specified by the Load Order Group because the services depend on each other. These dependent services require the presence of the antecedent services to function correctly.

To change a service from a network service to a local system the *StartName* and *StartPassword* parameters should have the following values:


```C++
StartName = "LocalSystem"
StartPassword = "" // - empty string, not NULL
```



To change a service from a local system service to a network the *StartName* and *StartPassword* parameters should have the following values:


```C++
StartName = "NT AUTHORITY\NetworkService"
StartPassword = "" // - empty string, not NULL
```



## Examples

The following VBScript changes the service account for services from running under a specified user account to LocalSystem.


```VB
strComputer = "."
Set objWMIService = GetObject("winmgmts:{impersonationLevel=impersonate}!\\" & strComputer & "\Root\CIMv2")
Set colServiceList = objWMIService.ExecQuery("SELECT * FROM Win32_Service WHERE StartName = '.\\NetSvc'")
For Each objService in colServices
 errServiceChange = objService.Change( , , , , , , ".\LocalSystem" , "")
Next
```



The following VBScript changes the service account password for all scripts running under Netsvc


```VB
strComputer = "."
Set objWMIService = GetObject("winmgmts:{impersonationLevel=impersonate}!\\" & strComputer & "\Root\CIMv2")
Set colServiceList = objWMIService.ExecQuery("SELECT * FROM Win32_Service WHERE StartName = '.\\NetSvc'")
For Each objservice in colServiceList
 errReturn = objService.Change( , , , , , , , "password")
Next
```



## Requirements



|                                     |                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista<br/>                                                                |
| Minimum supported server<br/> | Windows Server 2008<br/>                                                          |
| Namespace<br/>                | Root\\CIMV2<br/>                                                                  |
| Header<br/>                   | <dl> <dt>Mbnapi.h</dt> </dl>     |
| MOF<br/>                      | <dl> <dt>CIMWin32.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>CIMWin32.dll</dt> </dl> |



## See also

<dl> <dt>

[Operating System Classes](https://docs.microsoft.com/previous-versions//aa392727(v=vs.85))
</dt> <dt>

[**Win32\_Service**](win32-service.md)
</dt> <dt>

[WMI Tasks: Services](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-tasks--services)
</dt> </dl>

 

 




