# Go API client for swagger

# Introduction  Welcome to the ExaVault API documentation. Our API lets you control nearly all aspects of your ExaVault account programatically, from uploading and downloading files to creating and managing shares and notifications.   Capabilities of the API include - Uploading and downloading files. - Managing files and folders, including standard operations like move, copy and delete. - Getting information about activity occuring in your account. - Creating, updating and deleting users. - Creating and managing shares, including download-only shares and receive folders.  - Setting up and managing notifications.  The ExaVault API v2.0 is a RESTful API using JSON.  ## The API URL  You will access your account from your server address. For example, if your account is available at exampleaccount.exavault.com, you'll connect to the API at https://exampleaccount.exavault.com/api/v2  # Obtaining Your API Key and Access Token  Account admins can create API Keys and personal access tokens within the ExaVault File Manager web application.   ## Create an API Key  1. Log into the ExaVault File Manager at your account name address. i.e., if your account is exampleaccount.exavault.com, go to https://exampleaccount.exavault.com and log in with your username and password 2. Click on the **My Account** option in the left-hand sidebar 3. Click on the **Developer** tab 4. Click the + button next to the table of API Keys to create a new key 5. Enter a name that will uniquely identify connections using this key. This name will appear in your activity session logs. 6. Enter a description with any other information that you need to track the purpose of your API key 7. Save the new key  As soon as you save a new API key, you'll be prompted to create a personal access token which will allow a specific user to connect via the API using that API key (jump to step 5 in the instructions below)  ## Generate an Access Token 1. Log into the ExaVault File Manager at your account name address. i.e., if your account is exampleaccount.exavault.com, go to https://exampleaccount.exavault.com and log in with your username and password 1. Click on the **My Account** option in the left-hand sidebar 1. Click on the **Developer** tab 1. Click the + button next to the table of Access Tokens to create a new token 1. Select the API Key from the first dropdown. 1. Select the user who will use this token from the second dropdown. 1. Click the **GENERATE TOKEN** button  The confirmation popup will display your API key and your access token. **Copy this access token to a safe location (such as a password vault) immediately.** Once you close this popup, you will not be able to see the token again. After you have saved your token securely, click CLOSE to close the popup.  The access token you have created will allow any program using that token and its API key to masquerade as the associated user. You should keep the token safe.  # Authentication  The ExaVault API uses the combination of an API key and a persistent access token to authenticate a user. Both the API key and the access token can be created by an admin-level user  Each request made to the API must include 2 headers  | Header Name   | Contains      | | ---      | :---:          | | **ev-api-key**      |  Your API key   | | **ev-access-token**       |   Your access token          |     The access token uniquely identifies the user account for the connection. You should keep this token secure.   # HTTP Status Codes  The ExaVault API v2.0 is RESTful and returns appropriate HTTP status codes in its responses  **Success Statuses:**  | Status   | Notes   | | ---      | :---:       | | 200      | Successful operation   | | 201      | Successful creation operation     | | 207      | Multiple operation status |  **Request Error Statuses:**  | Status   | Notes   | | ---      | :---:       | | 400      | Bad Request   | | 401      | Unauthorized     | | 403      | Forbidden   | | 404      | Not Found* | | 429      | Too many requests |  **Server Error Statuses:**  | Status   | Notes | | ---      | ---   | | 500      | Server Error | | 503      | Service unavailable |   # Response Format  Nearly every response from the server will be a JSON object, which will contain a `responseStatus` attribute that matches the HTTP status of the response.  Most succesful responses will also include a `data` attribute that contains the data related to your request. For instance using GET /account will return the information for the account associated with your API key and access token.   ## Error Responses  Error responses will have a similar format. The response will contain a `responseStatus` which contains the HTTP status code and an `errors` array, which will contain pertinent errors for the request. Each object in the `errors` array will contain a human-readable `code` and some explanatory `detail` text.  ## Common Errors   As you work with our suite of APIs, you'll likely encounter one or more of these error codes throughout the process. Let's take a look at some of the most common errors and how to resolve them quickly and painlessly.   ### 400 Error - Bad Request:  ```json {   \"responseStatus\":400,   \"errors\":[     {       \"code\":\"ERROR_INVALID_PARAMETER\",       \"detail\":\"Destination path cannot be an existing folder.\"     }   ] } ```  ```json {  \"responseStatus\": 400,  \"errors\": [   {    \"code\": \"ERROR_INVALID_PASSWORD\",    \"detail\": \"Password must be longer than eight (8) characters and contain one uppercase letter, one lowercase letter, and one number.\"   }  ] } ```  This error will generally mean a paramater or body element is invalid or missing. We suggest taking another look at the documentation of the API endpoint you're hitting to double check for; missing required fields in the request, spelling errors, invalid values be used.   The error messaging returned should point you exactly to what you need to correct to avoid going through trial and error.    ### 401 Error - Unauthorized   ```json {  \"responseStatus\": 401,  \"errors\": [   {    \"code\": \"ERROR_INVALID_CREDENTIALS\",    \"detail\": \"HTTP_UNAUTHORIZED\"   }  ] } ```  If you encounter a 401, it means we're not recognizing the credentials you're attempting to authenticate with. To resolve the issue;    1. Double check that your credenitals (API Key and Access Token) are correct. 2. Creating a second set of credentials (see \"Obtaining Your API Key and Access Token\" above) and attempt the call again.  3. If you're able to successfully make a call, regenerate the Access Token of the first user and try the call one last time.   If you're still encountering a 401, contact us for help.  ### 403 Error - Forbidden  ```json {  \"responseStatus\": 403,  \"errors\": [   {    \"code\": \"ERROR_INSUFFICIENT_PRIVILEGES\",    \"detail\": \"An error occurred\"   }  ] } ```  Similarly to a 401, you'll be unable to complete an API call if you encounter this error. Unlike a 401, your credentials were authenticated, but the authenticated user does not have permission to perform the action you're attempting.   To resolve the issue you can either;  - Execute the call using an master user's credentials.  - Log in to the ExaVault File Manager OR use the **PATCH /updateUser** endpoint to update the user's permissions.  ### 404 Error - Not Found  ```json  {  \"responseStatus\": 404,  \"errors\": [   {    \"code\": \"ERROR_SHARE_NOT_FOUND\",    \"detail\": \"Share not found\"   }  ] } ```  Encountering a 404 error means whatever type of resource you're attempting to find or update; isn't being found. Usually, this is just a case of using the wrong ID when using a call, and can be resolved by fixing the ID on your call.    If the ID on the call appears to be correct we recommend taking the following steps:  - Attempt a more generic GET call to get a list of the type of resource you're looking for to see if you can find the ID you're looking for.  - Check your activity logs to see if what you're looking for was recently deleted.    # Identifying Resources  Many API methods require you to provide one or more resources, which may be expressed as paths, ids, hashes, or some combination of the three (for calls that act upon multiple resources).   To specify a resource by path, provide a fully qualified string to the resource _relative to the associated user's home directory_. This path will always begin with a forward slash. Only forward slash characters may be used to separate the folders within a path string.  To specify a resource by ID, you'll need to obtain that ID from some other API method first. For example, **GET /resources/list** will return a list of resources in your account along with their IDs. Once you have the ID of that resource, append it to the string \"id:\" to specify that resource, such as `id:124447`. IDs are always whole-number numeric values.   To specify a resource by hash, first obtain the hash from another API method. Once you have the hash representing the resource, append it to the string \"hash:\" to specify that resource, such as `hash:3a1597ca982231f6666c75bcc2bd9c85` to indicate the resource with the hash value **3a1597ca982231f6666c75bcc2bd9c85**. Hashes are always an alphanumeric sequence without any special characters or punctuation.  ## Paths and Home Folders  Users with different home folders will use different paths to refer to the same resource. As an example, suppose there is a file located at **_/Data/Production/Inbound/1595978053_G12.xml**. For an admin-level user, or any user whose home folder permits them access to the entire account, the path for that resource is **_/Data/Production/Inbound/1595978053_G12.xml**.  For a user whose home folder is **_/Data/Production/_**, the path to the file becomes **_/Inbound/1595978053_G12.xml**  # Transaction Limits  The daily transaction limit restricts the overall number of operations you can perform in a 24-hour period in your ExaVault account. Those transactions could be file uploads, file downloads, making a shared folder, creating a user, deleting files, to name a few examples. All operations performed in your account count against the total daily transactions for your account, including:  - FTP/SFTP operations - Actions by users who are logged into your web interface - Interacting with Receive folders - Receiving files through Send files and Shared Folders - Accessing files shared through direct links - API access from any user using any of the API keys for your account  Each request sent to the API is one transaction. When your account has exceeded its rolling 24-hour rate limit, new operations will become available once the number of operations in the past 24-hours is below your daily rate limit. The response status of rate-limited API operations will be **429**.  ## Rate Limit Headers  To monitor your daily account transaction usage, the response object returned by the server for all API requests will include these custom headers:  - **X-RateLimit-Limit** indicates the total number of operations permitted within a rolling 24-hour period across your entire account. This number is dependent upon the plan your account is subscribed to, and whether you have an enterprise agreement in place. - **X-RateLimit-Remaining** indicates the number of operations currently remaning to you at that moment in time.    # Webhooks  ExaVault provides a webhook system for notifying you of changes to your account. The webhook sender will send a POST request to an endpoint you have specified whenever certain actions happen within your account. Account administrators can change these settings within the ExaVault File Manager.  Webhooks will attempt to send a message up to 8 times with increasing timeouts between each attempt. All webhook requests are tracked in the webhooks log within the ExaVault File Manager web interface.  ## Configuring Webhooks  1. Log into the ExaVault File Manager at your account name address. i.e., if your account is exampleaccount.exavault.com, go to https://exampleaccount.exavault.com and log in with your username and password. 1. Click on the **My Account** option in the left-hand sidebar. 1. Click on the **Developer** tab 1. Add the URL where your webhook listener can receive requests 1. Check the boxes for the actions which should trigger your webhook. 1. Scroll to the bottom of the page to click SAVE SETTINGS.  ## Verification Signature  When you configure a webhook endpoint and triggering actions, a Verification Token will be displayed below the webhook endpoint URL. You may use this token in combination with the X-Exavault-Signature header to verify that ExaVault is the sender of the webhook request.  ## Comparing the Signature  You'll can use this 3-step procedure to validate an individual webhook request to ensure it was sent by ExaVault.  **1: Get Verification Token**  In order to verify the X-Exavault-Signature header value, you'll first need to obtain the Verification Token for your account:  1. Click on the **My Account** option in the left-hand sidebar. 1. Click on the **Developer** tab 1. Copy the Verification Token that appears below the Webhooks Endpoint url field.  Every webhook request sent to your endpoint URL will use the same verification token. This token won't change for your account.  **2: Concatenate Token and Request**  Once you have the verification token, you'll concatenate that token along with the raw string representing the request body that was received.   **Do not convert the request body to any other type** of object; if the library you're using automatically converts the request body to an object, look for a method to obtain the raw request body as text.  **3: Calculate MD5 Hash**  Calculate the md5 hash of that concatenation. The result should match the contents of your X-Exavault-Signature header.  ## Webhook Request Examples  The following examples demonstrate the structure of webhook requests and how to validate the verification signature for an individual request. All of these examples will use the same verification token; you'll need to use the token for your account to do the same checks on your own webhook requests.  **User Connect Example**  | Verification Token | X-Exavault-Signature header value | | --- | --- | | efb7e0030e6cef1b45d3d74a67881a2b | 6e13eb14edfd0bd54feff96be131e155 |  ```json {\"accountname\":\"exampleaccount\",\"username\":\"exampleaccount\",\"operation\":\"Connect\",\"protocol\":\"web\",\"path\":\"\",\"sourcepath\":\"\",\"attempt\":1} ```   **User Disconnect Example**  | Verification Token | X-Exavault-Signature header value | | --- | --- | | efb7e0030e6cef1b45d3d74a67881a2b | 186e8c73793666c8b5cfa0b55eee691d |  ```json {\"accountname\":\"exampleaccount\",\"username\":\"exampleaccount\",\"operation\":\"Disconnect\",\"protocol\":\"web\",\"path\":\"\",\"sourcepath\":\"\",\"attempt\":1} ```  **File Upload Example**  | Verification Token | X-Exavault-Signature header value | | --- | --- | | efb7e0030e6cef1b45d3d74a67881a2b | e86119ce1b679c7b6010d9ac9a843a36 |  ```json {\"accountname\":\"exampleaccount\",\"username\":\"exampleaccount\",\"operation\":\"Upload\",\"protocol\":\"web\",\"path\":\"/7df2beb1c50a8a066493ee47669a4319.jpg\",\"sourcepath\":\"\",\"attempt\":1} ```  ## Webhooks Logs  Account administrators can track all of the webhook requests sent for your account within the ExaVault File Manager web interface.   To access Webhook logs:  1. Log into the ExaVault File Manager at your account name address. i.e., if your account is exampleaccount.exavault.com, go to https://exampleaccount.exavault.com and log in with your username and password 1. Click on the **Activity** option in the left-hand sidebar 1. Click on **Webhooks Logs**  The webhook logs will show each time a webhook request was sent to your endpoint URL. The following information is recorded for each request:   - date and time - when the system sent the request   - endpoint url - where the webhook request was sent   - event - what triggered the webhook   - status - HTTP status or curl error code returned by the webhook endpoint   - attempt - how many times this request has been sent   - response size - size of the response from your webhook endpoint   - details - the response body returned from your webhook endpoint 

