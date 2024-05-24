Sure, here is the updated README.md with your contact details included:

---

# Yellow Pages Scraper

Yellow Pages Scraper is an [Apify actor](https://apify.com/actors) designed for scraping information from Yellow Pages listings. It allows you to search records based on a combination of search terms and location or a list of URLs. Built on top of the [Apify SDK](https://sdk.apify.com/), it can be run both on the [Apify platform](https://my.apify.com) and locally.

## Table of Contents
- [Input](#input)
- [Output](#output)
- [Compute Units Consumption](#compute-units-consumption)
- [Extend Output Function](#extend-output-function)
- [Contact](#contact)

## Input

| Field | Type | Description | Default Value |
| ----- | ---- | ----------- | ------------- |
| search | string | Query string to be searched on the site | `"Dentist"` |
| location | string | Location string to search the records in | `"Los Angeles"` |
| startUrls | array | List of [Request](https://sdk.apify.com/docs/api/request#docsNav) objects that will be deeply crawled. The URL can be any Yellowpages.com record list page | none |
| maxItems | number | Maximum number of pages that will be scraped | `200` |
| extendOutputFunction | string | Function that takes a Cheerio object and a Cheerio representation of the record element ($, record) as arguments and returns data that will be merged with the default output. More information in [Extend Output Function](#extend-output-function) | `($, record) => { return {}; }` |
| proxyConfiguration | object | Proxy settings of the run. If you have access to Apify proxy, you can set `{ "useApifyProxy": true }` to enable proxy usage | `{ "useApifyProxy": false }` |

Either the `search` and `location` attributes or the `startUrls` attribute must be set.

## Output

Output is stored in a dataset. Each item contains information about a record.

```json
{
    "name": "Kloesel's Steak House & Bar",
    "address": "101 W Moore Moulton, TX 77975",
    "phone": "(361) 596-7323",
    "website": "http://www.kloesel.com",
    "rating": 3.5,
    "reviewSnippet": "Top notch food! Best steaks within 100 miles!!! Excellent lunch specials as well.",
    "categories": [
        "Restaurants",
        "Steak Houses",
        "Night Clubs"
    ],
    "url": "https://www.yellowpages.com/moulton-tx/mip/kloesels-steak-house-bar-11137114?lid=171485443"
}
```

Please note that not all attributes will be present in all results.

## Compute Units Consumption

Keep in mind that it is more efficient to run one longer scrape (at least one minute) than multiple shorter ones due to the startup time.

The average consumption is about **0.04 Compute Units per 2000 results** scraped.

## Extend Output Function

You can use this function to customize the default output of this actor. This function takes a Cheerio object and a Cheerio representation of the record element ($, record) as arguments, allowing you to add or modify attributes as needed. The output from this function will be merged with the default output.

The return value of this function must be an object!

You can return fields to achieve three different things:
- **Add a new field**: Return an object with a field that is not in the default output.
- **Change a field**: Return an existing field with a new value.
- **Remove a field**: Return an existing field with a value of `undefined`.

```javascript
($, record) => {
    return {
        directionsLink: record.find('.directions').attr('href'),
        rating: 5,
        phone: undefined,
    }
}
```

This example will add a new field `directionsLink`, change the `rating` field, and remove the `phone` field.

## Contact

For any questions or support, please contact us at [support@example.com](mailto:contact@quicklifesolutions.com).

---

**Connect With Us**

- **YouTube**: [Visit our channel](https://www.youtube.com/@CodeMaster-421)
- **Instagram**: [Follow us on Instagram](https://www.instagram.com/quicklifesolutionsofficial/)
- **AI Newsletter**: [Subscribe to our newsletter](https://sendfox.com/quicklifesolutions)
- **Free Consultation**: [Book a free consultation call](https://tidycal.com/quicklifesolutions/free-consultation)
- **More Tools**: [Explore our Apify actors](https://apify.com/dainty_screw)
- **Discord**: [Raise a Support ticket here](https://discord.gg/2WGj2PDmHb)
- **Contact Email**: [codemasterdevops@gmail.com](mailto:codemasterdevops@gmail.com)

