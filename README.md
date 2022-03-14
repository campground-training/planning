# Camping Planning

This is a _temporary_ repo to hold some notes, ideas, and planning for the Camping adventure.

Here's the big picture:

Create a reference application. By "application" I mean:

- User Interface
- Backing Services to make the interface "Real"

All while not making a "real" application.

This will be used to show and explore various things, and various levels of details. Specific enough?

## The Frontend

I'm thinking the most useful thing for the frontend would be an Angular application. I want it to demonstrate the following, with a rough priority of how much emphasis I want to put into each of these things at the current point in time (1-5).

- Accessibility (5)
- Good UI/UX (3)
- Great guidance for state management with Redux / NGRX (5)
- Good test coverage (4)
  - Low level tests (Jest, Angular Testing Library or similiar)
  - UI Integration Tests (Cypress or similiar)
- Module Design (5)
  - Feature Modules (5)
  - Creating Libraries for reuse (4)
- Authz/Authn (4)

## The Services

The services should represent good, modern API design for application facing data (HTTP APIs and Websockets).
They should also is good microservice patterns, including:

- Pub/Sub
- Event-Driven

## The "Application"

The application will present the users with a list of campsites, includng their features.

- If the site has water hookups
- If the site has electrical hookups
- (sites with neither are "Primitive" sites)
- If a site is a waterfront site
  - Waterfront sites can be primitive, or have either water or electical or both.
- Each site has a few pictures associated with it.
- The user can see a particular site's availability.
  - Thinking about this one - maybe they can say "If I wanted to stay in this site through these dates, is it available?"
  - Perhaps show a calendar for a three month period showing site availability for a selected set of sites?

So, the user could select a few sites, and say "Show the availability of these sites for June, July and August" and a calendar would
appear with some way of indicating which days are available.

### Registration for a site.

The user must be logged in for this, and have an account. (we'll flesh this out later).

They can select an available site for a range of dates and make a reservation.

A reservation is always for one site on a set of one or more contiguous days.

- Need a site one weekend then the next? Two reservations.
- Need three sites at the same time? Three reservations.

That's the idea.

The folder `html-mockups` is a good place to start tinkering with UI design ideas.
