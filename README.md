# Tag Creator

### An app that create barcode tags to help markets on their daily demands

## Request to create a new tag

#### Request endpoint:

> POST: /create_tag

#### Request body:

```json
{
    "product_code": string
}
```

#### Response success:

> Status 200

```json
{
    "data": {
        "count": number,
        "path": string,
        "type": string
    }
}
```

#### Response error:

> Status 400 - 599

```json
{
    "errors": [
        {
            "detail": string,
            "title": string
        }
    ]
}
```

#### Request Example:

```properties
curl --location 'http://localhost:3000/create_tag' \
--header 'Content-Type: application/json' \
--data '{
    "product_code": "123-456-789-114"
}'
```

Above we have an example of request that can make to a server in localhost using port <code>3000</code> and the string <code>"123-456-789-114"</code> as the tag value.

#### Response Example:

> Status 200 OK

```json
{
  "data": {
    "count": 1,
    "path": "123-456-789-114.png",
    "type": "Tag Image"
  }
}
```

Above we have an example of response that the service can return, according to the previous request made.
