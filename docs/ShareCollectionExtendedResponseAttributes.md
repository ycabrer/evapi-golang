# ShareCollectionExtendedResponseAttributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** | Share name. | [optional] [default to null]
**HasPassword** | **bool** | True if the share has password. | [optional] [default to null]
**Public** | **bool** | True if the share has a public url. | [optional] [default to null]
**AccessMode** | **string** | Access rights for the share. | [optional] [default to null]
**AccessDescription** | **string** | Description of the share access rights. | [optional] [default to null]
**Embed** | **bool** | True if share can be embedded. | [optional] [default to null]
**Hash** | **string** | Share hash. | [optional] [default to null]
**OwnerHash** | **string** | Share owner&#x27;s hash. | [optional] [default to null]
**Expiration** | **string** | Expiration date of the share. | [optional] [default to null]
**Expired** | **bool** | True if the share has expired. | [optional] [default to null]
**Resent** | **string** | Invitations resent date. Can be &#x60;null&#x60; if resent never happened. | [optional] [default to null]
**Type_** | **string** | Type of share. | [optional] [default to null]
**RequireEmail** | **bool** | True if share requires email to access. | [optional] [default to null]
**FileDropCreateFolders** | **bool** | Flag to show if separate folders should be created for each file upload to receive folder. | [optional] [default to null]
**Paths** | **[]string** | Path to the shared resource in your account. | [optional] [default to null]
**Recipients** | [**[]ShareRecipient1**](ShareRecipient_1.md) | Array of recipients. | [optional] [default to null]
**Messages** | [**[]Message1**](Message_1.md) | Array of invitation messages. | [optional] [default to null]
**Inherited** | **bool** | True if share inherited from parent folder. | [optional] [default to null]
**Status** | **int32** | Share activity status. Can be active (1) or deactivated (0). | [optional] [default to null]
**HasNotification** | **bool** | True if share has notification. | [optional] [default to null]
**Created** | **string** | Timestamp of share creation. | [optional] [default to null]
**Modified** | **string** | Timestamp of share modification. Can be &#x60;null&#x60; if it wasn&#x27;t modified. | [optional] [default to null]
**TrackingStatus** | **string** | Checks recipient received status and returns whether it&#x27;s been recevied (&#x60;complete&#x60;,) partial recevied (&#x60;incomplete&#x60;,) or not recevied yet (&#x60;pending&#x60;.) | [optional] [default to null]
**FormId** | **int32** | ID of the form. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

