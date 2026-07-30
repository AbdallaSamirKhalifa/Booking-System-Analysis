# Booking System | Analysis and Design

## About This Project

I started this as a Skyscanner/Booking.com-style meta-search clone — search flights and hotels, compare prices, redirect the user out to book. That was a reasonable scope to cut my teeth on: real fan-out to multiple suppliers, aggressive caching, ranking logic, the usual aggregator problems.

But the more I designed it, the more the "redirect and walk away" model started to feel like it was avoiding the actual hard part. Anyone can compare prices and hand off a link. Owning the booking end-to-end — reserving the right seat or room, holding it, taking payment without losing the user's money or the airline's inventory in the process — is where the real distributed-systems problems live: idempotency, consistency across supplier and payment state, what happens when a payment succeeds but the reservation fails a second later.

So the system has grown up. It's no longer a meta-search tool — it's a full booking platform, end-to-end, including payment, for both flights and hotels.

## What It Does

- **Search & compare** flights and hotels across multiple suppliers, aggregated and ranked.
- **Reserve & book** directly through the platform — no redirect, no handoff. The system owns the transaction from search to confirmation.
- **Handle payment** as part of that transaction, not as an external site's problem.

For the full function-by-function breakdown, see [Features & Functions](./FEATURES-FUNCTIONS.md). For how the underlying booking concepts (offers, slices, segments, and the rest) actually work, see the [Domain Guide](./DOMAIN-EXPLAINED.md).

## Where It Stands

Still in the **Analysis & Design** phase — functions and API contracts are being specified and validated (including against how real platforms like Skyscanner actually behave) before any implementation starts. Architecture direction is a **modular monolith**: one deployable service with clean internal module boundaries.

The repo includes the two documents linked above.

---

## Contact & Collaboration

- **Author:** Abdalla Samir Khalifa
- **Role:** Systems Analyst & Backend Developer
- **Contact**:
  - GitHub: [@AbdallaSamirKhalifa](https://github.com/AbdallaSamirKhalifa)
  - Email: [abdallasamirkhalifa@gmail.com](abdallasamirkhalifa@gmail.com)
  - LinkedIn: [Abdalla Khalifa](https://linkedin.com/in/abdalla-khalifa)
