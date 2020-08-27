# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**DeleteSharesId**](SharesApi.md#DeleteSharesId) | **Delete** /shares/{id} | Deactivate a share
[**GetSharesId**](SharesApi.md#GetSharesId) | **Get** /shares/{id} | Get a share
[**PatchSharesId**](SharesApi.md#PatchSharesId) | **Patch** /shares/{id} | Update a share
[**PostShares**](SharesApi.md#PostShares) | **Post** /shares | Creates a share
[**PostSharesCompleteSendId**](SharesApi.md#PostSharesCompleteSendId) | **Post** /shares/complete-send/{id} | Complete send files

# **DeleteSharesId**
> DeleteSharesId(ctx, evAccessToken, id, evApiKey)
Deactivate a share

Delete a share. Deleting a share does not remove the underlying files for shared_folder and receive share types; it merely removes the access URL. Delating a send share type does remove the associated files, as files that have been sent are only associated with the share, and aren't stored anywhere else in the account.  **Notes:**  Authenticated user's role must be admin or master, or user must be the owner of the specified share.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the share | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

 (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetSharesId**
> InlineResponse20021 GetSharesId(ctx, evApiKey, evAccessToken, id, optional)
Get a share

Returns a share object specified by a given share ID.  **Notes:**    - Authenticated user should be the owner of the specified share.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **id** | **int32**| PLACEHOLDER | 
 **optional** | ***SharesApiGetSharesIdOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a SharesApiGetSharesIdOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;owner&#x60;, &#x60;resource&#x60;, &#x60;notifications&#x60;, &#x60;messages&#x60;. | 

### Return type

[**InlineResponse20021**](inline_response_200_21.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PatchSharesId**
> RegularShareResponse1 PatchSharesId(ctx, body, evApiKey, evAccessToken, id)
Update a share

Change the settings on an active share.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **body** | [**Body16**](Body16.md)|  | 
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **id** | **int32**| PLACEHOLDER | 

### Return type

[**RegularShareResponse1**](Regular share response_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PostShares**
> RegularShareResponse PostShares(ctx, evAccessToken, evApiKey, optional)
Creates a share

Creates a new share object for the given path in your account. We support three types of shares:    - A **shared folder** allows you to let outside parties access a folder in your account (including any files and nested subfolders) using just a link. Shared folders can be restricted; e.g. with an expiration date, password, download-only, etc. Shared folders are 'live'; if someone makes a change to a file in your shared folder, it will be immediately reflected in your account, and vice-versa.   - A **file send** lets you send one or more files via an easy download link. File sends are different than shared folders because file sends are 'point in time' -- the recipient will get the files as you sent them. If you later make a change to the source file, it will not be updated for the recipient.   - A **receive folder** lets you receive files into your account. You can either send users a link, or optionally [embed a customized form](https://www.exavault.com/docs/account/05-file-sharing/05-upload-widget) on your website.  **Notes:**  Authenticated user requires share permission.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***SharesApiPostSharesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a SharesApiPostSharesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body15**](Body15.md)|  | 

### Return type

[**RegularShareResponse**](Regular share response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PostSharesCompleteSendId**
> RegularShareResponse2 PostSharesCompleteSendId(ctx, evApiKey, evAccessToken, id)
Complete send files

After uploading the files to be sent, use this method to trigger invitation emails and finish the send files setup.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **id** | **int32**| PLACEHOLDER | 

### Return type

[**RegularShareResponse2**](Regular share response_2.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

