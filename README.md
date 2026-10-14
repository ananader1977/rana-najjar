# Rana Najjar — UAE New Developments

Mobile-first dashboard of new real estate development news across the UAE, in Al Bonian FM colours.

- **Dashboard** — KPIs, split by unit type (apartment / villa / townhouse / mixed), by emirate, top developers, weekly timeline.
- **News** — every item grouped by date, filterable by emirate, unit type, period, developer and search.
- **Developers** — portfolio summary per developer.

## Data
All content lives in `data/news.json`. Each item:

```json
{"id":1,"date":"2026-10-06","dateType":"reported|listed","developer":"Nakheel","project":"Bay Estate",
 "emirate":"Dubai","community":"Dubai Islands","unitType":"Apartment|Villa|Townhouse|Mixed",
 "unitBasis":"stated|inferred","priceFrom":null,"title":"…","summary":"…","source":"Zawya","url":"https://…"}
```

- `dateType: reported` = date of the news article. `listed` = date the project was captured from a launch register.
- To update: add items to `items`, bump `updated` to today's date, commit. GitHub Pages redeploys in ~1 minute.
- A Claude scheduled task appends new items every morning.
