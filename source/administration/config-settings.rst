Configuration Settings
======================
Configuration settings let System Admins manage their Mattermost server and multiple teams. System Admins can modify configuration settings directly in the ``config.json`` file or by using the web-based System Console user interface. Setting changes in the System Console are stored in ``config/config.json``. 

The first user added to a new Mattermost install is assigned the System Admin role and can access the System Console from the Main Menu of any team. 

Note: For any setting not explicitly set in ``config.json`` the Mattermost server will use the default value as documented here, which can be observed in the default ``config/config.json`` file included in each Mattermost release. 

Quick Links:

`General <http://docs.mattermost.com/administration/config-settings.html#id2>`_
	`Configuration <http://docs.mattermost.com/administration/config-settings.html#id3>`_ - `Localization <http://docs.mattermost.com/administration/config-settings.html#id4>`_ - `Users and Teams <http://docs.mattermost.com/administration/config-settings.html#id5>`_ - `Privacy <http://docs.mattermost.com/administration/config-settings.html#id6>`_ - `Policy <http://docs.mattermost.com/administration/config-settings.html#policy-enterprise>`_ - `Compliance <http://docs.mattermost.com/administration/config-settings.html#compliance-enterprise>`_ - `Logging <http://docs.mattermost.com/administration/config-settings.html#id7>`_

`Authentication <http://docs.mattermost.com/administration/config-settings.html#id12>`_
	`Email <http://docs.mattermost.com/administration/config-settings.html#id13>`_ - `GitLab <http://docs.mattermost.com/administration/config-settings.html#id14>`_ - `LDAP <http://docs.mattermost.com/administration/config-settings.html#ldap-enterprise>`_ - `SAML <http://docs.mattermost.com/administration/config-settings.html#saml-enterprise>`_

`Security <http://docs.mattermost.com/administration/config-settings.html#id20>`_
	`Sign Up <http://docs.mattermost.com/administration/config-settings.html#id21>`_ - `Password <http://docs.mattermost.com/administration/config-settings.html#id22>`_ - `Public Links <http://docs.mattermost.com/administration/config-settings.html#id23>`_ - `Sessions <http://docs.mattermost.com/administration/config-settings.html#id24>`_ - `Connections <http://docs.mattermost.com/administration/config-settings.html#id25>`_

`Notifications <http://docs.mattermost.com/administration/config-settings.html#id26>`_
	`Email <http://docs.mattermost.com/administration/config-settings.html#id27>`_ - `Mobile Push <http://docs.mattermost.com/administration/config-settings.html#id29>`_

`Integrations <http://docs.mattermost.com/administration/config-settings.html#id30>`_
	`Webhooks and Commands <http://docs.mattermost.com/administration/config-settings.html#id31>`_ - `External Services <http://docs.mattermost.com/administration/config-settings.html#id34>`_

`Files <http://docs.mattermost.com/administration/config-settings.html#id35>`_
	`Storage <http://docs.mattermost.com/administration/config-settings.html#id36>`_ - `Images <http://docs.mattermost.com/administration/config-settings.html#id37>`_

`Customization <http://docs.mattermost.com/administration/config-settings.html#id38>`_
	`Custom Branding <http://docs.mattermost.com/administration/config-settings.html#id39>`_ - `Custom Emoji <http://docs.mattermost.com/administration/config-settings.html#id40>`_ - `Legal and Support <http://docs.mattermost.com/administration/config-settings.html#id41>`_

`Advanced <http://docs.mattermost.com/administration/config-settings.html#id42>`_
	`Rate Limiting <http://docs.mattermost.com/administration/config-settings.html#id43>`_ - `Database <http://docs.mattermost.com/administration/config-settings.html#id44>`_ - `Developer <http://docs.mattermost.com/administration/config-settings.html#id45>`_

General
---------------------------------
General settings for server configuration, language defaults, user and team management, privacy, compliance reporting and logs.

Configuration
``````````````````````````
Listen Address  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
The IP address on which to listen and the port on which to bind. Entering ":8065" will bind to all interfaces or you can choose one like ``127.0.0.1:8065``. Changing this will require a server restart before taking effect.

+--------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ListenAddress": ":8065"``  |
+--------------------------------------------------------------------------+

Webserver Mode  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
gzip compression applies to the HTML, CSS, Javascript, and other static content files that make up the Mattermost web client. It is recommended to enable gzip to improve performance unless your environment has specific restrictions, such as a web proxy that distributes gzip files poorly. This setting requires a server restart to take effect.

**gzip**: The Mattermost server will serve static files compressed with gzip to improve performance.

**Uncompressed**: The Mattermost server will serve static files uncompressed.

