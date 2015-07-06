# Places API

- [Listing A Kit's Places](#listing-a-kit's-places)
- [Getting A Place](#getting-a-place)
- [Creating A Place](#creating-a-place)
- [Updating A Place Changing An Attribute](#updating-a-place-changing-an-attribute)
- [Updating A Place Not Changing An Attribute](#updating-a-place-not-changing-an-attribute)
- [Deleting A Place](#deleting-a-place)

All actions against places require at a minimum an authenticated user who
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

## Listing A Kit's Places <a href="#listing-a-kit's-places" class="header-link"></a>

```
GET /api/v1/kits/4/places
```

List places for the specified kit.

Places are associated to a specific `Kit`. The desired kit's `id`
must be provided in the URL.

### Response <a href="#listing-a-kit's-places-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "places.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{places.kit}"
  },
  "places": [
    {
      "id": "26",
      "name": "RSpec Place 1-3001341d",
      "latitude": null,
      "longitude": null,
      "address": null,
      "radius": null,
      "uuid": "a9924003-bc4f-4cc7-98f5-adad48cf4c6f",
      "major": 75,
      "minor": 58,
      "type": null,
      "created_at": "2015-07-06T18:03:36.607Z",
      "updated_at": "2015-07-06T18:03:36.607Z",
      "links": {
        "kit": "4",
        "parent": ""
      }
    },
    {
      "id": "27",
      "name": "RSpec Place 2-3001341d",
      "latitude": null,
      "longitude": null,
      "address": null,
      "radius": null,
      "uuid": "9860f506-b9b9-4de3-936f-b7b819ea789a",
      "major": 14,
      "minor": 97,
      "type": null,
      "created_at": "2015-07-06T18:03:36.613Z",
      "updated_at": "2015-07-06T18:03:36.613Z",
      "links": {
        "kit": "4",
        "parent": ""
      }
    }
  ]
}
```

### Curl Example <a href="#listing-a-kit's-places-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/4/places \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Getting A Place <a href="#getting-a-place" class="header-link"></a>

```
GET /api/v1/places/37
```

List a specific place for the authenticated user. The desired places's `id` needs to be provided in the URL.

### Response <a href="#getting-a-place-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "places.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{places.kit}"
  },
  "places": [
    {
      "id": "37",
      "name": "RSpec Place 1-ebbe4c25",
      "latitude": null,
      "longitude": null,
      "address": null,
      "radius": null,
      "uuid": "1b8447e8-fb4d-435f-93f5-547db57afaf4",
      "major": 82,
      "minor": 36,
      "type": null,
      "created_at": "2015-07-06T18:03:36.801Z",
      "updated_at": "2015-07-06T18:03:36.801Z",
      "links": {
        "kit": "2",
        "parent": ""
      }
    }
  ]
}
```

### Curl Example <a href="#getting-a-place-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/places/37 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Creating A Place <a href="#creating-a-place" class="header-link"></a>

```
POST /api/v1/kits/1/places
```

Create a place for the specified kit. The desired kit's `id` must be
provided in the URL. In order to create a place, the authenticated
user must be a member of the kit.

### Parameters <a href="#creating-a-place-parameters" class="header-link"></a>

All places **must** be sent in an array nested under a top level
`places` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `name` | `string` | Display name of the place (e.g. Front Door, Register, Shoe Rack) |
| `latitude` | `string` | The latitude of the place as a geofence |
| `longitude` | `string` | The longitude of the place as a geofence |
| `address` | `string` | The address of the place as a geofence |
| `radius` | `integer` | The radius of the place as a geofence |
| `uuid` | `string` | The proximity UUID of the place as a beacon |
| `major` | `integer` | The major value of the place as a beacon |
| `minor` | `integer` | The minor value of the place as a beacon |
| `type` | `integer` | The minor value of the place as a beacon |

### Example <a href="#creating-a-place-example" class="header-link"></a>

A successful place creation returns the generated place document with
updated timestamps.

```json
{
  "places": {
    "name": "RSpec Place 1-c64002d9",
    "uuid": "9234e964-7123-4b97-9c8b-8b9c76f2e4a2",
    "major": 81,
    "minor": 32
  }
}
```

### Response <a href="#creating-a-place-response" class="header-link"></a>

```
Status: 201 Created
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "places.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{places.kit}"
  },
  "places": [
    {
      "id": "72",
      "name": "RSpec Place 1-c64002d9",
      "latitude": null,
      "longitude": null,
      "address": null,
      "radius": null,
      "uuid": "9234e964-7123-4b97-9c8b-8b9c76f2e4a2",
      "major": 81,
      "minor": 32,
      "type": null,
      "created_at": "2015-07-06T18:03:37.218Z",
      "updated_at": "2015-07-06T18:03:37.218Z",
      "links": {
        "kit": "1",
        "parent": ""
      }
    }
  ]
}
```

### Curl Example <a href="#creating-a-place-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/1/places \
  -is \
  -X POST \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "places": {
      "name": "RSpec Place 1-c64002d9",
      "uuid": "9234e964-7123-4b97-9c8b-8b9c76f2e4a2",
      "major": 81,
      "minor": 32
    }
  }'
```

## Updating A Place Changing An Attribute <a href="#updating-a-place-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/places/98
```

In order to update a place, the authenticated user must be a member of
the kit that the place is associated with.

### Parameters <a href="#updating-a-place-changing-an-attribute-parameters" class="header-link"></a>

All places **must** be sent in an array nested under a top level
`places` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the place |
| `name` | `string` | Display name of the place (e.g. Front Door, Register, Shoe Rack) |
| `latitude` | `string` | The latitude of the place as a geofence |
| `longitude` | `string` | The longitude of the place as a geofence |
| `address` | `string` | The address of the place as a geofence |
| `radius` | `integer` | The radius of the place as a geofence |
| `uuid` | `string` | The proximity UUID of the place as a beacon |
| `major` | `integer` | The major value of the place as a beacon |
| `minor` | `integer` | The minor value of the place as a beacon |
| `type` | `integer` | The minor value of the place as a beacon |

### Example <a href="#updating-a-place-changing-an-attribute-example" class="header-link"></a>

A successful update modifies the place's `updated_at` field.

```json
{
  "places": {
    "id": 98,
    "uuid": "7c660318-35c4-4e87-8e7e-d8a954ae959f"
  }
}
```

### Response <a href="#updating-a-place-changing-an-attribute-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "places.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{places.kit}"
  },
  "places": [
    {
      "id": "98",
      "name": "RSpec Place 2-6635c43b",
      "latitude": null,
      "longitude": null,
      "address": null,
      "radius": null,
      "uuid": "7c660318-35c4-4e87-8e7e-d8a954ae959f",
      "major": 58,
      "minor": 83,
      "type": null,
      "created_at": "2015-07-06T18:03:37.573Z",
      "updated_at": "2015-07-06T18:03:37.605Z",
      "links": {
        "kit": "2",
        "parent": ""
      }
    }
  ]
}
```

### Curl Example <a href="#updating-a-place-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/places/98 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "places": {
      "id": 98,
      "uuid": "7c660318-35c4-4e87-8e7e-d8a954ae959f"
    }
  }'
```

