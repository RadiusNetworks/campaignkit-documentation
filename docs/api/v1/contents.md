# Contents API

- [Listing A Kit's Contents](#listing-a-kit's-contents)
- [Getting A Content](#getting-a-content)
- [Creating A Content](#creating-a-content)
- [Updating A Content Changing An Attribute](#updating-a-content-changing-an-attribute)
- [Updating A Content Not Changing An Attribute](#updating-a-content-not-changing-an-attribute)
- [Deleting A Content](#deleting-a-content)

All actions against contents require at a minimum an authenticated user who
is the owner, or a member of the kit to which the kit belongs.

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

## Listing A Kit's Contents <a href="#listing-a-kit's-contents" class="header-link"></a>

```
GET /api/v1/kits/1/contents
```

List contents for the specified kit.

Contents are associated to a specific `Kit`. The desired kit's `id`
must be provided in the URL.

### Response <a href="#listing-a-kit's-contents-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "contents.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{contents.kit}"
  },
  "contents": [
    {
      "id": "15",
      "name": "kshphvwphyzhlxucmlmf",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:34.636Z",
      "updated_at": "2015-07-06T18:03:34.636Z",
      "links": {
        "kit": "1"
      }
    },
    {
      "id": "16",
      "name": "blgywiujdjmszwkudceu",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:34.641Z",
      "updated_at": "2015-07-06T18:03:34.641Z",
      "links": {
        "kit": "1"
      }
    },
    {
      "id": "17",
      "name": "hzbfphnwyuawwqfojncj",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:34.646Z",
      "updated_at": "2015-07-06T18:03:34.646Z",
      "links": {
        "kit": "1"
      }
    },
    {
      "id": "18",
      "name": "ysiffnqkzdqucbdojrgx",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:34.652Z",
      "updated_at": "2015-07-06T18:03:34.652Z",
      "links": {
        "kit": "1"
      }
    }
  ]
}
```

### Curl Example <a href="#listing-a-kit's-contents-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/1/contents \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Getting A Content <a href="#getting-a-content" class="header-link"></a>

```
GET /api/v1/contents/44
```

List a specific content for the authenticated user. The desired contents's `id` needs to be provided in the URL.

### Response <a href="#getting-a-content-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "contents.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{contents.kit}"
  },
  "contents": [
    {
      "id": "44",
      "name": "mfbsbrrspjzskjqxfmbj",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:34.953Z",
      "updated_at": "2015-07-06T18:03:34.953Z",
      "links": {
        "kit": "4"
      }
    }
  ]
}
```

### Curl Example <a href="#getting-a-content-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/contents/44 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Creating A Content <a href="#creating-a-content" class="header-link"></a>

```
POST /api/v1/kits/2/contents
```

Create a content for the specified kit. The desired kit's `id` must be
provided in the URL. In order to create a content, the authenticated
user must be a member of the kit.

### Parameters <a href="#creating-a-content-parameters" class="header-link"></a>

All contents **must** be sent in an array nested under a top level
`contents` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `name` | `string` | Display name of the content (e.g. Weekly Promo, Fall Flyer) |
| `version` | `integer` | Optional version number to specify a revision for this content |
| `body` | `string` | **Required.** HTML representing the content |
| `alert_title` | `string` | The title of the alert associated with this content |
| `alert_message` | `string` | The message of the alert associated with this content |

### Example <a href="#creating-a-content-example" class="header-link"></a>

A successful content creation returns the generated content document with
updated timestamps.

```json
{
  "contents": {
    "name": "RSpec Content 1",
    "body": "<html/>"
  }
}
```

### Response <a href="#creating-a-content-response" class="header-link"></a>

```
Status: 201 Created
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "contents.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{contents.kit}"
  },
  "contents": [
    {
      "id": "76",
      "name": "RSpec Content 1",
      "version": 1,
      "type": null,
      "body": "<html/>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:35.284Z",
      "updated_at": "2015-07-06T18:03:35.284Z",
      "links": {
        "kit": "2"
      }
    }
  ]
}
```

### Curl Example <a href="#creating-a-content-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/2/contents \
  -is \
  -X POST \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "contents": {
      "name": "RSpec Content 1",
      "body": "<html/>"
    }
  }'
```

## Updating A Content Changing An Attribute <a href="#updating-a-content-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/contents/103
```

In order to update a content, the authenticated user must be a member of
the kit that the content is associated with.

### Parameters <a href="#updating-a-content-changing-an-attribute-parameters" class="header-link"></a>

All contents **must** be sent in an array nested under a top level
`contents` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the content |
| `name` | `string` | Display name of the content (e.g. Weekly Promo, Fall Flyer) |
| `version` | `integer` | Optional version number to specify a revision for this content |
| `body` | `string` | **Required.** HTML representing the content |
| `alert_title` | `string` | The title of the alert associated with this content |
| `alert_message` | `string` | The message of the alert associated with this content |

### Example <a href="#updating-a-content-changing-an-attribute-example" class="header-link"></a>

A successful update modifies the content's `updated_at` field.

```json
{
  "contents": {
    "id": 103,
    "body": "<html><body>updated</body></html>"
  }
}
```

### Response <a href="#updating-a-content-changing-an-attribute-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "contents.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{contents.kit}"
  },
  "contents": [
    {
      "id": "103",
      "name": "lygthumwuiawvjjsiedy",
      "version": 1,
      "type": null,
      "body": "<html><body>updated</body></html>",
      "alert_title": null,
      "alert_message": null,
      "created_at": "2015-07-06T18:03:35.567Z",
      "updated_at": "2015-07-06T18:03:35.602Z",
      "links": {
        "kit": "2"
      }
    }
  ]
}
```

### Curl Example <a href="#updating-a-content-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/contents/103 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "contents": {
      "id": 103,
      "body": "<html><body>updated</body></html>"
    }
  }'
```

## Updating A Content Not Changing An Attribute <a href="#updating-a-content-not-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/contents/119
```

In order to update a content, the authenticated user must be a member of
the kit that the content is associated with.

### Parameters <a href="#updating-a-content-not-changing-an-attribute-parameters" class="header-link"></a>

All contents **must** be sent in an array nested under a top level
`contents` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the content |
| `name` | `string` | Display name of the content (e.g. Weekly Promo, Fall Flyer) |
| `version` | `integer` | Optional version number to specify a revision for this content |
| `body` | `string` | **Required.** HTML representing the content |
| `alert_title` | `string` | The title of the alert associated with this content |
| `alert_message` | `string` | The message of the alert associated with this content |

### Example <a href="#updating-a-content-not-changing-an-attribute-example" class="header-link"></a>

If you do not provide attributes, or if all of the provided attributes
for a are the same, the content is not updated. In these cases a
`204 No Content` response is returned.

This response will have an empty body per HTTP schemantics.

```json
{
  "contents": {
    "id": 119,
    "body": "<html/>"
  }
}
```

### Response <a href="#updating-a-content-not-changing-an-attribute-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#updating-a-content-not-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/contents/119 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "contents": {
      "id": 119,
      "body": "<html/>"
    }
  }'
```

## Deleting A Content <a href="#deleting-a-content" class="header-link"></a>

```
DELETE /api/v1/contents/150
```

In order to delete a content, the authenticated user must be a member of
the kit that the content is associated with.

### Response <a href="#deleting-a-content-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#deleting-a-content-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/contents/150 \
  -is \
  -X DELETE \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```
