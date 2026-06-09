# GraphQL Apollo Sandbox Queries and Mutations

Use the following operations directly in Apollo Sandbox Explorer.

## Endpoint

Use your local endpoint:

- `http://localhost:4000/`

## Queries

### 1. Get all users

```graphql
query GetUsers {
  users {
    id
    name
    username
    age
    nationality
    friends {
      id
      name
      username
    }
    favoriteMovies {
      id
      name
      yearOfPublication
      isInTheaters
    }
  }
}
```

### 2. Get one user by id

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    username
    age
    nationality
    friends {
      id
      name
    }
  }
}
```

Variables:

```json
{
  "id": "1"
}
```

### 3. Get all movies

```graphql
query GetMovies {
  movies {
    id
    name
    yearOfPublication
    isInTheaters
  }
}
```

### 4. Get one movie by name

```graphql
query GetMovie($name: String!) {
  movie(name: $name) {
    id
    name
    yearOfPublication
    isInTheaters
  }
}
```

Variables:

```json
{
  "name": "Interstellar"
}
```

## Mutations

### 1. Create user

```graphql
mutation CreateUser($input: CreateUserInput!) {
  createUser(input: $input) {
    id
    name
    username
    age
    nationality
  }
}
```

Variables:

```json
{
  "input": {
    "name": "Alice",
    "username": "alice01",
    "age": 28,
    "nationality": "CANADA"
  }
}
```

### 2. Update username

```graphql
mutation UpdateUsername($input: UpdateUsernameInput!) {
  updateUsername(input: $input) {
    id
    name
    username
    age
    nationality
  }
}
```

Variables:

```json
{
  "input": {
    "id": "1",
    "newUsername": "johnny_new"
  }
}
```

### 3. Delete user

```graphql
mutation DeleteUser($id: ID!) {
  deleteUser(id: $id) {
    id
    name
    username
  }
}
```

Variables:

```json
{
  "id": "5"
}
```

## Notes

- If a query uses variables like `$id` or `$name`, make sure you provide the matching JSON in the Variables panel.
- The current `deleteUser` resolver removes the user but returns `null`.