**Disabled**: The Mattermost server will not serve static files.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"WebserverMode": "gzip"`` with options ``gzip``, ``uncompressed`` and ``disabled`` for above settings respectively.      |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Reload Configuration from Disk (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
This button resets the configuration settings by reloading the settings from the disk. The server will still need to be restarted if a setting requiring server restart was changed.

The workflow for failover without downing the server is to change the database line in the config.json file, click **Reload Configuration from Disk** then click **Recycle Database Connections** in the Advanced > Database section.

________

Localization
```````````````````````````
Default Server Language 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
Default language for system messages and logs. Changing this will require a server restart before taking effect.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"DefaultServerLocale": "en"`` with options ``de``, ``en``, ``es``, ``fr``, ``ja`` and ``pt-br``                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Default Client Language
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Default language for newly created users and pages where the user hasn't logged in.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"DefaultClientLocale": "en"`` with options ``de``, ``en``, ``es``, ``fr``, ``ja`` and ``pt-br``                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Available Languages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
Sets which languages are available for users in **Account Settings** > **Display** > **Languages**. Leave the field blank to add new languages automatically by default, or add new languages using the dropdown menu manually as they become available. If you're manually adding new languages, the **Default Client Language** must be added before saving the setting.

Note: Servers which upgraded to v3.1 need to manually set this field blank to have new languages added by default.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AvailableLocales": ""`` with options with options ``""``, ``de``, ``en``, ``es``, ``fr``, ``ja`` and ``pt-br``          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Users and Teams
``````````````````````````
Enable Account Creation 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
**True**: Ability to create new accounts is enabled via inviting new members or sharing the team invite link.

**False**: Ability to create accounts is disabled. The **Create Account** button displays an error when trying to signup via an email invite or team invite link.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableUserCreation": true`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+


Enable Team Creation 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
**True**: Ability to create a new team is enabled for all users.

**False**: Only System Administrators can create teams from the team selection page. The **Create A New Team** button is hidden in the main menu UI.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableTeamCreation": true`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Max Users Per Team
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
Maximum number of users per team, including both active and inactive users.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaxUsersPerTeam": 50`` with whole number input.                                                                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Restrict account creation to specified email domains
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~    
Teams and user accounts can only be created by a verified email from this list of comma-separated domains (e.g. "corp.mattermost.com, mattermost.org").

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictCreationToDomains": ""`` with string input.                                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Restrict Team Names 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
**True**: Newly created team names cannot contain the following restricted words: www, web, admin, support, notify, test, demo, mail, team, channel, internal, localhost, dockerhost, stag, post, cluster, api, oauth.

**False**: Newly created team names are not restricted. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableTeamCreation": true`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable users to open Direct Message channels with 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Any user on the Mattermost server**: The Direct Messages "More" menu has the option to open a Direct Message channel with any user on the server.  

**Any member of the team**: The Direct Messages "More" menu only has the option to open a Direct Message channel with users on the current team.  If a user belongs to multiple teams, direct messages will still be received regardless of what team they are currently on. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictDirectMessage": "any"`` with options ``any`` and ``team`` for above settings respectively.                      |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Team Directory  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
*Removed in May 16th, 2016 release* 

**True**: Teams that are configured to appear in the team directory will appear on the system main page. Teams can configure this setting from **Team Settings > Include this team in the Team Directory**.

**False**: Team directory on the system main page is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableTeamListing": false`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Policy (Enterprise)
``````````````````````````
Settings to configure the permission restrictions for sending team invite links and managing channels.  

Enable sending team invites from:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set policy on who can invite others to a team using "Invite New Member" to invite new users by email, or the "Get Team Invite Link" options from the main menu. If "Get Team Invite Link" is used to share a link, you can expire the invite code from **Team Settings** > **Invite Code** after the desired users joined the team. Options include: 

**All team members**: Allows any team member to invite others using an email invitation or team invite link.

**Team and System Admins**: Hides the email invitation and team invite link in the Main Menu from users who are not Team Admins or System Admins. 

**System Admins**: Hides the email invitation and team invite link in the Main Menu from users who are not System Admins. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictTeamInvite": "all"`` with options ``all``, ``team_admin`` and ``system_admin`` for above settings respectively. |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable public channel management permissions for 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Restrict the permission levels required to create, delete, rename, and set the header or purpose for public channels. The last member of a public channel has the ability to delete the channel regardless of their permission level.

**All team members**: Channel management permissions for public channels are enabled for all users.

**Team and System Admins**: Channel management permissions for public channels are restricted to Team and System Admins.

**System Admins**: Channel management permissions for public channels are restricted to System Admins.

+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictPublicChannelManagement": "all"`` with options ``all``, ``team_admin`` and ``system_admin`` for above settings respectively. |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable private channel management permissions for 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Restrict the permission levels required to to create, delete, rename, and set the header or purpose for private channels. The last member of a private channel has the ability to delete the channel regardless of their permission level.

**All team members**: Channel management permissions for private channels are enabled for all users.

**Team and System Admins**: Channel management permissions for private channels are restricted to Team and System Admins.

**System Admins**: Channel management permissions for private channels are restricted to System Admins.

+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictPrivateChannelManagement": "all"`` with options ``all``, ``team_admin`` and ``system_admin`` for above settings respectively. |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


________

Privacy
``````````````````````````
Settings to configure the name and email privacy of users on your system.  

Show Email Address 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
**True**: Show email address of all users.

**False**: Hide email address of users from other users in the user interface, including Team Admins. This is designed for managing teams where users choose to keep their contact information private. System Administrators will still be able to see email addresses in the UI. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ShowEmailAddress": true`` with options ``true`` and ``false`` for above settings respectively.                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Show Full Name 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Show full name of all users.

**False**: hide full name of users from other users including Team Admins. This is designed for managing teams where users choose to keep their contact information private. System Administrators will still be able to see full names in the UI.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ShowFullName": true`` with options ``true`` and ``false`` for above settings respectively.                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Compliance (Enterprise)
```````````````````````````
Settings used to enable and configure Mattermost compliance reports. 

Enable Compliance Reporting 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Compliance reporting is enabled in Mattermost.

**False**: Compliance reporting is disabled. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Enable": false`` with options ``true`` and ``false`` for above settings respectively.                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Compliance Report Directory 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Sets the directory where compliance reports are written. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Directory": "./data/"`` with string input.                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Daily Report
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Mattermost generates a daily compliance report.

**False**: Daily reports are not generated. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableDaily": false`` with options ``true`` and ``false`` for above settings respectively.                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Logging
``````````````````````````
Output logs to console 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~	

**True**: Output log messages to the console based on **ConsoleLevel** option. The server writes messages to the standard output stream (stdout).

**False**: Output log messages are not written to the console.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableConsole": true`` with options ``true`` and ``false`` for above settings respectively.                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Console Log Level
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Level of detail at which log events are written to the console when **EnableConsole**= ``true``. 

**DEBUG**: Prints high detail for developers debugging issues.

**ERROR**: Outputs only error messages.

**INFO**: Outputs error messages and information around startup and initialization,

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ConsoleLevel": "DEBUG"`` with options ``DEBUG``, ``ERROR`` and ``INFO`` for above settings respectively.                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Output logs to file 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
**True**:  Log files are written to files specified in **FileLocation**.

**False**: Log files are not written.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableFile": true`` with options ``true`` and ``false`` for above settings respectively.                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

File Log Level
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Level of detail at which log events are written to log files when **EnableFile**=``true``.

**ERROR**: Outputs only error messages.

**INFO**: Outputs error messages and information around startup and initialization,

**DEBUG**: Prints high detail for developers debugging issues.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FileLevel": "INFO"`` with options ``DEBUG``, ``ERROR`` and ``INFO`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

File Log Directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
Directory to which log files are written. If blank, log files write to ./logs/mattermost/mattermost.log. Log rotation is enabled and every 10,000 lines of log information is written to new files stored in the same directory, for example mattermost.2015-09-23.001, mattermost.2015-09-23.002, and so forth.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FileLocation": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

File Log Format  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Format of log message output. If blank, FileFormat = "[%D %T] [%L] (%S) %M", where:

.. list-table::
   :widths: 20 80

   * - %T
     - Time (15:04:05 MST) 
   * - %t
     - Time (15:04) 
   * - %D
     - Date (2006/01/02)
   * - %d
     - Date (01/02/06) 
   * - %L
     - Level (FNST, FINE, DEBG, TRAC, WARN, EROR, CRIT)
   * - %S
     - Source
   * - %M
     - Message  

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FileFormat": ""`` with string input.                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

     
Enable Webhook Debugging
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 

**True**: Contents of incoming webhooks are printed to log files for debugging.

**False**: Contents of incoming webhooks are not printed to log files.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableWebhookDebugging": true`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Authentication
-------------------------------
Authentication settings to enable account creation and sign in with email, GitLab OAuth or LDAP.

Email
``````````````````````````
Enable account creation with email 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  

**True**: Allow team creation and account signup using email and password.

**False**: Email signup is disabled and users are not able to invite new members. This limits signup to single-sign-on services like OAuth or LDAP.  

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableSignUpWithEmail": true`` with options ``true`` and ``false`` for above settings respectively.                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable sign-in with email 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  

**True**: Mattermost allows users to sign in using their email and password.

**False**: sign in with email is disabled and does not appear on the login screen.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableSignInWithEmail": true`` with options ``true`` and ``false`` for above settings respectively.                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable sign-in with username 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**True**: Mattermost allows users to sign in using their username and password. This setting is typically only used when email verification is disabled.

**False**: sign in with username is disabled and does not appear on the login screen.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``EnableSignInWithUsername": false`` with options ``true`` and ``false`` for above settings respectively.                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

GitLab
``````````````````````````
Enable authentication with GitLab  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Allow team creation and account signup using GitLab OAuth. To configure, input the **Secret** and **Id** credentials. 

**False**: GitLab OAuth cannot be used for team creation or account signup. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Enable": false`` with options ``true`` and ``false`` for above settings respectively.                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Application ID 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this value by logging into your GitLab account. Go to Profile Settings > Applications > New Application, enter a Name, then enter Redirect URLs ``https://<your-mattermost-url>/login/gitlab/complete`` (example: ``https://example.com:8065/login/gitlab/complete``and ``https://<your-mattermost-url>/signup/gitlab/complete``.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Id": ""`` with string input.                                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Application Secret Key  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this value by logging into your GitLab account. Go to Profile Settings > Applications > New Application, enter a Name, then enter Redirect URLs ``https://<your-mattermost-url>/login/gitlab/complete`` (example: ``https://example.com:8065/login/gitlab/complete``and ``https://<your-mattermost-url>/signup/gitlab/complete``.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Secret": ""`` with string input.                                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

User API Endpoint 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Enter ``https://<your-gitlab-url>/oauth/authorize`` (example: ``https://example.com:3000/api/v3/user``). Use HTTP or HTTPS depending on how your server is configured.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"UserApiEndpoint": ""`` with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Auth Endpoint  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Enter ``https://<your-gitlab-url>/oauth/authorize`` (example: ``https://example.com:3000/oauth/authorize``). Use HTTP or HTTPS depending on how your server is configured.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AuthEndpoint": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Token Endpoint  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Enter ``https://<your-gitlab-url>/oauth/authorize`` (example: ``https://example.com:3000/oauth/token``). Use HTTP or HTTPS depending on how your server is configured.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"TokenEndpoint": ""`` with string input.                                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

LDAP (Enterprise)
```````````````````````````
Enable sign-in with LDAP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Mattermost allows login using LDAP.

**False**: Login with LDAP is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Enable": false`` with options ``true`` and ``false`` for above settings respectively.                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

LDAP Server  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
The domain or IP address of the LDAP server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LdapServer": ""`` with string input.                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

LDAP Port 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The port Mattermost will use to connect to the AD/LDAP server. Default is 389.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LdapPort": 389`` with numerical input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Connection Security
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
The type of connection security Mattermost uses to connect to LDAP. 

**None**: No encryption, Mattermost will not attempt to establish an encrypted connection to the LDAP server.

**TLS**: Encrypts the communication between Mattermost and your server using TLS. 

**STARTTLS**: Takes an existing insecure connection and attempts to upgrade it to a secure connection using TLS. 

If the "No encryption" option is selected it is highly recommended that the LDAP connection is secured outside of Mattermost, for example, by adding a stunnel proxy. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ConnectionSecurity": ""`` with options ``""``, ``TLS`` and ``STARTTLS`` for above settings respectively.                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Base DN   
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
The **Base Distinguished Name** of the location where Mattermost should start its search for users in the LDAP tree.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"BaseDN": ""`` with string input.                                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Bind Username 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
The username used to perform the AD/LDAP search. This should be an account created specifically for use with Mattermost  Its permissions should be limited to read-only access to the portion of the LDAP tree specified in the **Base DN** field. When using Active Directory, **Bind Username** should specify domain in ``DOMAIN/username`` format. This field is required, and anonymous bind is not currently supported. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"BindUsername": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Bind Password   
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Password of the user given in **Bind Username**. This field is required, and anonymous bind is not currently supported. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"BindPassword": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

User Filter  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) Enter an LDAP Filter to use when searching for user objects (accepts `general syntax <http://www.ldapexplorer.com/en/manual/109010000-ldap-filter-syntax.htm>`_). Only the users selected by the query will be able to access Mattermost. For Active Directory, the query to filter out disabled users is ``(&(objectCategory=Person)(!(UserAccountControl:1.2.840.113556.1.4.803:=2)))``

This filter uses the permissions of the **Bind Username** account to execute the search. Administrators should make sure to use a specially created account for Bind Username with read-only access to the portion of the LDAP tree specified in the **Base DN** field. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"UserFilter": ""`` with string input.                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

First Name Attribute 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the LDAP server that will be used to populate the first name of users in Mattermost. This field is required.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FirstNameAttribute": ""``  with string input.                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Last Name Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the LDAP server that will be used to populate the last name of users in Mattermost. This field is required.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LastNameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Nickname Attribute 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) The attribute in the LDAP server that will be used to populate the nickname of users in Mattermost.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"NicknameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Email Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the LDAP server that will be used to populate the email addresses of users in Mattermost. 

Email notifications will be sent to this email address, and this email address may be viewable by other Mattermost users depending on privacy settings choosen by the System Admin. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EmailAttribute": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Username Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the LDAP server that will be used to populate the username field in Mattermost user interface. This attribute will be used within the Mattermost user interface to identify and mention users. For example, if a Username Attribute is set to **john.smith** a user typing ``@john`` will see ``@john.smith`` in their auto-complete options and posting a message with ``@john.smith`` will send a notification to that user that they've been mentioned. 

The **Username Attribute** may be set to the same value used to sign-in to the system, called an **ID Attribute**, or it can be mapped to a different value. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"UsernameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

ID Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the LDAP server that will be used as a unique identifier in Mattermost. It serves two purposes: 

This value is used to sign in to Mattermost in the **LDAP Username** field on the sign in page. This attribute can be the same as the **Username Attribute** field above, which is what is used to identify users in the Mattermost interface, or it can be a different value, for example a User ID number. If your team typically uses ``DOMAIN\username`` to sign in to other services with LDAP, you may enter a field name that maps to ``DOMAIN\username`` to maintain consistency between sites.

**This is the attribute that will be used to create unique Mattermost accounts.** This attribute should be an LDAP attribute with a value that does not change, such as ``username`` or ``uid``. If a user’s **ID Attribute** changes and the user attempts to login the Mattermost server will attempt to create a new Mattermost user account based on the new **ID Attribute** and fail since new Mattermost users accounts can't be created with duplicate email addresses or Mattermost usernames (as defined in the **Username Attribute**).  

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"IdAttribute": ""`` with string input.                                                                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Skip Certificate Verification 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) The attribute in the LDAP server that will be used to populate the nickname of users in Mattermost.

