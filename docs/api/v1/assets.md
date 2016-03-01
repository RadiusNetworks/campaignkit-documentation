# Assets API

- [Listing A Kit's Assets](#listing-a-kit's-assets)
- [Getting A Asset](#getting-a-asset)

All actions against assets require at a minimum an authenticated user who
is the owner, or a member of the kit to which the kit belongs.

## Headers <a href="#headers" id="headers" class="headerlink"></a>

#### Authorization <a href="#authorization" id="authorization" class="headerlink"></a>

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

#### Content Type <a href="#content-type" id="content-type" class="headerlink"></a>

The content type is `vnd.rn+json` and should be set in the `Content-Type`
header:

```
Content-Type: application/vnd.rn+json
```

## Listing A Kit's Assets <a href="#listing-a-kit's-assets" class="header-link"></a>

```
GET /api/v1/kits/2/assets
```

List assets for the specified kit.

Assets are associated to a specific `Kit`. The desired kit's `id`
must be provided in the URL.

#### Response <a href="#listing-a-kit's-assets-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "assets.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{assets.kit}"
  },
  "assets": [
    {
      "id": "5",
      "name": "yvnmwpwjfxsyvmjgovqn",
      "type": "Asset",
      "media": {
        "media": {
          "url": null,
          "thumb": {
            "url": null
          }
        }
      },
      "created_at": "2015-07-06T18:03:30.953Z",
      "updated_at": "2015-07-06T18:03:30.953Z",
      "links": {
        "kit": "2"
      }
    },
    {
      "id": "6",
      "name": "igdujxzdqcdeeeubjwwm",
      "type": "Asset",
      "media": {
        "media": {
          "url": null,
          "thumb": {
            "url": null
          }
        }
      },
      "created_at": "2015-07-06T18:03:30.958Z",
      "updated_at": "2015-07-06T18:03:30.958Z",
      "links": {
        "kit": "2"
      }
    }
  ]
}
```

#### Curl Example <a href="#listing-a-kit's-assets-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/kits/2/assets \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```

## Getting A Asset <a href="#getting-a-asset" class="header-link"></a>

```
GET /api/v1/assets/21
```

List a specific asset for the authenticated user. The desired assets's `id` needs to be provided in the URL.

#### Response <a href="#getting-a-asset-response" class="header-link"></a>

```
Status: 200 OK
Content-Type: application/json; charset=utf-8
CampaignKit-Media-Type: campaignkit.v1
CampaignKit-API-Version: 1.0
```
```json
{
  "links": {
    "assets.kit": "https://campaignkit.radiusnetworks.com/api/v1/kits/{assets.kit}"
  },
  "assets": [
    {
      "id": "21",
      "name": "aunpgqhfdfbszytzwzie",
      "type": "Asset",
      "media": {
        "media": {
          "url": null,
          "thumb": {
            "url": null
          }
        }
      },
      "created_at": "2015-07-06T18:03:31.277Z",
      "updated_at": "2015-07-06T18:03:31.277Z",
      "links": {
        "kit": "2"
      }
    }
  ]
}
```

#### Curl Example <a href="#getting-a-asset-curl-example" class="header-link"></a>

```
curl https://campaignkit.radiusnetworks.com/api/v1/assets/21 \
  -is \
  -X GET \
  -H 'Accept: application/vnd.rn+json' \
  -H 'Content-Type: application/vnd.rn+json' \
  -H 'Authorization: Token token="c0decafe1111180a29c8696adbd5307ccdcdaa6468c0ffee"'
```
