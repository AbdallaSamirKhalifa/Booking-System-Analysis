# Booking key concepts explained

## Flights

### What happens when we send an Offer request to Duffel?

- They send our search to a range of airlines, and come back with a series of `Offers`. Each `offer` represents a bundle from an airline for the exact same flight.
- Each `Offer` consists of one or more `Slice`.
- Each `Slice` consists of one or more `Segment`
  > All the concepts are explained below.

### Offer Request

Describes the passengers, where and when they want to travel (in the form of a list of `Slices`) with additional filters.

> | An Offer request includes one or more Slices

### Slice

Represents a journey that the passengers want to make between a particular origin and a particular destination, you just need to provide the code for the Airport, or the City.

### Segment

The `Segment` is the direct plane ride between two stops. Let us break it down a bit more.

- Assuming you want to travel from `Cairo International Airport (CAI)` &rarr; `Dubai Internation Airport (DXP)` which is one direct flight from `CAI` &rarr; `DXB`. This is the Segment. Which is also known as `One way direct trip` since there is no return flight.

### One way direct trip

> Cairo International Airport (CAI) &rarr; Dubai International Airport (DXB).

As above we sent an Offer request. The passenger wants to travel from `CAI` &rarr; `DXB`, we will receive an offer from `EgyptAir`, inside the offer we have our `Slice`, Inside the flight we have our `Segment` which says `CAI` &rarr; `DXB` departing at **specific time** on a **specific day**.

### One way indirect trip

> Cairo International Airport (CAI) &rarr; Leonardo da Vinci-Fiumicino Airport (FCO) &rarr; London Heathrow Airport (LHR).

We create an offer request for a passenger who wants to travel from `CAI` &rarr; `LHR` on 1st May.
And we get an `Offer` from `ITA Airways` with one `Slice` and two `Segments`

- First `CAI` &rarr; `FCO` which is in **Rome** our transit station departing at **specific time** on 1st May.
- Second `FCO` &rarr; `LHR`departing at **specific time** on 1st May.

### Return direct trip

> Cairo International Airport (CAI) &rarr; Dubai International Airport (DXB).

Return:

> Dubai International Airport (DXB) &rarr; Cairo International Airport (CAI).

Same as `One way direct trip` but with another slice for the return flight.

### Return indirect Trip

> Cairo International Airport (CAI) &rarr; Dubai International Airport (DXB) &rarr; Narita International Airport (NRT) **Tokyo**

Return:

> Narita International Airport (NRT) &rarr; Dubai International Airport (DXB) &rarr; Cairo International Airport (CAI).

We create an offer request for a passenger who wants to travel from `CAI` &rarr; `NRT` on 1st May and return to `CAI` on 3rd May.
And we get an `Offer` from `Emirates` with two `Slices` each consists of two `Segments` and our transit is `DXB`.

- Slice 1
  - First `CAI` &rarr; `DXB` departing at **specific time** on 1st May.
  - Second `DXB` &rarr; `NRT` departing at **specific time** on 1st May.
- Slice 2
  - First `NRT` &rarr; `DXB` departing at **specific time** on 3rd May.
  - Second `DXB` &rarr; `CAI` departing at **specific time** on 3rd May.
