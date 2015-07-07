# Kits API

- [Getting A Kit](#getting-a-kit)
- [Updating A Kit Changing An Attribute](#updating-a-kit-changing-an-attribute)
- [Updating A Kit Not Changing An Attribute](#updating-a-kit-not-changing-an-attribute)

A kit is tied to your Campaign Kit mobile app. You can add assets, content,
places, and campaigns to your kit.

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

## Getting A Kit <a href="#getting-a-kit" class="header-link"></a>

```
GET /api/v1/kits/3
```

List a specific kit for the authenticated user. The desired kit's `id` needs to be provided in the URL.

### Response <a href="#getting-a-kit-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "kits.places": "https://campaignkit.radiusnetworks.com/api/v1/places/{kits.places}",
    "kits.campaigns": "https://campaignkit.radiusnetworks.com/api/v1/campaigns/{kits.campaigns}",
    "kits.contents": "https://campaignkit.radiusnetworks.com/api/v1/contents/{kits.contents}",
    "kits.assets": "https://campaignkit.radiusnetworks.com/api/v1/assets/{kits.assets}"
  },
  "kits": [
    {
      "id": "3",
      "name": "snikofhuujmsbckocdfm",
      "created_at": "2015-07-06T18:03:36.126Z",
      "updated_at": "2015-07-06T18:03:36.126Z",
      "links": {
        "self": "https://campaignkit.radiusnetworks.com/api/v1/kits/3",
        "places": [

        ],
        "campaigns": [

        ],
        "contents": [

        ],
        "assets": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#getting-a-kit-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/3 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Updating A Kit Changing An Attribute <a href="#updating-a-kit-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/kits/2
```

Kits are created and typically managed on the Campaign Kit server.
However, the name can be updated via this API.

### Parameters <a href="#updating-a-kit-changing-an-attribute-parameters" class="header-link"></a>

All kits **must** be sent in an array nested under a top level
`kits` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The kit's id |
| `name` | `string` | The kit's unique name |

### Example <a href="#updating-a-kit-changing-an-attribute-example" class="header-link"></a>

Successfully updating a kit modifies the `updated_at` field. Since
this field is updated internally, the full kit resource is returned in
the response body.

```json
{
  "kits": {
    "id": 2,
    "name": "New Name"
  }
}
```

### Response <a href="#updating-a-kit-changing-an-attribute-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "kits.places": "https://campaignkit.radiusnetworks.com/api/v1/places/{kits.places}",
    "kits.campaigns": "https://campaignkit.radiusnetworks.com/api/v1/campaigns/{kits.campaigns}",
    "kits.contents": "https://campaignkit.radiusnetworks.com/api/v1/contents/{kits.contents}",
    "kits.assets": "https://campaignkit.radiusnetworks.com/api/v1/assets/{kits.assets}"
  },
  "kits": [
    {
      "id": "2",
      "name": "New Name",
      "created_at": "2015-07-06T18:03:36.320Z",
      "updated_at": "2015-07-06T18:03:36.335Z",
      "links": {
        "self": "https://campaignkit.radiusnetworks.com/api/v1/kits/2",
        "places": [

        ],
        "campaigns": [

        ],
        "contents": [

        ],
        "assets": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#updating-a-kit-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/2 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "kits": {
      "id": 2,
      "name": "New Name"
    }
  }'
```

## Updating A Kit Not Changing An Attribute <a href="#updating-a-kit-not-changing-an-attribute" class="header-link"></a>

### Parameters <a href="#updating-a-kit-not-changing-an-attribute-parameters" class="header-link"></a>

All kits **must** be sent in an array nested under a top level
`kits` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The kit's id |
| `name` | `string` | The kit's unique name |

