# User Guide: App Connectors [Download :fontawesome-solid-file-pdf:](/assets/connectors-guide.pdf){ .md-button .md-button--primary }

!!! Summary
    What does this guide do?

## Get Started with Insights Connectors 

Identity Security Insights connectors represent integrations with both first- and third-party software. The connectors dashboard allows you to add new connectors, manage or remove existing connectors, and view each connector's status and current connectivity.

After logging in, the connectors dashboard is available by selecting your desired tenant from the home screen, and clicking View Connectors in the tenant console.
Manage Existing Connectors

From the connectors dashboard, existing connectors can be managed from the Configured tab. The list of existing connectors provides additional information regarding connection status and connectivity, as well as high-level information like connector type, name, and activity.
Connection Options

Clicking on the ellipsis beside any connector provides a list of management options.

    View Connector displays the connector's detailed information.
    Turn Off Connector pauses any scans and new recommendations. Connectors which have been turned off can be turned on again from the same menu.

The Microsoft Active Directory connector cannot be turned off from this menu.

    Delete Connector removes the connector entirely. Deleted connectors must be added again from the Available Connectors tab.

Connectivity and Status

Connectors with a Status set to On actively scan and provide recommendations for the source service. Connectors with a status of Off have been paused, and do not scan the service or provide new recommendations until manually turned on.

Connectivity displays whether or not the connector is appropriately configured.

    Connected: The connector is appropriately configured, and is able to scan and provide recommendations for the source service.
    Failed: The connector is unable to scan or communicate with the source service.
    Connector Off: The connector has been paused from scanning and providing recommendations.
    Pending Agent Registration: In the case of Microsoft Active Directory, the connector is waiting to be registered with the installer.

Connection Details

Clicking View Connector from the Configured connectors list displays detailed information for the selected connector.

The connection Overview displays high-level information about the selected connector. From this window, the connection name can be edited, and the connector can be turned off, on, or deleted.

Settings allows you to review the connection information for your selected connector. Depending on the connector type, you can update configuration requirements such as the connector's domain, API keys, usernames, authentication rules, and other credentials.

Activity History displays a list of the date and time of any updates or changes made to the connector.
View Available Connectors

New connectors can be added from the Available tab.

Clicking Add beside any connector type begins the process of adding a new connector of that type. You can add multiple connectors of the same type to a single tenant.
Available Connectors

The available connectors are:

- Azure Active Directory
- Microsoft Active Directory
- Okta
- Password Safe Cloud
- Privilege Management Cloud
- Privileged Remote Access
- Remote Support

