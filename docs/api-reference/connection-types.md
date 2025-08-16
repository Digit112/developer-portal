---
id: connection-types
title: Connection Types
---

Connection types take the form of an existing object type like [`Event`](/docs/api-reference/event) or [`Standing`](/docs/api-reference/standing), followed by "Connection", e.g. EventConnection and StandingConnection. In addition to an array of the appropriate type called 'nodes', these types always contain a [`pageInfo`](/docs/api-reference/pageinfo) which contains information about the paging of the returned results.

```graphql
type StandingConnection {
  pageInfo: PageInfo
  nodes: [Standing]
}
```