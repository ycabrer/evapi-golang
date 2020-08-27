# Body13

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**QuotaNoticeEnabled** | **bool** | Whether the system should email the account owner when usage exceeds quotaNoticeThreshold value | [optional] [default to null]
**QuotaNoticeThreshold** | **int32** | Percent of account usage to trigger quota notices for. | [optional] [default to null]
**SecureOnly** | **bool** | Whether unencrypted FTP connections should be denied for the account. | [optional] [default to null]
**ComplexPasswords** | **bool** | Whether to require complex passwords for all passwords. | [optional] [default to null]
**ShowReferralLinks** | **bool** | Whether to display links for others to sign up on share views and invitation emails | [optional] [default to null]
**ExternalDomain** | [**[]Object**](.md) | Custom address used for web file manager. Not available for all account types. | [optional] [default to null]
**EmailContent** | **string** | Content of welcome email template. | [optional] [default to null]
**EmailSubject** | **string** | Subject line for welcome emails | [optional] [default to null]
**AllowedIpRanges** | [**[]AccountAllowedIpRanges**](account_allowedIpRanges.md) | IP Address Ranges for restricting account access | [optional] [default to null]
**CallbackSettings** | [***CallbackSettings1**](CallbackSettings_1.md) |  | [optional] [default to null]
**BrandingSettings** | [***BrandingSettings1**](BrandingSettings_1.md) |  | [optional] [default to null]
**AccountOnboarding** | **bool** | PLACEHOLDER | [optional] [default to null]
**CustomSignature** | **string** | PLACEHOLDER | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

