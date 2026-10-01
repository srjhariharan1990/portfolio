# User Roles and Application Permissions

**Audience:** System administrators, database administrators, and application users  
**Sample type:** Adapted and generalized technical writing sample

> This sample describes an illustrative analytics application. Product names, branded interface labels, proprietary script names, and internal documentation links have been removed or generalized. The permissions described here are adapted from a specific product and do not represent a universal access model.

## User role

If your role is **User** and you have no application permissions, you can access designated shared, personal, and sample folders in the file catalog. You can also download desktop tools from the administration console and access learning resources.

To work with an application, you must receive additional access from an authorized administrator. An application contains one or more analytical databases, referred to as **cubes** in this sample. You can see only the applications and cubes for which you have permission.

Permissions are assigned separately for each application. For example, you can have **Database Access** permission for one application and **Database Manager** permission for another.

## Application permission hierarchy

Application permissions range from least privileged to most privileged as follows.

| Permission | Primary capability |
| --- | --- |
| None | No application access has been granted. |
| Database Access | View cube data and metadata, subject to access filters. |
| Database Update | Perform permitted data updates and run supported data operations. |
| Database Manager | Manage cubes, database objects, and cube-level settings. |
| Application Manager | Manage the application and its cubes, including application permissions and settings. |

Each level above Database Access includes the capabilities of the preceding level. Filters, calculation-script permissions, ownership, cube type, and enabled features can impose additional conditions.

## Database Access permission

With **Database Access** permission, you can view data and metadata in the cubes within an application.

### Data access and restrictions

- Filters can restrict the data and metadata you can view.
- A filter can grant write access to specific cube regions, even when your application permission is Database Access.
- You can use available drill-through reports to access external source data when filters permit access to the relevant cube cells.

**Important:** Database Access is not necessarily read-only. The effective access also depends on assigned filters.

### Available operations

You can:

- View the cube outline.
- Download files and artifacts from application and cube directories.
- Build aggregations for aggregate storage cubes.
- Run multidimensional query scripts.
- View database size and monitor your own sessions in the administration console.

### Scenario participation

If you are a scenario participant, you can view base data and scenario changes. If you are a scenario approver, you can approve or reject a scenario.

## Database Update permission

With **Database Update** permission, you can perform all operations available with Database Access permission. You can also:

- Load, update, and clear cube data.
- Export cube data in tabular format.
- Run calculation scripts for which you have execution permission.
- Create, manage, and delete your own scenarios in block storage cubes with scenario management enabled.

**Note:** Database Update permission does not automatically grant permission to execute every calculation script.

## Database Manager permission

With **Database Manager** permission, you can perform all operations available with Database Update permission and manage the cubes within the application.

### Cube structure and lifecycle

You can:

- Upload files to cube directories.
- Edit cube outlines and build dimensions.
- Manage dimension generation and level names.
- Export data and export cubes to application workbooks.
- Start and stop cubes from the web interface.
- Enable scenarios and change the number of scenarios allowed.

### Files and scripts

You can access and manage database files, including creating and editing:

- Calculation scripts.
- Drill-through reports.
- Administrative command scripts.
- Multidimensional query scripts.
- Report scripts.
- Rules files for dimension building and data loading.

You can also assign users permission to execute calculation scripts.

### Data access filters

You can create and assign filters that grant or restrict data access for specific users and groups.

**Important:** You can assign cube filters only to users and groups already provisioned for the application. An Application Manager or a higher-level administrator must grant the underlying application access.

### Settings and monitoring

You can:

- Manage cube-level substitution variables.
- View locked cube objects and data blocks.
- View and change database settings.
- View database statistics.
- View and export audit records through the web interface.

To access these tasks, select the database in the application interface and open the relevant management area. Navigation labels depend on the implementation.

## Application Manager permission

With **Application Manager** permission, you can perform all operations available with Database Manager permission for every cube in the application. You can also manage application-wide access, configuration, and resources.

### Application and cube lifecycle

You can:

- Copy cubes within the application.
- Start and stop the application.
- View and terminate user sessions in the administration console.
- Run administrative command scripts.
- Export cube artifacts to a backup archive using the lifecycle export operation.
- Purge cube audit records.

### Ownership requirements

Application Manager permission alone does not authorize every copy or delete operation:

- You can copy or delete an application only if you are its owner—the privileged creator account in this illustrative model.
- You can delete a cube only if you are its owner—the privileged creator account in this illustrative model.

### Application administration

You can:

- Access and manage application files.
- Manage application-level connections and data sources for external data access.
- Change application configuration and general settings.
- Provision and manage user and group permissions for the application and its cubes.
- Add and remove application-level substitution variables.
- View application statistics.
- Download application logs.

To access these tasks, select the application and open the appropriate settings or administration area. Related tasks may be grouped together in the interface.

## Access examples

| Situation | Access consideration |
| --- | --- |
| A user needs to view cube data. | Database Access may be sufficient, subject to filters. |
| A user needs to load data. | Database Update or a higher permission is required. |
| A user needs to run a calculation script. | Database Update or higher is required, together with permission to execute the script. |
| A manager needs to assign a data filter to a new user. | The user must first be provisioned for the application by an Application Manager or higher. |
| An administrator needs to manage application-wide user permissions. | Application Manager or a higher administrative role is required. |
| An Application Manager needs to delete a cube. | The ownership requirement must also be satisfied. |

*This adapted sample demonstrates permission documentation and conditional access explanations. Confirm permission to publish company-derived material before sharing it externally.*
