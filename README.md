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
- `data/news.json` is the base archive. New items arrive as small daily files `data/daily/YYYY-MM-DD.json` (`{"items":[...]}`) listed in `data/manifest.json` (`{"updated":"YYYY-MM-DD","files":["daily/YYYY-MM-DD.json", …]}`). The page merges them and drops duplicates (same developer + project).
- A Claude scheduled task writes the day's file and the manifest every morning via the GitHub connector. GitHub Pages redeploys in ~1 minute.
