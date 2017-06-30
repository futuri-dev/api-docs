# Alexa endpoint documentation:

### `GET /configs/alexa`

*Returns a set of config values for the Alexa skills. This endpoint is not directly used. It may be hit to gather information about new skill builds. It essentially duplicates the `constants.js` file housed internally with skills.*

**Return:**

```
{
  "ok": true,
  "configs": {
      ...
  }
}
```

---

### `GET /alexa/audioAssets`

*Get audio assets (live stream, on-demand shows, and preroll content) for a given station's Alexa skill.*

**Params:**

`key`: {string} Station identifier

**Return:**

```
{
  "ok": true,
  "audioAssets": {
      streamData: {
        title: "Megahertz",
        url: "https://gruvrradio.streamon.fm/listen.m3u"
      },
      onDemandData: [
          [
              {
                  title: "Sample Open Mic",
                  url: "https://static-dev.ldrhub.com/stations/ryan/example_open_mic.mp3"
              },
              ...
          ],
          ...
      ],
      prerollData: {
          goodbye: [],
          ondemand_menu: [],
          welcome: [],
          welcome_back: [],
          ondemand: [
              [
                  "https://static-dev.ldrhub.com/stations/wgr/alexa_assets/ondemand_1_preroll-0-48kbps-16000Hz.mp3"
              ],
              null,
              [],
              [],
          ]
      }
  }
}
```

---