**True**: Skips the certificate verification step for TLS or STARTTLS connections. Not recommended for production environments where TLS is required. For testing only.

**False**: Mattermost does not skip certificate verification.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SkipCertificateVerification": false`` with options ``true`` and ``false`` for above settings respectively.              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Synchronization Interval (minutes) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set how often Mattermost accounts synchronize attributes with AD/LDAP, in minutes. When synchronizing, Mattermost queries AD/LDAP for relevant account information and updates Mattermost accounts based on changes to attributes (first name, last name, and nickname). When accounts are disabled in AD/LDAP users can no longer sign-in to Mattermost using AD/LDAP credentials, and their active sessions are revoked once Mattermost synchronizes attributes. Disabling a user in AD/LDAP does not automatically set its Mattermost account to "Inactive" it only disables AD/LDAP authentication.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SyncIntervalMinutes": 60`` with whole number input.                                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+ 

Query Timeout (seconds)  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The timeout value for queries to the LDAP server. Increase this value if you are getting timeout errors caused by a slow LDAP server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"QueryTimeout": 60`` with whole number input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum Page Size  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The maximum number of users the Mattermost server will request from the LDAP server at one time. Use this setting if your LDAP server limits the number of users that can be requested at once. 0 is unlimited. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaxPageSize": 0`` with whole number input.                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Login Field Name 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The placeholder text that appears in the login field on the login page. Typically this would be whatever name is used to refer to LDAP credentials in your company, so it is recognizable to your users. Defaults to **LDAP Username**.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LoginFieldName": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

