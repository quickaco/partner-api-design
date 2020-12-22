
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

### Success Response

  * Code: 200

    `{ message: "ok" }`

### Error Response

  *  Code: 400 BAD REQUEST

     The request was malformed
    
     `{ "error" : "Bad Request" }`

  *  Code: 404 NOT FOUND

     The combination of access_key and business_id was not found
    
     `{ "error" : "No match found for provided credentials" }`

  * Code: 401 UNAUTHORIZED
  
    `{ "error" : "You are not authorised for this request." }`


  * Code: 403 Forbidden
  
    `{ "error" : "You do not have permission to make this request." }`
