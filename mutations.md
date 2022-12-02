GraphQL mutations are operations that modify data on the server. They are typically used to create, update, or delete data.

Just like with queries, you can define variables in a GraphQL mutation. This allows you to reuse the same mutation with different variable values, making your code more modular and easier to maintain.

Here's an example of a GraphQL mutation:

```graphql
mutation CreateUser {
  createUser(name: "John Doe", email: "johndoe@example.com") {
    id
    name
    email
  }
}
```

This mutation uses the createUser field to create a new user with the name "John Doe" and the email "johndoe@example.com". The id, name, and email fields in the response are the fields that will be returned by the server after the mutation has been executed.

To execute this mutation, you would typically make a POST request to the GraphQL API endpoint, with the mutation as the payload. The server would then execute the mutation and return the specified fields in the response.

Here's an example of the response you might expect from the above mutation:

```json
{
  "data": {
    "createUser": {
      "id": "abc123",
      "name": "John Doe",
      "email": "johndoe@example.com"
    }
  }
}
```

In this example, the `createUser` field in the response contains the data for the newly created user, including the user's `id`, `name`, and `email` fields.


Here's an example of a GraphQL mutation with a defined variable:

```graphql
mutation CreateUser($name: String!, $email: String!) {
  createUser(name: $name, email: $email) {
    id
    name
    email
  }
}
```

In this mutation, the `$name` and `$email` variables are defined as required arguments of type `String`. This means that when this mutation is executed, values must be provided for these variables. The `createUser` field in the mutation uses these variables as its `name` and `email` arguments, allowing the client to create a new user with the specified name and email.

Here's an example of how this mutation could be executed with specific values for the `$name` and `$email` variables:

```json
{
  "name": "John Doe",
  "email": "johndoe@example.com"
}
```

This would create a new user with the name "John Doe" and the email "johndoe@example.com".

Just like with queries, you can pass defined variables as part of the query string in a URL when executing a mutation. For example, the above mutation could be executed by making a POST request to the following URL:

```graphql
https://my-api.com/graphql?query=mutation+CreateUser($name:+String!,+$email:+String!)+{%0A++createUser(name:+$name,+email:+$email)+{%0A++++id%0A++++name%0A++++email%0A++}%0A}&name=John+Doe&email=johndoe%40example.com
```

In this case, the `$name` and `$email` variables are passed as URL parameters, allowing the server to substitute the provided values for the variables in the mutation.
