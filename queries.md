In a GraphQL query, a client specifies the data they want to retrieve from the API, and the API returns only that data in the response.

Here is an example of a simple GraphQL query:

```graphql
query {
  user(id: "123") {
    name
    email
  }
}
```

In this example, the query specifies that the client wants to retrieve the name and email fields for the user with the ID 123. The API would then return the requested data in the following format:

```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "johndoe@example.com"
    }
  }
}
```

Another common use of GraphQL queries is to retrieve data from multiple resources in a single request. For example, the following query retrieves the user's name and email, as well as their recent posts:

```graphql
query {
  user(id: "123") {
    name
    email
    posts(last: 10) {
      title
      body
    }
  }
}
```

The API would then return the requested data in the following format:

```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "johndoe@example.com",
      "posts": [
        {
          "title": "My first post",
          "body": "This is the body of my first post"
        },
        {
          "title": "My second post",
          "body": "This is the body of my second post"
        },
        ...
      ]
    }
  }
}
```

These are just a few examples of how GraphQL queries can be used to request specific data from an API. The syntax and structure of GraphQL queries can vary depending on the specific implementation of the API, but the overall concept remains the same.
