# GARAIO REM GraphQL API

GARAIO REM implements a [GraphQL](https://graphql.org) API to communicate with a GARAIO REM instance. In order to use it, you

- need the url of the GARAIO REM endpoint that runs the GraphQL backend
- know your authentication credentials

Contact [garaio-rem@garaio.com](mailto:garaio-rem@garaio.com) to get this information.

Since GraphQL is self documenting, you won't find the API specs here. See "Schema Documentation" for further infos.

## Authentication

Use your credentials with the authenticateService Query to obtain an access token like so:

```graphql
query {
  authenticateService(clientId: "<your id>", clientSecret: "<your secret>") {
    accessToken
  }
}
```

Pass the access token in the authorization header for the following requests. Javascript example:

```javascript
const requestOptions = { headers: { Authorization: `Bearer ${accessToken}` } }
```

Access tokens have a short lifespan. They are good for a batch of queries, but do not store them for later use. If the token has expired, you'll get an error response and must authenticate again:

```json
{
  "errors": [
    {
      "extensions": {
        "code": "invalid_token"
      },
      "message": "token_expired"
    }
  ]
}
````

## Access Restrictions

Sensitive queries / mutations / fields are protected and not accessible unless we grant access to it, eg tenant / tenancy data. If you try to query fields without the required permissions you will get Not Authorized errors.

Contact us if you think you should have access to them.

## Schema Documentation

We run a [reference server](https://demo.garaio-rem.ch/external/graphql/graphiql) where you can explore the queries and mutations. If you want to extract the schema definition, use one of the many avaliable tools with this [endpoint](https://demo.garaio-rem.ch/external/graphql/)
