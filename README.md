# AutoScout24 Scraper: European Car Listings, Prices & Dealer Phone Numbers (DE, IT, FR, ES, NL, BE, AT)

[![Run on Apify](https://img.shields.io/badge/Apify-Run%20the%20Actor-00A67E?logo=apify&logoColor=white)](https://apify.com/fayoussef/autoscout24?fpr=youssef)
![Countries](https://img.shields.io/badge/Countries-DE%20%7C%20IT%20%7C%20FR%20%7C%20ES%20%7C%20NL%20%7C%20BE%20%7C%20AT%20%7C%20LU-2ea44f)
![Dealer phone](https://img.shields.io/badge/Dealer%20phone-included-1C7ED6)
![Search](https://img.shields.io/badge/Search-URL%20or%20filters-8B5CF6)
![Export](https://img.shields.io/badge/Export-JSON%20%7C%20CSV%20%7C%20Excel-F59E0B)

> ### ▶️ [Run the AutoScout24 Scraper on Apify](https://apify.com/fayoussef/autoscout24?fpr=youssef)
> Scrape **AutoScout24** car listings from autoscout24.de, .it, .fr, .es, .nl, .be, .at, .lu and .com with price, make, model, mileage, first registration, fuel, power, equipment, photos, GPS and **dealer phone number**. Paste a URL or search with filters, no URL needed.

**AutoScout24 Scraper** turns AutoScout24, Europe's largest online car marketplace, into clean structured data: 60+ fields per car across nine country sites. It is built for car dealers, importers and exporters, leasing firms, automotive market researchers and data aggregators who need cross-border used and new car data. This repository documents the Apify Actor and gives working Python, JavaScript and cURL examples for calling it through the API.

- **Run it in the browser:** [fayoussef/autoscout24 on Apify](https://apify.com/fayoussef/autoscout24?fpr=youssef)
- **Guide and docs:** [automationbyexperts.com/apify/autoscout24](https://automationbyexperts.com/apify/autoscout24)
- **Actor ID for the API:** `fayoussef/autoscout24`

## What the AutoScout24 scraper does

- **Nine AutoScout24 sites in one Actor**: Germany (.de), Italy (.it), France (.fr), Spain (.es), Netherlands (.nl), Belgium (.be), Austria (.at), Luxembourg (.lu) and .com.
- **Search by filters, no URL needed**: 293 makes, models, body type, condition, dealer or private seller, price, first registration, mileage, fuel, transmission, power, colours, equipment, emission class, postal code and radius.
- **Or paste any AutoScout24 URL**: a search page, a single car, or a dealer profile (you get the dealer's full stock).
- **Dealer contacts** on every dealer listing: company, contact name, phone and homepage.
- **Full equipment lists** grouped by comfort, safety, entertainment and extras.
- **GPS location** of every car.

## Output fields: what data you get

One row per car, 60+ fields. The main groups:

| Field | Description |
|---|---|
| `listing_id` / `listing_url` / `created_at` | Listing identity and date |
| `price` / `price_negotiable` / `vat_deductible` | Price in EUR and price flags |
| `make` / `model` / `model_version` / `body_type` | Vehicle identity |
| `mileage_km` / `first_registration` | Mileage and first registration date |
| `fuel_type` / `power_kw` / `power_hp` / `transmission` / `drive_train` | Engine and drivetrain |
| `fuel_consumption_combined` / `co2_emission` | Consumption and emissions |
| `had_accident` / `full_service_history` / `previous_owners` / `warranty_exists` | History and condition |
| `equipment_*` / `total_equipment_count` | Equipment by category |
| `country` / `city` / `zip` / `latitude` / `longitude` | Location and GPS |
| `seller_company` / `seller_contact_name` / `seller_phone` / `dealer_homepage` | Dealer contacts |
| `main_image` / `all_images` / `has_360_view` | Photos |
| `description` | Full listing text |

## Input

Paste AutoScout24 URLs into `start_urls`, or leave it empty and use the filters:

| Field | What it does |
|---|---|
| `search_domain` / `countries` | Which AutoScout24 site, and which countries to include |
| `makes` / `models` | Make and model |
| `conditions` / `seller_type` | New, used... dealer or private |
| `price_from` / `price_to` | Price range in EUR |
| `first_registration_from` / `first_registration_to` | Registration year range |
| `mileage_from_km` / `mileage_to_km` | Mileage range |
| `body_types` / `fuel_types` / `transmission` | Body, fuel and gearbox |
| `power_from` / `power_to` / `power_unit` | Power in hp or kW |
| `equipment` / `emission_class` | Required equipment and emission class |
| `postal_code` / `radius_km` | Search around a postal code or city |
| `listed_within_days` | Only recent listings |
| `max_items` | Number of cars to return |

## Use cases

- **Car import and export**: compare the same model's price in Germany, Italy, Belgium and the Netherlands.
- **Dealer pricing**: benchmark your stock against local and cross-border competitors.
- **Dealer lead generation**: build lists of European car dealers with phone numbers.
- **EV market research**: track electric car prices and supply by country.
- **Leasing and remarketing**: value used cars by mileage, age and equipment.

Ready-made examples you can run in one click:

- [Find used VW Golfs in Germany under 15,000 EUR](https://apify.com/fayoussef/autoscout24/examples/vw-golf-germany-under-15000?fpr=youssef): Uses the built in filter form to search autoscout24.de for used Volkswagen Golf listings from 2016 onwards priced under 15,000 EUR, cheapest first, and returns 50 plus fields per car: price, mileage, equipment, dealer contact, GPS location and every photo. No search URL to copy.
- [Export used electric cars in the Netherlands and Belgium](https://apify.com/fayoussef/autoscout24/examples/electric-cars-netherlands-belgium?fpr=youssef): Searches AutoScout24 for used fully electric cars located in the Netherlands and Belgium and exports each listing with price, mileage, battery and range fields, first registration, dealer details and photos. Built for EV dealers and researchers tracking the Benelux used EV market.

## Quick start

### 1. In the browser (no code)

1. Open the Actor on Apify and click **Try for free**.
2. Paste an AutoScout24 search URL into **Start URLs**, or leave it empty and pick the site, make, model and price in **Search filters**.
3. Set **Max results**, click **Start**, then download Excel, CSV or JSON from the **Output** tab.

### 2. Through the API

1. Create a free [Apify account](https://console.apify.com/sign-up?fpr=youssef) and copy your API token from [Settings > Integrations](https://console.apify.com/settings/integrations).
2. Set it as an environment variable: `export APIFY_TOKEN=...` (PowerShell: `$env:APIFY_TOKEN="..."`).
3. Edit [`input.json`](input.json) and run one of the examples below.

#### Python

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

#### JavaScript / Node.js

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

#### cURL (plain HTTP)

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
  "price": 9200,
  "price_formatted": "€ 9,200",
  "vat_deductible": false,
  "make": "BMW",
  "model": "114",
  "model_version": "114i CarPlay*Sièges Chauffants*Garantie",
  "body_type": "Sedan",
  "body_color": "White",
  "first_registration": "04/2014",
  "mileage_km": 136130,
  "mileage_formatted": "136,130 km",
  "fuel_type_formatted": "Gasoline",
  "power_kw": 75,
  "power_hp": 102,
  "transmission": "Manual",
  "drive_train": "Rear Wheel Drive",
  "doors": 5,
  "seats": 5,
  "had_accident": false,
  "full_service_history": true,
  "equipment_comfortAndConvenience": [
    "Cruise control",
    "Navigation system"
  ],
  "equipment_entertainmentAndMedia": [
    "Apple CarPlay",
    "Bluetooth"
  ],
  "total_equipment_count": 44,
  "country": "BE",
  "city": "Tubize",
  "zip": "1480",
  "latitude": 50.69989,
  "longitude": 4.20648,
  "is_dealer": true,
  "seller_company": "Urban Car",
  "seller_phone": "+32 (0)474 - 734924",
  "warranty_exists": true,
  "main_image": "https://prod.pictures.autoscout24.net/listing-images/53a8e594.jpg/1280x960.webp",
  "image_count": 15
}
```

## Integrations and automation

- **Schedule it** daily or weekly to follow prices and new listings across countries.
- **Send results** to Google Sheets, Airtable, Slack, a webhook, Make, Zapier or n8n with Apify integrations.
- **Use it from AI agents** through the Apify MCP server.

## FAQ

### Does AutoScout24 have a public API?
Only for registered dealers uploading their own stock. There is no public API for searching listings. This Actor is an AutoScout24 API alternative that returns structured JSON through one Apify API call.

### Which AutoScout24 countries are supported?
autoscout24.de, .it, .fr, .es, .nl, .be, .at, .lu and .com.

### Can I get the dealer phone number?
Yes. `seller_phone` is filled on dealer listings, with `seller_company`, `seller_contact_name` and `dealer_homepage`.

### Do I need to paste a URL?
No. Leave Start URLs empty and fill in the search filters; the Actor builds the AutoScout24 search for you.

### Can I scrape a whole dealer inventory?
Yes. Paste the dealer profile URL and the Actor returns every car that dealer has listed.

### How do I compare car prices between countries?
Run the same make and model filters with different `countries` values and compare `price` by `country`.

### What output formats are available?
JSON, CSV, Excel, XML and HTML from the Apify dataset, or through the API.

## AutoScout24 Scraper auf Deutsch

Der **AutoScout24 Scraper** liefert Fahrzeugangebote von autoscout24.de und acht weiteren Länderseiten als strukturierte Daten: Preis, Marke, Modell, Kilometerstand, Erstzulassung, Kraftstoff, Leistung, Ausstattung, Fotos, GPS-Standort und **Telefonnummer des Händlers**. Suchen Sie per URL oder mit Filtern, ganz ohne Programmierung, und exportieren Sie die Ergebnisse als Excel, CSV oder JSON. [Jetzt auf Apify testen](https://apify.com/fayoussef/autoscout24?fpr=youssef).

## Pricing

Pay per use on Apify: you are charged per event (results produced), with no subscription to this Actor. The current rate is shown on the [Actor's Store page](https://apify.com/fayoussef/autoscout24?fpr=youssef). Free-plan runs are capped; an [Apify plan](https://apify.com/pricing?fpr=youssef) unlocks full runs.

## Related scrapers by AutomationByExperts

- [AutoTrader.ca Scraper: Canada Car Listings, VIN & Dealers](https://github.com/automationbyexperts/autotrader-canada-scraper)
- [Kijiji.ca Scraper: Cars, Rentals & Classifieds with Phones](https://github.com/automationbyexperts/kijiji-scraper)
- [CarGurus Scraper: US, Canada & UK Car Listings](https://github.com/automationbyexperts/cargurus-scraper)
- [AutoTrader.co.za Scraper: South Africa Cars with Seller Phones](https://github.com/automationbyexperts/autotrader-south-africa-scraper)
- [Bulk AI Image Generator: Nano Banana & GPT Image](https://github.com/automationbyexperts/bulk-ai-image-generator)
- [Bulk LLM Runner: ChatGPT, Claude & Gemini in Bulk](https://github.com/automationbyexperts/bulk-llm-runner)
- [Full catalog of our web scraping APIs](https://github.com/automationbyexperts/web-scraping-apis)

## Support

Questions, bugs or a custom scraper: open an issue here, use the Issues tab on the [Apify page](https://apify.com/fayoussef/autoscout24?fpr=youssef), or email youssefarhan24@gmail.com.

## License

The example code in this repo is MIT licensed. The Actor itself runs on Apify under its own terms.
