# ts-pubsy

Fully Typed PubSub Mechanism with Channel and Payload autocompletion.

# Usage

```
import { Pubsy } from 'ts-pubsy';

type Game = {
  id: string;
  players: [User[id], User[id]];
  winner?: User[id];
}

type GameEvents = {
  onNewGame: Game;
  onGameFinish: { id: string, winner: User[id] };
}

const gamePubsy = new Pubsy<GameEvents>();

// Subscriptions

gamePubsy.subscribe('onNewGame', (game) => {
  // do stuff with the Game object
});

gamePubsy.subscribe('onGameFinished', (game) => {
  console.log(game.winner);
});

```

// Publish (later on)

gamePubsy.publish('onNewGame', {
  id: '1',
  players: ['player-1', 'player-2'],
  winner: undefined,
});

gamePubsy.publish('onGameFinish', {
  id: '1',
  winner: 'player-2',
});

