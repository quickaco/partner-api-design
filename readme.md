# QuickaPay Partner API Design

All API endpoints are relative to the API Base URL (BASE_URL) which is currently:
`https://my.quicka.co/v1/`

## Security

You will be provided a partner key that _must_ be used for all partner originated requests:

`curl -H 'Accept: application/json' -H "Authorization: Bearer ${PARTNER_TOKEN}" "$BASEURL/{endpoint}"`

We reserve the right to suspend your token should abuse (subject to good faith agreement) be detected. 

## Webhooks

Partners _must_ specify their preferred webhook endpoint as part of commercials.
This endpoint is where the QuickaPay engine will return updates on submerchant onboarding to.

## APIs

* [Creating a submerchant](create-merchant.md)
* [Recheck submerchant status](check-merchant-status.md)
* [Verifying submerchant access keys](verify-merchant-keys.md)
