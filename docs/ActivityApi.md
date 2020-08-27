# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**GetActivityLogs**](ActivityApi.md#GetActivityLogs) | **Get** /activity/session | Get activity logs
[**GetWebhookLogs**](ActivityApi.md#GetWebhookLogs) | **Get** /activity/webhooks | Get webhook logs

# **GetActivityLogs**
> SessionActivityResponse GetActivityLogs(ctx, evApiKey, evAccessToken, optional)
Get activity logs

Returns the activity logs for your account. Optional query paramaters will filter the returned results based on a number of options including usernames, activtiy types, or date ranges. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
 **optional** | ***ActivityApiGetActivityLogsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ActivityApiGetActivityLogsOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **offset** | **optional.Int32**| Offset of the records list | 
 **limit** | **optional.Int32**| Limit of the records list | 
 **userName** | **optional.String**| Username used for filtering a list | 
 **path** | **optional.String**| Path used to filter records | 
 **ipAddress** | **optional.String**| Used to filter session logs by ip address | 
 **type_** | **optional.String**| Filter session logs for operation type | 
 **startDate** | **optional.String**| Start date of the filter data range | 
 **endDate** | **optional.String**| End date of the filter data range | 
 **sort** | **optional.String**| Comma separated list sort params | 

### Return type

[**SessionActivityResponse**](SessionActivityResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

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
 **optional** | ***ActivityApiGetWebhookLogsOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ActivityApiGetWebhookLogsOpts struct
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

