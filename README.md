# REA Group (rea-group)

REA Group Limited is an ASX-listed (ASX:REA) digital real estate advertising business headquartered in Melbourne, Australia and majority-owned by News Corp. It operates realestate.com.au and realcommercial.com.au, the property data and analytics brand PropTrack, the Mortgage Choice broking network, and REA India (Housing.com, PropTiger, and Makaan). REA Group's public developer surface is delivered through PropTrack, whose developer portal documents a suite of property data APIs sourced from Australia's largest real estate portal.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/rea-group/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/rea-group/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Property Data
- Valuations
- Market Insights
- Listings
- PropTech
- Australia

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## Access

The PropTrack developer portal ([developer.proptrack.com.au](https://developer.proptrack.com.au/)) is publicly readable, but the underlying data APIs are **partner-gated**: the data endpoints (base URL `https://data.proptrack.com/api/v2`) return HTTP 403 without credentials and are authenticated via REA Group's OAuth identity service. Access requires a commercial agreement - prospective users are directed to "speak to a specialist" or trial the APIs. There is no self-serve API key signup and no separate public developer portal at realestate.com.au (that hostname does not resolve).

## APIs

### PropTrack Properties API

Retrieves data on a specific property - attributes, history, and property reports - drawn from PropTrack's property dataset behind realestate.com.au.

- **Human URL:** [https://developer.proptrack.com.au/docs/property-data-apis/properties](https://developer.proptrack.com.au/docs/property-data-apis/properties)
- **Base URL:** `https://data.proptrack.com/api/v2`

#### Tags

- Property Data
- Property Reports
- Real Estate

### PropTrack Address API

Address match and address suggest endpoints that resolve free-text or partial addresses to canonical Australian property records, with structured address match noted as coming soon.

- **Human URL:** [https://developer.proptrack.com.au/docs/property-data-apis/address](https://developer.proptrack.com.au/docs/property-data-apis/address)
- **Base URL:** `https://data.proptrack.com/api/v2`

#### Tags

- Address
- Geocoding
- Matching

### PropTrack Valuations API (AVM)

PropTrack's Automated Valuation Model (AVM) and valuation endpoints return estimated property values and confidence ranges used across banking, broking, and valuation workflows.

- **Human URL:** [https://developer.proptrack.com.au/docs/apis/home](https://developer.proptrack.com.au/docs/apis/home)
- **Base URL:** `https://data.proptrack.com/api/v2`

#### Tags

- Valuations
- AVM
- Automated Valuation Model

### PropTrack Listings API

Listing details, listing history, and listings search by point and radius, plus sold transactions search by point and radius, exposing for-sale and sold listing data from realestate.com.au.

- **Human URL:** [https://developer.proptrack.com.au/docs/apis/branches/main/listings](https://developer.proptrack.com.au/docs/apis/branches/main/listings)
- **Base URL:** `https://data.proptrack.com/api/v2`

#### Tags

- Listings
- Search
- Real Estate

### PropTrack Market API

Suburb-level market statistics including sale insights, rent insights, best value insights, and economic reports for researching property market trends across Australia.

- **Human URL:** [https://developer.proptrack.com.au/docs/property-data-apis/market](https://developer.proptrack.com.au/docs/property-data-apis/market)
- **Base URL:** `https://data.proptrack.com/api/v2`

#### Tags

- Market Insights
- Analytics
- Suburb Trends

## Common Properties

- [Website](https://www.rea-group.com/)
- [Documentation](https://developer.proptrack.com.au/docs/apis/home)
- [Developer Portal](https://developer.proptrack.com.au/)
- [GitHub Organization](https://github.com/realestate-com-au)
- [LinkedIn](https://www.linkedin.com/company/rea-group/)
- [X](https://twitter.com/REA_Group)
- [YouTube](https://www.youtube.com/channel/UCfLcFXAN3pjad2aCzUNhUaA)
- [Blog](https://www.rea-group.com/about-us/news-and-insights/)
- [Support](https://www.proptrack.com.au/contact-us/)
- [Privacy Policy](https://www.rea-group.com/privacy/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
