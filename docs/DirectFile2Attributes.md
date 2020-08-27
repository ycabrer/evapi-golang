# DirectFile2Attributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Path** | **string** | Path to the folder direct file is set on. | [optional] [default to null]
**IsEnabled** | **bool** | Flag indicates if direct file is turned &#x60;on&#x60; or &#x60;off&#x60;. | [optional] [default to null]
**IsIndexEnabled** | **bool** | Flag indicates if folder listing is &#x60;on&#x60; or &#x60;off&#x60;. If it is enabled you can see folder content in the browser. | [optional] [default to null]
**BlockUntil** | **string** | Timestamp of direct file block until date. Equals &#x60;0000-00-00 00:00:00&#x60; when no block date is setup. Used when direct file bandwidth quota limit crossed. | [optional] [default to null]
**Created** | **string** | Unix timestamp of direct file creation. | [optional] [default to null]
**Modified** | **string** | Unix timestamp of direct file modification. | [optional] [default to null]
**AccountId** | **int32** | ID of the account the direct file belongs to.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

