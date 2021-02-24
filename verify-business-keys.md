
## Verify a Business Access Keys

Verifies the validity of an onboarded business's access keys.
This is useful if you need to ensure they are copying/pasting them correctly from
their QuickaPay dashboard

### URL

  `/partner/check-business`

### Method

  `POST`

### Data Payload

```json
{
  "business_id": "00000000-0000-0000-0000-000000000000",
  "access_key": "$2y$12$0AuijE2G2w3H2J74A4nnt.1Z/SOMETHING/COOL"
}
```

### Example snippit

```bash

curl --location --request POST 'https://my.quicka.co/v1/partner/check-business' \
--header 'Authorization: Bearer ${PARTNER_TOKEN}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "business_id": "${BUSINESS_UUID}",
    "access_key": "${BUSINESS_ACCESS_KEY}"
}'


```

### Success Response

  * Code: 200

```json
{
  "message": "ok"
}
```

### Error Response

  *  Code: 400 BAD REQUEST

     The request was malformed


```json
{
  "type": "Bad Request",
  "message": "", // for example: Missing header: Authorization
  "Messages": [] // for example [ "business_id: Required" ]
}
```


  *  Code: 404 NOT FOUND

     The combination of access_key and business_id was not found

```json
{
  "type": "Not Found",
  "message": "No match found for provided credential",
}
```

  * Code: 401 UNAUTHORIZED

```json
{
  "type": "Unauthorized",
  "message": "You are not authorised for this request.",
}
```


  * Code: 403 Forbidden


```json
{
  "type": "Forbidden",
  "message": "You do not have permission to make this request",
}
```

