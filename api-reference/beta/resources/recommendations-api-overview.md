---
title: "Use the Azure AD recommendations API to implement Azure AD best practices for your tenant"
description: "Azure Active Directory (Azure AD) Recommendations are personalized and actionable insights for you to implement Azure AD best practices in your tenant."
author: "hafowler"
ms.localizationpriority: medium
ms.prod: "directory-management"
doc_type: resourcePageType
ms.date: 02/02/2023
---

# Use the Azure AD recommendations API to implement Azure AD best practices for your tenant

Azure Active Directory (Azure AD) Recommendations are personalized and actionable insights for you to implement Azure AD best practices in your tenant. Use the recommendations API in Microsoft Graph to identify and track the insights, assess the guidance provided for implementing the best practices, and keep your tenant healthy, secure and optimized.

## The nature of Azure AD recommendations

Azure AD recommendations are of the following five categories:

- Productivity – Recommendations that affect admins and end user’s productive usage of Azure AD features.
- Security – Recommendations that affect your tenant’s security posture.
- Health – Recommendations that affect reliability, performance, availability, latency, errors, and service outages.
- Configuration – Recommendations that relate to resource configurations.
- Usage and compliance – Recommendations that relate to underutilization of Azure AD features and licenses or out of compliance resources.

Currently, 31 recommendations are available that map to these five categories.

## Manage recommendations

Azure AD recommendations are made up of two building blocks: **recommendations** and **the Azure AD resources they apply to**.

A single recommendation can apply to one or more Azure AD resource instances. For example, a recommendation relating to expiring application credentials will reference all apps in your tenant that have expiring application credentials.

For each recommendation, you have the following data:

- The type of recommendation. Up to 31 types are supported.
- The Azure AD resources to which the recommendation applies. These include users, groups, and applications.
- When Azure AD recommends the recommendation to have been completed before it impacts the associated service.
- The impact of the recommendation, which can be tenant-wide or resource-specific.
- A Microsoft-assigned priority ranking for the recommendation.
- The type of recommendation. For more information about types of recommendations, see [Types of recommendations](#types-of-recommendations).
- The status of the recommendation such as whether it’s still active or has been completed, dismissed, or postponed to a future date.

### Types of recommendations

31 types of recommendations are currently available in Azure AD Recommendations. These recommendations are identified in a recommendationType object that’s part of the recommendation object.

The following table lists all recommendation types and maps to their user-friendly names that are used on the Azure portal.

| recommendationType | Friendly name in the Azure portal | Comments |
|---|---|---|
| `adfsAppsMigration` | Migrate apps from ADFS to Azure AD | For more information, see [Migrate apps from ADFS to Azure AD](/azure/active-directory/reports-monitoring/recommendation-migrate-apps-from-adfs-to-azure-ad) |
| `enableDesktopSSO` |  |  |
| `enablePHS` |  |  |
| `enableProvisioning` |  |  |
| `switchFromPerUserMFA` | Convert per-user MFA to Conditional Access MFA | For more information, see [Convert per-user MFA to Conditional Access MFA](/azure/active-directory/reports-monitoring/recommendation-turn-off-per-user-mfa) |
| `tenantMFA` |  |  |
| `thirdPartyApps` | Integrate third party apps | **This one is temporarily offline (not sure the right term there). But the article linked here is not published, so will not work. For more information, see [Integrate third party apps](/azure/active-directory/reports-monitoring/recommendation-integrate-third-party-apps) |
| `turnOffPerUserMFA` |  | Should this also go to "Convert to Conditional Access MFA"? Or is there a separate rec for turning it off? |
| `useAuthenticatorApp` | Migrate to Microsoft authenticator | For more information, see [Migrate to Microsoft authenticator](/azure/active-directory/reports-monitoring/recommendation-migrate-to-authenticator) |
| `useMyApps` |  |  |
| `staleApps` | Remove unused apps | Moving to preview. https://review.learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/recommendation-remove-unused-apps?branch=pr-en-us-224791 |
| `staleAppCreds` | Remove unused credentials from apps | Moving to preview. https://review.learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/recommendation-remove-unused-credential-from-apps?branch=pr-en-us-224791 |
| `applicationCredentialExpiry` | Renew expiring application credentials | Moving to preview. https://review.learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/recommendation-remove-unused-credential-from-apps?branch=pr-en-us-224791 |
| `servicePrincipalKeyExpiry` | Renew expiring service principal credentials | Moving to preview. https://review.learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/recommendation-renew-expiring-service-principal-credential?branch=pr-en-us-224791 |
| `adminMFAV2` |  |  |
| `blockLegacyAuthentication` |  |  |
| `integratedApps` |  |  |
| `mfaRegistrationV2` |  |  |
| `pwagePolicyNew` |  |  |
| `passwordHashSync` |  |  |
| `oneAdmin` |  |  |
| `roleOverlap` |  |  |
| `selfServicePasswordReset` |  |  |
| `signinRiskPolicy` |  |  |
| `userRiskPolicy` |  |  |
| `verifyAppPublisher` |  |  |
| `privateLinkForAAD` |  |  |
| `appRoleAssignmentsGroups` |  |  |
| `appRoleAssignmentsUsers` |  |  |
| `managedIdentity` |  |  |
| `overprivilegedApps` |  |  |
| `unknownFutureValue` | Evolvable enumeration sentinel value. Do not use.  |

## API scenarios

You manage recommendations through the [recommendation resource type](recommendation.md) and its associated methods. This resource type exposes the impactedResources relationship that you use to query the Azure AD resource to which the recommendations apply.

The following are some of the most popular requests for working with the Microsoft Graph recommendations API:

| Scenarios | API |
|---|---|
| Retrieve all recommendations and their associated data, including the impacted resources. | [List recommendations](../api/directory-list-recommendation.md) |
| Retrieve a recommendation and its associated data, including the impacted resources. | [Get recommendation](../api/recommendation-get.md) |
| Act on a recommendation | [Dismiss](../api/recommendation-dismiss.md) |
| [Postpone](../api/recommendation-postpone.md) |
| [Complete](../api/recommendation-complete.md) |
| [Reactivate](../api/recommendation-reactivate.md) |
| Retrieve details of all impacted resources for a recommendation. | [List impactedResources](../api/recommendation-list-impactedresource.md) |
| Retrieve details of an impacted resource for a recommendation. | [Get impactedResource](../api/impactedresource-get.md) |
| Act on a recommendation for an impacted resource | [Dismiss](../api/impactedresource-dismiss.md) |
| [Postpone](../api/impactedresource-postpone.md) |
| [Complete](../api/impactedresource-complete.md) |
| [Reactivate](../api/impactedresource-reactivate.md) |

## See also

- [What is Azure Active Directory recommendations (preview)]( /azure/active-directory/reports-monitoring/overview-recommendations)