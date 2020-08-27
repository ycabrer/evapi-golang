# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**GetShares**](ShareApi.md#GetShares) | **Get** /shares | Get a list of shares

# **GetShares**
> InlineResponse20020 GetShares(ctx, evAccessToken, evApiKey, optional)
Get a list of shares

Returns array of all share objects that the authenticated user has access to. Sorting and filtering options allow you to limit the returned list.  Notes: Authenticated user requires share permission. To get share objects with type send, authenticated user's role must be admin or master.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***ShareApiGetSharesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ShareApiGetSharesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **hash** | **optional.String**| Returns single share by hash | 
 **offset** | **optional.Int32**| Current offset of records (for pagination) | [default to 0]
 **limit** | **optional.Int32**| Limit of records to be returned (for pagination) | [default to 100]
 **scope** | **optional.String**| PLACEHOLDER | [default to all]
 **sort** | **optional.String**| PLACEHOLDER | 
 **type_** | **optional.String**| Filter shares by type | 
 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;owner&#x60;, &#x60;resource&#x60;, &#x60;notifications&#x60;, &#x60;messages&#x60;, &#x60;activity&#x60;. | 
 **path** | **optional.String**| Path expression to filter shares by | 

### Return type

[**InlineResponse20020**](inline_response_200_20.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

