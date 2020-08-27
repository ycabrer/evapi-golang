# Body15

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Type_** | **string** | The type of share to create. See above for a description of each. | [default to null]
**Name** | **string** | Name of the share. | [default to null]
**FilePaths** | **[]string** | Array of strings containing the file paths to share. | [default to null]
**AccessMode** | **[]string** | Type of permissions share recipients have. | [default to null]
**CcEmail** | **string** | Array of strings for CC email recipients (for email invitations). | [optional] [default to null]
**Embed** | **bool** | Allows user to embed a widget with the share. | [optional] [default to null]
**Expiration** | **string** | Expiration date for the share | [optional] [default to null]
**HasNotification** | **bool** | True if notifications are set up for the share.  | [optional] [default to null]
**IsPublic** | **bool** | True if a public link is available.  | [optional] [default to null]
**Message** | **string** |  | [optional] [default to null]
**NotificationEmails** | **[]string** | Emails that will recevie notificiations. | [optional] [default to null]
**Password** | **string** | Set a password for recipients to access the share.  | [optional] [default to null]
**RequireEmail** | **bool** | True if recipients must provide their email to access the share.  | [optional] [default to null]
**Subject** | **string** |  | [optional] [default to null]
**FileDropCreateFolders** | **bool** | True if files uploaded should create new folders.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

