These constants map directly to the official Creators API resource paths and prevent the use of magic strings.

# Why Use AmazonFields?

* Avoid magic strings
* Compile-time safety
* IntelliSense support
* Cleaner request building
* Easier future API updates

## Usage Example

```csharp
var request = new AmazonRequest
{
    Resources = new[]
    {
        AmazonFields.ItemInfo.Title,
        AmazonFields.Images.Primary.Large,
        AmazonFields.Offers.Listings.Price,
        AmazonFields.CustomerReviews.StarRating
    }
};
```

# ItemInfo

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/item-info](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/item-info)

Contains general product metadata such as title, brand, features, technical details and identifiers.

| Constant                                | Resource Path              |
| --------------------------------------- | -------------------------- |
| `AmazonFields.ItemInfo.ExternalIds`     | `itemInfo.externalIds`     |
| `AmazonFields.ItemInfo.Classifications` | `itemInfo.classifications` |
| `AmazonFields.ItemInfo.ManufactureInfo` | `itemInfo.manufactureInfo` |
| `AmazonFields.ItemInfo.ByLineInfo`      | `itemInfo.byLineInfo`      |
| `AmazonFields.ItemInfo.ContentRating`   | `itemInfo.contentRating`   |
| `AmazonFields.ItemInfo.TradeInInfo`     | `itemInfo.tradeInInfo`     |
| `AmazonFields.ItemInfo.Features`        | `itemInfo.features`        |
| `AmazonFields.ItemInfo.Title`           | `itemInfo.title`           |
| `AmazonFields.ItemInfo.ProductInfo`     | `itemInfo.productInfo`     |
| `AmazonFields.ItemInfo.ContentInfo`     | `itemInfo.contentInfo`     |
| `AmazonFields.ItemInfo.TechnicalInfo`   | `itemInfo.technicalInfo`   |

# Images

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/images](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/images)

Provides primary and variant product images in different resolutions.

## Primary Images

| Constant                             | Resource Path           |
| ------------------------------------ | ----------------------- |
| `AmazonFields.Images.Primary.Small`  | `images.primary.small`  |
| `AmazonFields.Images.Primary.Medium` | `images.primary.medium` |
| `AmazonFields.Images.Primary.Large`  | `images.primary.large`  |

## Variant Images

| Constant                              | Resource Path            |
| ------------------------------------- | ------------------------ |
| `AmazonFields.Images.Variants.Small`  | `images.variants.small`  |
| `AmazonFields.Images.Variants.Medium` | `images.variants.medium` |
| `AmazonFields.Images.Variants.Large`  | `images.variants.large`  |

# OffersV2

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/offersV2](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/offersV2)

Contains pricing, merchant, availability and deal information.

## Listings

| Constant                                      | Resource Path                      |
| --------------------------------------------- | ---------------------------------- |
| `AmazonFields.Offers.Listings.Price`          | `offersV2.listings.price`          |
| `AmazonFields.Offers.Listings.LoyaltyPoints`  | `offersV2.listings.loyaltyPoints`  |
| `AmazonFields.Offers.Listings.IsBuyBoxWinner` | `offersV2.listings.isBuyBoxWinner` |
| `AmazonFields.Offers.Listings.DealDetails`    | `offersV2.listings.dealDetails`    |
| `AmazonFields.Offers.Listings.Condition`      | `offersV2.listings.condition`      |
| `AmazonFields.Offers.Listings.MerchantInfo`   | `offersV2.listings.merchantInfo`   |
| `AmazonFields.Offers.Listings.Type`           | `offersV2.listings.type`           |
| `AmazonFields.Offers.Listings.Availability`   | `offersV2.listings.availability`   |

# Parent ASIN

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/parent-asin](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/parent-asin)

Used to retrieve the parent ASIN of a variation item.

| Constant                  | Resource Path |
| ------------------------- | ------------- |
| `AmazonFields.ParentASIN` | `parentASIN`  |

# BrowseNodeInfo

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/browse-node-info](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/browse-node-info)

Contains category and ranking information.

| Constant                                       | Resource Path                          |
| ---------------------------------------------- | -------------------------------------- |
| `AmazonFields.BrowseNodeInfo.BrowseNodes`      | `browseNodeInfo.browseNodes`           |
| `AmazonFields.BrowseNodeInfo.Ancestor`         | `browseNodeInfo.browseNodes.ancestor`  |
| `AmazonFields.BrowseNodeInfo.SalesRank`        | `browseNodeInfo.browseNodes.salesRank` |
| `AmazonFields.BrowseNodeInfo.WebsiteSalesRank` | `browseNodeInfo.websiteSalesRank`      |

# BrowseNodes

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/browse-nodes](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/browse-nodes)

Provides detailed information about specific browse nodes.

> Note: These are returned when explicitly requested via the browse node resources.

# Search Refinements

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/search-refinements](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/search-refinements)

Provides refinement data when performing search requests (e.g. brand filters, price ranges, categories).

> Currently not wrapped in `AmazonFields` constants.
> Can be added manually as resource strings if required.

# Variation Summary

Official reference:
[https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/variation-summary](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/api-reference/resources/variation-summary)

Provides high-level information about product variations.

> Currently not wrapped in `AmazonFields` constants.
> Can be added manually as resource strings if required.

# CustomerReviews

Provides aggregated review information.

| Constant                                  | Resource Path                |
| ----------------------------------------- | ---------------------------- |
| `AmazonFields.CustomerReviews.StarRating` | `customerReviews.starRating` |
| `AmazonFields.CustomerReviews.Count`      | `customerReviews.count`      |
