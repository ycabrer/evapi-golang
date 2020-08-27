# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**GetWebhookLogs**](WebhooksApi.md#GetWebhookLogs) | **Get** /activity/webhooks | Get webhook logs

# **GetWebhookLogs**
> WebhooksActivityResponse GetWebhookLogs(ctx, evApiKey, evAccessToken, optional)
Get webhook logs

Returns the webhook logs for your account. Optional query paramaters will filter the returned results based on a number of options including path, tpye of event, or status code. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
 **optional** | ***WebhooksApiGetWebhookLogsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a WebhooksApiGetWebhookLogsOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **offset** | **optional.Int32**| Records to skip before returning results | 
 **limit** | **optional.Int32**| Limit of the records list | 
 **path** | **optional.String**| Path used to filter records | 
 **statusCode** | **optional.Int32**| Filter by webhook response status code | 
 **event** | **optional.String**| Filter by triggered event | 
 **sort** | **optional.String**| Comma separated list sort params | 
 **username** | **optional.String**| Filter by triggering username | 

### Return type

[**WebhooksActivityResponse**](WebhooksActivityResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

