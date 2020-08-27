# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**DeleteEmailList**](EmailListsApi.md#DeleteEmailList) | **Delete** /email-lists/{id} | Delete an email list with given id
[**GetEmailLists**](EmailListsApi.md#GetEmailLists) | **Get** /email-lists | Get all email groups
[**GetEmailListsId**](EmailListsApi.md#GetEmailListsId) | **Get** /email-lists/{id} | Get individual email list
[**PatchEmailList**](EmailListsApi.md#PatchEmailList) | **Patch** /email-lists/{id} | Update an email list
[**PostEmailLists**](EmailListsApi.md#PostEmailLists) | **Post** /email-lists | Create new email list

# **DeleteEmailList**
> InlineResponse2001 DeleteEmailList(ctx, evAccessToken, id, evApiKey)
Delete an email list with given id

Permanently delete an email list. List action is not reversable. We recommend making a user confirm this action before sending the API call. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **string**| Form id | 
  **evApiKey** | **string**| API Key required to make the API call.  | 

### Return type

[**InlineResponse2001**](inline_response_200_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetEmailLists**
> InlineResponse200 GetEmailLists(ctx, evAccessToken, evApiKey, optional)
Get all email groups

Retrieve a list of all email groups by default. Results can optionally be limited by using paramaters to specify the request. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***EmailListsApiGetEmailListsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a EmailListsApiGetEmailListsOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **include** | **optional.String**| Related record types to include in the response. | 

### Return type

[**InlineResponse200**](inline_response_200.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetEmailListsId**
> EmailListResponse1 GetEmailListsId(ctx, evAccessToken, id, evApiKey)
Get individual email list

Retrieve all the metadata tied to a specific email list. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **string**| Form id | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**EmailListResponse1**](EmailListResponse_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PatchEmailList**
> EmailListsResponse2 PatchEmailList(ctx, evAccessToken, id, evApiKey, optional)
Update an email list

Update an email list in your account. This is full replace, so if you do not want to delete an email already on your list, be sure to include the email in your call. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **string**| Form id | 
  **evApiKey** | **string**| API Key required to make the API call.  | 
 **optional** | ***EmailListsApiPatchEmailListOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a EmailListsApiPatchEmailListOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body1**](Body1.md)|  | 

### Return type

[**EmailListsResponse2**](EmailListsResponse_2.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PostEmailLists**
> EmailListsResponse1 PostEmailLists(ctx, evAccessToken, evApiKey, optional)
Create new email list

Create a new email list. Among other things, email lists can be used to send files or share folders with a group of email addresses at once.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***EmailListsApiPostEmailListsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a EmailListsApiPostEmailListsOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body**](Body.md)|  | 

### Return type

[**EmailListsResponse1**](EmailListsResponse_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

