# AccountAttributesQuota

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**DiskLimit** | **int64** | Amount of disk space that the account has available to it. This may be increased by upgrading to a larger plan. | [optional] [default to null]
**BandwidthLimit** | **int64** | Amount of bandwidth that the account has available before a warning is generated. All ExaVault accounts include unlimited bandwidth, but we flag high-bandwidth users. | [optional] [default to null]
**DiskUsed** | **int64** | Amount of disk space currently in use. | [optional] [default to null]
**BandwidthUsed** | **int64** | Amount of bandwidth used by this account in the last billing period. | [optional] [default to null]
**NoticeEnabled** | **int32** | Should a quota warning be sent to the account owner when a threshold level of space utilization is reached? | [optional] [default to null]
**NoticeThreshold** | **int32** | Treshold that triggers a quota notification. This represents the \&quot;percent full\&quot; your account must be before the quota notification is generated. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

