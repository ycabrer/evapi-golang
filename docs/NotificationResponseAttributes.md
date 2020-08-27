# NotificationResponseAttributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**UserId** | **string** | ID of the user that the notification belongs to. | [optional] [default to null]
**Type_** | **string** | Type of the resoucre the notification is attached to.  | [optional] [default to null]
**Path** | **string** | Path to the item that the notification is set on. | [optional] [default to null]
**Name** | **string** | Name of the item that the notification is set on. | [optional] [default to null]
**Action** | **string** | Action that triggers notification. | [optional] [default to null]
**Usernames** | **[]string** | Detail on which users can trigger the notification. | [optional] [default to null]
**Recipients** | [**[]NotificartionRecipient**](NotificartionRecipient.md) | Notification recipients. | [optional] [default to null]
**RecipientEmails** | **[]string** | Email addresses of all recipients. | [optional] [default to null]
**SendEmail** | **string** | Whether or not an email will send when the notification is triggered. | [optional] [default to null]
**ReadableDescription** | **string** | Human readable description of the notification. | [optional] [default to null]
**ReadableDescriptionWithoutPath** | **string** | Human readable description of the notification without item path. | [optional] [default to null]
**ShareId** | **string** | ID of the share that the notification belogns to. | [optional] [default to null]
**Message** | **string** | Custom message that will be sent to the notification recipients. | [optional] [default to null]
**Created** | **string** | Timestamp of notifiction creation. | [optional] [default to null]
**Modified** | **string** | Timestamp of notification modification. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

