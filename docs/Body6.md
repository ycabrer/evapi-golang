# Body6

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Type_** | **string** | Type of resource you&#x27;re setting the notification on. | [default to null]
**Action** | **string** | Type of action to filter on. Notifications will only be fired for the given type of action. | [default to null]
**Usernames** | **[]string** | Determines which users should trigger the notification. Either one of the values above, or an array of usernames. | [default to null]
**SendEmail** | **bool** | Set to true if the user should be notified by email when the notification is triggered. | [default to null]
**Emails** | **[]string** | Email addresses to send the notification to. If not specified, sends to the authenticated user. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

