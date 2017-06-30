## Nav Menu Configurations

*Standard set of data to describe a navigation item*

There are currently three sets of app-wide navigation menus, the same data format drives
all three.

Sample item:
```
    {
      "title": "Push Notifications",
      "icon": "pushNotifications",
      "action": "view",
      "target": "notification-settings"
    }
```

`title`: {string} for display
`icon`: {string} for hamburger or navbar items, the icon from the iconfont to display. Only
the portion after "icon-" is included, so in this example, the icon labeled "icon-pushNotifications"
should be used.
`target`: {string} used with the `action` value to determine the click handle event
`action`: {string} one of the following:
- `"view"`: An in-app view. `target` contains a slug-style name of the view
- `"call"`: Load a `tel://` url, `target` contains the number to call
- `"in_app_browser"`: Load a url in the in-app browser, `target` contains the url to load
- `"external_browser"`: Load a url in the system browser, `target` contains the url to load

For Home Page navigation tiles, `title` `action` and `target` are the same, but instead
of `icon`, two properties `tile` and `data` define the larger content below the title.

In the following example, display the image from `data.url` (applying rounded corners or other style as
consistent with the standard image style for this page):

```
{
    "title": "Traffic",
    "tile": "image",
    "data": {
        "url": "https://static.ldrhub.com/stations/chris/gruvr_tiles/current_traffic.png?1495487648"
    },
    "action": "in_app_browser",
    "target": "https://maps.google.com/"
},
```

In the following example, update and display the dynamic weather widget based on the data.
(Further documentation on this widget to follow)

```
{
    "title": "Weather",
    "tile": "weather",
    "data": {
        "background_image": "https://static.ldrhub.com/gruvr/v11/weather/rain.png",
        "current_temp": "62",
        "feels_like": "57",
        "weather": "Scattered Showers",
        "icon": "part-clouds",
        "high": "72",
        "low": "57"
    },
    "action": "in_app_browser",
    "target": "https://wunderground.com/"
},
```
