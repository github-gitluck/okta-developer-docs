---
title: API service integrations in the OIN
meta:
  - name: description
    content: Provides an overview of why and when to build API service integrations for the Okta Integration Network.
---

<ApiLifecycle access="ea" />

> **Note:** The API Service Integration is a [Self-service Early Access (EA)](/docs/concepts/feature-lifecycle-management/#self-service-features) feature. Enable this feature in your org to obtain the API service integration capability.
<!-- Need OAUTH_ADMIN_CONSENT_DIALOG FF enabled in monolith org -->

Service apps that access or modify Okta resources, like system logs, apps, sessions, and policies can be published in the Okta Integration Network (OIN) as an API service integration. This integration type allows your service app to access your customer tenant Okta org through [Okta management APIs](/docs/reference/core-okta-api/) using OAuth 2.0.

Previously, if you have a service app requiring Okta management API access, you need to use an API token that was tied to a specific Okta user and you can't restrict access to certain resources. With an OAuth 2.0 API service integration, your service app can have secure, reliable, and granular access to Okta APIs without being associated with a user.

When your service app integration is in the Okta Integration Network (OIN), your customers can discover and configure your integration through the OIN catalog in their own Okta tenant org. Configuration is easy and consistent for your customers because you've already done the hard work by building the integration with the required configuration instructions. Customers trust that integrations in the OIN are secure and reliable because it's Okta verified.

## When to build an API service integration

API service integrations access [Okta management APIs](/docs/reference/core-okta-api/) using OAuth 2.0 and are sometimes referred to as service-to-service or machine-to-machine integrations. This API access represents the application itself rather than a particular user. Consider the following scenarios to determine if you need to build a service-based or a user-based OAuth 2.0 API integration.

| &nbsp; |  Service-based API access | User-based API access |
| ------ | :------------------- | :----------------------- |
| **Use cases** | <ul><li>Log entries need to have the application name instead of a user name for auditing purposes.</li> <li>API requests aren't initiated by a user action (for example, a user clicking a button or starting a script).</li> <li>The application that requests API access is hosted on a secure server (this type of application is also known as a confidential client).</li></ul> | <ul><li>A new custom application is configured from a user entry form.</li> <li>An admin user takes action by making API requests.</li></ul> |
| **Examples** | <ul><li>An app that access certain types of Okta system log entries for occasional analysis</li> <li>An app that sends risk signals to Okta</li> <li>An app that occasionally syncs Okta user profile information to another system</li></ul> |  <ul><li>An IT support ticketing system integration that allows an Okta admin to assign an application directly from the access request support ticket</li></ul> |
| **Best-fit API integration** | If these use cases and examples describe your needs, then implementing an API service integration for the OIN is a best-fit solution. See [Build an API service integration](/docs/guides/build-api-integration/).  | If these use cases and examples describe your needs, then implementing a user-based API integration is a better solution. User-based API integrations aren't currently supported in the OIN. See [Implement OAuth for Okta](/docs/guides/implement-oauth-for-okta/main/) to learn more about user-based API integrations. |

## API service integration benefits

Before API service integrations were supported in the OIN, Okta API tokens were a common way for integrations to access the Okta management APIs. API service integrations offer improved security and reliability:

| &nbsp; | &nbsp; |
| ------ | ------ |
| **Access granularity** | Using OAuth 2.0 scopes, you can restrict access request to specific resources instead of all the resources that a user can access. |
| **Configuration experience** | API service integrations can be discovered and added directly from the OIN catalog. You don't need to create a service account or an anonymous activity user for the integration. |
| **Service integration** | Okta API tokens represent a user, which means they're not a great fit for service integrations where a user context isn’t needed or desirable. |
| **Reliability** | Okta API tokens expire after 30 days of inactivity or when a user leaves the Okta org. After being authorized, API service integrations can request a new access token whenever necessary and without manual action from an admin. |
| **Rotation** | Okta API tokens must be rotated manually. API service integration access tokens can be rotated programmatically. |

## Next steps

Ready to get started? Sign up for a free [developer-edition Okta org](/signup) and see [Build an API service integration](/docs/guides/build-api-integration/).

Post your questions on the [Okta Developer Forum](https://devforum.okta.com/c/questions/oin-submissions/19) if you need help or have an issue.