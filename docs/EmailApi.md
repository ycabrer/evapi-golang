# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**PostEmailReferral**](EmailApi.md#PostEmailReferral) | **Post** /email/referral | Send referral email to a given address
[**PostEmailWelcomeUsername**](EmailApi.md#PostEmailWelcomeUsername) | **Post** /email/welcome/{username} | Resend welcome email to specific user

# **PostEmailReferral**
> InlineResponse2014 PostEmailReferral(ctx, evAccessToken, evApiKey, optional)
Send referral email to a given address

Send a referral email to an email address. If the recipient signs up for ExaVault, we'll apply a credit to your account for the referral. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***EmailApiPostEmailReferralOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a EmailApiPostEmailReferralOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body14**](Body14.md)|  | 

### Return type

[**InlineResponse2014**](inline_response_201_4.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **PostEmailWelcomeUsername**
> InlineResponse2014 PostEmailWelcomeUsername(ctx, evAccessToken, username, evApiKey)
Resend welcome email to specific user

Resend the initial welcome email to specific user.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **username** | **string**| A username to send welcome email to | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse2014**](inline_response_201_4.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

