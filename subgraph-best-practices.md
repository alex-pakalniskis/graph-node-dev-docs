# Subgraph best practices and pitfalls

### `Bytes` type for entity `id` fields

> Each entity must have an `id` field, which must be of type `Bytes!` or `String!`. It is generally recommended to use `Bytes!`, unless the `id` contains human-readable text, since entities with `Bytes!` id's will be faster to write and query as those with a `String!` `id`. The `id` field serves as the primary key, and needs to be unique among all entities of the same type. For historical reasons, the type `ID!` is also accepted and is a synonym for `String!`. \
> [- The Graph docs](https://thegraph.com/docs/en/developing/creating-a-subgraph/#optional-and-required-fields)

Example

```graphql
type TokenBalance @entity {
  id: Bytes!
  amount: Int!
  token: Token!
}
```

### Immutable entities

> By default, entities are mutable, meaning that mappings can load existing entities, modify them and store a new version of that entity. Mutability comes at a price, and for entity types for which it is known that they will never be modified, for example, because they simply contain data extracted verbatim from the chain, it is recommended to mark them as immutable with `@entity(immutable: true)`. Mappings can make changes to immutable entities as long as those changes happen in the same block in which the entity was created. Immutable entities are much faster to write and to query, and should therefore be used whenever possible.
>
> [- The Graph docs](https://thegraph.com/docs/en/developing/creating-a-subgraph/#optional-and-required-fields)

Example

```graphql
type Gravatar @entity(immutable: true) {
  id: Bytes!
  owner: Bytes
  displayName: String
  imageUrl: String
  accepted: Boolean
}
```

### Reduce number (or entirely avoid) [eth\_calls](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_call)

> Many smart contracts do not emit all necessary data in their events directly. To determine the new smart contract state after a completed transaction, it is often necessary to send an [eth\_call](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_call) back to the smart contract to retrieve that data. However, JSON RPC calls are generally slow. Each call usually takes 100ms up to several seconds to resolve. That’s why developers are discouraged from using them at all in their UIs for displaying information. These eth\_calls are also slow if they run as part of the mappings inside the Graph Node.
>
> \- [The Graph docs](https://thegraph.com/blog/improve-subgraph-performance-reduce-eth-calls/)

### Avoid large arrays

TODO

### Aggregations

TODO

[https://github.com/graphprotocol/graph-node/blob/master/docs/aggregations.md](https://github.com/graphprotocol/graph-node/blob/master/docs/aggregations.md)
