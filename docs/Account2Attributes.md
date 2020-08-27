# Account2Attributes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccountName** | **string** | PLACEHOLDER | [optional] [default to null]
**Username** | **string** | Name of the account. | [optional] [default to null]
**MaxUsers** | **int32** | Maximum number of users the account can have. This can be increased by contacting ExaVault Support. | [optional] [default to null]
**UserCount** | **int32** | Current number of users on the account. | [optional] [default to null]
**Status** | **int32** | Account status flag. A one (1) means the account is active; zero (0) means it is suspended. | [optional] [default to null]
**Branding** | **bool** | Branding flag. Set to &#x60;true&#x60; if the account has branding functionality enabled. | [optional] [default to null]
**CustomDomain** | **bool** | Custom domain flag. Set to &#x60;true&#x60; if account type allows custom domain functionality. | [optional] [default to null]
**PlanCode** | **string** | (ExaVault Use Only) Code of the plan account is signed up for. | [optional] [default to null]
**WhmcsPlanId** | **int32** | (ExaVault Use Only) Internal ID of the service in CMS. | [optional] [default to null]
**Quota** | [***AccountAttributesQuota**](AccountAttributes_quota.md) |  | [optional] [default to null]
**SecureOnly** | **bool** | Flag to indicate whether the account disables connections via insecure protocols (e.g. FTP). Set to &#x60;true&#x60; to disable all traffic over port 21. | [optional] [default to null]
**ComplexPasswords** | **bool** | Flag to indicate whether the account requires complex passwords. Set to &#x60;true&#x60; to require complex passwords on all users and shares. | [optional] [default to null]
**ShowReferralLinks** | **bool** | Flag to indicate showing of referrals links in the account. Set to &#x60;true&#x60; to include marketing messages in share invitations. | [optional] [default to null]
**ExternalDomains** | **string** | Custom domain used to brand this account. | [optional] [default to null]
**AllowedIp** | **string** | Range of IP addresses allowed to access this account. | [optional] [default to null]
**CallbackSettings** | [**[]CallbackSettings2**](CallbackSettings_2.md) | Callback settings (Webhooks) of the account. | [optional] [default to null]
**BrandingSettings** | [***BrandingSettings2**](BrandingSettings_2.md) |  | [optional] [default to null]
**Trial** | [***AccountAttributesTrial**](AccountAttributes_trial.md) |  | [optional] [default to null]
**ClientId** | **int32** | (ExaVault Use Only) Internal ID of the account in CMS. | [optional] [default to null]
**WelcomeEmailContent** | **string** | Content of welcome email each new user will receive. | [optional] [default to null]
**WelcomeEmailSubject** | **string** | Subject of welcome email each new user will receive. | [optional] [default to null]
**CustomSignature** | **string** | Custom signature for all account emails users or recipients will receive. | [optional] [default to null]
**AccountOnboarding** | **bool** | Whether the web application onboarding help is enabled for new users in the account. | [optional] [default to null]
**Created** | **string** | Timestamp of account creation. | [optional] [default to null]
**Modified** | **string** | Timestamp of account modification. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

