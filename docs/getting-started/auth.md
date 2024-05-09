# Authentication

You will need your `API_KEY` in order to make requests to this API. Make sure you never share your API key with anyone, and you never commit it to a public repository. Include this key in the `X-API-KEY` header of your requests.

You can request your API key by contacting us at [].

Example of how to include the `X-API-KEY` header in your request:

### cURL

```bash
curl -X POST \
  https://brand-service.api.genera.space/graphql \
  -H 'Content-Type: application/json' \
  -H 'X-API-KEY: <YOUR_API_KEY>' \
  -d '{
    "query": "query { products { items { id, name } } }"
  }
```

### JavaScript

```javascript
fetch("https://brand-service.api.genera.space/graphql", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "X-API-KEY": "<YOUR_API_KEY>",
  },
  body: JSON.stringify({
    query: "query { products { items { id, name } } }",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```
