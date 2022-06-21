# Battle Royal Workshop

## Problem statement

In your game, groups of 50 players join a session to play a game, which typically takes around 30 minutes to play. During the game, you have to update a specific player’s record to indicate the amount of time the player has been playing, the number of kills they’ve recorded, or whether they won the game. Users want to see old games they’ve played, either to view the games’ winners or to watch a replay of each game’s action

The first step of any data modeling exercise is to build a diagram to show the entities in your application and how they relate to each other.

### Relationships

In the application, you have the following entities:

- User
- Game
- UserGameMapping

A User entity represents a user in the application. A user can create multiple Game entities, and the creator of a game will determine which map is played and when the game starts. A User can create multiple Game entities, so there is a one-to-many relationship between Users and Games
Finally, a Game contains multiple Users and a User can play in multiple different Games over time.

Thus, there is a many-to-many relationship between Users and Games. You can represent this relationship with the UserGameMapping entity

### User profiles

The users of the gaming application need to create user profiles. These profiles include data such as a user name, avatar, game statistics, and other information about each user. The game displays these user profiles when a user logs in. Other users can view the profile of a user to review their game statistics and other details.

As a user plays games, the game statistics are updated to reflect the number of games the user has played, the number of games the user has won, and the number of kills by the user.


### Pre-game

The game is an online multiplayer game similar to Fortnite or PUBG. Players can create a game at a particular map, and other players can join the game. When 50 players have joined the game, the game starts and no additional players can join.
When searching for games to join, players may want to play a particular map. Other players won’t care about the map and will want to browse open games across all maps.

When adding a new user to a game, you need to:

- Confirm that there are not already 50 players in the game (each game can have a maximum of 50 players).
- Confirm that the user is not already in the game.
- Create a new UserGameMapping entity to add the user to the game.
- Increment the people attribute on the Game entity to track how many players are in the game.


### In-game

During the game, players try to defeat other players with the goal of being the last player standing. The application tracks how many kills each player has during a game as well as the amount of time a player survives in a game. If a player is one of the last three surviving in a game, the player receives a gold, silver, or bronze medal for the game.

### Post-game

Later, players may want to review past games they’ve played or that other players have played

## Identify access patterns

| Access pattern | Access type (Read/Write) |
|----------------|-------------------------|
| _App action_   | Read                    |


## Design primary keys

Write down the entities and their primary keys identified in the problem statement 

| Entity          | Partition Key | Sort Key   |
|-----------------|---------------|------------|
| Entity name     | PREFIX#$ID    | #METADATA# |

## Further steps

- Create a table: Create a table with the primary keys defined on previous steps
- Bulk load data: Load the data in the item.json file
- Retrieve an item collection (is a set of items with the same partition key value but different sort key values where the items of different entity types have relationships with the partition key)
- Make a query (join-like). Hint: Use filters


[An introduction to DynamoDB data modelling](https://blog.theodo.com/2021/04/introduction-to-dynamo-db-modeling/)

[Credits to AWS Game Player Workshop](https://amazon-dynamodb-labs.workshop.aws/game-player-data.html)

