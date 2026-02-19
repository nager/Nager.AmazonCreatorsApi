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

Retrieve product information using ASINs:

```cs
var clientId = "";
var clientSecret = "";
var partnerTag = "";

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

var itemResponse = await client.GetItemsAsync(itemRequest);
```

## 📚 Resources

Full resource documentation:
👉 [Resources.md](./Resources.md)
