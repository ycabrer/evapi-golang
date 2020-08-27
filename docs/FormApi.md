# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**AddFormMessage**](FormApi.md#AddFormMessage) | **Post** /forms/entries/{shareHash}/{entryId}/{nodeId} | Add a form submission
[**FormEntries**](FormApi.md#FormEntries) | **Post** /forms/{shareHash}/entries | Add user data to a form
[**FormsEntriesCompleteEntryIdPost**](FormApi.md#FormsEntriesCompleteEntryIdPost) | **Post** /forms/entries/complete-entry/{id} | 
[**FormsEntriesIdDelete**](FormApi.md#FormsEntriesIdDelete) | **Delete** /forms/entries/{id} | 
[**FormsEntriesIdGet**](FormApi.md#FormsEntriesIdGet) | **Get** /forms/entries/{id} | 
[**GetForms**](FormApi.md#GetForms) | **Get** /forms | Get form data for a receive folder
[**GetFormsId**](FormApi.md#GetFormsId) | **Get** /forms/{id} | Get form details
[**UpdateForm**](FormApi.md#UpdateForm) | **Patch** /forms/{id} | Updates a form with given parameters

# **AddFormMessage**
> InlineResponse2011 AddFormMessage(ctx, evApiKey, evAccessToken, entryId, nodeId, shareHash)
Add a form submission

Adds a set of submission data to the form submission history 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **entryId** | **string**| Id of the entry to associate a node with | 
  **nodeId** | **string**| Id of the node to be associated with an entry | 
  **shareHash** | **string**| Hash of a share that owns current form | 

### Return type

[**InlineResponse2011**](inline_response_201_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **FormEntries**
> InlineResponse201 FormEntries(ctx, evApiKey, shareHash, optional)
Add user data to a form

Upload collected form field data and associate the data with files that are in the receive folder. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API key required to make the API call. | 
  **shareHash** | **string**| Hash of a receive that related to a given form | 
 **optional** | ***FormApiFormEntriesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a FormApiFormEntriesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body3**](Body3.md)|  | 

### Return type

[**InlineResponse201**](inline_response_201.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **FormsEntriesCompleteEntryIdPost**
> InlineResponse2004 FormsEntriesCompleteEntryIdPost(ctx, evApiKey, id)


Notifies about form entry completion 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API key required to make the API call. | 
  **id** | **string**| Id of the entry to be completed | 

### Return type

[**InlineResponse2004**](inline_response_200_4.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **FormsEntriesIdDelete**
> FormsEntriesIdDelete(ctx, evAccessToken, id, evApiKey)


Deletes form data for a given entry id 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **string**| Id of the entry to be deleted data for | 
  **evApiKey** | **string**| API Key required to make the API call.  | 

### Return type

 (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **FormsEntriesIdGet**
> FormDataResponse FormsEntriesIdGet(ctx, evAccessToken, formId, evApiKey, optional)


Returns form data entries for a specific form 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **formId** | **string**|  | 
  **evApiKey** | **string**| API Key required to make the API call.  | 
 **optional** | ***FormApiFormsEntriesIdGetOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a FormApiFormsEntriesIdGetOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **limit** | **optional.Int32**| Limit of records to be returned (for pagination) | 
 **offset** | **optional.Int32**| Current offset of records (for pagination) | 

### Return type

[**FormDataResponse**](FormDataResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetForms**
> InlineResponse2002 GetForms(ctx, evApiKey, shareHash, evAccessToken, optional)
Get form data for a receive folder

Returns the details of the form assigned to a receive folder. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API key required to make the API call. | 
  **shareHash** | **string**| Share hash to retrieve the form for. | 
  **evAccessToken** | **string**| Access Token required to make the API call. | 
 **optional** | ***FormApiGetFormsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a FormApiGetFormsOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Related record types to include in the response. | 

### Return type

[**InlineResponse2002**](inline_response_200_2.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetFormsId**
> InlineResponse2003 GetFormsId(ctx, evApiKey, id, evAccessToken, optional)
Get form details

Returns the details of the designated from on a receive folder. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API key required to make the API call. | 
  **id** | **int32**| Form ID to retrieve the setup for | 
  **evAccessToken** | **string**| Access Token required to make the API call. | 
 **optional** | ***FormApiGetFormsIdOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a FormApiGetFormsIdOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Related record types to include in the response. | 

### Return type

[**InlineResponse2003**](inline_response_200_3.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **UpdateForm**
> RegularFormResponse UpdateForm(ctx, evAccessToken, id, evApiKey, optional)
Updates a form with given parameters

Add, update, or delete a form's parameters. This call will replace your current form in its entirety, so if you want to keep any existing elements unchanged, submit the call with an element's current settings to preserve them. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **string**| Form id | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***FormApiUpdateFormOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a FormApiUpdateFormOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body2**](Body2.md)|  | 

### Return type

[**RegularFormResponse**](Regular form response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

