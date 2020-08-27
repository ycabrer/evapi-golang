# Body4

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Path** | **string** | Full path of file/folder where the notification is set. | [optional] [default to null]
**Action** | **string** | Type of action to filter on. Notifications will only be fired for the given type of action. | [optional] [default to null]
**Usernames** | **[]string** | Array of usernames or with one flag to filter on. This options allows to filter what users will trigger the notification. | [optional] [default to null]
**SendEmail** | **bool** | Set to true if the user should be notified by email when the notification is triggered. | [optional] [default to null]
**Emails** | **[]string** | Email addresses to send notification to. If not specified, sends to the authenticated user. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

