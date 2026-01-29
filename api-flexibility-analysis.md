# API Flexibility Analysis

## The Over-fetching Problem

In the context of the REST API, overfetching is when you recieve extra data you *don't* need from a fetch request. Overfetching is the exact opposite, where you instead need to make *multiple* fetch requests to get the data you need. GraphQL's query language inherently solves this problem by allowing the client to specify exactly what data they need.


## Endpoint and Schema Philosophy

GraphQL's strongly typed schema benefits frontend developers by:

- Allowing specific request for data within a single request based upon the schema created via the GraphQL Schema Definition Language (SDL).
- Providing instant feedback when querying for data, after a change occurs on the backend.
- Easing the creation of different frontend clients that require different data requirements through it's simple data fetching structure.

## Caching and Complexity

Caching is simplier in REST compared to GraphQL because it can leverage the caching mechanisms of HTTP. When a response is cacheable, clients can reuse that data, and it can invalidate cached responses to prevent client use of stale or innapropriate data. With GraphQL, you have to explicitly create your own caching solution, there is nothing built in. Though a case where GraphQL's flexibility can outweigh it's caching complexity is the need for an API that can house the information you need for creating multiple frontend clients.