[[ReadItLater]] [[Article]]

# [OAuth vs SAML vs OpenID: Learn the Differences between Them](https://www.parallels.com/blogs/ras/oauth-vs-saml-vs-openid/)

![](_Inbox/Read%20Later/assets/SAML.jpg)

[![Alex Hunter](https://secure.gravatar.com/avatar/ffc6a7f958825577ebb8f964e9bc2f6f?s=165&r=g)](https://www.parallels.com/blogs/ras/author/alex-hunter/)

April 2, 2021  
Last updated on September 23, 2021

Authentication allows entry into a system, and authorization allows access to specific features within the same system. Security Assertion Markup Language (SAML) is an open standard that attempts to bridge the divide between authentication and authorization. OAuth is an open authorization standard. OpenID Connect is an authentication standard that runs on top of OAuth 2.0. The differences in these standards and their roles in authentication and authorization are detailed below.

## What Is SAML?

SAML 2.0 is [an open standard for passing authentication and authorization information](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) among three actors, namely, the principal, the service provider and the identity provider.

The principal is the user, the service provider is the owner of a web resource, and the identity provider performs identity access management services. Most SAML implementations today still support the previous version, SAML 1.1, for backward compatibility.

SAML leaves it to the identity provider to use a suitable authentication method, though it recommends implementation of transport-level security and message-level security. Instead, the standard enforces the use of XML-based messages to pass information between the service provider and the identity provider. Known as security assertions, these messages can be of any of three types, namely:

-   **Authentication statements:** An assertion that confirms to the service provider that the identity provider has authenticated a principal.
-   **Attribute statements:** Contains one or more attributes, or name-value pairs, on the basis of which access is given to the principal.
-   **Authorization decision statements:** An assertion that a principal can perform one or more actions once they have access to the web resource provided by the service provider.

SAML purposely limits what the parties can perform with XML assertions. The XML-based Extensible Access Control Markup Language (XACML) can be used for fine-grained access control.

## How Does SAML Work?

The typical SAML exchange involves the principal, via a web browser or some other so-called user agent, trying to access the service provider’s web resource.

-   The service provider sends an authentication request to the identity provider using the web browser.
-   The identity provider may request the user to provide a user name or password or both.
-   Upon verifying the user’s identity, the identity provider sends back an authentication assertion, together with the user credentials, to the service provider.
-   On the basis of the message from the identity provider, the service provider either allows or disallows the user’s attempt to access its service.

SAML simplifies the implementation of [federated authentication and authorization](https://www.hackedu.com/blog/analysis-of-common-federated-identity-protocols-openid-connect-vs-oauth-2.0-vs-saml-2.0), which involves multiple service providers across multiple organizations and security domains using a single identity provider. An example of federated identification is single sign-on (SSO). In SAML, SSO takes the form of a browser session cookie that allows access to multiple applications.

## What Is OAuth?

OAuth is an [open standard for authorization that grants secure delegated access](https://en.wikipedia.org/wiki/OAuth) to applications, devices, application programming interfaces (APIs) and servers via access tokens. OAuth authorizes an application to access your data without giving it access to your credentials.

Prior to OAuth, HTTP basic authentication was the most commonly used form of gaining access to systems, requiring only the use of a username and password. SSO came about when SAML became popular, <mark style="background: #ADCCFFA6;">but the problem with SAML is that it isn’t particularly suitable for single-page applications and modern web applications that make background HTTP calls to APIs via Asynchronous JavaScript and XML (AJAX) </mark>and web services. Also, <mark style="background: #ADCCFFA6;">SAML isn’t ideal for mobile phones, smart TVs and the Internet of Things. </mark>OAuth, with its use of JSON packets and API calls, is ideal for the modern web.

The typical OAuth workflow involves three actors, namely, the user, the consumer and the service provider.

-   The workflow begins with the user showing an intent to perform an action involving the consumer to the service provider.
-   The consumer gets a request token and a secret from the service provider, hands these off to the user, then redirects the user to the service provider so that the former can authorize the request token explicitly with the latter.
-   The service provider then grants an access token that allows the consumer to access the protected resource on behalf of the user.

Refresh tokens are often long-lived and can be used to get new access tokens from the service provider. Access tokens, on the other hand, are short-lived.

OAuth is not backward compatible with the earlier OAuth 1.0a. OAuth 2.0 is more widely used, although there are some that remain on OAuth 1.0a. If you’re thinking of using OAuth, it is recommended to use OAuth 2.0. Aside from easier implementation, another advantage of OAuth 2.0 is that tokens passed between the actors are encrypted during transit.

## What Is OpenID Connect?

Based on the OpenID [decentralized authentication protocol](https://en.wikipedia.org/wiki/OpenID), OpenID Connect provides an authentication layer atop OAuth 2.0. It addresses the lack of an authentication mechanism in OAuth, which is a weakness when it comes to authorizing sensitive transactions such as payments.

A typical [OpenID Connect](https://en.wikipedia.org/wiki/OpenID_Connect) workflow involves three parties, namely, the client, the end user and the identity provider.

-   The client, or the Relying Party, sends the end user to the identity provider, where the end user authenticates the identity and authorizes access to the client.
-   The identity provider sends an authorization code to the client, which then uses it to request access and ID tokens from the identity provider.
-   Once the client gets the tokens, it is allowed to perform an action on behalf of the end user.

OpenID Connect uses a signed and cryptographically verifiable JSON Web Token to ensure that the access and ID tokens are not tampered with during the exchange of information between parties.

## What Are the Differences between OAuth, SAML and OpenID Connect?

While the use cases for OAuth, SAML and OpenID Connect are varied, in terms of function, OAuth is used in access authorization while SAML and OpenID Connect are used in user authentication. Thus, OAuth is [used in markedly different situations](https://www.cloudflare.com/en-gb/learning/access-management/what-is-oauth/) than SAML and OpenID Connect. It can also be used with either SAML or OpenID Connect.

#### OAuth

You might have used OAuth when you let an application, say Trello, access your Gmail contacts. In this situation, you are the user, Trello is the consumer and Gmail is the service provider. Gmail provides the tokens that allow Trello to access your contacts.

#### OpenID Connect

In the case of OpenID Connect, you’ve likely used it if you’ve authenticated your account in another application using Facebook or some other application. You sign in to Facebook, which is the identity provider, to access the third-party application (e.g., Spotify). You might have logged on to Facebook but your credentials are stored safely within Facebook, safe from any potential threat in case Spotify gets hacked.

#### SAML

SAML is used mostly in enterprises. Many organizations use it for logging in users to internal networks. Once you’ve logged on, you don’t need to enter your credentials to access applications within the network.

## Simplify Integration and Enhance Security with Parallels RAS and SAML

Parallels® Remote Application Server uses SAML to provide SSO authentication, allowing for a smoother and more secure user experience. Parallels RAS also offers several features and tools for securing remote access to your applications and data, including:

-   Multi-factor authentication.
-   Data segregation.
-   Granular filtering rules.
-   Smart card authentication.
-   Client group policies.
-   Clipboard restrictions.

Parallels RAS also supports Secure Sockets Layer (SSL) or Federal Information Processing Standards (FIPS) 140-2 protocol encryption, in adherence to the Payment Card Industry Data Security Standard (PCI DSS), Health Insurance Portability and Accountability Act (HIPAA) and General Data Protection Regulation (GDPR), among other standards.

The Parallels RAS Reporting Engine provides detailed reports that allow detection of any suspicious activity within your network, and it generates useful insights into usage and user or user-group activities.

Check out how Parallels RAS can help secure your networks by [downloading the trial](https://www.parallels.com/products/ras/download/choose-trial/?utm_source=blogs-ras&utm_medium=blogs&utm_campaign=blogs-ras)!