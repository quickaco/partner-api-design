# QuickaPay Partner API Design

All API endpoints are relative to the API Base URL (BASE_URL) which is currently:
`https://my.quicka.co/v1/`

## Security

You will be provided a partner key that _must_ be used for all partner originated requests:

`curl -H 'Accept: application/json' -H "Authorization: Bearer ${PARTNER_TOKEN}" "$BASEURL/{endpoint}"`

We reserve the right to suspend your token should abuse (subject to good faith agreement) be detected. 

## Webhooks

Partners _must_ specify their preferred webhook endpoint as part of commercials.
This endpoint is where the QuickaPay engine will return updates on the business being onboarding to.

## APIs

* [Creating a business](create-business.md)
* [Recheck business status](check-business-status.md)
* [Verifying business access keys](verify-business-keys.md)
