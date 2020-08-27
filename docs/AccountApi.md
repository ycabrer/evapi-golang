# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**GetAccount**](AccountApi.md#GetAccount) | **Get** /account | Get account settings
[**PatchAccount**](AccountApi.md#PatchAccount) | **Patch** /account | Update account settings

# **GetAccount**
> InlineResponse20019 GetAccount(ctx, evApiKey, evAccessToken)
Get account settings

Get information about the an account  At least one of the headers **ev-api-key** and **ev-access-token** are required.  If both headers are specified, only information about the the account associated with the key/token is returned.  If only one of the headers is provided, you must also provide an **accountName** parameter with the name of the desired account, which will provide more limited information.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| Optional if seeking limited info about account, and ev-access-token is provided. | 
  **evAccessToken** | **string**| Optional if seeking limited info about account, and ev-api-key is present | 

### Return type

[**InlineResponse20019**](inline_response_200_19.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PatchAccount**
> AccountPublicResponse PatchAccount(ctx, evApiKey, evAccessToken, optional)
Update account settings

Update account settings. Only an admin user or the master user can perform this operation.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| ExaVault API Key | 
  **evAccessToken** | **string**| Access token required to make the API call. | 
 **optional** | ***AccountApiPatchAccountOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a AccountApiPatchAccountOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body13**](Body13.md)| Update Account Settings | 

### Return type

[**AccountPublicResponse**](AccountPublicResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

