# ShareRecipient

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int32** | ID of the recipient. | [optional] [default to null]
**ShareId** | **string** | ID of the share that the recipoient belongs to. | [optional] [default to null]
**Type_** | **string** | Type of the recipient. | [optional] [default to null]
**Hash** | **string** | Share hash. | [optional] [default to null]
**Email** | **string** | Recipient email address. | [optional] [default to null]
**Sent** | **bool** | Set to true if invite email was sent; false otherwise. | [optional] [default to null]
**Received** | **bool** | Set to true if recipient has accessed the share. Note this is set to true when the recipient clicks the link to access the share; not when they download a file. | [optional] [default to null]
**Created** | **string** | Timestamp of adding recipient to the share. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

