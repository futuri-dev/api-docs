## RSS Feed content

*Standard set of data to describe a news feed*

Data of type `{feed}` is returned as part of the homepage configuration, and for the specific
live news pages. For each feed the following:

```
    {
     "id" => "76",
     "name" => "KRMG methode",
     "url" => "http://krmg.com/news/local/top-stories/GbrbrR8blbDmyDrM0BcjJM/rss2/",
     "icon" => "",
     "deleted" => "0",
     "default" => "1",
     "display_order" => "1",
     "articles": [
          {
            "title": "Ending May with great temps and rain chances",
            "date": "2017-05-30 12:01:00",
            "body": "<div>\n\t\t\t\t\t<p>Quick Facts:Â </p> <ul> <li> Temperatures remain nice in the 80s without getting too hot</li> <li> Dewpoints climb back into the 60sÂ by the weekend, making it feel very humid</li> <li> Rain chances return for the mid and latter part of the work week</li> </ul> <p>Â </p> <h2> Tuesday</h2> <p>Cloud coverage increases into Tuesday with winds back out of the south bringing in some moisture. The moisture in turn, increases the dewpoints putting Green Country into the muggy category.</p><p>Temperatures remain nice in the mid-80s with a mixture of sunshine and clouds. Rain chances return later in the day on Tuesday, with some isolated shower and storm chances. The severe risk is very low at this time.</p><img src=\"http://mediaweb.fox23.com/photo/2017/05/29/17_3Day_UV_Index_20170529074647961_8185101_ver1.0_640_360.png\" /><p>If you are spending time outside over the next couple of days, be sure that you have your sunglasses and sunscreen. The UV Index, or the expected risk of overexposure to UV radiation from the sun, is at a 9 out of 11 over the next three days. That means that it can take anywhere from 15-20 minutes for some people to burn.</p> <h2> Wednesday</h2> <p>Rain chances continue for Hump Day but become more widespread. Temperatures stay in the 80sÂ but conditions do become more muggy as the moisture continues to move into Green County.</p><img src=\"http://mediaweb.fox23.com/photo/2017/05/29/Dewpoint%20Scale_20170529074647770_8183100_ver1.0_640_360.png\" /> <h2> Thursday</h2> <p>The chance for showers and storms increase, but the severe risk is still low in Green Country. Temperatures come down just a little bit into the low 80s.</p><p>With rain chances on the increase, the chance of the rain being more wide spread also increases. The day will not be a complete washout, but keeping your umbrella handy will be key moving into Friday. Convection will gradually increase in coverage during the evening across Oklahoma with the highest chance of the strongest storms being in the Red River Valley.</p> <h2> Friday</h2> <img src=\"http://mediaweb.fox23.com/photo/2017/05/29/Storm%20Planner_20170529074744097_8185102_ver1.0_640_360.png\" /><p>Rain chances ramp up and the chance for severe weather increases as well. Right now the timing and location are becoming a little more consistent with timing but not location for Friday.</p><p>The biggest threat will be some large hail especially moving into Saturday.</p> <h2> Weekend</h2> <p>Saturday and Sunday will remain in the 80s and climb from the low 80s into the mid-80s. Rain chances will still be present, especially on Saturday. Some of Saturday's storms could turn severe with especially large hail. Moving into Sunday, rain chances will be decreasing but you'll want to keep your umbrella handy.</p></div>",
            "link": "http://www.krmg.com/news/ending-may-with-great-temps-and-rain-chances/dSOlRLP1xFMDwJXYruRYJI/",
            "guid": "15044236ab32943e86a0b0e7151de98f",
            "content_id": "0bd4fc81-d8f5-4d94-a45d-e99cba7fa079",
            "image:crop": "http://static.dev.ldrhub.com/stations/chris/gruvr_news_images/d9f4b31fb10c10d767b321e8603cb395-crop.jpg",
            "image:thumb": "http://static.dev.ldrhub.com/stations/chris/gruvr_news_images/d9f4b31fb10c10d767b321e8603cb395-thumb.jpg"
          },
          ...
      ]
    }
```

For each `articles` the following:

`name` - Title for use in feed indexes
`date` - Date posted to the feed. This should be the sort order for feed indexes (newest-first)
`body` - Content for rending the story. Contains HTML.
`link` - Used for the "Share" dialogs
`guid` - (currently unused)
`content_id` - Reference to the feed provider's data, sent with analytics
`image:crop` - URL for full-size image
`image:thumb` - URL for thumbnail image, for use on the homepage carousel or feed indexes
