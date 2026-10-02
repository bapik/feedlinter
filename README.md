# Product Feed Quality Checklist for Google Merchant Center

This guide is a practical first pass for reviewing an XML product feed before submitting it to Google Merchant Center. Requirements can vary by destination, country, and product type, so use Google's current specification for the final checks.

## Review each product record

- **Parse the feed.** Confirm the XML is well formed, uses the correct format and namespaces, and includes every product record you expect to send.
- **Keep product IDs stable and unique.** Use the same ID for the same product on later updates. Give each separately submitted variant its own ID.
- **Describe the product accurately.** Check that `title` and `description` identify the item and agree with its product page.
- **Check product and image URLs.** `link` should open the relevant product page; `image_link` should open that product's main image. Make sure both URLs work and can be crawled.
- **Match price and availability.** Format `price` with an amount and ISO currency code, such as `59.90 PLN`. Use a supported `availability` value (`in_stock`, `out_of_stock`, `preorder`, or `backorder`) and keep it aligned with the product page and checkout.
- **Use real product identifiers.** Submit the manufacturer's GTIN when one is assigned and required. Provide `brand` and `mpn` where applicable. Never make up a GTIN to fill a blank field.
- **Review variants and conditional fields.** Apply the current rules for `item_group_id`, `condition`, and other attributes to the product type and destination.

## Minimal RSS example

This illustrative record shows common fields. Replace the example URLs and values with real product data, then check the current specification for any additional fields your products require.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:g="http://base.google.com/ns/1.0">
  <channel>
    <title>Example store</title>
    <link>https://store.example/</link>
    <description>Example product feed</description>
    <item>
      <g:id>SKU-001</g:id>
      <g:title>Stainless steel kettle, 1.5 L</g:title>
      <g:description>Electric kettle with a 1.5 L capacity.</g:description>
      <g:link>https://store.example/products/kettle</g:link>
      <g:image_link>https://store.example/images/kettle.jpg</g:image_link>
      <g:price>59.90 PLN</g:price>
      <g:availability>in_stock</g:availability>
    </item>
  </channel>
</rss>
```

## After the feed is submitted

Check Merchant Center diagnostics after processing. A clean feed can reduce data errors, but it does not guarantee approval: Google may also review product policies, the store website, and account settings.

## Polski skrót

Przed wysłaniem sprawdź, czy XML jest poprawny, a każdy produkt ma stabilne ID, dokładny tytuł i opis, działający adres produktu i zdjęcia oraz cenę i dostępność zgodne ze stroną sklepu. Używaj prawdziwych identyfikatorów producenta; nie dopisuj fikcyjnych GTIN-ów. Wymagania zależą od rynku, miejsca wyświetlania i rodzaju produktu, więc po przetworzeniu feedu sprawdź też diagnostykę Merchant Center.

## Official references

- [Google Merchant Center product data specification](https://support.google.com/merchants/answer/7052112?hl=en)
- [Google guidance on unique product identifiers](https://support.google.com/merchants/answer/160161?hl=en)
- [Google guidance on high-quality product data](https://support.google.com/merchants/answer/188489?hl=en)

Feedlinter maintains this checklist. To run a first-pass review of a public XML feed, use the [free Feedlinter audit](https://feedlinter.com/audit).
