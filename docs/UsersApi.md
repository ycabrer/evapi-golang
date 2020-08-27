# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**CreateUser**](UsersApi.md#CreateUser) | **Post** /users | Create a user
[**DeleteUser**](UsersApi.md#DeleteUser) | **Delete** /users/{id} | Delete a user
[**GetUser**](UsersApi.md#GetUser) | **Get** /users/{id} | Get info for a user
[**GetUsers**](UsersApi.md#GetUsers) | **Get** /users | Get a list of users
[**UpdateUser**](UsersApi.md#UpdateUser) | **Patch** /users/{id} | Update a user

# **CreateUser**
> UserResponseObject CreateUser(ctx, evAccessToken, evApiKey, optional)
Create a user

Adds a new user to the account. The user may be configured as an admin or standard user, and (if a standard user) may be assigned a restricted home directory and restricted permissions.   **Notes:** - Authenticated user's role must be admin or master; standard users are not allowed to create other users. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API key required to make the API call | 
 **optional** | ***UsersApiCreateUserOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a UsersApiCreateUserOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body7**](Body7.md)|  | 

### Return type

[**UserResponseObject**](User response object.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, multipart/form-data
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **DeleteUser**
> InlineResponse20010 DeleteUser(ctx, evAccessToken, id, evApiKey)
Delete a user

Delete a user from the account. Deleting a user does **NOT** delete any files from the account; it merely removes a user's access.   Only account administrators can delete a user 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| The user&#x27;s ID. Note that this is our internal ID, and _not the username_. You can obtain it by calling the &lt;a href&#x3D;\&quot;#operation/getUser\&quot;&gt;getUser&lt;/a&gt; method. | 
  **evApiKey** | **string**| API key required to make the API call. | 

### Return type

[**InlineResponse20010**](inline_response_200_10.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetUser**
> InlineResponse2009 GetUser(ctx, evAccessToken, id, evApiKey, optional)
Get info for a user

Get details for the specified user in your account.  See the response sample, below, for full details. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| The user&#x27;s ID. Note that this is our internal ID, and _not the username_. You can obtain it by calling the &lt;a href&#x3D;\&quot;#operation/getUser\&quot;&gt;getUser&lt;/a&gt; method. | 
  **evApiKey** | **string**| API Key | 
 **optional** | ***UsersApiGetUserOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a UsersApiGetUserOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Comma-separated list of relationships to include in response. Possible values include &#x60;homeResource&#x60; and &#x60;ownerAccount&#x60;. | 

### Return type

[**InlineResponse2009**](inline_response_200_9.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetUsers**
> InlineResponse2008 GetUsers(ctx, evAccessToken, evApiKey, optional)
Get a list of users

Gets array of all user objects in your account. Each element of the array will contain details on a single user.  **Notes:** - Authenticated user's role must be admin or master. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API key required to make the API call. | 
 **optional** | ***UsersApiGetUsersOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a UsersApiGetUsersOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **username** | **optional.String**|  | 
 **offset** | **optional.Int32**| Starting user record in the result set. Can be used for pagination. | [default to 0]
 **sort** | **optional.String**| Endpoint support multiple sort fields by allowing array of sort params. Sort fields should be applied in the order specified. The sort order for each sort field is ascending unless it is prefixed with a minus (“-“), in which case it will be descending. | [default to sort_users_nickname]
 **limit** | **optional.Int32**| Number of users to return. Can be used for pagination. | [default to 25]
 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;resource&#x60;, &#x60;account&#x60;. | 

### Return type

[**InlineResponse2008**](inline_response_200_8.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **UpdateUser**
> InlineResponse20011 UpdateUser(ctx, evAccessToken, id, evApiKey, optional)
Update a user

Updates specified user record in your account. Note that the unique key for this API call is our internal ID, and _not_ the username, as the username can be changed.    **Notes:** - Authenticated user's role must be admin or master. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| The user&#x27;s ID. Note that this is our internal ID, and _not the username_. You can obtain it by calling the &lt;a href&#x3D;\&quot;#operation/getUser\&quot;&gt;getUser&lt;/a&gt; method. | 
  **evApiKey** | **string**| API key required to make the API call. | 
 **optional** | ***UsersApiUpdateUserOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a UsersApiUpdateUserOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body8**](Body8.md)|  | 

### Return type

[**InlineResponse20011**](inline_response_200_11.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

