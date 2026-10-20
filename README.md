# ✨ Boutiqaat Scraper API — Kuwait & GCC Celebrity Beauty Catalog Intelligence

<p align="center">
  <a href="https://console.apify.com/actors?search=boutiqaat-scraper"><img src="https://img.shields.io/badge/Run%20on-Apify%20Store-orange?logo=apify&style=for-the-badge" alt="Run on Apify" /></a>
  <a href="#-python-quickstart"><img src="https://img.shields.io/badge/Python-3.8+-blue?logo=python&style=for-the-badge" alt="Python" /></a>
  <a href="#-nodejs-quickstart"><img src="https://img.shields.io/badge/Node.js-18+-green?logo=node.js&style=for-the-badge" alt="Node.js" /></a>
  <a href="#-pricing"><img src="https://img.shields.io/badge/Pricing-Pay--Per--Event%20($2.50%2F1k)-brightgreen?style=for-the-badge" alt="Pay Per Event" /></a>
</p>

> 🌐 **Tracking the broader GCC fragrance & beauty market?** Check out our sibling APIs:
> | Marketplace | Official Scraper Client | Market Focus |
> |---|---|---|
> | **Boutiqaat** | **This API Client (`boutiqaat-scraper`)** | Kuwait & celebrity beauty exclusives (`boutiqaat.com`) |
> | **NiceOne Saudi Arabia** | [NiceOne Scraper API](https://github.com/smidaJaber/niceone-scraper-api) | KSA beauty unicorn (`niceonesa.com`) |
> | **GoldenScent** | [GoldenScent Scraper API](https://github.com/smidaJaber/goldenscent-scraper-api) | Gulf designer & Arabian oud (`goldenscent.com`) |

---

The unofficial Node.js & Python client, SDK wrapper, and automation templates for the **Boutiqaat Scraper Apify Actor** (`boutiqaat.com`).

Extract live celebrity boutique makeup, exclusive Gulf perfumes, oud blends, and cosmetics pricing across Kuwait (`KWD`), Saudi Arabia (`SAR`), and the UAE (`AED`), discount percentages, stock availability, and deep **Olfactory Pyramid fragrance notes (Top, Middle, Base)**.

---

## ⚡ Quickstart

### 🐍 Python Quickstart
```python
import os
from apify_client import ApifyClient

client = ApifyClient(os.getenv("APIFY_TOKEN", "YOUR_APIFY_TOKEN"))

run_input = {
    "platform": "boutiqaat.com",
    "countryStorefront": "kw-KWD",
    "searchQueries": ["Boutiqaat Exclusives", "Musk", "Oud", "Atyab Al Marshoud"],
    "maxItemsPerSource": 25,
    "onlyNewOrPriceChanged": True, # Delta monitor mode
}

run = client.actor("boutiqaat-scraper").call(run_input=run_input)
items = client.dataset(run["defaultDatasetId"]).list_items().items

for p in items:
    print(f"[Boutiqaat] {p['title']} - {p['salePrice']} {p['currency']}")
```

### 📦 Node.js Quickstart
```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: process.env.APIFY_TOKEN });

const run = await client.actor('boutiqaat-scraper').call({
    platform: 'boutiqaat.com',
    countryStorefront: 'kw-KWD',
    searchQueries: ['Boutiqaat Exclusives', 'Oud'],
    maxItemsPerSource: 25,
    onlyNewOrPriceChanged: true,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(`Extracted ${items.length} products from Boutiqaat`);
```

---

## 🔄 Salla (سلة) & n8n Price Alert Webhook Template

Looking to trigger automatic price-drop alerts or synchronize prices with your **Salla (سلة)** or **Zid (زد)** store?

Check out our production-ready n8n template:
- 📁 [`templates/n8n-salla-price-alert-workflow.json`](./templates/n8n-salla-price-alert-workflow.json): Import directly into n8n.
- 📁 [`templates/salla-price-alert-webhook.js`](./templates/salla-price-alert-webhook.js): Standalone Node.js Express webhook server.
- 📖 [`templates/README.md`](./templates/README.md): Setup instructions for Telegram alerts and Salla Merchant API.

---

## 🇰🇼 أداة سحب ومراقبة أسعار بوتيكات (Boutiqaat API)
واجهة برمجية متخصصة لمراقبة وتتبع أسعار عطور المشاهير ومستحضرات التجميل الحصرية على موقع **بوتيكات (Boutiqaat)** في الكويت والخليج:
- سحب الأسعار بالدينار الكويتي (KWD)، الريال السعودي (SAR)، والدرهم الإماراتي (AED).
- استخراج بوتيك المشهور/الفنان المرتبط بالمنتج والمواصفات الكاملة.
- رصد وتنبيهات الخصومات وعروض المكياج الحصرية عبر n8n و Webhook.

---

## 📄 License
MIT © 2026