LDAP Synchronize Now
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
This button causes LDAP synchronization to occur as soon as it is pressed. Use it whenever you have made a change in the LDAP server you want to take effect immediately. After using the button, the next LDAP synchronization will occur after the time specified by the Synchronization Interval.  

________

SAML (Enterprise)
```````````````````````````
Enable Login With SAML 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Mattermost allows login using SAML. Please see `documentation <http://docs.mattermost.com/deployment/sso-saml.html>`_ to learn more about configuring SAML for Mattermost.

**False**: Login with SAML is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Enable": false`` with options ``true`` and ``false`` for above settings respectively.                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SAML SSO URL 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The URL where Mattermost sends a SAML request to start login sequence.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"IdpURL": ""``  with string input.                                                                                       |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Identity Provider Issuer URL 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The issuer URL for the Identity Provider you use for SAML requests.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"IdpDescriptorUrl": ""``  with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Identity Provider Public Certificate  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The public authentication certificate issued by your Identity Provider.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"IdpCertificateFile": ""`` with string input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Verify Signature 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
``true``: When true, Mattermost verifies that the signature sent from the SAML Response matches the Service Provider Login URL.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Verify": false`` with string input.                                                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Service Provider Login URL  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Enter ``https://<your-mattermost-url>/login/sso/saml`` (example: ``https://example.com/login/sso/saml``). Make sure you use HTTP or HTTPS in your URL depending on your server configuration. This field is also known as the Assertion Consumer Service URL.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AssertionConsumerServiceURL": ""`` with string input.                                                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Encryption
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Mattermost will decrypt SAML Assertions encrypted with your Service Provider Public Certificate.

**False**: Encyption is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Encrypt": false`` with options ``true`` and ``false`` for above settings respectively.                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Service Provider Private Key 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The private key used to decrypt SAML Assertions from the Identity Provider.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PrivateKeyFile": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Service Provider Public Certificate 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The certificate file used to generate the signature on a SAML request to the Identity Provider for a service provider initiated SAML login, when Mattermost is the Service Provider.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PublicCertificateFile": ""`` with string input.                                                                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Email Attribute 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the SAML Assertion that will be used to populate the email addresses of users in Mattermost. 

Email notifications will be sent to this email address, and this email address may be viewable by other Mattermost users depending on privacy settings choosen by the System Admin. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EmailAttribute": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Username Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the SAML Assertion that will be used to populate the username field in Mattermost user interface. This attribute will be used within the Mattermost user interface to identify and mention users. For example, if a Username Attribute is set to **john.smith** a user typing ``@john`` will see ``@john.smith`` in their auto-complete options and posting a message with ``@john.smith`` will send a notification to that user that they've been mentioned. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"UsernameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

First Name Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the SAML Assertion that will be used to populate the first name of users in Mattermost.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FirstNameAttribute": ""`` with string input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Last Name Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The attribute in the SAML Assertion that will be used to populate the last name of users in Mattermost.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LastNameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Nickname Attribute  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) The attribute in the SAML Assertion that will be used to populate the nickname of users in Mattermost.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"NicknameAttribute": ""`` with string input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Preferred Language Attribute 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) The attribute in the SAML Assertion that will be used to populate the language of users in Mattermost.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LocaleAttribute": ""`` with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Login Button Text  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(Optional) The text that appears in the login button on the login page. Defaults to ``With SAML``.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"LoginButtonText": ""`` with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________


