# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**DeleteRecipientsSharesEmail**](RecipientsApi.md#DeleteRecipientsSharesEmail) | **Delete** /recipients/shares/{email} | Delete a share recipient from all shares
[**DeleteRecipientsSharesShareIdEmail**](RecipientsApi.md#DeleteRecipientsSharesShareIdEmail) | **Delete** /recipients/shares/{shareId}/{email} | Delete a share recipient from a single share
[**GetRecipients**](RecipientsApi.md#GetRecipients) | **Get** /recipients | Get share recipient emails
[**PostRecipientsSharesInvitesShareId**](RecipientsApi.md#PostRecipientsSharesInvitesShareId) | **Post** /recipients/shares/invites/{shareId} | Resend invitations to share recipients

# **DeleteRecipientsSharesEmail**
> InlineResponse20023 DeleteRecipientsSharesEmail(ctx, evAccessToken, email, evApiKey)
Delete a share recipient from all shares

Delete a share recipient from all shares they've been invited to. This will not delete any files or folders. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **email** | **string**| PLACEHOLDER | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse20023**](inline_response_200_23.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **DeleteRecipientsSharesShareIdEmail**
> InlineResponse20023 DeleteRecipientsSharesShareIdEmail(ctx, evAccessToken, shareId, email, evApiKey)
Delete a share recipient from a single share

Delete a share recipient from a single share they've been invited to. This will not delete any files or folders. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **shareId** | **int32**| PLACEHOLDER | 
  **email** | **string**| PLACEHOLDER | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse20023**](inline_response_200_23.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetRecipients**
> InlineResponse20022 GetRecipients(ctx, evAccessToken, evApiKey)
Get share recipient emails

Retrieve all email addresses that have been sent a share in the past.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse20022**](inline_response_200_22.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PostRecipientsSharesInvitesShareId**
> InlineResponse2015 PostRecipientsSharesInvitesShareId(ctx, evAccessToken, shareId, evApiKey)
Resend invitations to share recipients

Resend invitations to all recipients on a defined share. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **shareId** | **int32**| PLACEHOLDER | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse2015**](inline_response_201_5.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

