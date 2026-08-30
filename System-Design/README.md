## Initial High Level Design
High-level design of the system's core modules and how they interact.

<div align="center">

[![High Level Design](./images/booking-initial-HLD.jpg)](https://miro.com/app/board/uXjVHtcJ3_s=/?share_link_id=325636074611)

</div>

Note: Clicking the image will take you to the interactive diagram for better experience

 

## Decisions

- Auth Module gates all requests; OTP/refresh tokens live in Redis with a TTL, backed by Postgres as source of truth.
- Postgres runs Master/Replica — writes go to Master, reads can be served from the Replica.
- Booking and payment success events publish to RabbitMQ; Notification Module subscribes independently rather than being
  called synchronously.
- Search Module caches results with a TTL — see [Search Flights](../search-flights/SEARCH-FLIGHTS.md) for the detailed design.
- Dashboard acts as a facade on top of Customer Management & Booking modules.

> Note: coordination between Booking, Payment, and Provider calls (what happens if payment succeeds but the provider
> booking fails, or vice versa) is a known open question, not yet resolved at this diagram's level of detail.
