# Nager.AmazonCreatorsApi

A lightweight and easy-to-use .NET client for the **Amazon Creators API**.

`Nager.AmazonCreatorsApi` simplifies authentication and sending requests to the Amazon Creators API.
Currently, the package supports **GetItems** requests to retrieve product data.

## ✨ Features

* Simple authentication workflow
* Strongly-typed request and response models
* Easy-to-use `GetItems` implementation
* Built for modern .NET applications
* Minimal dependencies

## License Key Logic

The `Nager.AmazonCreatorsApi` uses a hybrid access model. While basic product metadata is accessible for free, any requests involving pricing, savings, or availability data require a valid License Key.

### Feature Access Overview

| Category             | Access           | Resource Scope           | Example Fields                         |
| :------------------- | :--------------: | :----------------------- | :------------------------------------- |
| **Basic Metadata**   | 🔓 **Free**     | `AmazonFields.ItemInfo.*` | Title, Features, ...                  |
| **Media Assets**     | 🔓 **Free**     | `AmazonFields.Images.*`   | Primary, Variants                     |
| **Pricing & Offers** | 🔐 **License**  | `AmazonFields.Offers.*`   | **Price, Availability, MerchantInfo** |

## Deprecation Notice: PA-API (Feb 2, 2026)

> [!IMPORTANT]  
> The **Product Advertising API (PA-API)** will be **deprecated on April 30, 2026**.  
> This project has been renamed and updated to support the **new Amazon Creators API**.

> ⚠️ The old PA-API documentation is no longer maintained and contains outdated information.  
> Please refer to the official Creators API documentation:  
> [https://affiliate-program.amazon.com/creatorsapi/docs/en-us/introduction](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/introduction)

**Action Required:** If you are still using PA-API, migrate your integration to the Creators API before the deprecation date.

## Installation
The package is available on [NuGet](https://www.nuget.org/packages/Nager.AmazonCreatorsApi)
```powershell
PM> install-package Nager.AmazonCreatorsApi
```

## 🚀 Getting Started

### GetItems

Retrieve detailed product data using ASINs.

```cs
var clientId = "YOUR_CLIENT_ID";
var clientSecret = "YOUR_CLIENT_SECRET";
var partnerTag = "YOUR_PARTNER_TAG";

var client = new AmazonCreatorsApiClient(new HttpClient());
if (!await client.AuthenticateAsync(AmazonEndpoint.US, clientId, clientSecret))
{
    Console.WriteLine("Cannot Authenticate");
    return;
}

var itemRequest = new ItemsRequest
{
    ItemIds = new string[] { "B09B2SBHQK", "B09B8V1LZ3" },
    PartnerTag = partnerTag,
    Resources = new string[]
    {
        AmazonFields.ParentASIN,
        AmazonFields.ItemInfo.Title,
    }
};

try
{
    var itemResponse = await client.GetItemsAsync(itemRequest);
}
catch (RequestException exception)
{
    var amazonErrorMessage = exception.ErrorResponse.Message;
}
catch (Exception exception)
{
}
```

### Global Marketplaces

Switching the target marketplace is a one-liner. This automatically adjusts the base URL for all subsequent requests.

```cs
client.ChangeMarketplace(AmazonEndpoint.DE); // Germany
client.ChangeMarketplace(AmazonEndpoint.JP); // Japan
client.ChangeMarketplace(AmazonEndpoint.BR); // Brazil
```

### Set LicenseKey

You can set your license key globally on the client class. This key is required if you plan to request any resources from the `Offers` scope.

```cs
AmazonCreatorsApiClient.LicenseKey = "YOUR_NAGER_LICENSE_KEY";
```

## 📚 Resources

Full resource documentation:
👉 [Resources.md](./Resources.md)
