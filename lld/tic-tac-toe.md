# Tic Tac Toe

### Requirements

1. Player should be able to send invite to any other player
2. Players should have a profile with their score ( win - loss - draws - total games played )

<img src="../.gitbook/assets/file.drawing (1) (1) (1) (1).svg" alt="" class="gitbook-drawing">

### Solution

```python
class StatsModel:
    wins: int = 0
    draws: int = 0
    losses: int  = 0


class StatsModelView(Readonly):
    ...


class StatsController:
    def incr_win(self, user_id):
        ...
    
    def incr_draw(self, user_id):
        ...
    
    def incr_loss(self, user_id):
        ...


class User:
    username: str
    user_id: UUID4
    stats_profile: StatsModelView


class GameMediator(Mediator):
    def __init__(self, game, player1, player2):
        self.game = game
        self.player1 = player1
        self.player2 = player2
    
    def notify(self, sender, event):
        if sender is game:
            if event.type is start:
                self.player1.can_start(event.player1_mark)
                self.player2.can_start(event.player2_mark)
            elif event.type is end:
                self.player1.terminate(event.winner)
                self.player2.terminate(event.winner)
        elif sender is player:
            if event is move:
                self.game.register_move(player_id=sender.user_id, move=event.move)


class Game(User, Mediated):
    def start(self):
        player1_mark, player2_mark = self._toss()
        event = Event(
            type=start,
            player1_mark=player1_mark,
            player2_mark=player2_mark
        )
        self.mediator.notify(self, event)
        
    def register_move(self, player_id, move):
        ...
    
    def end(self):
        if player1 has won:
            self.stats_controller.incr_win(user_id=player1)
            self.stats_controller.incr_loss(user_id=player2)
        elif player2 has won:
            self.stats_controller.incr_win(user_id=player2)
            self.stats_controller.incr_loss(user_id=player1)
        else:
            self.stats_controller.incr_draw(user_id=player1)
            self.stats_controller.incr_draw(user_id=player2)
        event = Event(
            type=end,
            winner=None # 
        )
        self.mediator.notify(self, event)


class Player(User, Mediated):
    def make_move(self, move: Tuple[int, int]):
        event = Event(
            type=move,
            move=move
        )
        self.mediator.notify(self, event)
    
    def terminate(self):
        ...
        
 
     
  
```

{% content-ref url="mediator-pattern.md" %}
[mediator-pattern.md](mediator-pattern.md)
{% endcontent-ref %}
