# Node GrapQL Server

Testing out building a GraphQL server with file based [lowdb](https://github.com/typicode/lowdb).

# Install dependencies

```
yarn
```

# Development

```
yarn dev
```

# Playground

[Test out the api live here](https://node-graphql.onrender.com)

# Create User mutation

```graphql
mutation {
  signup(input: { email: "admin@admin.com", password: "password", role: ADMIN }) {
    token <--- use token to access protected resources
  }
}

mutation {
  signup(input: { email: "member@member.com", password: "password", role: MEMBER }) {
    token <--- use token to access protected resources
  }
}

mutation {
  signup(input: { email: "guest@guest.com", password: "password", role: GUEST }) {
    token <--- use token to access protected resources
    user {
      id
    }
  }
}


```

# Signin mutation

```graphql
mutation {
  signin(input: { email: "admin@admin.com", password: "password" }) {
    token <--- use token to access protected resources
  }
}
```

# Create post mutation

```graphql
mutation {
  createPost(input: { message: "Hello there!" }) {
    id
    message
  }
}
```

#### HTTP HEADERS

```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```

# Invite mutation

```graphql
mutation {
  invite(input: { email: "newmember@member.com", role: MEMBER }) {
    email
  }
}
```
#### HTTP HEADERS

```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```
# Update me mutation

```graphql
mutation {
  updateMe(
    input: { email: "newemail@admin.com", avatar: "avatar-url", verified: true }
  ) {
    email
    avatar
    verified
  }
}
```
#### HTTP HEADERS

```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```
# Update settings mutation

```graphql
mutation {
  updateSettings(input: { pushNotifications: false }) {
    pushNotifications
  }
}
```
#### HTTP HEADERS

```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```

# Feed query

```graphql
query {
  feed {
    message
  }
}

```

# Post query

```graphql
query {
  posts {
    message
  }
}

```
 HTTP HEADERS
```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```


# User settings query

```graphql
query {
  userSettings {
    id
    user {
      id
    }
    theme
    emailNotifications
    pushNotifications
  }
}

```
HTTP HEADERS
```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```
# Me query

```graphql
query {
  userSettings {
    id
    user {
      id
    }
    theme
    emailNotifications
    pushNotifications
  }
}

```
HTTP HEADERS
```graphql
{
  "Authorization": "your-token-from-signin-mutation"
}
```
