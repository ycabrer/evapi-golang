# ResourceCollectionExtendedResponseAttributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Hash** | **string** | Unique hash of the resource. | [optional] [default to null]
**Name** | **string** | Resource name, e.g. the name of the file or folder. | [optional] [default to null]
**Extension** | **string** | Resource extension. Property exists only if resource &#x60;type&#x60; is file. | [optional] [default to null]
**Type_** | **string** | Type of the resource. | [optional] [default to null]
**CreatedBy** | **string** | Username of the creator. | [optional] [default to null]
**UploadDate** | **string** | Timestamp of resource upload. | [optional] [default to null]
**CreatedAt** | **string** | Timestamp of resource creation. | [optional] [default to null]
**UpdatedAt** | **string** | Timestamp of resource modification. | [optional] [default to null]
**AccessedAt** | **string** | Timestamp of the time when resource was accessed. | [optional] [default to null]
**Parent** | **string** | Parent path of the resource. | [optional] [default to null]
**Path** | **string** | Full path to the resource. | [optional] [default to null]
**FileCount** | **int32** | Count of files in resource. Property exists only if resource &#x60;type&#x60; is folder. | [optional] [default to null]
**Size** | **int64** | Resource size. | [optional] [default to null]
**Previewable** | **bool** | Can resource be previewed. Property equals &#x60;null&#x60; if resource &#x60;type&#x60; is folder. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

