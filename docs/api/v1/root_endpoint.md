# Campaign Kit API Root Endpoint

- [Requesting Resource Endpoints](#requesting-resource-endpoints)

This describes the resources that make up the official Campaign Kit API v1.
If you have any problems or requests please contact
[support](http://www.radiusnetworks.com/support.html). Issue a `GET`
request to the root endpoint to get a list of all the resource endpoints
this API supports.

## Headers <a href="#headers" id="headers" class="headerlink"></a>

### Authorization <a href="#authorization" id="authorization" class="headerlink"></a>

The API Key is passed via the Authorization header:

```
Authorization: Token token="secret"
```

The API Key is associated with your account and has access to all the resources
associated with your account. Account specific API keys have different
permissions than the web login users that can interact with the dashboard, and
the access may be different.

If you do not have an API key, [you can create one here](https://account.radiusnetworks.com/personal_token).

**Note:** Per [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec2.html#sec2.2) the Authorization Header's token needs to be
surrounded by double quotes (`"`).

### Content Type <a href="#content-type" id="content-type" class="headerlink"></a>

The content type is `vnd.rn+json` and should be set in the `Content-Type`
header:

```
Content-Type: application/vnd.rn+json
```

## Requesting Resource Endpoints <a href="#requesting-resource-endpoints" class="header-link"></a>

```
GET /api/v1
```

### Response <a href="#requesting-resource-endpoints-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "users.kits": "https://campaignkit.radiusnetworks.com/api/v1/kits/{users.kits}",
    "kits.places": "https://campaignkit.radiusnetworks.com/api/v1/places/{kits.places}",
    "kits.campaigns": "https://campaignkit.radiusnetworks.com/api/v1/campaigns/{kits.campaigns}",
    "kits.contents": "https://campaignkit.radiusnetworks.com/api/v1/contents/{kits.contents}",
    "kits.assets": "https://campaignkit.radiusnetworks.com/api/v1/assets/{kits.assets}"
  }
}
```

### Curl Example <a href="#requesting-resource-endpoints-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```
