
## Ignore This

Returns json data about a single user.

### URL

  /users/:id

### Method:

  `GET`
  
### Get URL Params

#### Required

   `id=[integer]`

#### Optional

   `id=[integer]`

### Data Payload

  None

### Success Response

  * Code: 200

    `{ id : 12, name : "Michael Bloom" }`

### Error Response

  *  Code: 404 NOT FOUND

        `{ error : "User doesn't exist" }`

  OR

  * Code: 401 UNAUTHORIZED
  
    `{ "error" : "You are unauthorized to make this request." }`

### Sample Call

  ```javascript
  ```


### Notes

