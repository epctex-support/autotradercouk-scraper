[https://apify.com/epctex/autotradercouk-scraper](https://apify.com/epctex/autotradercouk-scraper?fpr=yhdrb)

# Actor - Autotrader UK Scraper

## Autotrader UK scraper

Since Autotrader.co.uk doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Autotrader UK data scraper supports the following features:

-   Search - Get any search results. You can use all cars, vans, bikes, motorhomes, caravans, trucks, farms, and plant search URLs.

-   Listing details - Retrieve information about the cars, vans, bikes, motorhomes, caravans, trucks, farms, and plants. Brand, model, price, mileage, fuel type, transmission, interior colors, exterior colors, and many other features.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/autotradercouk-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Autotrader UK that should be visited. Possible fields are:

- `startUrls`: (Required) (Array) List of Autotrader UK URLs. It should be a search, list, or listing detail URL.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns an object with executing the function.

This solution requires using **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.1-0.2 compute units.

### Autotrader UK Scraper Input example

```json
{
  "startUrls":[
    "https://www.autotrader.co.uk/car-search?page=2&postcode=E1%207DJ&sort=relevance",
    "https://www.autotrader.co.uk/motorhome-search?postcode=E1%207DJ&berth=2&include-delivery-option=on&advertising-location=at_motorhomes&page=1",
    "https://www.autotrader.co.uk/caravan-search?postcode=E1%207DJ&include-delivery-option=on&advertising-location=at_caravans&page=1",
    "https://www.autotrader.co.uk/truck-search?postcode=E1%207DJ&make=DAF&include-delivery-option=on&advertising-location=at_trucks",
    "https://www.autotrader.co.uk/farm-search?postcode=E1%207DJ&category=ATVS&include-delivery-option=on&advertising-location=at_farm",
    "https://www.autotrader.co.uk/plant-search?postcode=E1%207DJ&category=ATTACHMENTS&include-delivery-option=on&advertising-location=at_plants",
    "https://www.autotrader.co.uk/car-details/202306299089853",
    "https://www.autotrader.co.uk/car-details/202304266675832?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_cars&include-delivery-option=on&make=Audi&model=A6%20Saloon&page=1&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/van-details/202306148523378?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_vans&include-delivery-option=on&page=1&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/bike-details/202303074975713?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_bikes&include-delivery-option=on&page=1&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/motorhome-details/202212162575381?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_motorhomes&include-delivery-option=on&page=1&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/caravan-details/202306138460879?advertising-location=at_caravans&include-delivery-option=on&page=1&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/truck-details/202306128433310?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_trucks&include-delivery-option=on&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/plant-machinery-details/202304276732947?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_plants&include-delivery-option=on&postcode=E1%207DJ&fromsra",
    "https://www.autotrader.co.uk/farm-machinery-details/202305107209361?journey=YOU_MAY_ALSO_LIKE_JOURNEY&advertising-location=at_farm&include-delivery-option=on&postcode=E1%207DJ&fromsra"    
  ],
  "maxItems": 50,
  "proxy":{
    "useApifyProxy":true,
    "countryCode":"US"
  }
}


```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Autotrader UK Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Autotrader UK actor.

## Scraped Autotrader UK Output

The structure of each item in Autotrader UK looks like this:

```json
{
  "id": "202304266675832",
  "stockItemId": "8a42e6f787b806ba0187bb07b5de1998",
  "isAuction": false,
  "hoursUsed": null,
  "serviceHistory": null,
  "title": "Audi A6 40 TDI S Line 4dr S Tronic Diesel Saloon 2.0",
  "excludePreviousOwners": false,
  "advertisedLocations": [
    "at_cars",
    "at_stock_cars",
    "retailer_websites",
    "trade_advertiser_stock"
  ],
  "dueAtSeller": null,
  "motExpiry": null,
  "motInsurance": null,
  "lastServiceOdometerReadingMiles": null,
  "lastServiceDate": null,
  "warrantyMonthsOnPurchase": null,
  "twelveMonthsMotIncluded": false,
  "heading": {
    "title": "Audi A6",
    "subtitle": "40 TDI S Line 4dr S Tronic Diesel Saloon 2.0"
  },
  "attentionGrabber": "SAT NAV & Heated Seats",
  "rrp": null,
  "price": 26702,
  "priceCurrency": "£",
  "priceExcludingFees": 26702,
  "suppliedPrice": 26702,
  "suppliedPriceExcludingFees": 26702,
  "priceOnApplication": false,
  "plusVatIndicated": false,
  "vatStatus": null,
  "saving": null,
  "noAdminFees": true,
  "adminFee": null,
  "adminFeeInfoDescription": null,
  "dateOfRegistration": "2019-10-31",
  "homeDeliveryRegionCodes": null,
  "deliversToMyPostcode": null,
  "capabilities": {
    "marketExtensionHomeDelivery": null,
    "marketExtensionClickAndCollect": null,
    "marketExtensionCentrallyHeld": null,
    "marketExtensionOem": null,
    "sellerPromise": null,
    "digitalRetailing": null
  },
  "collectionLocations": null,
  "registration": "A****UJ",
  "encryptedRegistration": "TBVOkZskcDuhb+8PH+X8Z+7K18PtSVU=",
  "generation": {
    "generationId": "b1a67f706add4bdfa54b18bfe4e2addb",
    "name": "Saloon (2018 - )",
    "review": {
      "ownerReviewsSummary": {
        "aggregatedRating": 4.1,
        "countOfReviews": 2
      },
      "expertReviewSummary": {
        "rating": 4,
        "reviewUrl": "https://www.autotrader.co.uk/content/car-reviews/audi-a6-saloon-review-2018"
      }
    }
  },
  "hasShowroomProductCode": true,
  "isPartExAvailable": true,
  "isFinanceAvailable": true,
  "isFinanceFullApplicationAvailable": false,
  "financeProvider": "DEALER",
  "financeDefaults": {
    "term": "48",
    "mileage": "10000",
    "depositAmount": "2671"
  },
  "retailerId": "2669123",
  "hasClickAndCollect": true,
  "privateAdvertiser": null,
  "advertiserSegment": "Franchise",
  "dealer": {
    "dealerId": "2669123",
    "distance": null,
    "stockLevels": {
      "atStockCounts": {
        "car": 45,
        "van": null
      }
    },
    "assignedNumber": {
      "number": null
    },
    "awards": {
      "isWinner2018": false,
      "isWinner2019": false,
      "isWinner2020": false,
      "isWinner2021": false,
      "isWinner2022": false,
      "isFinalist2018": false,
      "isFinalist2019": false,
      "isFinalist2020": false,
      "isFinalist2021": false,
      "isFinalist2022": false,
      "isHighlyRated2018": false,
      "isHighlyRated2019": false,
      "isHighlyRated2020": false,
      "isHighlyRated2021": false,
      "isHighlyRated2022": false
    },
    "branding": {
      "accreditations": [],
      "brands": []
    },
    "capabilities": {
      "instantMessagingChat": {
        "enabled": true,
        "provider": "LivePersonConversationalCloud"
      },
      "instantMessagingText": {
        "enabled": true,
        "provider": "LivePersonConversationalCloud",
        "overrideSmsNumber": "+447449384898"
      }
    },
    "reviews": {
      "numberOfReviews": "84",
      "overallReviewRating": "4.6"
    },
    "location": {
      "addressOne": "26 Richfield Avenue",
      "addressTwo": null,
      "town": "Reading",
      "county": "Berkshire",
      "postcode": "RG1 8EQ",
      "latLong": "51.4632806,-0.9851001"
    },
    "marketing": {
      "profile": null,
      "brandingBanner": {
        "href": "https://dealerlogo.atcdn.co.uk/at2/adbranding/2669123/images/fpa_logo.gif"
      }
    },
    "media": {
      "email": "yes",
      "dealerWebsite": {
        "href": "https://www.vertumotors.com/autotradervehiclelocator?vehicleid=202304266675832&VRM=AF69VUJ&extref=0M4-524033"
      },
      "phoneNumber1": "(0118) 443 8739",
      "phoneNumber2": null,
      "protectedNumber": false
    },
    "name": "Reading Mercedes-Benz",
    "servicesOffered": {
      "sellerPromise": null,
      "services": [],
      "products": [
        "ADF",
        "ADVANTAGEPLUS",
        "APXV",
        "AT18FINANCECUST",
        "AT18SELLCUST",
        "AT18SL6",
        "BSPKFGMCUST",
        "BSPKFGM_PRODCAT",
        "DB01",
        "DFIN",
        "DVID",
        "FCS",
        "FPBARGAIN",
        "FPBONUS",
        "FPS",
        "ICAPI",
        "PPI_6_ULTRA",
        "PROFILE",
        "PROMOTED",
        "RETAILESSENTIALS",
        "RTLACC",
        "TOPSPOT",
        "VMET",
        "VVAL",
        "WATC",
        "WAV",
        "WDPS",
        "WDSV",
        "WFP",
        "WFPMM",
        "WICA",
        "WIMT",
        "WKSP",
        "WLGE",
        "WM01",
        "WMOS",
        "WMPS",
        "WND2",
        "WND2M",
        "WSCO",
        "WSDG",
        "WSL"
      ],
      "safeSelling": {
        "bulletPoints": [
          "Social distancing measures in place",
          "Contactless collection"
        ],
        "paragraphs": [
          "Sales safety options:",
          "o             Video appointments and vehicle tours",
          "o             Click and collect or home delivery ",
          "o             Designated collection bays with contactless handover",
          "o             Vehicles sanitised before handover",
          "o             Masks, hand sanitiser and gloves will all be used ",
          "o             Electronic payments and paperwork",
          "Aftersales safety options:",
          "o             Appointment system (customers must book aftersales appts in advance)",
          "o             Social distancing rules at all times",
          "o             Vehicles sanitised before and after working on car",
          "o             Masks, hand sanitiser and gloves will all be used ",
          "o             Electronic payments and paperwork"
        ]
      },
      "homeDelivery": {
        "bulletPoints": [
          "Detailed handover to get to know your new vehicle"
        ],
        "paragraphs": [
          "We're now able to offer safe home delivery (delivery charges apply) - or you can arrange to collect from your nearest retailer. Our advisers are available to speak to with any of your enquiries via email, live chat or telephone."
        ],
        "deliveryCostPerMile": null,
        "deliveryCostFlatFee": null,
        "freeDeliveryRadiusInMiles": null
      },
      "videoWalkAround": {
        "bulletPoints": [
          "View the vehicle from your home",
          "Arrange a time to suit you",
          "Ask our experts any questions"
        ],
        "paragraphs": null
      },
      "clickAndCollect": {
        "bulletPoints": [
          "Reserve online for £99 and use Click & Collect to order your car for collection or home delivery",
          "Our Sales teams are available online or on the phone and you can also book a virtual appointment",
          "Handovers will be Covid-safe and we offer a 14-day money-back guarantee on all used cars"
        ],
        "paragraphs": [
          "Our aftersales departments will remain open, with bookings still being taken for MOTs and Services"
        ]
      },
      "buyOnline": null,
      "nccApproved": false,
      "isHomeDeliveryProductEnabled": false,
      "isPartExAvailable": true,
      "hasSafeSelling": true,
      "hasHomeDelivery": true,
      "hasVideoWalkAround": true,
      "additionalLinks": null
    }
  },
  "video": {
    "url": "https://autotrader.aos.tv/iframe/pIoRDONBL-2hQmrWiahvmkJwT2UFwGBepP4m3F855A0=",
    "preview": null
  },
  "spin": null,
  "imageList": {
    "nextCursor": null,
    "size": 46,
    "images": [
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/22933d70b3c3408ab8ad88b4b2dfc397.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/fe9c637574a042d7bc0509b479869128.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/8895159d5997499181b0d5d984f3f9c3.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/d77fed9f5873401ea37b17d5251f9d4e.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/20ef4eaf986c4abbaef46bf366b644c0.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/189e5bf4070748e598628242513ec5dd.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/7eb1d62b21f0493d9f964e2e9c71c08b.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/d723e15c817e4744981f02e89067aae3.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/96cd0c267a71462eb78dac613f26e687.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e4c6aeb5c2f4483c86e13f2f38e58a65.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/a4cb6a1138c64c09ae10ad0ebbfe736c.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/ef4b38cecbae4840a839ee97fe142761.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/7fa629a511b449349152f8ba41d1e054.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e7f1ad6d6ccf4186a47f105ad01d555e.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/7d7297decb934ebdb48fc5dac1ebdec6.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/bfcd2015ac83489aa3f52f436137354e.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/9a3ea23e1eaa48ef96051813a1f915e2.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/f7f1feef42174b05ac88a28caf1797ba.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/da1ff1a55a6e481e9b8775e2e8d4d42c.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/dae1b7e03cd44d4c8a8d9f0d74ddac18.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/2f41297b07564a368dd3f9cd5d40e9f1.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/fda40ccc91534f55981c55abbd73ac7a.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/cdadd47a9cd84e80a3f2cf1004fa7289.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/d62a08b3e6d8488596aa91401c11fbe1.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/9c5ec698a61f4787907f2e019932ace3.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e0a484776a6b4a65837fd63006dac556.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e115e9f490dc45ca98d9f28ad6fdfdd6.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/f3fe9e7bca6e4b3eb7440dc5e90f0af3.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/eb6176ef78b54271ad5cfa338e4d8b53.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/901e6438474e424cb3e9128c3117fe6e.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/bdc45cf59fd943a2bf7ec61feaf4f3c8.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/f6205fd5158d4e889b7ff595813a9f96.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/c119dc152e1348c38974cefc75fbbfec.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/a694fe21312a4fe5a82886f63f109956.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/9397659a94f24b95ba6d78ab7f04a28a.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e54eba27c6b040b0a556d2cff0fa519d.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/ad3448cb69904b2d80959b04afc89b18.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/b76395fb84eb45258a76b898d7444bb8.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/d16c0555ddd24a73924760b5e1164d6c.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/98164d409afd40db864c0a8f38018751.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/a2b623f4f7de4d4bb8604786aee03879.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e077e9e9ba09440e9b4bb591dba17e8d.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/e1d6fafcb38b4e88be477d7559175cac.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/8e4110ca5d864eeca8547d4cfb9f2a74.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/b5af2dfa55d942989846b7f39f147c02.jpg",
        "templated": true,
        "autotraderAllocated": false
      },
      {
        "url": "https://m.atcdn.co.uk/a/media/{resize}/114ac1df7f654cd8aa0bbf8573b657a4.jpg",
        "templated": true,
        "autotraderAllocated": false
      }
    ]
  },
  "priceIndicatorRating": "GREAT",
  "priceIndicatorRatingLabel": "Great price",
  "priceDeviation": -1072,
  "mileageDeviation": -4153,
  "mileage": {
    "mileage": 32283,
    "unit": "MILE"
  },
  "plate": "69",
  "year": 2019,
  "vehicleCheckId": null,
  "vehicleCheckStatus": "PASSED",
  "vehicleCheckSummary": {
    "type": "BASIC",
    "title": "5 checks passed",
    "performed": null,
    "writeOffCategory": null,
    "checks": [
      {
        "key": "STOLEN",
        "failed": false,
        "advisory": false,
        "critical": true,
        "warning": false
      },
      {
        "key": "SCRAPPED",
        "failed": false,
        "advisory": false,
        "critical": true,
        "warning": false
      },
      {
        "key": "WRITE_OFF_CATEGORY",
        "failed": false,
        "advisory": false,
        "critical": true,
        "warning": false
      },
      {
        "key": "IMPORTED",
        "failed": false,
        "advisory": false,
        "critical": true,
        "warning": false
      },
      {
        "key": "EXPORTED",
        "failed": false,
        "advisory": false,
        "critical": true,
        "warning": false
      }
    ]
  },
  "sellerName": "Reading Mercedes-Benz",
  "sellerType": "Trade",
  "sellerProducts": [
    "ADF",
    "ADVANTAGEPLUS",
    "APXV",
    "AT18FINANCECUST",
    "AT18SELLCUST",
    "AT18SL6",
    "BSPKFGMCUST",
    "BSPKFGM_PRODCAT",
    "DB01",
    "DFIN",
    "DVID",
    "FCS",
    "FPBARGAIN",
    "FPBONUS",
    "FPS",
    "ICAPI",
    "PPI_6_ULTRA",
    "PROFILE",
    "PROMOTED",
    "RETAILESSENTIALS",
    "RTLACC",
    "TOPSPOT",
    "VMET",
    "VVAL",
    "WATC",
    "WAV",
    "WDPS",
    "WDSV",
    "WFP",
    "WFPMM",
    "WICA",
    "WIMT",
    "WKSP",
    "WLGE",
    "WM01",
    "WMOS",
    "WMPS",
    "WND2",
    "WND2M",
    "WSCO",
    "WSDG",
    "WSL"
  ],
  "sellerLocation": "READING",
  "sellerLocationDistance": {
    "unit": "M",
    "value": 40
  },
  "sellerContact": {
    "phoneNumberOne": "(0118) 443 8739",
    "phoneNumberTwo": null,
    "protectedNumber": null,
    "byEmail": true
  },
  "description": "Looking for a luxurious and spacious car that offers unparalleled safety, comfort, and technology? Look no further than the Audi A6 Diesel Saloon 40 TDI S Line!, , This stunning car has just 32,283 miles on the clock and was manufactured in 2019. It comes packed with features that are sure to delight any driver or passenger, including a reverse camera, parking sensors, electric seats, and much more., , One of the standout features of the Audi A6 Diesel Saloon 40 TDI S Line is its spacious interior, which offers ample room for passengers and cargo alike. Whether you're heading out on a long road trip or just running errands around town, you'll appreciate the comfortable and roomy cabin., , The reverse camera and parking sensors are also a huge plus, making it easy to navigate even the tightest parking spots without worry. And with electric seats, you can easily adjust your position for maximum comfort, whether you're driving for a few minutes or a few hours., , And if you're looking to buy this car, there's no better place to do it than Vertu Mercedes-Benz of Reading. With our manufacturer trained technicians and comprehensive warranty, you can buy with confidence, knowing that your car is in the best possible hands., , So if you're in the market for a luxurious and technologically advanced car that offers unbeatable comfort, safety, and space, look no further than the Audi A6 Diesel Saloon 40 TDI S Line. Come visit us at Vertu Mercedes-Benz of Reading and take a test drive today! White, £26,702",
  "colour": "White",
  "manufacturerApproved": false,
  "insuranceWriteOffCategory": null,
  "owners": null,
  "vehicleCondition": null,
  "specification": {
    "isCrossover": false,
    "operatingType": null,
    "emissionClass": "Euro 6",
    "co2Emissions": {
      "co2Emission": 146,
      "unit": "g/km"
    },
    "topSpeed": {
      "topSpeed": 152
    },
    "minimumKerbWeight": {
      "weight": null,
      "unit": null
    },
    "endLayout": null,
    "trailerAxleNumber": null,
    "bedroomLayout": null,
    "grossVehicleWeight": {
      "weight": null,
      "unit": null
    },
    "capacityWeight": {
      "weight": null,
      "unit": null
    },
    "liftingCapacity": {
      "weight": null,
      "unit": null
    },
    "operatingWidth": {
      "width": null,
      "unit": null
    },
    "maxReach": {
      "length": null,
      "unit": null
    },
    "wheelbase": "STD",
    "berth": null,
    "bedrooms": null,
    "engine": {
      "power": {
        "enginePower": 204,
        "unit": "PS"
      },
      "sizeLitres": 2,
      "sizeCC": 1968,
      "manufacturerEngineSize": 2
    },
    "exteriorWidth": {
      "width": 2110,
      "unit": "mm"
    },
    "exteriorLength": {
      "length": 4939,
      "unit": "mm"
    },
    "exteriorHeight": {
      "height": 1457,
      "unit": "mm"
    },
    "capacityWidth": {
      "width": null,
      "unit": null
    },
    "capacityLength": {
      "length": null,
      "unit": null
    },
    "capacityHeight": {
      "height": null,
      "unit": null
    },
    "seats": 5,
    "axleConfig": null,
    "ulezCompliant": true,
    "doors": 4,
    "bodyType": "Saloon",
    "cabType": "Unlisted",
    "rawBodyType": "Saloon",
    "fuel": "Diesel",
    "transmission": "Automatic",
    "style": null,
    "subStyle": null,
    "make": "Audi",
    "model": "A6 Saloon",
    "trim": "S line",
    "vehicleCategory": "Car",
    "optionalFeatures": [
      {
        "description": "Door Mirrors - Electrically Adjustable - Heated and Folding - Automatically Dimming - with Driver Memory",
        "category": "Optional"
      },
      {
        "description": "Leather-Alcantara - Sport Seats with S Embossed Logo - Black with Rock Grey Stitching",
        "category": "Optional"
      }
    ],
    "standardFeatures": [
      {
        "description": "S line front and rear floor mats with contrast stitching",
        "category": "Standard"
      },
      {
        "description": "Heat insulating glass in side and rear windows",
        "category": "Standard"
      },
      {
        "description": "EBD - Electronic brakeforce distribution",
        "category": "Standard"
      },
      {
        "description": "Voice control system",
        "category": "Standard"
      },
      {
        "description": "Electro-mechanical PAS",
        "category": "Standard"
      },
      {
        "description": "Automatic start/stop system with coasting functionality",
        "category": "Standard"
      },
      {
        "description": "7\" high resolution colour driver information display system",
        "category": "Standard"
      },
      {
        "description": "Frameless auto dimming interior rear view mirror",
        "category": "Standard"
      },
      {
        "description": "Diesel particulate filter",
        "category": "Standard"
      },
      {
        "description": "DAB Digital radio",
        "category": "Standard"
      },
      {
        "description": "Matt black side air intake grille with inlay in matt aluminium",
        "category": "Standard"
      },
      {
        "description": "LED signature front daytime running light",
        "category": "Standard"
      },
      {
        "description": "Auxiliary heater",
        "category": "Standard"
      },
      {
        "description": "Progressive steering",
        "category": "Standard"
      },
      {
        "description": "Non smoking pack - A6",
        "category": "Standard"
      },
      {
        "description": "Audi connect safety and service (e-call)",
        "category": "Standard"
      },
      {
        "description": "40/20/40 split folding 3 rear seat bench in 3 parts with rear centre armrest",
        "category": "Standard"
      },
      {
        "description": "Keyless Go",
        "category": "Standard"
      },
      {
        "description": "Illuminated sun visors with vanity mirrors",
        "category": "Standard"
      }
    ],
    "driverPosition": "Unlisted",
    "battery": null,
    "techData": {
      "co2Emissions": "146 g/km",
      "fuelConsumptionCombined": "50.40 mpg",
      "fuelConsumptionExtraUrban": null,
      "fuelConsumptionUrban": null,
      "insuranceGroup": "32E",
      "minimumKerbWeight": "1645 kg",
      "zeroToSixtyMph": null,
      "zeroToSixtyTwoMph": "8.10 seconds",
      "cylinders": "4",
      "valves": "16",
      "enginePower": "201 bhp",
      "topSpeed": "152 mph",
      "engineTorque": "295.00 lbs/ft",
      "vehicleHeight": "1457 mm",
      "vehicleLength": "4939 mm",
      "vehicleWidth": "2110 mm",
      "wheelbase": "2924 mm",
      "fuelTankCapacity": "63.00 litres",
      "grossVehicleWeight": "2255 kg",
      "luggageCapacitySeatsDown": "995 litres",
      "bootspaceSeatsUp": "530 litres",
      "vehicleWidthInclMirrors": null,
      "maxLoadingWeight": null,
      "standardFeatures": [
        {
          "description": "19in Alloy Wheels - 5 Twin Spoke Design in Contrast Grey - Partly Polished",
          "category": "Exterior"
        },
        {
          "description": "4-Way Electric Lumbar Support",
          "category": "Interior"
        },
        {
          "description": "AMI - Audi Music Interface",
          "category": "Audio and Communications"
        },
        {
          "description": "Airbags - Driver",
          "category": "Safety and Security"
        },
        {
          "description": "Airbags - Front Passenger",
          "category": "Safety and Security"
        },
        {
          "description": "Amazon Alexa Integration - Part of Connect Navigation and Information Plus",
          "category": "Audio and Communications"
        },
        {
          "description": "Anti Theft Locking Wheel Bolts and Wheel Loosening Detection",
          "category": "Exterior"
        },
        {
          "description": "Anti-Theft Alarm with Tow-Away Protection",
          "category": "Safety and Security"
        },
        {
          "description": "Audi Connect Safety and Service - e-call",
          "category": "Audio and Communications"
        },
        {
          "description": "Audi Pre-Sense Front",
          "category": "Safety and Security"
        },
        {
          "description": "Audi Smartphone Interface",
          "category": "Audio and Communications"
        },
        {
          "description": "Auto Dimming and Frameless Rear View Mirror",
          "category": "Interior"
        },
        {
          "description": "Bluetooth Interface",
          "category": "Audio and Communications"
        },
        {
          "description": "Body Coloured Door Mirrors",
          "category": "Exterior"
        },
        {
          "description": "Colour Drivers Information System with 7in High-Resolution TFT Screen",
          "category": "Drivers Assistance"
        },
        {
          "description": "Cruise Control System with Speed Limiter",
          "category": "Drivers Assistance"
        },
        {
          "description": "DAB Digital Radio",
          "category": "Audio and Communications"
        },
        {
          "description": "Deluxe 2-Zone Electronic Climate Control",
          "category": "Interior"
        },
        {
          "description": "Door Mirrors - Electrically Adjustable - Heated and Folding with Memory Function and Integrated LED Indicator",
          "category": "Exterior"
        },
        {
          "description": "ESC - Electronic Stabilisation Control inc ABS - ASR and EDL",
          "category": "Safety and Security"
        },
        {
          "description": "Electric Windows - Front and Rear",
          "category": "Exterior"
        },
        {
          "description": "Electrically Adjustable Front Seats with Memory Function for Drivers Side",
          "category": "Interior"
        },
        {
          "description": "Electromechanical Parking Brake",
          "category": "Safety and Security"
        },
        {
          "description": "Extended Pedestrian Protection Measures",
          "category": "Safety and Security"
        },
        {
          "description": "First Aid Kit and Warning Triangle",
          "category": "Safety and Security"
        },
        {
          "description": "Front Centre Armrest",
          "category": "Interior"
        },
        {
          "description": "Front Sports Seats",
          "category": "Interior"
        },
        {
          "description": "Front and Rear Side Airbags with Head Airbag System",
          "category": "Safety and Security"
        },
        {
          "description": "Headlight Washers",
          "category": "Illumination"
        },
        {
          "description": "Heated Front Seats",
          "category": "Interior"
        },
        {
          "description": "ISOFIX Child Seat Mounting and Top Tether - Front Passenger Airbag Deactivation",
          "category": "Safety and Security"
        },
        {
          "description": "Keyless Go",
          "category": "Interior"
        },
        {
          "description": "Lane Departure Warning",
          "category": "Drivers Assistance"
        },
        {
          "description": "Leatherette Upper Instrument Panel and Door Shoulders",
          "category": "Interior"
        },
        {
          "description": "Light and Rain Sensor",
          "category": "Illumination"
        },
        {
          "description": "Luggage Compartment Floor",
          "category": "Interior"
        },
        {
          "description": "MMI Navigation with MMI Touch",
          "category": "Audio and Communications"
        },
        {
          "description": "Matrix LED Headlights with Signature Front Daytime Running Light",
          "category": "Illumination"
        },
        {
          "description": "Parking System Plus - Front and Rear Sensors",
          "category": "Drivers Assistance"
        },
        {
          "description": "Privacy Glass",
          "category": "Exterior"
        },
        {
          "description": "Progressive Steering",
          "category": "Performance"
        },
        {
          "description": "Rear-View Camera",
          "category": "Drivers Assistance"
        },
        {
          "description": "S Line Front and Rear Bumpers",
          "category": "Exterior"
        },
        {
          "description": "S Line Side Skirts",
          "category": "Exterior"
        },
        {
          "description": "S line Front and Rear Floor Mats with Contrast Stitching",
          "category": "Interior"
        },
        {
          "description": "S line Rear Diffuser and Grille in Matt Black with Matt Aluminium Tailpipes",
          "category": "Exterior"
        },
        {
          "description": "Seat Belt Monitoring",
          "category": "Safety and Security"
        },
        {
          "description": "Side and Rear Windows in Heat-Insulating Glass",
          "category": "Exterior"
        },
        {
          "description": "Signature Rear LED Light Design",
          "category": "Illumination"
        },
        {
          "description": "Sport Suspension",
          "category": "Performance"
        },
        {
          "description": "Steering Wheel - 3-Spoke Multi-Function Perforated Leather Steering Wheel with Contrast Stitching and Shift Paddles",
          "category": "Interior"
        },
        {
          "description": "Tool Kit and Car Jack",
          "category": "Interior"
        },
        {
          "description": "Tyre Pressure Warning Light",
          "category": "Drivers Assistance"
        },
        {
          "description": "Tyre Repair Kit",
          "category": "Exterior"
        },
        {
          "description": "Voice Control System",
          "category": "Drivers Assistance"
        },
        {
          "description": "Windscreen with Acoustic Glazing",
          "category": "Exterior"
        }
      ],
      "chargingData": null
    },
    "annualTax": {
      "standardRate": 180
    },
    "oemDrivetrain": null,
    "bikeLicenceType": null,
    "derivative": "2.0 TDI 40 S line S Tronic Euro 6 (s/s) 4dr",
    "derivativeId": "ef6e5d179170478181f261447b443945"
  },
  "stockType": "physical-stock",
  "versionNumber": "70",
  "tradeLifecycleStatus": "FORECOURT",
  "condition": "Used",
  "finance": null,
  "locationArea": {
    "code": "e17",
    "region": "londoneastwest",
    "areaOfInterest": {
      "postCode": "E1 7",
      "manufacturerCodes": [
        "PEU005",
        "HYU110",
        "FIA042",
        "LEX049",
        "MIN114",
        "BMW116",
        "ISU049",
        "FER007",
        "JAG074",
        "VWA001"
      ]
    }
  },
  "reservation": {
    "status": null,
    "eligibility": "NOT_ELIGIBLE",
    "feeCurrency": "GBP",
    "feeInFractionalUnits": 0
  },
  "url": "https://www.autotrader.co.uk/car-details/202304266675832?journey=FEATURED_LISTING_JOURNEY&advertising-location=at_cars&include-delivery-option=on&make=Audi&model=A6%20Saloon&page=1&postcode=E1%207DJ&fromsra"
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
