## Проектирование GraphQL API

1. Анализ swagger контракт client-inf

- /clients/{id}: Базовая информация о клиенте.
- /clients/{id}/documents: Список документов клиента
- /clients/{id}/relatives: Список родственников клиента

Все операции — только чтение (GET).

2. GraphQL схема

```graphql
type Query {
  client(id: ID!): Client
}

type Client {
  id: ID!
  name: String!
  age: Int
  documents: [Document!]!
  relatives: [Relative!]!
}

type Document {
  id: ID!
  type: String!
  number: String!
  issueDate: String
  expiryDate: String
}

type Relative {
  id: ID!
  relationType: String!
  name: String!
  age: Int
}
```

3. Queries(Запросы)

Достаточно одного корневого запроса — client(id: "...").

```graphql
type Query {
  client(id: ID!): Client
}
```