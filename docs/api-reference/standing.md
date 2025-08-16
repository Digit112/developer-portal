---
id: standing
title: Standing
---

A Standing object represents a player's current standing relative to some container. Standings may be retrieved via various methods off of Leagues, Events, or PhaseGroups.

When filtering standings using a StandingPageFilter, a [`PaginatedSearchType`](/docs/api-reference/paginated-search-type) may be provided, *however*, the `fieldsToSearch` field is ignored. The provided `searchString` will be matched against the names of the entrants associated with the standings being filtered.

Standings are contextualized by their containers, which also give semantic meaning to the "player" and "entrant" fields. Typically, "entrant" is the field you should use.

Internally, standings retrieved from a league (apparently) use a hidden PhaseGroup belonging to a hidden Phase and Event. Leagues with sub-leagues do not have standings of their own ((ever?))

The 'player' field will give the associated player if one exists, 

```graphql
union StandingContainer = Tournament | Event | PhaseGroup | Set

type Standing {
  id: ID
  
  # The containing entity that contextualizes this standing. Event standings, for
  # example, represent an entrant's standing in the entire event vs. Set standings
  # which is an entrant's standing in only a single set within an event.
  container: StandingContainer
  
  # If the entity this standing is assigned to can be resolved into an entrant, this
  # will provide the entrant.
  entrant: Entrant
  
  isFinal: Boolean
  
  # Metadata that goes along with this standing. Can take on different forms based
  # on standing group type and settings.
  metadata: JSON
  
  placement: Int
  
  # The player associated with this standing, if any.
  player: Player
  
  standing: Int @deprecated( reason: "The "placement" field is identical and will eventually replace "standing"" )
  
  stats: StandingStats
  
  totalPoints: Float
}
```