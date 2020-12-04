# GARAIO REM GraphQL API

GARAIO REM implements a [GraphQL](https://graphql.org) API to communicate with a GARAIO REM instance. In order to use it, you

- need the url of the GARAIO REM endpoint that runs the GraphQL backend
- know your authentication credentials

Contact [garaio-rem@garaio.com](mailto:info@garaio-rem.ch) to get this information.

Since GraphQL is self documenting, you won't find the API specs here. See "Schema Documentation" for further infos. Every request in GraphQL is a POST request with the Query inside the body.
In Graphiql (the webinterface of GraphQL) you have the keyboard shortcut crtl+space for the autocompletion.

Find out what's new in the [Changelog](Changelog.md)

## Authentication

Send a POST request to /external/graphql/authenticate/token, eg <https://demo.garaio-rem.net/external/graphql/authenticate/token>...

### As a service partner

with the following params:

- grant_type: "client_credentials"
- client_id: "\<your  client id>"
- client_secret: "\<your  client secret>"

### As a GARAIO REM user

with the following params:

- grant_type: "password"
- username: "\<the user name>"
- password: "\<the user password>"

### Using the access token

You will receive an access token in the response. Pass the access token in the authorization header for the following requests. Javascript example:

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

***Please note that access restrictions are not enforced for authenticated GARAIO REM users. Therefore, GARAIO REM user authentication is meant for apps and internal use, not for services where you do not have control over the queries / mutations that are executed***

## Schema Documentation

We run a [reference server](https://demo.garaio-rem.ch/external/graphql/graphiql) where you can explore the queries and mutations. If you want to extract the schema definition, use one of the many avaliable tools against <https://demo.garaio-rem.ch/external/graphql>. Be aware some tools like Insomnia need the graphiql endpoint <https://demo.garaio-rem.ch/external/graphql/graphiql> and some other tools like graphql playground not.
