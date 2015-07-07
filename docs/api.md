# Campaign Kit Admin API

This document describes the API designed to integrate Campaign Kit with other systems. It is specifically intended to manage creation and deletion of kits, campaigns, places, and content.

Data synchronization, communicating with the SDKs, configuring hardware is not part of the Admin API. Radius Networks has [other resources](http://developer.radiusnetworks.com/) for many of those needs.

## Overview

The API uses IDs for linkage, which makes it possible to cache documents from compound responses and then limit subsequent requests to only the documents that aren't already present locally.

Resource relationships are created through the use of URI templates and resource identifiers. To prevent future breakage we recommend creating the URIs from the templates over hardcoding to the individual resources.

## Headers

### Authorization

The API Key is passed via the Authorization header:

    Authorization: Token token="secret"

The API Key is associated with your account and has access to all the resources associated with your account. Account-specific API keys have different permissions than the web login users that can interact with the dashboard, and the access may be different.

Example:

    curl -H 'Authorization: Token token="sandbox"' "https://campaignkit.radiusnetworks.com/api/v1.json"

API Tokens can be managed in your [Radius Networks Account Profile](https://account.radiusnetworks.com/personal_tokens).

Note: Per [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec2.html#sec2.2) the Authorization Header's token needs to be surrounded by double quotes (`"`).

### Content Type

The content type is `vnd+json`, and should be set in the Content-Type header:

    Content-Type: application/vnd.api+json

# Resources

- [Root Endpoint](api/v1/root_endpoint.md)
- [Kits](api/v1/kits.md)
- [Campaigns](api/v1/campaigns.md)
- [Assets](api/v1/assets.md)
- [Contents](api/v1/contents.md)
- [Places](api/v1/places.md)
