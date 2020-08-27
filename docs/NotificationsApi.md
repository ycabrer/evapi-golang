# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**NotificationsGet**](NotificationsApi.md#NotificationsGet) | **Get** /notifications | Get a list of notifications
[**NotificationsIdDelete**](NotificationsApi.md#NotificationsIdDelete) | **Delete** /notifications/{id} | Delete a notification
[**NotificationsIdGet**](NotificationsApi.md#NotificationsIdGet) | **Get** /notifications/{id} | Get a notification&#x27;s metadata
[**NotificationsIdPatch**](NotificationsApi.md#NotificationsIdPatch) | **Patch** /notifications/{id} | Update a notification
[**NotificationsPost**](NotificationsApi.md#NotificationsPost) | **Post** /notifications | Create a new notification
[**NotificationsUnsubscribePost**](NotificationsApi.md#NotificationsUnsubscribePost) | **Post** /notifications/unsubscribe | Unsubscribe an email from a notification

# **NotificationsGet**
> InlineResponse2007 NotificationsGet(ctx, evAccessToken, evApiKey, optional)
Get a list of notifications

Returns array of all notification objects owned by the authenticated user. You can use sorting and filtering to limit the returned list.  **Notes:**   - Autheticated user should have notification permission

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call.  | 
 **optional** | ***NotificationsApiNotificationsGetOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a NotificationsApiNotificationsGetOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **type_** | **optional.String**| Type of notification to filter on. | 
 **offset** | **optional.Int32**| Starting notification record in the result set. Can be used for pagination. | [default to 0]
 **sort** | **optional.String**| Endpoint support multiple sort fields by allowing array of sort params. Sort fields should be applied in the order specified. The sort order for each sort field is ascending unless it is prefixed with a minus (“-“), in which case it will be descending. | [default to sort_notifications_date]
 **limit** | **optional.Int32**| Number of notification records to return. Can be used for pagination. | [default to 25]
 **include** | **optional.String**| Related record types to include in the response. | 

### Return type

[**InlineResponse2007**](inline_response_200_7.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **NotificationsIdDelete**
> InlineResponse2006 NotificationsIdDelete(ctx, evAccessToken, id, evApiKey)
Delete a notification

Deletes the specified notification. Note that deleting a notification _only_ deletes the notification &ndash; it does not delete any underlying files or folders. > **Notes:** - Authenticated user requires notification permission.  - Authenticated user should be the owner of the specified notification. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the notification. Use &lt;a href&#x3D;\&quot;#operation/getNotifications\&quot;&gt;getNotifications&lt;/a&gt; if you need to lookup an ID. | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse2006**](inline_response_200_6.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **NotificationsIdGet**
> InlineResponse2005 NotificationsIdGet(ctx, evAccessToken, id, evApiKey, optional)
Get a notification's metadata

Returns the specified notification object's metadata.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the notification. Use &lt;a href&#x3D;\&quot;#operation/getNotifications\&quot;&gt;getNotifications&lt;/a&gt; if you need to lookup an ID. | 
  **evApiKey** | **string**| API Key required to make the API call.  | 
 **optional** | ***NotificationsApiNotificationsIdGetOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a NotificationsApiNotificationsIdGetOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Related record types to include in the response. | 

### Return type

[**InlineResponse2005**](inline_response_200_5.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **NotificationsIdPatch**
> NotificationResponseObject NotificationsIdPatch(ctx, evAccessToken, id, evApiKey, optional)
Update a notification

Update an existing notification object.  **Notes:** - Authenticated user should have notification permission.  - Authenticated user should be the owner of the specified notification. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the notification. Use &lt;a href&#x3D;\&quot;#operation/getNotifications\&quot;&gt;getNotifications&lt;/a&gt; if you need to lookup an ID. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***NotificationsApiNotificationsIdPatchOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a NotificationsApiNotificationsIdPatchOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body4**](Body4.md)|  | 

### Return type

[**NotificationResponseObject**](Notification response object.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **NotificationsPost**
> NotificationResponseObject1 NotificationsPost(ctx, evAccessToken, evApiKey, resource, optional)
Create a new notification

Create a new notification for the given path in the current account. Notifications can be sent via email or webhook. To enable email, pass an array of email addresses to the `emails` parameter of this call. To enable webhooks, setup the webhook callback URL in your account settings.   **Notes:** - Authenticated user requires notification permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make API call.  | 
  **resource** | **string**| Path to the resource where a notification will be created.  | 
 **optional** | ***NotificationsApiNotificationsPostOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a NotificationsApiNotificationsPostOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body6**](Body6.md)|  | 

### Return type

[**NotificationResponseObject1**](Notification response object_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **NotificationsUnsubscribePost**
> NotificationsUnsubscribePost(ctx, evApiKey, evAccessToken, optional)
Unsubscribe an email from a notification

Unsubscribe an email address from a notification. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API key required to make the API call. | 
  **evAccessToken** | **string**| Access Token required to make the API call.  | 
 **optional** | ***NotificationsApiNotificationsUnsubscribePostOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a NotificationsApiNotificationsUnsubscribePostOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body5**](Body5.md)|  | 

### Return type

 (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

