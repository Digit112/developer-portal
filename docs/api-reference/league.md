---
id: league
title: League
---

A League object is a container for one or more tournaments.

The slug field is prefixed "tournament/" which is valid and will redirect to the page with the "league/" prefix. The shortSlug can also be used with the league/ prefix specifically to link to a version of the page which has no banner, possibly meant to be used with embeds.

```graphql
type League {
  id: ID
  
  addrState: String
  
  city: String
  
  countryCode: String
  
  # When the tournament was created (unix timestamp)
  createdAt: Timestamp
  
  currency: String
  
  # When the tournament ends
  endAt: Timestamp
  
  entrantCount: Int
  
  # Arguments
  # query: [Not documented]
  eventOwners(query: EventOwnersQuery): EventOwnerConnection
  
  # When does event registration close
  eventRegistrationClosesAt: Timestamp
  
  # Paginated list of events in a league
  #
  # Arguments
  # query: [Not documented]
  events(query: LeagueEventsQuery): EventConnection
  
  # Hacked "progression" into this final event
  finalEventId: Int @deprecated( reason: "No longer used" )
  
  # True if tournament has at least one offline event
  hasOfflineEvents: Boolean
  
  hasOnlineEvents: Boolean
  
  hashtag: String
  
  # Arguments
  # type: [Not documented]
  images(type: String): [Image]
  
  # True if tournament has at least one online event
  isOnline: Boolean
  
  lat: Float
  
  links: TournamentLinks
  
  lng: Float
  
  mapsPlaceId: String
  
  # The tournament name
  name: String
  
  # Top X number of people in the standings who progress to final event
  numProgressingToFinalEvent: Int @deprecated( reason: "No longer used" )
  
  numUniquePlayers: Int
  
  postalCode: String
  
  primaryContact: String
  
  primaryContactType: String
  
  # Publishing settings for this tournament
  publishing: JSON
  
  # When does registration for the tournament end
  registrationClosesAt: Timestamp
  
  rules: String
  
  # The short slug used to form the url
  shortSlug: String
  
  # Whether standings for this league should be visible
  showStandings: Boolean
  
  slug: String
  
  # Paginated list of standings
  #
  # Arguments
  # query: [Not documented]
  standings(query: StandingGroupStandingPageFilter): StandingConnection
  
  # When the tournament Starts
  startAt: Timestamp
  
  # State of the tournament, can be ActivityState::CREATED, ActivityState::ACTIVE,
  # or ActivityState::COMPLETED
  state: Int
  
  # When is the team creation deadline
  teamCreationClosesAt: Timestamp
  tiers: [EventTier]
  
  # The timezone of the tournament
  timezone: String
  
  # The type of tournament from TournamentType
  tournamentType: Int
  
  # When the tournament was last modified (unix timestamp)
  updatedAt: Timestamp
  
  # Build Tournament URL
  #
  # Arguments
  # tab: Tournament tab to add to URL
  # relative: Generate a relative URL. Defaults to true. Setting to
  # false will generate an absolute URL
  url(tab: String, relative: Boolean): String
  
  venueAddress: String
  venueName: String
  videogames: [Videogame]
}
```