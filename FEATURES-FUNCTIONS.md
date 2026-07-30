# Flight Search Aggregator — Flights Function Specification

A Skyscanner-style flight meta-search system. This document defines the core functions for the Flights vertical, ahead of API design.

## Product Model

This is a **meta-search / redirect platform**, not a booking platform. The system aggregates and compares flight prices across providers; once a user selects an itinerary, they're redirected to the airline or OTA to complete the purchase. As a result, payment processing, seat locking, and reservation (PNR) management are out of scope.

## Architecture Note

Modular monolithic architecture — a single deployable service with clearly separated internal modules, rather than microservices from the outset.

## Functions

### User & Profile

| Function                                                 | Description                                                                                                               |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `login`                                                  | Authenticates via email/password or a third-party identity provider.                                                      |
| `searchAirportByName`                                    | Looks up airports and cities via a hierarchical picker: Country → City → Airport.                                         |
| `addAirport`                                             | Saves a preferred departure airport to the user's profile.                                                                |
| `subscripeToNewsLetter` / `unsubscripeToNewsLetter`      | Opts a user in or out of general marketing communications.                                                                |
| `saveBookable` / `removeSavedBookable` / `getFavourites` | Adds or removes a flight from the user's favorites/saved list. Saving an item automatically creates a price alert for it. |

### Flights

| Function                                                  | Description                                                                                                                                                                    |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `searchFlights`                                           | Core search: origin (required), destination, and fixed or flexible dates. Leaving the destination empty routes the user into `searchEverywhere` instead of returning an error. |
| `getFlightDetails`                                        | Returns full details for a single flight result.                                                                                                                               |
| `redirectToProvider`                                      | Hands the user off to the selected airline to complete booking — the system's endpoint in the flow.                                                                            |
| `createPriceAlert` / `getPriceAlert` / `deletePriceAlert` | Tracks a specific route and date combination, notifying the user when its price changes.                                                                                       |
| `searchEverywhere`                                        | Given just a departure airport, returns a ranked list of destinations by price. Supports filtering by category (e.g. beach, art & culture, food).                              |
| `getWholeMonthPrices`                                     | Given a fixed route, returns a calendar of prices across a selected month, with an optional chart view of the same data.                                                       |
| `searchMultiCity`                                         | Searches an itinerary of up to six flight legs as a single trip.                                                                                                               |
| `getNearbyAirportOptions`                                 | Expands search results to include nearby airports for a given origin or destination.                                                                                           |
| `getCountries`                                            | Returns the registerd counteries that you can travel from or to                                                                                                                |
| `getAirlines`                                             | Returns the registerd available airlines                                                                                                                                       |

### Hotels

| Function             | Description                                                                                                            |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `getCountries`       | Returns the registered countries                                                                                       |
| `getCities`          | Returns the registered citeis                                                                                          |
| `getHotels`          | Returns the registered hotels                                                                                          |
| `searchHotels`       | Core search: (country, city, hotle) is required alongside _check in & check out & guists and rooms_                    |
| `getHotelDetails`    | The hotel information gathered from providers alongside reviews, location, and the providers that you can book through |
| `redirectToProvider` | The hotel information gathered from providers alongside reviews, location, and the providers that you can book through |

> The maximum allowed duration is 30 days.