## Overview
This API client was generated by the [swagger-codegen](https://github.com/swagger-api/swagger-codegen) project.  By using the [swagger-spec](https://github.com/swagger-api/swagger-spec) from a remote server, you can easily generate an API client.

- API version: 2.0
- Package version: 1.0.0
- Build package: io.swagger.codegen.v3.generators.go.GoClientCodegen

## Installation
Put the package under your project folder and add the following in import:
```golang
import "./swagger"
```

## Documentation for API Endpoints

All URIs are relative to *https://accountname.exavault.com/api/v2*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AccountApi* | [**GetAccount**](docs/AccountApi.md#getaccount) | **Get** /account | Get account settings
*AccountApi* | [**PatchAccount**](docs/AccountApi.md#patchaccount) | **Patch** /account | Update account settings
*ActivityApi* | [**GetActivityLogs**](docs/ActivityApi.md#getactivitylogs) | **Get** /activity/session | Get activity logs
*ActivityApi* | [**GetWebhookLogs**](docs/ActivityApi.md#getwebhooklogs) | **Get** /activity/webhooks | Get webhook logs
*EmailApi* | [**PostEmailReferral**](docs/EmailApi.md#postemailreferral) | **Post** /email/referral | Send referral email to a given address
*EmailApi* | [**PostEmailWelcomeUsername**](docs/EmailApi.md#postemailwelcomeusername) | **Post** /email/welcome/{username} | Resend welcome email to specific user
*EmailListsApi* | [**DeleteEmailList**](docs/EmailListsApi.md#deleteemaillist) | **Delete** /email-lists/{id} | Delete an email list with given id
*EmailListsApi* | [**GetEmailLists**](docs/EmailListsApi.md#getemaillists) | **Get** /email-lists | Get all email groups
*EmailListsApi* | [**GetEmailListsId**](docs/EmailListsApi.md#getemaillistsid) | **Get** /email-lists/{id} | Get individual email list
*EmailListsApi* | [**PatchEmailList**](docs/EmailListsApi.md#patchemaillist) | **Patch** /email-lists/{id} | Update an email list
*EmailListsApi* | [**PostEmailLists**](docs/EmailListsApi.md#postemaillists) | **Post** /email-lists | Create new email list
*FormApi* | [**AddFormMessage**](docs/FormApi.md#addformmessage) | **Post** /forms/entries/{shareHash}/{entryId}/{nodeId} | Add a form submission
*FormApi* | [**FormEntries**](docs/FormApi.md#formentries) | **Post** /forms/{shareHash}/entries | Add user data to a form
*FormApi* | [**FormsEntriesCompleteEntryIdPost**](docs/FormApi.md#formsentriescompleteentryidpost) | **Post** /forms/entries/complete-entry/{id} | 
*FormApi* | [**FormsEntriesIdDelete**](docs/FormApi.md#formsentriesiddelete) | **Delete** /forms/entries/{id} | 
*FormApi* | [**FormsEntriesIdGet**](docs/FormApi.md#formsentriesidget) | **Get** /forms/entries/{id} | 
*FormApi* | [**GetForms**](docs/FormApi.md#getforms) | **Get** /forms | Get form data for a receive folder
*FormApi* | [**GetFormsId**](docs/FormApi.md#getformsid) | **Get** /forms/{id} | Get form details
*FormApi* | [**UpdateForm**](docs/FormApi.md#updateform) | **Patch** /forms/{id} | Updates a form with given parameters
*NotificationsApi* | [**NotificationsGet**](docs/NotificationsApi.md#notificationsget) | **Get** /notifications | Get a list of notifications
*NotificationsApi* | [**NotificationsIdDelete**](docs/NotificationsApi.md#notificationsiddelete) | **Delete** /notifications/{id} | Delete a notification
*NotificationsApi* | [**NotificationsIdGet**](docs/NotificationsApi.md#notificationsidget) | **Get** /notifications/{id} | Get a notification&#x27;s metadata
*NotificationsApi* | [**NotificationsIdPatch**](docs/NotificationsApi.md#notificationsidpatch) | **Patch** /notifications/{id} | Update a notification
*NotificationsApi* | [**NotificationsPost**](docs/NotificationsApi.md#notificationspost) | **Post** /notifications | Create a new notification
*NotificationsApi* | [**NotificationsUnsubscribePost**](docs/NotificationsApi.md#notificationsunsubscribepost) | **Post** /notifications/unsubscribe | Unsubscribe an email from a notification
*RecipientsApi* | [**DeleteRecipientsSharesEmail**](docs/RecipientsApi.md#deleterecipientssharesemail) | **Delete** /recipients/shares/{email} | Delete a share recipient from all shares
*RecipientsApi* | [**DeleteRecipientsSharesShareIdEmail**](docs/RecipientsApi.md#deleterecipientssharesshareidemail) | **Delete** /recipients/shares/{shareId}/{email} | Delete a share recipient from a single share
*RecipientsApi* | [**GetRecipients**](docs/RecipientsApi.md#getrecipients) | **Get** /recipients | Get share recipient emails
*RecipientsApi* | [**PostRecipientsSharesInvitesShareId**](docs/RecipientsApi.md#postrecipientssharesinvitesshareid) | **Post** /recipients/shares/invites/{shareId} | Resend invitations to share recipients
*ResourcesApi* | [**CompressFiles**](docs/ResourcesApi.md#compressfiles) | **Post** /resources/compress | Compress resources
*ResourcesApi* | [**CopyResources**](docs/ResourcesApi.md#copyresources) | **Post** /resources/copy | Copy resources
*ResourcesApi* | [**CreateFolder**](docs/ResourcesApi.md#createfolder) | **Post** /resources | Create a folder
*ResourcesApi* | [**DeleteResource**](docs/ResourcesApi.md#deleteresource) | **Delete** /resources/{id} | Delete a Resource
*ResourcesApi* | [**DeleteResources**](docs/ResourcesApi.md#deleteresources) | **Delete** /resources | Delete Resources
*ResourcesApi* | [**Download**](docs/ResourcesApi.md#download) | **Get** /resources/download | Download a file
*ResourcesApi* | [**ExtractFiles**](docs/ResourcesApi.md#extractfiles) | **Post** /resources/extract | Extract resources
*ResourcesApi* | [**GetResourceList**](docs/ResourcesApi.md#getresourcelist) | **Get** /resources/list | Get a list of all resources
*ResourcesApi* | [**GetResourceProperties**](docs/ResourcesApi.md#getresourceproperties) | **Get** /resources/{id} | Get resource metadata
*ResourcesApi* | [**GetResourceProperties_0**](docs/ResourcesApi.md#getresourceproperties_0) | **Get** /resources | Get Resource Properties
*ResourcesApi* | [**MoveResources**](docs/ResourcesApi.md#moveresources) | **Post** /resources/move | Move resources
*ResourcesApi* | [**Preview**](docs/ResourcesApi.md#preview) | **Get** /resources/preview | Preview a file
*ResourcesApi* | [**ResourcesIdPatch**](docs/ResourcesApi.md#resourcesidpatch) | **Patch** /resources/{id} | Rename a resource.
*ResourcesApi* | [**ResourcesListIdGet**](docs/ResourcesApi.md#resourceslistidget) | **Get** /resources/list/{id} | Get a list of resources
*ResourcesApi* | [**Upload**](docs/ResourcesApi.md#upload) | **Post** /resources/upload | Upload a file
*ShareApi* | [**GetShares**](docs/ShareApi.md#getshares) | **Get** /shares | Get a list of shares
*SharesApi* | [**DeleteSharesId**](docs/SharesApi.md#deletesharesid) | **Delete** /shares/{id} | Deactivate a share
*SharesApi* | [**GetSharesId**](docs/SharesApi.md#getsharesid) | **Get** /shares/{id} | Get a share
*SharesApi* | [**PatchSharesId**](docs/SharesApi.md#patchsharesid) | **Patch** /shares/{id} | Update a share
*SharesApi* | [**PostShares**](docs/SharesApi.md#postshares) | **Post** /shares | Creates a share
*SharesApi* | [**PostSharesCompleteSendId**](docs/SharesApi.md#postsharescompletesendid) | **Post** /shares/complete-send/{id} | Complete send files
*UsersApi* | [**CreateUser**](docs/UsersApi.md#createuser) | **Post** /users | Create a user
*UsersApi* | [**DeleteUser**](docs/UsersApi.md#deleteuser) | **Delete** /users/{id} | Delete a user
*UsersApi* | [**GetUser**](docs/UsersApi.md#getuser) | **Get** /users/{id} | Get info for a user
*UsersApi* | [**GetUsers**](docs/UsersApi.md#getusers) | **Get** /users | Get a list of users
*UsersApi* | [**UpdateUser**](docs/UsersApi.md#updateuser) | **Patch** /users/{id} | Update a user
*WebhooksApi* | [**GetWebhookLogs**](docs/WebhooksApi.md#getwebhooklogs) | **Get** /activity/webhooks | Get webhook logs

## Documentation For Models

 - [Account](docs/Account.md)
 - [Account1](docs/Account1.md)
 - [Account1Attributes](docs/Account1Attributes.md)
 - [Account1Relationships](docs/Account1Relationships.md)
 - [Account1RelationshipsMasterUser](docs/Account1RelationshipsMasterUser.md)
 - [Account2](docs/Account2.md)
 - [Account2Attributes](docs/Account2Attributes.md)
 - [Account2Relationships](docs/Account2Relationships.md)
 - [Account2RelationshipsMasterUser](docs/Account2RelationshipsMasterUser.md)
 - [AccountAllowedIpRanges](docs/AccountAllowedIpRanges.md)
 - [AccountAttributes](docs/AccountAttributes.md)
 - [AccountAttributesQuota](docs/AccountAttributesQuota.md)
 - [AccountAttributesTrial](docs/AccountAttributesTrial.md)
 - [AccountExtendedResponse](docs/AccountExtendedResponse.md)
 - [AccountPublic](docs/AccountPublic.md)
 - [AccountPublicAttributes](docs/AccountPublicAttributes.md)
 - [AccountPublicResponse](docs/AccountPublicResponse.md)
 - [AccountPublicResponseData](docs/AccountPublicResponseData.md)
 - [AccountPublicResponseDataAttributes](docs/AccountPublicResponseDataAttributes.md)
 - [AccountRelationships](docs/AccountRelationships.md)
 - [AccountRelationshipsMasterUser](docs/AccountRelationshipsMasterUser.md)
 - [AccountRelationshipsMasterUserData](docs/AccountRelationshipsMasterUserData.md)
 - [AccountResponse](docs/AccountResponse.md)
 - [AllOfResourceDeleteMultiResponseObjectResponsesItems](docs/AllOfResourceDeleteMultiResponseObjectResponsesItems.md)
 - [AllOfResourceMultiResponseDeleteResponsesItems](docs/AllOfResourceMultiResponseDeleteResponsesItems.md)
 - [AllOfResourceMultiResponseObjectResponsesItems](docs/AllOfResourceMultiResponseObjectResponsesItems.md)
 - [AllOfResourceMultiResponseResponsesItems](docs/AllOfResourceMultiResponseResponsesItems.md)
 - [AnyOfDirectFileExtendedResponseIncludedItems](docs/AnyOfDirectFileExtendedResponseIncludedItems.md)
 - [AnyOfFormAttributesElementsItems](docs/AnyOfFormAttributesElementsItems.md)
 - [AnyOfFormExtendedResponseAttributesElementsItems](docs/AnyOfFormExtendedResponseAttributesElementsItems.md)
 - [AnyOfFormResponseAttributesElementsItems](docs/AnyOfFormResponseAttributesElementsItems.md)
 - [AnyOfShareExtendedResponseIncludedItems](docs/AnyOfShareExtendedResponseIncludedItems.md)
 - [AvailableUser](docs/AvailableUser.md)
 - [AvailableUser1](docs/AvailableUser1.md)
 - [AvailableUserResponse](docs/AvailableUserResponse.md)
 - [Body](docs/Body.md)
 - [Body1](docs/Body1.md)
 - [Body10](docs/Body10.md)
 - [Body11](docs/Body11.md)
 - [Body12](docs/Body12.md)
 - [Body13](docs/Body13.md)
 - [Body14](docs/Body14.md)
 - [Body15](docs/Body15.md)
 - [Body16](docs/Body16.md)
 - [Body2](docs/Body2.md)
 - [Body3](docs/Body3.md)
 - [Body4](docs/Body4.md)
 - [Body5](docs/Body5.md)
 - [Body6](docs/Body6.md)
 - [Body7](docs/Body7.md)
 - [Body8](docs/Body8.md)
 - [Body9](docs/Body9.md)
 - [BrandingSettings](docs/BrandingSettings.md)
 - [BrandingSettings1](docs/BrandingSettings1.md)
 - [BrandingSettings2](docs/BrandingSettings2.md)
 - [CallbackSettings](docs/CallbackSettings.md)
 - [CallbackSettings1](docs/CallbackSettings1.md)
 - [CallbackSettings2](docs/CallbackSettings2.md)
 - [CallbackSettingsTriggers](docs/CallbackSettingsTriggers.md)
 - [DirectFile](docs/DirectFile.md)
 - [DirectFile1](docs/DirectFile1.md)
 - [DirectFile2](docs/DirectFile2.md)
 - [DirectFile2Attributes](docs/DirectFile2Attributes.md)
 - [DirectFile2Relationships](docs/DirectFile2Relationships.md)
 - [DirectFile2RelationshipsOwnerAccount](docs/DirectFile2RelationshipsOwnerAccount.md)
 - [DirectFile2RelationshipsResource](docs/DirectFile2RelationshipsResource.md)
 - [DirectFile3](docs/DirectFile3.md)
 - [DirectFile3Relationships](docs/DirectFile3Relationships.md)
 - [DirectFile3RelationshipsOwnerAccount](docs/DirectFile3RelationshipsOwnerAccount.md)
 - [DirectFileAttributes](docs/DirectFileAttributes.md)
 - [DirectFileCollectionExtendedResponse](docs/DirectFileCollectionExtendedResponse.md)
 - [DirectFileCollectionResponse](docs/DirectFileCollectionResponse.md)
 - [DirectFileExtendedResponse](docs/DirectFileExtendedResponse.md)
 - [DirectFileRelationships](docs/DirectFileRelationships.md)
 - [DirectFileRelationshipsOwner](docs/DirectFileRelationshipsOwner.md)
 - [DirectFileRelationshipsResource](docs/DirectFileRelationshipsResource.md)
 - [DirectFileResponse](docs/DirectFileResponse.md)
 - [DownloadPolling](docs/DownloadPolling.md)
 - [DownloadPolling1](docs/DownloadPolling1.md)
 - [DownloadPollingResponse](docs/DownloadPollingResponse.md)
 - [DownloadWithPollingResponseObject](docs/DownloadWithPollingResponseObject.md)
 - [EmailList](docs/EmailList.md)
 - [EmailList1](docs/EmailList1.md)
 - [EmailList2](docs/EmailList2.md)
 - [EmailList2Attributes](docs/EmailList2Attributes.md)
 - [EmailListAttributes](docs/EmailListAttributes.md)
 - [EmailListRelationships](docs/EmailListRelationships.md)
 - [EmailListRelationshipsOwner](docs/EmailListRelationshipsOwner.md)
 - [EmailListRelationshipsOwnerData](docs/EmailListRelationshipsOwnerData.md)
 - [EmailListResponse](docs/EmailListResponse.md)
 - [EmailListResponse1](docs/EmailListResponse1.md)
 - [EmailListsIncludedResponse](docs/EmailListsIncludedResponse.md)
 - [EmailListsIncludedResponseAttributes](docs/EmailListsIncludedResponseAttributes.md)
 - [EmailListsIncludedResponseAttributes1](docs/EmailListsIncludedResponseAttributes1.md)
 - [EmailListsIncludedResponseRelationships](docs/EmailListsIncludedResponseRelationships.md)
 - [EmailListsIncludedResponseRelationships1](docs/EmailListsIncludedResponseRelationships1.md)
 - [EmailListsIncludedResponseRelationships1HomeResource](docs/EmailListsIncludedResponseRelationships1HomeResource.md)
 - [EmailListsIncludedResponseRelationships1OwnerAccount](docs/EmailListsIncludedResponseRelationships1OwnerAccount.md)
 - [EmailListsIncludedResponseRelationshipsOwnerUser](docs/EmailListsIncludedResponseRelationshipsOwnerUser.md)
 - [EmailListsIncludedResponseRelationshipsOwnerUserData](docs/EmailListsIncludedResponseRelationshipsOwnerUserData.md)
 - [EmailListsResponse](docs/EmailListsResponse.md)
 - [EmailListsResponse1](docs/EmailListsResponse1.md)
 - [EmailListsResponse2](docs/EmailListsResponse2.md)
 - [EmailListsResponseAttributes](docs/EmailListsResponseAttributes.md)
 - [EmailListsResponseRelationships](docs/EmailListsResponseRelationships.md)
 - [EmailListsResponseRelationshipsOwnerUser](docs/EmailListsResponseRelationshipsOwnerUser.md)
 - [EmailListsResponseRelationshipsOwnerUserData](docs/EmailListsResponseRelationshipsOwnerUserData.md)
 - [Error401](docs/Error401.md)
 - [Error401Errors](docs/Error401Errors.md)
 - [Error403](docs/Error403.md)
 - [Error403Errors](docs/Error403Errors.md)
 - [Form](docs/Form.md)
 - [FormAttributes](docs/FormAttributes.md)
 - [FormDataResponse](docs/FormDataResponse.md)
 - [FormExtendedResponse](docs/FormExtendedResponse.md)
 - [FormExtendedResponseAttributes](docs/FormExtendedResponseAttributes.md)
 - [FormField](docs/FormField.md)
 - [FormFieldData](docs/FormFieldData.md)
 - [FormFieldData1](docs/FormFieldData1.md)
 - [FormFieldSettings](docs/FormFieldSettings.md)
 - [FormRelationships](docs/FormRelationships.md)
 - [FormRelationshipsShare](docs/FormRelationshipsShare.md)
 - [FormRelationshipsShareData](docs/FormRelationshipsShareData.md)
 - [FormResponse](docs/FormResponse.md)
 - [FormResponseAttributes](docs/FormResponseAttributes.md)
 - [FormResponseRelationships](docs/FormResponseRelationships.md)
 - [FormResponseRelationshipsShare](docs/FormResponseRelationshipsShare.md)
 - [FormResponseRelationshipsShareData](docs/FormResponseRelationshipsShareData.md)
 - [FormsidElements](docs/FormsidElements.md)
 - [FormsidSettings](docs/FormsidSettings.md)
 - [InlineResponse200](docs/InlineResponse200.md)
 - [InlineResponse2001](docs/InlineResponse2001.md)
 - [InlineResponse20010](docs/InlineResponse20010.md)
 - [InlineResponse20011](docs/InlineResponse20011.md)
 - [InlineResponse20012](docs/InlineResponse20012.md)
 - [InlineResponse20013](docs/InlineResponse20013.md)
 - [InlineResponse20014](docs/InlineResponse20014.md)
 - [InlineResponse20014Data](docs/InlineResponse20014Data.md)
 - [InlineResponse20014DataMeta](docs/InlineResponse20014DataMeta.md)
 - [InlineResponse20015](docs/InlineResponse20015.md)
 - [InlineResponse20016](docs/InlineResponse20016.md)
 - [InlineResponse20017](docs/InlineResponse20017.md)
 - [InlineResponse20017Meta](docs/InlineResponse20017Meta.md)
 - [InlineResponse20018](docs/InlineResponse20018.md)
 - [InlineResponse20018Meta](docs/InlineResponse20018Meta.md)
 - [InlineResponse20019](docs/InlineResponse20019.md)
 - [InlineResponse2002](docs/InlineResponse2002.md)
 - [InlineResponse20020](docs/InlineResponse20020.md)
 - [InlineResponse20021](docs/InlineResponse20021.md)
 - [InlineResponse20022](docs/InlineResponse20022.md)
 - [InlineResponse20023](docs/InlineResponse20023.md)
 - [InlineResponse2003](docs/InlineResponse2003.md)
 - [InlineResponse2004](docs/InlineResponse2004.md)
 - [InlineResponse2005](docs/InlineResponse2005.md)
 - [InlineResponse2006](docs/InlineResponse2006.md)
 - [InlineResponse2007](docs/InlineResponse2007.md)
 - [InlineResponse2008](docs/InlineResponse2008.md)
 - [InlineResponse2009](docs/InlineResponse2009.md)
 - [InlineResponse201](docs/InlineResponse201.md)
 - [InlineResponse2011](docs/InlineResponse2011.md)
 - [InlineResponse2012](docs/InlineResponse2012.md)
 - [InlineResponse2013](docs/InlineResponse2013.md)
 - [InlineResponse2014](docs/InlineResponse2014.md)
 - [InlineResponse2015](docs/InlineResponse2015.md)
 - [InlineResponse2015Data](docs/InlineResponse2015Data.md)
 - [InlineResponse201Data](docs/InlineResponse201Data.md)
 - [Message](docs/Message.md)
 - [Message1](docs/Message1.md)
 - [MessageAttributes](docs/MessageAttributes.md)
 - [ModelError](docs/ModelError.md)
 - [NotificartionRecipient](docs/NotificartionRecipient.md)
 - [Notification](docs/Notification.md)
 - [Notification1](docs/Notification1.md)
 - [NotificationCollectionExtendedResponse](docs/NotificationCollectionExtendedResponse.md)
 - [NotificationCollectionExtendedResponseAttributes](docs/NotificationCollectionExtendedResponseAttributes.md)
 - [NotificationCollectionExtendedResponseRelationships](docs/NotificationCollectionExtendedResponseRelationships.md)
 - [NotificationCollectionExtendedResponseRelationshipsNode](docs/NotificationCollectionExtendedResponseRelationshipsNode.md)
 - [NotificationCollectionExtendedResponseRelationshipsOwner](docs/NotificationCollectionExtendedResponseRelationshipsOwner.md)
 - [NotificationCollectionExtendedResponseRelationshipsShare](docs/NotificationCollectionExtendedResponseRelationshipsShare.md)
 - [NotificationCollectionResponse](docs/NotificationCollectionResponse.md)
 - [NotificationExtendedResponse](docs/NotificationExtendedResponse.md)
 - [NotificationRecipient](docs/NotificationRecipient.md)
 - [NotificationResponse](docs/NotificationResponse.md)
 - [NotificationResponseAttributes](docs/NotificationResponseAttributes.md)
 - [NotificationResponseObject](docs/NotificationResponseObject.md)
 - [NotificationResponseObject1](docs/NotificationResponseObject1.md)
 - [NotificationResponseRelationships](docs/NotificationResponseRelationships.md)
 - [NotificationResponseRelationshipsOwnerUser](docs/NotificationResponseRelationshipsOwnerUser.md)
 - [NotificationResponseRelationshipsResource](docs/NotificationResponseRelationshipsResource.md)
 - [NotificationResponseRelationshipsShare](docs/NotificationResponseRelationshipsShare.md)
 - [OneOfinlineResponse200](docs/OneOfinlineResponse200.md)
 - [OneOfinlineResponse2002](docs/OneOfinlineResponse2002.md)
 - [OneOfinlineResponse20020](docs/OneOfinlineResponse20020.md)
 - [OneOfinlineResponse20021](docs/OneOfinlineResponse20021.md)
 - [OneOfinlineResponse2003](docs/OneOfinlineResponse2003.md)
 - [OneOfinlineResponse2005](docs/OneOfinlineResponse2005.md)
 - [OneOfinlineResponse2007](docs/OneOfinlineResponse2007.md)
 - [OneOfinlineResponse2008](docs/OneOfinlineResponse2008.md)
 - [OneOfinlineResponse2009](docs/OneOfinlineResponse2009.md)
 - [PreivewFileResponseObject](docs/PreivewFileResponseObject.md)
 - [PreviewFile](docs/PreviewFile.md)
 - [PreviewFile1](docs/PreviewFile1.md)
 - [PreviewFile1Attributes](docs/PreviewFile1Attributes.md)
 - [PreviewFile2](docs/PreviewFile2.md)
 - [PreviewFileResponse](docs/PreviewFileResponse.md)
 - [RegularFormResponse](docs/RegularFormResponse.md)
 - [RegularShareResponse](docs/RegularShareResponse.md)
 - [RegularShareResponse1](docs/RegularShareResponse1.md)
 - [RegularShareResponse2](docs/RegularShareResponse2.md)
 - [ReportResponse](docs/ReportResponse.md)
 - [Resource](docs/Resource.md)
 - [Resource1](docs/Resource1.md)
 - [Resource2](docs/Resource2.md)
 - [Resource2Attributes](docs/Resource2Attributes.md)
 - [ResourceAttributes](docs/ResourceAttributes.md)
 - [ResourceCollectionExtendedResponse](docs/ResourceCollectionExtendedResponse.md)
 - [ResourceCollectionExtendedResponseAttributes](docs/ResourceCollectionExtendedResponseAttributes.md)
 - [ResourceCollectionExtendedResponseRelationships](docs/ResourceCollectionExtendedResponseRelationships.md)
 - [ResourceCollectionExtendedResponseRelationshipsDirectFile](docs/ResourceCollectionExtendedResponseRelationshipsDirectFile.md)
 - [ResourceCollectionExtendedResponseRelationshipsNotification](docs/ResourceCollectionExtendedResponseRelationshipsNotification.md)
 - [ResourceCollectionExtendedResponseRelationshipsParentNode](docs/ResourceCollectionExtendedResponseRelationshipsParentNode.md)
 - [ResourceCollectionExtendedResponseRelationshipsShare](docs/ResourceCollectionExtendedResponseRelationshipsShare.md)
 - [ResourceCollectionMetaResponse](docs/ResourceCollectionMetaResponse.md)
 - [ResourceCollectionMetaResponseMeta](docs/ResourceCollectionMetaResponseMeta.md)
 - [ResourceCollectionResponse](docs/ResourceCollectionResponse.md)
 - [ResourceDeleteMultiResponseObject](docs/ResourceDeleteMultiResponseObject.md)
 - [ResourceDeleteResponse](docs/ResourceDeleteResponse.md)
 - [ResourceDeleteResponseData](docs/ResourceDeleteResponseData.md)
 - [ResourceExtendedResponse](docs/ResourceExtendedResponse.md)
 - [ResourceMultiResponse](docs/ResourceMultiResponse.md)
 - [ResourceMultiResponseDelete](docs/ResourceMultiResponseDelete.md)
 - [ResourceMultiResponseObject](docs/ResourceMultiResponseObject.md)
 - [ResourceResponse](docs/ResourceResponse.md)
 - [ResourceResponseAttributes](docs/ResourceResponseAttributes.md)
 - [ResourceResponseObject](docs/ResourceResponseObject.md)
 - [ResourceResponseObject1](docs/ResourceResponseObject1.md)
 - [ResourceResponseRelationships](docs/ResourceResponseRelationships.md)
 - [ResourceResponseRelationshipsDirectFile](docs/ResourceResponseRelationshipsDirectFile.md)
 - [ResourceResponseRelationshipsNotification](docs/ResourceResponseRelationshipsNotification.md)
 - [ResourceResponseRelationshipsOwnerAccount](docs/ResourceResponseRelationshipsOwnerAccount.md)
 - [ResourceResponseRelationshipsOwnerUser](docs/ResourceResponseRelationshipsOwnerUser.md)
 - [ResourceResponseRelationshipsParentResource](docs/ResourceResponseRelationshipsParentResource.md)
 - [ResourceResponseRelationshipsShare](docs/ResourceResponseRelationshipsShare.md)
 - [SessionActivityEntry](docs/SessionActivityEntry.md)
 - [SessionActivityResponse](docs/SessionActivityResponse.md)
 - [SessionActivityResponseAttributes](docs/SessionActivityResponseAttributes.md)
 - [Share](docs/Share.md)
 - [Share1](docs/Share1.md)
 - [Share1Attributes](docs/Share1Attributes.md)
 - [Share1Relationships](docs/Share1Relationships.md)
 - [Share1RelationshipsMessages](docs/Share1RelationshipsMessages.md)
 - [Share1RelationshipsNotifications](docs/Share1RelationshipsNotifications.md)
 - [Share1RelationshipsOwner](docs/Share1RelationshipsOwner.md)
 - [Share1RelationshipsResource](docs/Share1RelationshipsResource.md)
 - [Share2](docs/Share2.md)
 - [Share3](docs/Share3.md)
 - [Share4](docs/Share4.md)
 - [ShareAttributes](docs/ShareAttributes.md)
 - [ShareCollectionExtendedResponse](docs/ShareCollectionExtendedResponse.md)
 - [ShareCollectionExtendedResponseAttributes](docs/ShareCollectionExtendedResponseAttributes.md)
 - [ShareCollectionExtendedResponseRelationships](docs/ShareCollectionExtendedResponseRelationships.md)
 - [ShareCollectionExtendedResponseRelationshipsResource](docs/ShareCollectionExtendedResponseRelationshipsResource.md)
 - [ShareCollectionResponse](docs/ShareCollectionResponse.md)
 - [ShareCollectionResponseRelationships](docs/ShareCollectionResponseRelationships.md)
 - [ShareCollectionResponseRelationshipsNotifications](docs/ShareCollectionResponseRelationshipsNotifications.md)
 - [ShareCollectionResponseRelationshipsOwner](docs/ShareCollectionResponseRelationshipsOwner.md)
 - [ShareCollectionResponseRelationshipsResource](docs/ShareCollectionResponseRelationshipsResource.md)
 - [ShareExtendedResponse](docs/ShareExtendedResponse.md)
 - [ShareRecipient](docs/ShareRecipient.md)
 - [ShareRecipient1](docs/ShareRecipient1.md)
 - [ShareRelationship](docs/ShareRelationship.md)
 - [ShareRelationships](docs/ShareRelationships.md)
 - [ShareRelationshipsMessages](docs/ShareRelationshipsMessages.md)
 - [ShareRelationshipsNotifications](docs/ShareRelationshipsNotifications.md)
 - [ShareRelationshipsResource](docs/ShareRelationshipsResource.md)
 - [ShareResponse](docs/ShareResponse.md)
 - [ShareResponseRelationships](docs/ShareResponseRelationships.md)
 - [ShareResponseRelationshipsMessages](docs/ShareResponseRelationshipsMessages.md)
 - [ShareResponseRelationshipsNotifications](docs/ShareResponseRelationshipsNotifications.md)
 - [ShareResponseRelationshipsOwner](docs/ShareResponseRelationshipsOwner.md)
 - [ShareResponseRelationshipsResources](docs/ShareResponseRelationshipsResources.md)
 - [SingleEntryOfSessionActivity](docs/SingleEntryOfSessionActivity.md)
 - [SingleEntryOfSessionActivity1](docs/SingleEntryOfSessionActivity1.md)
 - [User](docs/User.md)
 - [User1](docs/User1.md)
 - [User2](docs/User2.md)
 - [User3](docs/User3.md)
 - [UserAttributes](docs/UserAttributes.md)
 - [UserAttributesPermissions](docs/UserAttributesPermissions.md)
 - [UserCollectionExtendedResponse](docs/UserCollectionExtendedResponse.md)
 - [UserCollectionExtendedResponseAttributes](docs/UserCollectionExtendedResponseAttributes.md)
 - [UserCollectionExtendedResponseAttributesPermissions](docs/UserCollectionExtendedResponseAttributesPermissions.md)
 - [UserCollectionExtendedResponseRelationships](docs/UserCollectionExtendedResponseRelationships.md)
 - [UserCollectionExtendedResponseRelationshipsAccount](docs/UserCollectionExtendedResponseRelationshipsAccount.md)
 - [UserCollectionResponse](docs/UserCollectionResponse.md)
 - [UserCollectionResponseAttributes](docs/UserCollectionResponseAttributes.md)
 - [UserCollectionResponseRelationships](docs/UserCollectionResponseRelationships.md)
 - [UserCollectionResponseRelationshipsHomeResource](docs/UserCollectionResponseRelationshipsHomeResource.md)
 - [UserCollectionResponseRelationshipsOwnerAccount](docs/UserCollectionResponseRelationshipsOwnerAccount.md)
 - [UserExtendedResponse](docs/UserExtendedResponse.md)
 - [UserPermissions](docs/UserPermissions.md)
 - [UserRelationships](docs/UserRelationships.md)
 - [UserRelationshipsHomeResource](docs/UserRelationshipsHomeResource.md)
 - [UserRelationshipsHomeResourceData](docs/UserRelationshipsHomeResourceData.md)
 - [UserRelationshipsOwnerAccount](docs/UserRelationshipsOwnerAccount.md)
 - [UserRelationshipsOwnerAccountData](docs/UserRelationshipsOwnerAccountData.md)
 - [UserResponse](docs/UserResponse.md)
 - [UserResponseAttributes](docs/UserResponseAttributes.md)
 - [UserResponseObject](docs/UserResponseObject.md)
 - [UserResponseRelationships](docs/UserResponseRelationships.md)
 - [UserResponseRelationshipsHomeResource](docs/UserResponseRelationshipsHomeResource.md)
 - [UserResponseRelationshipsOwnerAccount](docs/UserResponseRelationshipsOwnerAccount.md)
 - [WebhooksActivityEntry](docs/WebhooksActivityEntry.md)
 - [WebhooksActivityEntryAttributes](docs/WebhooksActivityEntryAttributes.md)
 - [WebhooksActivityResponse](docs/WebhooksActivityResponse.md)
 - [WebhooksActivityResponseAttributes](docs/WebhooksActivityResponseAttributes.md)

## Documentation For Authorization
 Endpoints do not require authorization.


## Author

Copyright © 2020 Kimono LLC. All rights reserved.
