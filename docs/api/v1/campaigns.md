# Campaigns API

- [Listing A Kit's Campaigns](#listing-a-kit's-campaigns)
- [Getting A Campaign](#getting-a-campaign)
- [Creating A Campaign](#creating-a-campaign)
- [Updating A Campaign Changing An Attribute](#updating-a-campaign-changing-an-attribute)
- [Updating A Campaign Not Changing An Attribute](#updating-a-campaign-not-changing-an-attribute)
- [Deleting A Campaign](#deleting-a-campaign)

All actions against campaigns require at a minimum an authenticated user who
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

## Listing A Kit's Campaigns <a href="#listing-a-kit's-campaigns" class="header-link"></a>

```
GET /api/v1/kits/4/campaigns
```

List campaigns for the specified kit.

Campaigns are associated to a specific `Kit`. The desired kit's `id`
must be provided in the URL.

### Response <a href="#listing-a-kit's-campaigns-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "campaigns.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{campaigns.kit}"
  },
  "campaigns": [
    {
      "id": "8",
      "name": "kfemuvzwbszsmrzucary",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:31.734Z",
      "updated_at": "2015-07-06T18:03:31.734Z",
      "links": {
        "kit": "4",
        "content": "1",
        "places": [
          1
        ],
        "fulfillment_places": [

        ]
      }
    },
    {
      "id": "9",
      "name": "qxnbnzvrztlopzmyiyrs",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:31.748Z",
      "updated_at": "2015-07-06T18:03:31.748Z",
      "links": {
        "kit": "4",
        "content": "1",
        "places": [
          1
        ],
        "fulfillment_places": [

        ]
      }
    },
    {
      "id": "10",
      "name": "zysxmkkksrstmhmerugb",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:31.763Z",
      "updated_at": "2015-07-06T18:03:31.763Z",
      "links": {
        "kit": "4",
        "content": "1",
        "places": [
          1
        ],
        "fulfillment_places": [

        ]
      }
    },
    {
      "id": "11",
      "name": "kckcxeslbdntwqqadjfv",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:31.778Z",
      "updated_at": "2015-07-06T18:03:31.778Z",
      "links": {
        "kit": "4",
        "content": "1",
        "places": [
          1
        ],
        "fulfillment_places": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#listing-a-kit's-campaigns-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/4/campaigns \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Getting A Campaign <a href="#getting-a-campaign" class="header-link"></a>

```
GET /api/v1/campaigns/32
```

List a specific campaign for the authenticated user. The desired campaigns's `id` needs to be provided in the URL.

### Response <a href="#getting-a-campaign-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "campaigns.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{campaigns.kit}"
  },
  "campaigns": [
    {
      "id": "32",
      "name": "gdoomfrzxbyizrzrmfcy",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:32.287Z",
      "updated_at": "2015-07-06T18:03:32.287Z",
      "links": {
        "kit": "4",
        "content": "3",
        "places": [
          3
        ],
        "fulfillment_places": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#getting-a-campaign-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/campaigns/32 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Creating A Campaign <a href="#creating-a-campaign" class="header-link"></a>

```
POST /api/v1/kits/1/campaigns
```

Create a campaign for the specified kit. The desired kit's `id` must be
provided in the URL. In order to create a campaign, the authenticated
user must be a member of the kit.

### Parameters <a href="#creating-a-campaign-parameters" class="header-link"></a>

All campaigns **must** be sent in an array nested under a top level
`campaigns` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `name` | `string` | Display name of the campaign (e.g. Weekly Promo, Fall Favorites, BOGO) |
| `start_at` | `datetime` | The start date/time of the campaign |
| `end_at` | `datetime` | The end date/time of the campaign |
| `min_recur_secs` | `integer` | **Required.** The minimum recurrence of the campaign in seconds. By default, a campaign is
	      one time only (value -1). |
| `foreground_only` | `string` | Set to true to make the campaing forground only |
| `active` | `string` | Set to true to make the campaing active, set to false to disable campaign |
| `trigger_distance` | `integer` | Minimum distance before campaign is triggered |
| `content_id` | `integer` | **Required.** ID of the content associated with this campaign |
| `place_ids` | `integer` | **Required.** Array if IDs of the places where this campaign is being hosted |
| `fulfillment_place_ids` | `integer` | Array if IDs of the places where this campaign can be fulfilled |

### Example <a href="#creating-a-campaign-example" class="header-link"></a>

A successful campaign creation returns the generated campaign document with
updated timestamps.

```json
{
  "campaigns": {
    "name": "RSpec Campaign 1",
    "content_id": "6",
    "place_ids": [
      6
    ]
  }
}
```

### Response <a href="#creating-a-campaign-response" class="header-link"></a>

```
Status: 201 Created
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "campaigns.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{campaigns.kit}"
  },
  "campaigns": [
    {
      "id": "58",
      "name": "RSpec Campaign 1",
      "start_at": null,
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:32.839Z",
      "updated_at": "2015-07-06T18:03:32.839Z",
      "links": {
        "kit": "1",
        "content": "6",
        "places": [
          6
        ],
        "fulfillment_places": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#creating-a-campaign-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/1/campaigns \
  -is \
  -X POST \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "campaigns": {
      "name": "RSpec Campaign 1",
      "content_id": "6",
      "place_ids": [
        6
      ]
    }
  }'
```

## Updating A Campaign Changing An Attribute <a href="#updating-a-campaign-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/campaigns/86
```

In order to update a campaign, the authenticated user must be a member of
the kit that the campaign is associated with.

### Parameters <a href="#updating-a-campaign-changing-an-attribute-parameters" class="header-link"></a>

All campaigns **must** be sent in an array nested under a top level
`campaigns` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the campaign |
| `name` | `string` | Display name of the campaign (e.g. Weekly Promo, Fall Favorites, BOGO) |
| `start_at` | `datetime` | The start date/time of the campaign |
| `end_at` | `datetime` | The end date/time of the campaign |
| `min_recur_secs` | `integer` | **Required.** The minimum recurrence of the campaign in seconds. By default, a campaign is
	      one time only (value -1). |
| `foreground_only` | `string` | Set to true to make the campaing forground only |
| `active` | `string` | Set to true to make the campaing active, set to false to disable campaign |
| `trigger_distance` | `integer` | Minimum distance before campaign is triggered |
| `content_id` | `integer` | **Required.** ID of the content associated with this campaign |
| `place_ids` | `integer` | **Required.** Array if IDs of the places where this campaign is being hosted |
| `fulfillment_place_ids` | `integer` | Array if IDs of the places where this campaign can be fulfilled |

### Example <a href="#updating-a-campaign-changing-an-attribute-example" class="header-link"></a>

A successful update modifies the campaign's `updated_at` field.

```json
{
  "campaigns": {
    "id": 86,
    "start_at": "2015-07-06T14:03:33.532Z"
  }
}
```

### Response <a href="#updating-a-campaign-changing-an-attribute-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "campaigns.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{campaigns.kit}"
  },
  "campaigns": [
    {
      "id": "86",
      "name": "oruytdmvuwukhkaowjgi",
      "start_at": "2015-07-06T14:03:33.532Z",
      "end_at": null,
      "min_recur_secs": -1,
      "foreground_only": false,
      "active": true,
      "trigger_distance": null,
      "created_at": "2015-07-06T18:03:33.431Z",
      "updated_at": "2015-07-06T18:03:33.540Z",
      "links": {
        "kit": "2",
        "content": "9",
        "places": [
          9
        ],
        "fulfillment_places": [

        ]
      }
    }
  ]
}
```

### Curl Example <a href="#updating-a-campaign-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/campaigns/86 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "campaigns": {
      "id": 86,
      "start_at": "2015-07-06T14:03:33.532Z"
    }
  }'
```

## Updating A Campaign Not Changing An Attribute <a href="#updating-a-campaign-not-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/campaigns/120
```

In order to update a campaign, the authenticated user must be a member of
the kit that the campaign is associated with.

### Parameters <a href="#updating-a-campaign-not-changing-an-attribute-parameters" class="header-link"></a>

All campaigns **must** be sent in an array nested under a top level
`campaigns` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the campaign |
| `name` | `string` | Display name of the campaign (e.g. Weekly Promo, Fall Favorites, BOGO) |
| `start_at` | `datetime` | The start date/time of the campaign |
| `end_at` | `datetime` | The end date/time of the campaign |
| `min_recur_secs` | `integer` | **Required.** The minimum recurrence of the campaign in seconds. By default, a campaign is
	      one time only (value -1). |
| `foreground_only` | `string` | Set to true to make the campaing forground only |
| `active` | `string` | Set to true to make the campaing active, set to false to disable campaign |
| `trigger_distance` | `integer` | Minimum distance before campaign is triggered |
| `content_id` | `integer` | **Required.** ID of the content associated with this campaign |
| `place_ids` | `integer` | **Required.** Array if IDs of the places where this campaign is being hosted |
| `fulfillment_place_ids` | `integer` | Array if IDs of the places where this campaign can be fulfilled |

### Example <a href="#updating-a-campaign-not-changing-an-attribute-example" class="header-link"></a>

If you do not provide attributes, or if all of the provided attributes
for a are the same, the campaign is not updated. In these cases a
`204 No Content` response is returned.

This response will have an empty body per HTTP schemantics.

```json
{
  "campaigns": {
    "id": 120,
    "start_at": null
  }
}
```

### Response <a href="#updating-a-campaign-not-changing-an-attribute-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#updating-a-campaign-not-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/campaigns/120 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "campaigns": {
      "id": 120,
      "start_at": null
    }
  }'
```

## Deleting A Campaign <a href="#deleting-a-campaign" class="header-link"></a>

```
DELETE /api/v1/campaigns/140
```

In order to delete a campaign, the authenticated user must be a member of
the kit that the campaign is associated with.

### Response <a href="#deleting-a-campaign-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#deleting-a-campaign-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/campaigns/140 \
  -is \
  -X DELETE \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```
