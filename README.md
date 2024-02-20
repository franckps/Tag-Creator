# Tag Creator

### An app that create barcode tags to help markets on their daily demands

<br/>
<br/>

## Request to create a new tag

#### Request endpoint:

> POST: /create_tag

#### Request body:

```json
{
    "product_code": string
}
```

<br/>

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

<br/>

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

<br/>

#### Request Example:

```properties
curl --location 'http://localhost:3000/create_tag' \
--header 'Content-Type: application/json' \
--data '{
    "product_code": "123-456-789-114"
}'
```

Above we have an example of request that can make to a server in <code>localhost</code> using port <code>3000</code> and the string <code>"123-456-789-114"</code> as the tag value.
<br/>

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

This is an example of response that the service can return, according to the previous request made.
<br/>

#### Wrong Request Example:

```properties
curl --location 'http://localhost:3000/create_tag' \
--header 'Content-Type: application/json' \
--data '{
    "product": "123-456-789-114"
}'
```

Above we have an example of wrong request made to a server in <code>localhost</code> using port <code>3000</code> but the body has <code>"product"</code> instead of <code>"product_code"</code> as property. It will result in an error response.
<br/>

#### Error Response Example:

> Status 422 UNPROCESSABLE ENTITY

```json
{
  "errors": [
    {
      "detail": "{'product': ['unknown field'], 'product_code': ['required field']}",
      "title": "Server Error"
    }
  ]
}
```

This is the response error resulted of the previous request, made with a wrong property replacing the right one <code>"product_code"</code>.
