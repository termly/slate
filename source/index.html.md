---
title: Termly API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true

code_clipboard: true

meta:
  - name: Termly API
    content: Reference documentation for Termly API.
---

# Introduction


This repository has documentation for the various endpoints that make up the Termly API.

Please see here for how to create the security elements required for each request.

## General Information


Attributes that start with `_` are meta attributes that are not related to the action the API is performing

* _idx refers to the index of the request that this response relates to.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "api_key: <key>"
```

> Make sure to replace `<key>` with your API key.

Termly API is authenticated using the `api_key` header.



`api_key: <key>`

<aside class="notice">
You must replace <code>&lt;key&gt;</code> with your personal API key.
</aside>

# Endpoints

## Read Banners

> Input Structure

```json
[
  {
    "account_id": "<string>",
    "website_id": "<string>"
  }
]
```

> Response Structure

```json
{
  "results": [
    {
      "account_id": "<string>",
      "auto_accept_on_scroll": "<bool>",
      "display_consent_banner_by_region": "<bool>",
      "display_style": "<enum{'banner', 'tooltip', 'modal'}>",
      "id": "<string>",
      "personalized_content": "<bool>",
      "position": "<enum{'bottom', 'bottom_left', 'bottom_right', 'top', 'top_left', 'top_right'}>",
      "running_targeted_advertising": "<bool>",
      "share_data_to_3rd_party": "<bool>",
      "show_cookie_preference": "<bool>",
      "theme_color": "<string>",
      "website_id": "<string>"
    }
  ],
  "errors": [
    {
      "error": "<string>",
      "account_id": "<string>",
      "website_id": "<string>"
    }
  ],
  "paging": {
    "count": <integer>,
    "current_page": <integer>,
    "next_page": "<string>",
    "previous_page": "<string>",
    "per_page": <integer>,
    "total_count": <integer>,
    "total_pages": <integer>
  }
}
```

> Input Example

```json
[
  {
    "account_id": "acct_1234",
    "website_id": "web_1234"
  }
]

```

```shell
curl "https://api.termly.io/api/v1/websites/banners?query=%5B%0A%20%20%7B%0A%20%20%20%20%22account_id%22%3A%20%22acct_1234%22%2C%0A%20%20%20%20%22website_id%22%3A%20%22web_1234%22%0A%20%20%7D%0A%5D%0A" \
  -H "api_key: <key>"
```

> Example Response

```json
{
  "results": [
    {
      "account_id": "acct_1234",
      "auto_accept_on_scroll": true,
      "display_consent_banner_by_region": true,
      "display_style": "banner",
      "id": "ban_1234",
      "personalized_content": true,
      "position": "bottom",
      "running_targeted_advertising": true,
      "share_data_to_3rd_party": true,
      "show_cookie_preference": true,
      "theme_color": "blue",
      "website_id": "web_1234"
    }
  ],
  "errors": [],
  "paging": {
    "count": 1,
    "current_page": 1,
    "next_page": null,
    "previous_page": null,
    "per_page": 25,
    "total_count": 1,
    "total_pages": 1
  }
}

```

Retrieve all banners for the specified query. The query has the following shape:

### HTTP Request

`GET https://api.termly.io/api/v1/websites/banners`

### Query Parameters

The Query has shape shown in `Input Structure`

At least 1 object with the field account_id and website_id is required. Once the query is constructed, pass the URL encoded value in the query string parameter query. 

### Response Attributes

- `account_id` is the unique identifier of the account
- `auto_accept_on_scroll` is a user scrolling accepted as consent?
- `display_consent_banner_by_region` are there User region-specific settings?
- `display_style` is one of `banner`, `tooltip`, `modal`.
- `id` is the unique identifier of the banner
- `personalized_content` does the website have content personalized for the user?
- `position` is the position of the Banner
- `running_targeted_advertising` are there targeted advertisements on the website?
- `share_data_to_3rd_party` does the Website share data with third parties?
- `show_cookie_preference` show the Cookie Preference Button in the banner?
- `theme_color` is the color of the theme
- `website_id` is the unique identifier of the website
