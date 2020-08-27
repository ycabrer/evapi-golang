# {{classname}}

All URIs are relative to *https://accountname.exavault.com/api/v2*

Method | HTTP request | Description
------------- | ------------- | -------------
[**CompressFiles**](ResourcesApi.md#CompressFiles) | **Post** /resources/compress | Compress resources
[**CopyResources**](ResourcesApi.md#CopyResources) | **Post** /resources/copy | Copy resources
[**CreateFolder**](ResourcesApi.md#CreateFolder) | **Post** /resources | Create a folder
[**DeleteResource**](ResourcesApi.md#DeleteResource) | **Delete** /resources/{id} | Delete a Resource
[**DeleteResources**](ResourcesApi.md#DeleteResources) | **Delete** /resources | Delete Resources
[**Download**](ResourcesApi.md#Download) | **Get** /resources/download | Download a file
[**ExtractFiles**](ResourcesApi.md#ExtractFiles) | **Post** /resources/extract | Extract resources
[**GetResourceList**](ResourcesApi.md#GetResourceList) | **Get** /resources/list | Get a list of all resources
[**GetResourceProperties**](ResourcesApi.md#GetResourceProperties) | **Get** /resources/{id} | Get resource metadata
[**GetResourceProperties_0**](ResourcesApi.md#GetResourceProperties_0) | **Get** /resources | Get Resource Properties
[**MoveResources**](ResourcesApi.md#MoveResources) | **Post** /resources/move | Move resources
[**Preview**](ResourcesApi.md#Preview) | **Get** /resources/preview | Preview a file
[**ResourcesIdPatch**](ResourcesApi.md#ResourcesIdPatch) | **Patch** /resources/{id} | Rename a resource.
[**ResourcesListIdGet**](ResourcesApi.md#ResourcesListIdGet) | **Get** /resources/list/{id} | Get a list of resources
[**Upload**](ResourcesApi.md#Upload) | **Post** /resources/upload | Upload a file

# **CompressFiles**
> InlineResponse2012 CompressFiles(ctx, evAccessToken, evApiKey, resources, parentResource, optional)
Compress resources

Create a zip archive containing the files from given set of paths. Note that this can be a very slow operation if you have indicated many files should be included in the archive.  **Notes:** - Authenticated user should have modify permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
  **resources** | **string**| Array of resources to be compressed into a zip archive. | 
  **parentResource** | **string**| Path where the new archive will be stored. | 
 **optional** | ***ResourcesApiCompressFilesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiCompressFilesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------




 **archiveName** | **optional.String**| Name of the newly created archive. | 

### Return type

[**InlineResponse2012**](inline_response_201_2.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **CopyResources**
> InlineResponse20017 CopyResources(ctx, evAccessToken, evApiKey, resources, parentResource)
Copy resources

Copies a set of exisiting files/folders (provided by an array **filePaths**) to the requested **destinationPath** in your account. In the **filePaths** array, you may specify paths pointing files/folders throughout the account, but everything will be copied to the  root of the **destinationPath**.  **Notes:** - Authenticated user should have modify permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
  **resources** | **string**| Array of resources to be copied. Can be path/id/hash | 
  **parentResource** | **string**| Destination of the copied files or folders. Can be path/id/hash | 

### Return type

[**InlineResponse20017**](inline_response_200_17.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **CreateFolder**
> ResourceResponseObject1 CreateFolder(ctx, evAccessToken, evApiKey, optional)
Create a folder

Create a new folder at the specified path. > **Notes:** - Authenticated user should have modify permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***ResourcesApiCreateFolderOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiCreateFolderOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **body** | [**optional.Interface of Body10**](Body10.md)|  | 

### Return type

[**ResourceResponseObject1**](Resource response object_1.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **DeleteResource**
> InlineResponse20014 DeleteResource(ctx, evAccessToken, id, evApiKey)
Delete a Resource

Delete the files/folders located at a given set of paths. Note that this call performs the delete **immediately**, and it is irreversible. We strongly recommend that you confirm your user's intention to delete file(s) before issuing this API call.  **Notes:** - Authenticated user should have delete permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the file or folder to delete. | 
  **evApiKey** | **string**| API Key required to make the API call. | 

### Return type

[**InlineResponse20014**](inline_response_200_14.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **DeleteResources**
> InlineResponse20014 DeleteResources(ctx, evApiKey, evAccessToken, filePaths, id, hash)
Delete Resources

Delete the files/folders located at a given set of paths. Note that this call performs the delete **immediately**, and it is irreversible. We strongly recommend that you confirm your user's intention to delete file(s) before issuing this API call.  **Notes:** - Authenticated user should have delete permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **filePaths** | [**[]string**](string.md)| Array containing paths of the files or folder to delete. | 
  **id** | [**[]string**](string.md)| Array containing ids of the files or folder to delete. | 
  **hash** | [**[]string**](string.md)| Array containing hashes of the files or folder to delete. | 

### Return type

[**InlineResponse20014**](inline_response_200_14.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **Download**
> Download(ctx, evAccessToken, resources, evApiKey, optional)
Download a file

Download a file. If more than one path is supplied, the files will be zipped before downloading with the downloadName param if supplied. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **resources** | **string**| Path of file or folder to be downloaded, starting from the root. Can also be an array of paths. | 
  **evApiKey** | **string**| API Key required to make the API call | 
 **optional** | ***ResourcesApiDownloadOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiDownloadOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **downloadName** | **optional.String**| If zipping multiple files, the name of the zip file to create and download. | 
 **polling** | **optional.Bool**| Used when downloading multiple files so url will be pulled till zip file is created. | 
 **pollingZipName** | **optional.String**| Reference to the previously created zip for polling operation. | 

### Return type

 (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **ExtractFiles**
> InlineResponse2013 ExtractFiles(ctx, evAccessToken, evApiKey, resource, parentResource)
Extract resources

Extract the contents of a zip archive to a specified directory. Note that this can be a very slow operation.  **Notes:** - Authenticated user should have modify permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
  **resource** | **string**| Path of the compressed resource, including the archive name.  | 
  **parentResource** | **string**| Path for the extracted resoure(s) to be stored.  | 

### Return type

[**InlineResponse2013**](inline_response_201_3.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetResourceList**
> InlineResponse20012 GetResourceList(ctx, evAccessToken, evApiKey, optional)
Get a list of all resources

Returns a list of all resources in the account. List can be filtered with the addition of query parameters.

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***ResourcesApiGetResourceListOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiGetResourceListOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------


 **hash** | **optional.String**| Hash of the resource to get listing of resources for. Required if no path specified. | 
 **path** | **optional.String**| Path to get listing of resources for. Required if no hash specified. | 
 **type_** | **optional.String**| Optional param to get only folder resources. | [default to folder]
 **sortBy** | **optional.String**| Endpoint support multiple sort fields by allowing array of sort params. Sort fields should be applied in the order specified. The sort order for each sort field is ascending unless it is prefixed with a minus (“-“), in which case it will be descending. | [default to sort_files_name]
 **offset** | **optional.Int32**| Determines which item to start on for pagination. Use zero (0) to start at the beginning of the list. | [default to 0]
 **limit** | **optional.Int32**| The number of files to limit the result. Cannot be set higher than 100. If you have more than one hundred files in your directory, make multiple calls to **getResourceList**, incrementing the **offset** parameter, above. | [default to 50]
 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;share&#x60;, &#x60;notification&#x60;, &#x60;directFile&#x60;, &#x60;parentNode&#x60;. | 

### Return type

[**InlineResponse20012**](inline_response_200_12.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetResourceProperties**
> InlineResponse20013 GetResourceProperties(ctx, evAccessToken, id, evApiKey, optional)
Get resource metadata

Gets metadata for specified file/folder path, including things like upload date, size and type. For the full list of returned properties, see the response syntax, below. > **Notes:** - Authenticated user should have list permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the file or folder to get metadata for. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***ResourcesApiGetResourcePropertiesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiGetResourcePropertiesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;share&#x60;, &#x60;notification&#x60;, &#x60;directFile&#x60;, &#x60;parentNode&#x60;. | 

### Return type

[**InlineResponse20013**](inline_response_200_13.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **GetResourceProperties_0**
> InlineResponse20015 GetResourceProperties_0(ctx, evAccessToken, path, hash, evApiKey, optional)
Get Resource Properties

Gets metadata for specified file/folder id or hash, including things like upload date, size and type. For the full list of returned properties, see the response syntax, below. > **Notes:** - Authenticated user should have list permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **path** | **string**| Paths of the file or folder to get metadata for. | 
  **hash** | **string**| Hash of the file or folder to get metadata for. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
 **optional** | ***ResourcesApiGetResourceProperties_1Opts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiGetResourceProperties_1Opts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------




 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;share&#x60;, &#x60;notification&#x60;, &#x60;directFile&#x60;, &#x60;resource&#x60;. | 

### Return type

[**InlineResponse20015**](inline_response_200_15.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **MoveResources**
> InlineResponse20018 MoveResources(ctx, evAccessToken, evApiKey, resources, parentResource, optional)
Move resources

Moves a set of exisiting files/folders (provided by an array **filePaths**) to the requested **destinationPath** in your account. In the **filePaths** array, you may specify paths pointing files/folders throughout the account, but everything will be moved to the  root of the **destinationPath**.  **Notes:** - Authenticated user should have modify permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API Key required to make the API call. | 
  **resources** | **string**| Resource name. | 
  **parentResource** | **string**| Path to the resource. | 
 **optional** | ***ResourcesApiMoveResourcesOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiMoveResourcesOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------




 **body** | [**optional.Interface of Body11**](Body11.md)|  | 

### Return type

[**InlineResponse20018**](inline_response_200_18.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **Preview**
> PreivewFileResponseObject Preview(ctx, evApiKey, evAccessToken, resource, size, optional)
Preview a file

Returns a resized image of the specified document for supported file types.  Image data returned is encoded in base64 format and can be viewed using the `<img>` element.   ```<img src='data:image/jpeg;base64' + results.image/>```  **Notes:** - Supported files types are `'jpg'`, `'jpeg'`, `'gif'`, `'png'`, `'bmp'`, `'pdf'`, `'psd'`, `'doc'` 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evApiKey** | **string**| API Key | 
  **evAccessToken** | **string**| Access Token | 
  **resource** | **string**| Path of the image relative to the user&#x27;s home directory. | 
  **size** | **string**| The size of the image. | 
 **optional** | ***ResourcesApiPreviewOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiPreviewOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------




 **width** | **optional.Int32**| Overrides sizes. Sets to a specific width. | 
 **height** | **optional.Int32**| Overrides sizes. Sets to a specific height. | 
 **page** | **optional.Int32**| Page number for the &#x60;.pdf&#x60; or &#x60;.doc&#x60; files. | [default to 0]

### Return type

[**PreivewFileResponseObject**](PreivewFile response object.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **ResourcesIdPatch**
> ResourceResponseObject ResourcesIdPatch(ctx, evAccessToken, evApiKey, id, optional)
Rename a resource.

Allows for updating the specified file or folder resource record's \"name\" parameter. The resource is identified by the numeric resource ID that is passed in as the last segment of the URI. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **evApiKey** | **string**| API key required to make the API call. | 
  **id** | **int32**| The numeric resource identifier. Resource IDs for all resources within a given directory, can be found by calling GET /resources/list using the resource ID of, or path to, that directory. | 
 **optional** | ***ResourcesApiResourcesIdPatchOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiResourcesIdPatchOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **body** | [**optional.Interface of Body9**](Body9.md)|  | 

### Return type

[**ResourceResponseObject**](Resource response object.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **ResourcesListIdGet**
> InlineResponse20016 ResourcesListIdGet(ctx, evAccessToken, id, evApiKey, optional)
Get a list of resources

Get a listing of files/folders for the specified path.   You can use this API call to get information about all files and folders at a specified path. By default, the API returns basic metadata on each file/folder. An optional 'detailed' parameter forces the return of additional metadata. As with all API calls, the path should be the full path relative to the user's home directory (e.g. `/myfiles/some_folder`).  **Notes:** - Authenticated user should have list permission. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **id** | **int32**| ID of the resource to get listing of resources for. | 
  **evApiKey** | **string**| API Key required to make the API call.  | 
 **optional** | ***ResourcesApiResourcesListIdGetOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiResourcesListIdGetOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------



 **sort** | **optional.String**| Sort method. Use in conjunction with **sort_order**, below. | [default to sort_files_name]
 **offset** | **optional.Int32**| Determines which item to start on for pagination. Use zero (0) to start at the beginning of the list. | [default to 0]
 **limit** | **optional.Int32**| The number of files to limit the result. Cannot be set higher than 100. If you have more than one hundred files in your directory, make multiple calls to **getResourceList**, incrementing the **offset** parameter, above. | [default to 50]
 **include** | **optional.String**| Comma separated list of relationships to include in response. Possible values are &#x60;share&#x60;, &#x60;notification&#x60;, &#x60;directFile&#x60;, &#x60;resource&#x60;. | 

### Return type

[**InlineResponse20016**](inline_response_200_16.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **Upload**
> ResourceResponseObject Upload(ctx, evAccessToken, path, fileSize, evApiKey, optional)
Upload a file

Uploads a file, with optional support for resuming a partially uploaded existing file. 

### Required Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **ctx** | **context.Context** | context for authentication, logging, cancellation, deadlines, tracing, etc.
  **evAccessToken** | **string**| Access token required to make the API call. | 
  **path** | **string**| Destination path for the file being uploaded, including the file name. | 
  **fileSize** | **int32**| File size, in bits, of the file being uploaded. | 
  **evApiKey** | **string**| API Key required to make API call. | 
 **optional** | ***ResourcesApiUploadOpts** | optional parameters | nil if no parameters

### Optional Parameters
Optional parameters are passed through a pointer to a ResourcesApiUploadOpts struct
Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------




 **file** | **optional.Interface of *os.File****optional.**|  | 
 **offsetBytes** | **optional.**| Allows a file upload to resume at a certain number of bytes. | 
 **resume** | **optional.**| True if upload resume is supported, false if it isn&#x27;t.  | [default to true]
 **allowOverwrite** | **optional.**| True if the file should be overwritten, false if different file names should be generated. Call checkFilesExist first if you need to determine whether or not a file with the same name already exists. | [default to false]

### Return type

[**ResourceResponseObject**](Resource response object.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