## Updating A Place Not Changing An Attribute <a href="#updating-a-place-not-changing-an-attribute" class="header-link"></a>

```
PUT /api/v1/places/114
```

In order to update a place, the authenticated user must be a member of
the kit that the place is associated with.

### Parameters <a href="#updating-a-place-not-changing-an-attribute-parameters" class="header-link"></a>

All places **must** be sent in an array nested under a top level
`places` parameter.

| **Name** | **Type** | **Description** |
| -------- | -------- | --------------- |
| `id` | `string` | **Required.** The id of the place |
| `name` | `string` | Display name of the place (e.g. Front Door, Register, Shoe Rack) |
| `latitude` | `string` | The latitude of the place as a geofence |
| `longitude` | `string` | The longitude of the place as a geofence |
| `address` | `string` | The address of the place as a geofence |
| `radius` | `integer` | The radius of the place as a geofence |
| `uuid` | `string` | The proximity UUID of the place as a beacon |
| `major` | `integer` | The major value of the place as a beacon |
| `minor` | `integer` | The minor value of the place as a beacon |
| `type` | `integer` | The minor value of the place as a beacon |

### Example <a href="#updating-a-place-not-changing-an-attribute-example" class="header-link"></a>

If you do not provide attributes, or if all of the provided attributes
for a are the same, the place is not updated. In these cases a
`204 No Content` response is returned.

This response will have an empty body per HTTP schemantics.

```json
{
  "places": {
    "id": 114,
    "uuid": "29201587-1591-4c02-b446-210d02ea8107"
  }
}
```

### Response <a href="#updating-a-place-not-changing-an-attribute-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#updating-a-place-not-changing-an-attribute-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/places/114 \
  -is \
  -X PUT \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"' \
  -d '{
    "places": {
      "id": 114,
      "uuid": "29201587-1591-4c02-b446-210d02ea8107"
    }
  }'
```

## Deleting A Place <a href="#deleting-a-place" class="header-link"></a>

```
DELETE /api/v1/places/131
```

In order to delete a place, the authenticated user must be a member of
the kit that the place is associated with.

### Response <a href="#deleting-a-place-response" class="header-link"></a>

```
Status: 204 No Content
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```

### Curl Example <a href="#deleting-a-place-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/places/131 \
  -is \
  -X DELETE \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```
