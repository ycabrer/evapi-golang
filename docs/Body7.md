# Body7

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Username** | **string** | Username of the user to create. This should follow standard username conventions; e.g. all lowercase, no spaces, etc. We do allow email addresses as usernames. | [default to null]
**Nickname** | **string** | An optional nickname (e.g. &#x27;David from Sales&#x27;). | [optional] [default to null]
**HomeResource** | **string** | The path to the user&#x27;s home folder. For the account root, specify &#x60;/&#x60;. Otherwise, use standard Unix path format, e.g. &#x60;/path/to/some/dir&#x60;. The user will be locked to this directory and unable to move &#x27;up&#x27; in the account. If the folder does not exist in the account, it will be created. Note that users with the role &#x60;admin&#x60; cannot have a folder other than &#x60;/&#x60;. | [default to null]
**Email** | **string** | The user&#x27;s email address. | [default to null]
**Password** | **string** | The user&#x27;s password. | [default to null]
**Role** | **string** | The user&#x27;s role. Note that admin users cannot have a &#x60;homeResource&#x60; other than &#x60;/&#x60;, and will be setup with full permissions regardless of what you specify in the &#x60;permissions&#x60; property. | [default to null]
**Permissions** | **string** | A CSV string of user permissions. For example: &#x60;upload,download,list&#x60;. Note that users will be unable to see any files in the account unless you include &#x60;list&#x60; permission.   | [default to null]
**TimeZone** | **string** | The user&#x27;s timezone, used for accurate time display within the application. See &lt;a href&#x3D;&#x27;https://php.net/manual/en/timezones.php&#x27; target&#x3D;&#x27;blank&#x27;&gt;this page&lt;/a&gt; for allowed values.  | [default to null]
**Expiration** | [***Object**](.md) | Optional timestamp when the user should expire, formatted in ISO 8601. | [optional] [default to null]
**Locked** | **bool** | If true, the user&#x27;s account is locked by default. Locked users cannot log in. | [optional] [default to false]
**WelcomeEmail** | **bool** | If &#x60;true&#x60;, send a user email upon creation. The default welcome email can be configured from the settings page in your account. | [optional] [default to false]
**Onboarding** | **bool** | If &#x60;true&#x60;, enable extra help popups in the web application for this user. | [optional] [default to false]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

