# API Flexibility Analysis

## The Over-fetching Problem

In the context of the REST API, overfetching is when you recieve extra data you *don't* need from a fetch request. Overfetching is the exact opposite, where you instead need to make *multiple* fetch requests to get the data you need. GraphQL's query language inherently solves this problem by allowing the client to specify exactly what data they need.


## Endpoint and Schema Philosophy
Typical REST APIs function through an endpoint structure. This means that developers can perform fetch (or axios) request via the endpoint provided after an origin. For example, if you want a user by specifically that user's one-hundrenth twenty-second blog post, you would request to this uniform resouce locator (url): `https://dummyjson.com/users/965256201541254869328/blogs/4654187748641515348778523` or just with the endpoint itself when on the same server like so `/users/965256201541254869328/blogs/4654187748641515348778523`. This method is effective in getting information BUT it return too much or too little information. When this occurs, it's called over-fetching or under-fetching. GraphQL does not suffer this problem. Let's look into how that is so.


GraphQL's has a strongly typed schema that benefits frontend developers by:

- Allowing frontend developers to make specific requests for data within a single request based upon the schema created via the GraphQL Schema Definition Language (SDL).
- Providing frontend develops instant feedback when querying for data, after the backend developers have made a change to API and updated the overall backend.
- Easing frontend developers's process of creating multiple different kinds of frontend clients that require different data requirements through it's simple data fetching structure.

    - Example
        - API Exist: An GraphQL API that contains patient data of **name, address, age, height, medication history, prespription, prescription refills, diagnosis, care plan, care providers, and more.**
        - Front Clients from API
            - **Mobile App** to view a patient's current prescription refills and all prescriptions they have.
                - Only queries for prescription and prescription.
            - **Desktop App** to view patient files with basic information about the patient.
                - Only queries for name, address, age, height, and medication history.
            - **Tablet App** for quickly updating a patient's file with diagnosis and a care plan while also properly assigning the visit under the correct provider.
                - Only queries for user name, address, age, and height for verifying the correct patient. Additionally, in the same request, queries for the care providers and care plan to update the system.



## Caching and Complexity

Caching is simplier in REST compared to GraphQL because it can leverage the caching mechanisms of HTTP. When a response is cacheable, clients can reuse that data, and it can invalidate cached responses to prevent client use of stale or innapropriate data. With GraphQL, you have to explicitly create your own caching solution, there is nothing built in. Though a case where GraphQL's flexibility can outweigh it's caching complexity is the need for an API that can house the information you need for creating multiple frontend clients.