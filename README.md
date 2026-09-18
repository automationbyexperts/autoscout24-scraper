# AutoScout24 All-Country Scraper

Our autoscout24 scraper makes it simple to collect listings at scale and in all countries. Works on autoscout24.de, .at, .fr, .it, .es, .nl, .be, .lu and .com

This repo shows how to call the [AutoScout24 All-Country Scraper](https://apify.com/fayoussef/autoscout24?fpr=youssef) Apify Actor from your own code: a Python and a JavaScript example, the input they send, and a sample of the output. Everything runs in the Apify cloud, so there is nothing to host, scale or maintain on your side.

- **Run it in the browser:** [fayoussef/autoscout24 on Apify](https://apify.com/fayoussef/autoscout24?fpr=youssef)
- **Guide and docs:** [automationbyexperts.com/apify/autoscout24](https://automationbyexperts.com/apify/autoscout24)
- **Actor ID for the API:** `fayoussef/autoscout24`

## Use cases

- [Find used VW Golfs in Germany under 15,000 EUR](https://apify.com/fayoussef/autoscout24/examples/vw-golf-germany-under-15000?fpr=youssef): Uses the built in filter form to search autoscout24.de for used Volkswagen Golf listings from 2016 onwards priced under 15,000 EUR, cheapest first, and returns 50 plus fields per car: price, mileage, equipment, dealer contact, GPS location and every photo. No search URL to copy.
- [Export used electric cars in the Netherlands and Belgium](https://apify.com/fayoussef/autoscout24/examples/electric-cars-netherlands-belgium?fpr=youssef): Searches AutoScout24 for used fully electric cars located in the Netherlands and Belgium and exports each listing with price, mileage, battery and range fields, first registration, dealer details and photos. Built for EV dealers and researchers tracking the Benelux used EV market.
- [Track new dealer SUV listings in Italy each week](https://apify.com/fayoussef/autoscout24/examples/new-dealer-suv-listings-italy?fpr=youssef): Returns SUV and off road listings posted by dealers on autoscout24.it in the last 7 days, newest first. Schedule it weekly and you have a running feed of fresh dealer stock in Italy, with price, mileage, equipment and the dealer's contact details on every row.

## Quick start

1. Create a free [Apify account](https://console.apify.com/sign-up?fpr=youssef) and copy your API token from [Settings > Integrations](https://console.apify.com/settings/integrations).
2. Set it as an environment variable: `export APIFY_TOKEN=...` (PowerShell: `$env:APIFY_TOKEN="..."`).
3. Edit [`input.json`](input.json) and run one of the examples below.

### Python

```bash
pip install apify-client
python examples/python/run_actor.py
```

```python
import os
from apify_client import ApifyClient

client = ApifyClient(os.environ["APIFY_TOKEN"])
run = client.actor("fayoussef/autoscout24").call(run_input={'search_domain': 'de',
 'countries': ['germany'],
 'makes': ['Volkswagen'],
 'models': ['Golf'],
 'conditions': ['used'],
 'price_to': 15000,
 'first_registration_from': 2016,
 'sort_by': 'price',
 'max_items': 300})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

### JavaScript / Node.js

```bash
npm install apify-client
node examples/javascript/run_actor.mjs
```

```javascript
import { ApifyClient } from "apify-client";

const client = new ApifyClient({ token: process.env.APIFY_TOKEN });
const run = await client.actor("fayoussef/autoscout24").call({
    "search_domain": "de",
    "countries": [
        "germany"
    ],
    "makes": [
        "Volkswagen"
    ],
    "models": [
        "Golf"
    ],
    "conditions": [
        "used"
    ],
    "price_to": 15000,
    "first_registration_from": 2016,
    "sort_by": "price",
    "max_items": 300
});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

### cURL (plain HTTP)

Runs the Actor and returns the dataset items in one synchronous call:

```bash
curl -X POST "https://api.apify.com/v2/acts/fayoussef~autoscout24/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d @input.json
```

Synchronous calls time out after 300 seconds. For larger runs use the client libraries above, or start the run with `POST /v2/acts/fayoussef~autoscout24/runs` and read the dataset when it finishes.

## Sample output

One record, from [`sample-output.json`](sample-output.json). Export the full dataset as JSON, CSV, Excel or HTML from the Apify Console, or read it through the API as shown above.

```json
{
  "listing_id": "53a8e594-eb3a-4871-9252-1e37b6d29816",
  "listing_url": "https://www.autoscout24.com/offers/53a8e594-eb3a-4871-9252-1e37b6d29816",
  "status": "Active",
  "created_at": "2025-09-30T12:17:46.407Z",
  "make": "BMW",
  "model": "114",
  "model_version": "114i CarPlay*Sièges Chauffants*Garantie",
  "body_type": "Sedan",
  "body_color": "White",
  "first_registration": "04/2014",
  "mileage_km": 136130,
  "mileage_formatted": "136,130 km",
  "power_kw": 75,
  "power_hp": 102,
  "transmission": "Manual",
  "drive_train": "Rear Wheel Drive",
  "fuel_type_formatted": "Gasoline",
  "doors": 5,
  "seats": 5,
  "had_accident": false,
  "full_service_history": true,
  "price": 9200,
  "price_formatted": "€ 9,200",
  "vat_deductible": false,
  "total_equipment_count": 44,
  "equipment_comfortAndConvenience": [
    "Cruise control",
    "Navigation system"
  ],
  "equipment_entertainmentAndMedia": [
    "Apple CarPlay",
    "Bluetooth"
  ],
  "country": "BE",
  "city": "Tubize",
  "zip": "1480",
  "latitude": 50.69989,
  "longitude": 4.20648,
  "seller_company": "Urban Car",
  "seller_phone": "+32 (0)474 - 734924",
  "is_dealer": true,
  "warranty_exists": true,
  "image_count": 15,
  "main_image": "https://prod.pictures.autoscout24.net/listing-images/53a8e594.jpg/1280x960.webp"
}
```

## Pricing

Pay per use on Apify: you are charged per event (results produced), with no subscription to this Actor. The current rate is shown on the [Actor's Store page](https://apify.com/fayoussef/autoscout24?fpr=youssef). Free-plan runs are capped; an [Apify plan](https://apify.com/pricing?fpr=youssef) unlocks full runs.

## More Actors by AutomationByExperts

- [AutoTrader Canada Car Scraper: Prices, VIN, Mileage & Dealers](https://github.com/automationbyexperts/autotrader-canada-scraper)
- [Kijiji.ca Scraper: Autos, Real Estate & Classifieds](https://github.com/automationbyexperts/kijiji-scraper)
- [CarGurus Scraper (US, Canada & UK Car Listings)](https://github.com/automationbyexperts/cargurus-scraper)
- [autotrader.co.za Car Scraper with Seller Phone Numbers](https://github.com/automationbyexperts/autotrader-south-africa-scraper)
- [Bulk AI Image Generator (NO API KEY)](https://github.com/automationbyexperts/bulk-ai-image-generator)
- [Bulk LLM Runner GPT, Claude, Perplexity, Kimi (No API Key)](https://github.com/automationbyexperts/bulk-llm-runner)
- [Full catalog of our web scraping APIs](https://github.com/automationbyexperts/web-scraping-apis)

## Support

Questions, bugs or a custom scraper: open an issue here, use the Issues tab on the [Apify page](https://apify.com/fayoussef/autoscout24?fpr=youssef), or email youssefarhan24@gmail.com.

## License

The example code in this repo is MIT licensed. The Actor itself runs on Apify under its own terms.
