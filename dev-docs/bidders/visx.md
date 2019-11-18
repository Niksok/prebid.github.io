---
layout: bidder
title: VIS.X
description: Prebid VIS.X Bidder Adaptor
hide: true
biddercode: visx
gdpr_supported: true
---

### Note
To be able to use the full bandwidth of VIS.X high impact ad products, we strongly recommend disabling SafeFrames:
- If you are using Google Ad Manager (GAM), make sure the “Serve in Safeframe” box in creative settings is unchecked,
- If you are using AppNexus Seller Tag, make sure the enableSafeFrame parameter is set to False.

If you require SafeFrames to be activated, please reach out to your YOC account manager to obtain further details.

The YOC VIS.X adaptor requires setup and approval from your YOC account manager team, even for existing YOC publishers. Please reach out to your account manager to enable Prebid.js for your account.

### Bid params

{: .table .table-bordered .table-striped }
| Name        | Scope    | Description                                                                                                                                                                                                                                 | Example    | Type     |
|-------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|----------|
| `uid`       | required | The publisher's ad unit ID in VIS.X                                                                                                                                                                                                         | `'903536'` | `string` |

### Configuration

The VIS.X adaptor has the ability to work in different currencies. Currently this adaptor supports `'EUR'`, `'USD'`, `'GBP'`, `'PLN'`. Defaults to `'EUR'`.
If you would like to get bids in a currency different from EUR, you should make some settings. 
​
1. Set the Curreny module.
http://prebid.org/dev-docs/modules/currency.html
​
​
2. Setup the currency in Currency config.
For example:
​
```javascript
pbjs.setConfig({
    "currency": {
        "adServerCurrency": "GBP",
	"bidderCurrencyDefault": {"visx": "USD"}
    }
});
```
​
where:
`"adServerCurrency"` - default currency for ad server.
`"bidderCurrencyDefault"` - currency that is used for particular bidder. 
​
In example from the above for bids in USD the currency will be converted into GBP.
​
Take into account that:
- If you set only `"adServerCurrency"` value - this default ad server value will be used for Visx adapter.
- If you set no currency - the default prebid currency value will be used, it is EUR.
- You should not set `"bidderCurrencyDefault"` parameter without `"adServerCurrency"` one.
- Don't set unsupported currency values. If the currency is not from the list of supported currencies, the request will be rejected.