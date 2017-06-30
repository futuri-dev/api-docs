# API v3 Documentation

---

## Basic Usage

All calls require a station short key as a get parameter.

`?key=wbab`

All methods return a json object with at least the following:

```
{
    "ok" => true
}
```

Or if an error occured:

```
{
    "ok" => false,
    "error" => "error_identifier",
    "message" => "A longer worded error message in English"
}
```

The value of `error` may be used for lookup of localized error messages.

---

## Sample endpoint documentation:

### `GET /route/:id`

*Short description of what this route does*

**Params:**

`id`: {string} Route identifier

**Return:**

```
{
  "message": "Route success"
}
```

---

## Station Configs

### `GET /configs/:application`

*Returns a set of config values appropriate for the application*

Station configs are represented as a nested array of key-parts, separated by `:` delimiters.
A key-part may contain a single scalar value or a deeper array, so in the example return
below, the config key `gruvr:main_menu:custom_links` would resolve to an array of objects
for building links, while `gruvr:open_mic:enabled` would resolve to true.

Scalar values may be filled, or missing, or empty. When empty or missing, there is often a
default value hardcoded into the consuming app. Booleans are typically represented as a
string "0" or "1", but from practical purposes, any non-empty, non-zero string should be
treated as truthy.

Reference code for storing and using configs is available to Futuri partners.

**Params:**

`application`: {string} Currently supported: `gruvr`

**Return:**

Everything within the "configs" object is fair game to reference as a nested config.

```
{
    "ok": true,
    "configs": {
        "gruvr": {
            "public_telephone_number": "216-555-1212",
            "open_mic: {
                "enabled": 1
            },
            "main_menu": {
                "custom_links": [
                    {
                        "is_external": "0",
                        "subtitle": "subtitle",
                        "title": "Station Site Link",
                        "url": "http://futurimedia.com/"
                    },
                    {
                        "is_external": "0",
                        "subtitle": "subtitle",
                        "title": "Title",
                        "url": "http://futurimedia.com/"
                    }
                ]
            }
        },
        "options": {
            "locale": "en_US"
        }
    }
}
```
---

## Abacus Stats

### `POST /stats`

*Saves events to the internal analytics system*

Analytics events triggered within frontend apps should be queued and posted to the api
periodically. Current versions of Futuri Mobile dequeue every 10 seconds, but a longer
interval is fine as long as events are dequeued before the app closes.

There are three classes of analytics events used in Futuri products.

- `action`, a non pageview event. Typically namespaced like "gruvr.main_menu.call_station"
- `view`, a pageview.
- `song_action`, for music stations, actions specific to a song. Saved with a string `custom_id` for the song

**POST data:**

`product`: {string} One of "gruvr", "engage"
`timestamp`: {int} unix timestamp when this api request was initiated. Used to calculate relative offsets for the per-event timestamps
`events`: Array of objects per each event:

- `type`: {string} "action" or "view" or "song_action"
- `label`: {string} The name of the page or action
- `timestamp`: {int} unix timestamp when the event occurred
- `data`: optional object containing additional data. When `type == "song_action"`, this must contain `custom_id` {string} of the song

**Return:**

```
{
    "ok": true
}
```

## Home Page Content

### `GET /gruvr/homepage`

This returns two sets of data for displaying on the homepage.

For `menu_items` see the data definitions in [MENU_ITEMS.md]
For `feed` see the definitions in [RSS_FEEDS.md]

**Return:**
```
{
    "menu_items": [
        ...
    ],
    "feed": {
        "name": "Top 3 things you need to know",
        "articles": [
            ...
        ]
    }
}
```

## News Feeds Index

### `GET /gruvr/news_feeds/`

*Returns all feeds used by the app, for index pages*

**Return:**
```
{
    "feeds": [
        {
            "id": "24",
            "name": "National",
            "url": "http://www.wsbradio.com/api/content/v1/automaticlist/17736/?verbose=1",
            "icon": "",
            "deleted": "0",
            "default": "0",
            "display_order": "2"
          },
        ...
    ]
}
```

## News Feeds Index

### `GET /gruvr/news_feeds/:id`

*Return title and contents of a single feed*

**Return:**
```
{
    "feed": {
        "id": "76",
        "name": "KRMG methode",
        "url": "http://krmg.com/news/local/top-stories/GbrbrR8blbDmyDrM0BcjJM/rss2/",
        "icon": "",
        "deleted": "0",
        "default": "1",
        "articles": [
            {
                "title": "Trump is broadening his search for FBI director",
                "date": "2017-05-30 16:10:00",
                "body": "<div>\t\t\t\t\n\t\t\t\t\t\t<p>President Donald Trump is widening his search for FBI director, meeting with two additional candidates to replace ousted director James Comey.</p></div>\t\t\t\t\t\n\t\t\t\t<div>\t\t\t\t\n\t\t\t\t\t\t<p>White House press secretary Sean Spicer says Trump is meeting Tuesday with two additional candidates to lead the agency: former Transportation Security Administration head John Pistole and Chris Wray, a former top Justice Department official who has served as New Jersey Gov. Chris Christie's personal lawyer.</p></div>\t\t\t\t\t\n\t\t\t\t<div>\t\t\t\t\n\t\t\t\t\t\t<p>Trump is still on the hunt for a new FBI director three weeks after he fired Comey.</p></div>\t\t\t\t\t\n\t\t\t\t<div>\t\t\t\t\n\t\t\t\t\t\t<p>Spicer is declining to provide a short list for the position, telling reporters that when Trump \"feels as though he's met with the right candidate he'll let us know.\"</p></div>",
                "link": "http://www.krmg.com/news/national-govt--politics/trump-broadening-his-search-for-fbi-director/OCFOhG4RA1ZUD4VHEsexdM/",
                "guid": "017e7b29d0eea7abe6503c6179a4e919",
                "content_id": "9a12e89c-457c-11e7-a701-04cf7605a5fe",
                "image:station": "http://widget.ldrhub.com/new/content/img/ldr1_df.png"
            },
            ...
        ],
    }
}
```
