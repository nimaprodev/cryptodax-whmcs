# CryptoDAX Payment Gateway for WHMCS

Accept crypto payments in WHMCS with [CryptoDAX](https://pay.cryptodax.io). This module adds CryptoDAX as a payment gateway for WHMCS 7 and 8.

## Requirements

- WHMCS 7 or 8
- A CryptoDAX API Key and API URL

## Installation

1. Download or clone this repository.
2. Copy the `modules` folder into your WHMCS root directory.
3. In the WHMCS admin area, go to **Setup > Payments > Payment Gateways**.
4. Enable **CryptoDAX**.
5. Enter your API Key and API URL.

## Currency

The CryptoDAX API accepts USD only. If your customers are not billed in USD, set **Convert To For Processing** to USD in the gateway settings.

## Webhook

The module automatically sends this webhook address as `callback_url`:

```text
https://YOUR-WHMCS/modules/gateways/callback/cryptodax.php
```

Replace `YOUR-WHMCS` with your WHMCS address when testing or checking the URL.

## Payment Verification

Webhook data is not trusted on its own. Before a payment is recorded, the module:

- Verifies the payment again through the API using `/v1/invoices/{id}` and `/v1/merchant/payment/{id}`
- Checks that the `tx_hash` belongs to a transaction on the same invoice
- Requires the payment status to be `paid` or `overpaid`
- Does not record a duplicate `tx_hash` again

## Related Resources

- [CryptoDAX website](https://pay.cryptodax.io)
- [Python API examples](https://github.com/Crypto-DAX/python-examples)

## Support

For help with this module, [open an issue](https://github.com/Crypto-DAX/cryptodax-whmcs/issues).

## License

[Add your license here, for example MIT.]