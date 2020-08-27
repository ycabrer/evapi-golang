# UserAttributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Status** | **int32** | Indicates user activity status. &#x60;0&#x60; means the user is locked and cannot log in. &#x60;1&#x60; means the user is active and can log in. | [default to null]
**Expiration** | [***Object**](.md) | Timestamp of user expiration. | [optional] [default to null]
**Created** | [**time.Time**](time.Time.md) | Timestamp of user creation. | [default to null]
**Modified** | **string** | Timestamp of user modification. | [default to null]
**AccessTimestamp** | [***Object**](.md) | Timestamp of most recent successful user login. | [optional] [default to null]
**AccountName** | **string** | Name of the account this user belongs to. | [default to null]
**Username** | **string** | Username of the user. | [default to null]
**Nickname** | **string** | Nickname of the user. | [default to null]
**Email** | [***Object**](.md) | Email address of the user. | [optional] [default to null]
**HomeDir** | **string** | Path to the user&#x27;s home folder. | [default to null]
**Permissions** | [***UserAttributesPermissions**](User_attributes_permissions.md) |  | [default to null]
**Role** | **string** | User&#x27;s access level | [default to null]
**TimeZone** | **string** | User&#x27;s timezone. See &lt;a href&#x3D;&#x27;https://php.net/manual/en/timezones.php&#x27; target&#x3D;&#x27;blank&#x27;&gt;this page&lt;/a&gt; for allowed values. | [default to null]
**Onboarding** | **bool** | Whether the onboarding help system is enabled for this user. &#x60;true&#x60; means that additional help popups are displayed in the web application for this user. | [default to null]
**FirstLogin** | [***Object**](.md) | &#x60;true&#x60; if the user has logged into the system. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

