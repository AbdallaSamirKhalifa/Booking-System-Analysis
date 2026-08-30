# Booking System | Analysis and Design

## Repo Structure
- [High level system design (HLD)](./System-Design/README.md)
- [Search Flights (LLD)](./search-flights/SEARCH-FLIGHTS.md)

## About This Project

## About This Project

We started this as a Skyscanner clone, search and compare, then redirect the user out to actually book. Good enough scope to practice the real aggregator problems: fanning out to multiple suppliers, caching,etc...

But redirecting felt like skipping the interesting part. Anyone can compare prices and hand off a link. The real problems, holding a reservation, taking payment without losing the user's money or the airline's seat if something fails.

So that's what this is now: a full booking platform with its problems and race conditions, payment included, for flights and hotels.
## What It Does

- **Search & compare** flights and hotels across multiple suppliers, aggregated and ranked.
- **Reserve & book** directly through the platform no redirect, no handoff. The system owns the transaction from search to confirmation.
- **Handle payment** as part of that transaction, not as an external site's problem.

For the full function-by-function breakdown, see [Features & Functions](./FEATURES-FUNCTIONS.md). For how the underlying booking concepts (offers, slices, segments, and the rest) actually work, see the [Domain Guide](./DOMAIN-EXPLAINED.md).

## Where It Stands

Still in the **Analysis & Design** phase — functions and API contracts are being specified and validated (including against how real platforms like Skyscanner actually behave) before any implementation starts. Architecture direction is a **modular monolith**: one deployable service with clean internal module boundaries.

---

## Contact & Collaboration

- **Author:** Abdalla Samir Khalifa
- **Role:** Systems Analyst & Backend Developer
- **Contact**:
  - GitHub: [@AbdallaSamirKhalifa](https://github.com/AbdallaSamirKhalifa)
  - Email: [abdallasamirkhalifa@gmail.com](abdallasamirkhalifa@gmail.com)
  - LinkedIn: [Abdalla Khalifa](https://linkedin.com/in/abdalla-khalifa)