Security
--------------------------------
Configure security settings for account creation, login, public links and connection requests.

Sign Up
```````````````````````````
Require Email Verification  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Require email verification after account creation prior to allowing login.

**False**: Users do not need to verify their email address prior to login. Developers may set this field to false so skip sending verification emails for faster development.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RequireEmailVerification": false`` with options ``true`` and ``false`` for above settings respectively.                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Email Invite Salt  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
32-character (to be randomly generated via System Console) salt added to signing of email invites. Click **Regenerate** to create new salt.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"InviteSalt": ""`` with string input.                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Open Server  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Users can sign up to the server from the root page without an invite. 

**False**: Users can only sign up to the server if they receive an invite.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableOpenServer": false`` with options ``true`` and ``false`` for above settings respectively.                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Password
```````````````````````````
Minimum Password Length (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Minimum number of characters required for a valid password. Must be a whole number greater than or equal to 5 and less than or equal to 64.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MinimumLength": 5"`` with whole number input.                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Password Requirements (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the required character types to be included in a valid password. Defaults to allow any characters unless otherwise specified by the checkboxes. The error messasage previewed in the System Console will appear on the account creation page if a user enters an invalid password.

- **At least one lowercase letter**: Select this checkbox if a valid password must contain at least one lowercase letter.    
- **At least one uppercase letter**: Select this checkbox if a valid password must contain at least one uppercase letter.    
- **At least one number**: Select this checkbox if a valid password must contain at least one number.    
- **At least one symbol**: Select this checkbox if a valid password must contain at least one symbol. Valid symbols include: ``!"#$%&'()*+,-./:;<=>?@[]^_`|~``   

This features's ``config.json`` settings are, respectively:

.. list-table::
    :widths: 80

    * - ``"Lowercase": false`` with options ``true`` and ``false``
    * - ``"Number": false`` with options ``true`` and ``false``
    * - ``"Uppercase": false`` with options ``true`` and ``false``
    * - ``"Symbol": false`` with options ``true`` and ``false``


Password Reset Salt 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
32-character (to be randomly generated via Admin Console) salt added to signing of password reset emails. Click **Regenerate** to create new salt.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PasswordResetSalt": ""``  with string input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum Login Attempts 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Failed login attempts allowed before a user is locked out and required to reset their password via email.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaximumLoginAttempts": 10`` with whole number input.                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Multi-factor Authentication (Enterprise) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: When true, users will be given the option to require a phone-based passcode, in addition to their password-based authentication, to sign-in to the Mattermost server. Specifically, they will be asked to download the `Google Authenticator <https://en.wikipedia.org/wiki/Google_Authenticator>`_ app to their iOS or Android mobile device, connect the app with their account, and then enter a passcode generated by the app on their phone whenever they log in to the Mattermost server.

**False**: Multi-factor authentication is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableSecurityFixAlert": true`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Public Links
```````````````````````````
Enable Public File Links 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Allow users to share public links to files and images when previewing.

**False**: The Get Public Link option is hidden from the image preview user interface.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnablePublicLink": true`` with options ``true`` and ``false`` for above settings respectively.                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Public Link Salt 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
32-character (to be randomly generated via Admin Console) salt added to signing of public image links. Click **Regenerate** to create new salt.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PublicLinkSalt": ""``  with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

_________

Sessions
``````````````````````````
Session length for email and LDAP authentication (days)  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the number of days before web sessions expire and users will need to log in again.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SessionLengthWebInDays" : 30`` with whole number input.                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Session length for mobile apps (days) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the number of days before native mobile sessions expire.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SessionLengthMobileInDays" : 30`` with whole number input.                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Session length for GitLab SSO authentication (days) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the number of days before SSO sessions expire.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SessionLengthSSOInDays" : 30`` with whole number input.                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Session Cache (minutes) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the number of minutes to cache a session in memory.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SessionCacheInMinutes" : 10`` with whole number input.                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Connections
``````````````````````````
Enable cross-origin requests from  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Enable HTTP cross-origin requests from specific domains separated by spaces. Type ``*`` to allow CORS from any domain or leave it blank to disable it.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AllowCorsFrom": ""`` with string input.                                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Insecure Outgoing Connections 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Outgoing HTTPS requests can accept unverified, self-signed certificates. For example, outgoing webhooks to a server with a self-signed TLS certificate, using any domain, will be allowed.

**False**: Only secure HTTPS requests are allowed.

Security note: Enabling this feature makes these connections susceptible to man-in-the-middle attacks.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableInsecureOutgoingConnections": false`` with options ``true`` and ``false`` for above settings respectively.        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Notifications
--------------------------------
Settings to configure email and mobile push notifications.

Email
``````````````````````````
Enable Email Notifications  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Enables sending of email notifications. 

**False**: Disables email notifications for developers who may want to skip email setup for faster development. Setting this to true removes the **Preview Mode: Email notifications have not been configured** banner (requires logging out and logging back in after setting is changed)

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SendEmailNotifications": false`` with options ``true`` and ``false`` for above settings respectively.                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Notification Display Name  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Name displayed on email account used when sending notification emails from Mattermost system.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FeedbackName": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Notification From Address  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Address displayed on email account used when sending notification emails from Mattermost system.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FeedbackEmail": ""`` with string input.                                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Notification Footer Mailing Address  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Organization name and mailing address displayed in the footer of email notifications from Mattermost, such as "© ABC Corporation, 565 Knight Way, Palo Alto, California, 94305, USA". If the field is left empty, the organization name and mailing address will not be displayed.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"FeedbackOrganization": ""`` with string input.                                                                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SMTP Server Username  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this credential from the administrator setting up your email server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SMTPUsername": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SMTP Server Password  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this credential from the administrator setting up your email server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SMTPPassword": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SMTP Server 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Location of SMTP email server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SMTPServer": ""``  with string input.                                                                                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SMTP Server Port  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Port of SMTP email server.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SMTPPort": ""`` with string input.                                                                                      |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Connection Security 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
``""``: Send email over an unsecure connection.

``TLS``: Communication between Mattermost and your email server is encrypted.

``STARTTLS``: Attempts to upgrade an existing insecure connection to a secure connection using TLS.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ConnectionSecurity": ""`` with options ``""``, ``TLS`` and ``STARTTLS`` for above settings respectively.                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Security Alerts 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**true**: System Admins are notified by email if a relevant security fix alert has been announced in the last 12 hours. Requires email to be enabled.

**False**: Security alerts are disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableSecurityFixAlert": true`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Mobile Push
```````````````````````````
Enable Push Notifications  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Your Mattermost server sends mobile push notifications to the server specified in **PushNotificationServer**.

**False**: Mobile push notifications are disabled.  

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SendPushNotifications": false`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Push Notification Server 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Location of Mattermost Push Notification Service (MPNS), which re-sends push notifications from Mattermost to services like Apple Push Notification Service (APNS) and Google Cloud Messaging (GCM).  

To confirm push notifications are working, connect to the `Mattermost iOS App on iTunes <https://itunes.apple.com/us/app/mattermost/id984966508?mt=8>`_ or the `Mattermost Android App on Google Play <https://play.google.com/store/apps/details?id=com.mattermost.mattermost&hl=en>`_: 

- For Enterprise Edition, enter ``http://push.mattermost.com``
- For Team Edition, enter ``http://push-test.mattermost.com``

Please review full documentation on `push Notifications and mobile applications <http://docs.mattermost.com/deployment/push.html>`_ including guidance on compiling your own mobile apps and MPNS before deploying to production. 

Note: The ``http://push-test.mattermost.com`` provided for testing push notifications prior to compiling your own service please make sure `to read about its limitations <http://docs.mattermost.com/deployment/push.html#push-notifications-for-team-edition-users>`_. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PushNotificationServer": ""`` with string input.                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Push Notification Contents
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Send generic description with user and channel names**: Selecting "Send generic description with user and channel names" provides push notifications with generic messages, including names of users and channels but no specific details from the message text.  

**Send full message snippet**: Selecting "Send full message snippet" sends excerpts from messages triggering notifications with specifics and may include confidential information sent in messages. If your Push Notification Service is outside your firewall, it is HIGHLY RECOMMENDED this option only be used with an "https" protocol to encrypt the connection.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PushNotificationContents": "generic"`` with options ``generic`` and ``full`` for above settings respectively.           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Troubleshooting Push Notifications**

To confirm push notifications are working: 

1. Set **System Console** > **Email Settings** > **Send Push Notifications** to `true`.
2. Set **System Console** > **Email Settings** > **Send Push Notifications** to `true` (if using Mattermost 1.4 or earlier).
3. Set **System Console** > **Email Settings** > **Push Notification Server** to ``http://push.mattermost.com`` if using Enterprise Edition or if using Team Edition, set the value to `http://push-test.mattermost.com`.
4. Download and install `the Mattermost iOS app from iTunes <https://itunes.apple.com/us/app/mattermost/id984966508?mt=8>`_ on your iPhone or iPad and log in to your team site. 
5. Close the app on your device, and close any other connections to your team site.
6. Wait 5 minutes and have another team member send you a direct messages, which should trigger a push notification to the Mattermost app on your mobile device. 
7. You should receive a push notification on your device alerting you of the direct message. 

If you did not receive an alert: 

1. Set **System Console** > **Log Settings** > **File Log Level** to `DEBUG` (make sure to set this back to `INFO` after troubleshooting to save disk space). 
2. Repeat the above steps
3. Go to **System Console** > **OTHER** > **Logs** and copy the log output into a file 
4. For Enterprise Edition customers, `submit a support request with the file attached <https://mattermost.zendesk.com/hc/en-us/requests/new>`_. For Team Edition users, please start a thread in the `Troubleshooting forum <https://forum.mattermost.org/t/how-to-use-the-troubleshooting-forum/150>`_ for peer-to-peer support. 


________

Integrations
--------------------------------
Settings to configure webhooks, slash commands and external integration services.

Webhooks and Commands
``````````````````````````
Enable Incoming Webhooks    
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Developers building integrations can create webhook URLs for channels and private groups. Please see our `documentation page <http://docs.mattermost.com/developer/webhooks-incoming.html>`_ to learn about creating webhooks, view samples, and to let the community know about integrations you have built. 

**True**: Incoming webhooks will be allowed. To manage incoming webhooks, go to **Account Settings > Integrations**. The webhook URLs created in Account Settings can be used by external applications to create posts in any channels or private groups that you have access to.

**False**: The Integrations > Incoming Webhooks section of Account Settings is hidden and all incoming webhooks are disabled.

Security note: By enabling this feature, users may be able to perform `phishing attacks <https://en.wikipedia.org/wiki/Phishing>`_ by attempting to impersonate other users. To combat these attacks, a BOT tag appears next to all posts from a webhook. Enable at your own risk.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableIncomingWebhooks": true`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Outgoing Webhooks    
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Developers building integrations can create webhook tokens for public channels. Trigger words are used to fire new message events to external integrations. For security reasons, outgoing webhooks are only available in public channels. Please see our `documentation page <http://docs.mattermost.com/developer/webhooks-outgoing.html>`_ to learn about creating webhooks and view samples. 

**True**: Outgoing webhooks will be allowed. To manage outgoing webhooks, go to **Account Settings > Integrations**.

**False**: The Integrations > Outgoing Webhooks section of Account Settings is hidden and all outgoing webhooks are disabled.

Security note: By enabling this feature, users may be able to perform `phishing attacks <https://en.wikipedia.org/wiki/Phishing>`_ by attempting to impersonate other users. To combat these attacks, a BOT tag appears next to all posts from a webhook. Enable at your own risk.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableOutgoingWebhooks": true`` with options ``true`` and ``false`` for above settings respectively.                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Custom Slash Commands  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Slash commands send events to external integrations that send a response back to Mattermost. 

**True**: Allow users to create custom slash commands from **Main Menu** > **Integrations** > **Commands**.

**False**: Slash Commands are hidden in the **Integrations** user interface.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableCommands": false`` with options ``true`` and ``false`` for above settings respectively.                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Restrict creating integrations to Team and System Admins  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: User created integrations can only be created by System or Team Admins. Members who are not admins trying to create integrations will hit an error message on the **Integrations** page.

**False**: Any team members can create integrations from **Main Menu** > **Integrations**.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableOnlyAdminIntegrations": true`` with options ``true`` and ``false`` for above settings respectively.               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable webhooks and slash commands to override usernames  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Webhooks will be allowed to change the username they are posting as.

**False**: Webhooks can only post as the username they were set up with. See http://mattermost.org/webhooks for more details.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnablePostUsernameOverride": false`` with options ``true`` and ``false`` for above settings respectively.               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable webhooks and slash commands to override profile picture iconss  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Webhooks will be allowed to change the icon they post with.

**False**: Webhooks can only post with the profile picture of the account they were set up with. See http://mattermost.org/webhooks for more details.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnablePostIconOverride": false`` with options ``true`` and ``false`` for above settings respectively.                   |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

External Services
```````````````````````````
Segment Write Key  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
For deployments seeking additional tracking of system behavior using Segment.com, you can enter a Segment WRITE_KEY using this field. This value works like a tracking code and is used in client-side Javascript and will send events to Segment.com attributed to the account you used to generate the WRITE_KEY.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SegmentDeveloperKey": ""`` with string input.                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Google API Key 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Mattermost offers the ability to embed YouTube videos from URLs shared by end users. If Google detects the number of views is exceedingly high, they may throttle embed access. Should this occur, you can remove the throttle by registering for a Google Developer Key and entering it in this field following these instructions: https://www.youtube.com/watch?v=Im69kzhpR3I. Your Google Developer Key is used in client-side Javascript.

Using a Google Developer Key allows Mattermost to detect when a video is no longer available and display the post with a *Video not found* label.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"GoogleDeveloperKey": ""`` with string input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Files
--------------------------------
Settings to configure files storage and image handling.

Storage
```````````````````````````
File Storage System  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Storage system where files and image attachments are saved. 

**Local File System**: Files and images are stored in the specified local file directory. 

“Amazon S3”: Files and images are stored on Amazon S3 based on the provided access key, bucket and region fields.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"DriverName": "local"`` with options ``local`` and ``amazons3`` for above settings respectively.                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Local Storage Directory  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Directory to which files are written. If blank, directory will be set to ./data/.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Directory": "./data/"`` with string input.                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Access Key ID 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this credential from your Amazon EC2 administrator.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3AccessKeyId": ""`` with string input.                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Secret Access Key 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Obtain this credential from your Amazon EC2 administrator.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3SecretAccessKey": ""`` with string input.                                                                       |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Bucket 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Name you selected for your S3 bucket in AWS.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3Bucket": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Region 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
AWS region you selected for creating your S3 bucket. Refer to `AWS Reference Documentation <http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region>`_ and choose this variable from the Region column.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3Region": ""`` with string input.                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum File Size 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum file size for message attachments entered in megabytes in the System Console UI. Converted to bytes in ``config.json`` at 1048576 bytes per megabyte.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaxFileSize": 52428800`` with whole number input.                                                                       |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. warning:: Verify server memory can support your setting choice. Large file sizes increase the risk of server crashes and failed uploads due to network disruptions.

________

Images
```````````````````````````
Attachment Thumbnail Width  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Width of thumbnails generated from uploaded images. Updating this value changes how thumbnail images render in future, but does not change images created in the past.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ThumbnailWidth": 120`` with whole number input.                                                                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attachment Thumbnail Height 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Height of thumbnails generated from uploaded images. Updating this value changes how thumbnail images render in future, but does not change images created in the past.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ThumbnailHeight": 100`` with whole number input.                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Image Preview Width 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum width of preview image. Updating this value changes how preview images render in future, but does not change images created in the past.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PreviewWidth": 1024`` with whole number input.                                                                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Image Preview Height 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum height of preview image ("0": Sets to auto-size). Updating this value changes how preview images render in future, but does not change images created in the past.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PreviewHeight": 0`` with whole number input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Profile Picture Width 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The width to which profile pictures are resized after being uploaded via Account Settings.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ProfileWidth": 128`` with whole number input.                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Profile Picture Height 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The height to which profile pictures are resized after being uploaded via Account Settings.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ProfileHeight": 128`` with whole number input.                                                                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Customization
--------------------------------
Settings to customize your deployment with custom branding and legal and support links.

Custom Branding
```````````````````````````

Site Name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Name of service shown in login screens and UI. Maximum 30 characters.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictCreationToDomains": ""`` with string input.                                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Custom Branding (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Enables custom branding to show a JPG image some custom text on the server login page. 

**False**: Custom branding is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableCustomBrand": false`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Custom Brand Image (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Custom JPG image is displayed on left side of server login page. Recommended maximum image size is less than 2 MB because image will be loaded for every user who logs in.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features has no ``config.json`` setting and must be set in the System Console user interface.                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Custom Brand Text (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Custom text will be shown below custom brand image on left side of server login page. Maximum 500 characters allowed. You can format this text using the same `Markdown formatting codes <http://docs.mattermost.com/help/messaging/formatting-text.html>`_ as using in Mattermost messages. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"CustomBrandText": ""`` with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Custom Emoji
```````````````````````````
Enable Custom Emoji  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Enables a Custom Emoji option in the Main Menu, where users can go to create customized emoji.

**False**: Custom emojis are disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableCustomEmoji": false`` with options ``true`` and ``false`` for above settings respectively.                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Restrict Custom Emoji Creation (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Allow everyone to create custom emoji**: Allows everyone to create custom emoji from the **Main Menu** > **Custom Emoji**.

**Allow System and Team Admins to create custom emoji**: The Custom Emoji option is hidden from the Main Menu for users who are not System or Team Admins.

**Only allow System Admins to create custom emoji**: The Custom Emoji option is hidden from the Main Menu for users who are not System or Team Admins.

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"RestrictCustomEmojiCreation": "all"`` with options ``all``, ``admin`` and ``system_admin`` for above settings respectively. |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________

Legal and Support
```````````````````````````
Terms of Service link 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Configurable link to Terms of Service your organization may provide to end users. By default, links to an editable file hosted in the ``static/help/terms.html`` found in the directory where the Mattermost server installed. Default file may be updated to state the terms under which your organization is providing its server to end users, in addition to the "Mattermost Conditions of Use" notice to end users that must also be shown to users from the "Terms of Service" link. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"TermsOfServiceLink": "/static/help/terms.html"`` with string input.                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Privacy Policy link  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Configurable link to Privacy Policy your organization may provide to end users. By default, links to an editable file hosted in the ``static/help/privacy.html`` found in the directory where the Mattermost server installed. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PrivacyPolicyLink": "/static/help/privacy.html"`` with string input.                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

About link  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Configurable link to an About page describing your organization may provide to end users. By default, links to an editable file hosted in the ``static/help/about.html`` found in the directory where the Mattermost server installed. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AboutLink": "/static/help/about.html"`` with string input.                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Help link  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Configurable link to an About page describing your organization may provide to end users. By default, points to Mattermost default help documentation. Can be links to an editable file hosted in the ``static/help/help.html`` found in the directory where the Mattermost server installed. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"HelpLink": "/static/help/help.html"`` with string input.                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Report a Problem link  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set the link for the support website.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"ReportAProblemLink": "/static/help/report_problem.html"`` with string input.                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Support Email  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set an email for feedback or support requests.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"SupportEmail":"feedback@mattermost.com"`` with string input.                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________


Advanced
--------------------------------
Advanced settings to configure rate limiting, databases and developer options.

Rate Limiting
```````````````````````````
Changing properties in this section will require a server restart before taking effect.

Enable Rate Limiting  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: APIs are throttled at the rate specified by **PerSec**.

**False**: APIs are not throttled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableRateLimiter": true`` with options ``true`` and ``false`` for above settings respectively.                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum Queries per Second  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Throttle API at this number of requests per second if rate limiting is enabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"PerSec": 10`` with whole number input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Memory Store Size  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum number of user sessions connected to the system as determined by **VaryByRemoteAddr** and **VaryByHeader** variables.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MemoryStoreSize": 10000`` with whole number input.                                                                      |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Vary rate limit by remote address  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Rate limit API access by IP address.

**False**: Rate limiting does not vary by IP address.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"VaryByRemoteAddr": true`` with options ``true`` and ``false`` for above settings respectively.                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Vary rate limit by HTTP header  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Vary rate limiting by HTTP header field specified (e.g. when configuring Ngnix set to "X-Real-IP", when configuring AmazonELB set to "X-Forwarded-For").

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"VaryByHeader": ""`` with string input.                                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________


Database
```````````````````````````
Changing properties in this section will require a server restart before taking effect. 

Driver Name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This setting can only be changed from config.json file, it cannot be changed from the System Console user interface.

``mysql``: enables driver to MySQL database.

``postgres``: enables driver to PostgreSQL database.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"DriverName": "mysql"`` with string input.                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Data Source 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This is the connection string to the master database. When **DriverName** ="postgres" then use a connection string in the form ``postgres://mmuser:password@localhost:5432/mattermost_test?sslmode=disable&connect_timeout=10``. This setting can only be changed from config.json file, it cannot be changed from the System Console user interface.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"DataSource": ""`` with string input.                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum Idle Connections  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum number of idle connections held open to the database.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaxIdleConns": 10`` with whole number input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maximum Open Connections 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maximum number of open connections held open to the database.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"MaxOpenConns": 10`` with whole number input.                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

At Rest Encrypt Key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
32-character (to be randomly generated via Admin Console) salt available to encrypt and decrypt sensitive fields in database.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AtRestEncryptKey": ""`` with string input.                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Trace  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Executing SQL statements are written to the log for development.

**False**: SQL statements are not written to the log.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Trace": false`` with options ``true`` and ``false`` for above settings respectively.                                    |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Recycle Database Connections (Enterprise)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This button reconnects to the database listed in the configuration settings. All old connections are closed after 20s.

The workflow for failover without downing the server is to change the database line in the config.json file, click **Reload Configuration from Disk** in the General > Configuration section then click **Recycle Database Connections**.

________


Developer
```````````````````````````

Enable Testing Commands  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: `/loadtest` slash command is enabled to load test accounts and test data.

**False**: `/loadtest` slash command is disabled.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableTesting": false`` with options ``true`` and ``false`` for above settings respectively.                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Enable Developer Mode  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Javascript errors are shown in a red bar at the top of the user interface. Not recommended for use in production.

**False**: Users are not alerted to Javascript errors. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableDeveloper": false`` with options ``true`` and ``false`` for above settings respectively.                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
________


Settings configurable only in config.json
-------------------------------

There are a number of settings customizable in ``config.json`` unavailable in the System Console and require updating from the file itself. 

Service Settings
```````````````````````````

Enable OAuth Service Provider  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: Allow Mattermost to function as an OAuth provider, allowing 3rd party apps access to your user store for authentication.

**False**: Mattermost does not function as an OAuth provider.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"EnableOAuthServiceProvider": false`` with options ``true`` and ``false`` for above settings respectively.               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

WebSocket Secure Port 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(Optional) This setting defines the port on which the secured WebSocket will listen using the `wss` protocol. Otherwise it defaults to `443`. When the client attempts to make a WebSocket connection it first checks to see if the page is loaded with HTTPS. If so, it will use the secure WebSocket connection. If not, it will use the unsecure WebSocket connection. IT IS HIGHLY RECOMMENDED PRODUCTION DEPLOYMENTS ONLY OPERATE UNDER HTTPS AND WSS. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is  ``"WebsocketSecurePort" : 443`` with whole number input.                                                                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

WebSocket Port 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(Optional) this setting defines the port on which the unsecured WebSocket will listen using the `ws` protocol. Otherwise it defaults to `80`. When the client attempts to make a WebSocket connection it first checks to see if the page is loaded with HTTPS. If so, it will use the secure WebSocket connection. If not, it will use the unsecure WebSocket connection. IT IS HIGHLY RECOMMENDED PRODUCTION DEPLOYMENTS ONLY OPERATE UNDER HTTPS AND WSS. 

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``WebsocketPort": 80`` with whole number input.                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________


File Settings
```````````````````````````
Initial Font 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Font used in auto-generated profile pics with colored backgrounds.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"InitialFont": "luximbi.ttf"`` with string input.                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Endpoint  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set an endpoint URL for an Amazon S3 instance.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3Endpoint": ""`` with string input.                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Bucket Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Set an endpoint URL for Amazon S3 buckets.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3BucketEndpoint": ""`` with string input.                                                                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Location Constraint  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: S3 region is location constrained.

**False**: S3 region is not location constrained.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3LocationConstraint": false`` with options ``true`` and ``false`` for above settings respectively.               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Amazon S3 Lowercase Bucket    
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**True**: S3 bucket names are fully lowercase.

**False**: S3 bucket names may contain uppercase and lowercase letters.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"AmazonS3LowercaseBucket": false`` with options ``true`` and ``false`` for above settings respectively.                  |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

________


GitLab Settings
```````````````````````````
Scope  
~~~~~~~~~~~~~~~~~~~~~~~~~
Standard setting for OAuth to determine the scope of information shared with OAuth client. Not currently supported by GitLab OAuth.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| This features's ``config.json`` setting is ``"Scope": ""`` with string input.                                                                                         |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+