Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python imports]]

--- 

**import_tut/**

```py
% mkdir import_tut
% touch import_tut/__init__.py
% touch import_tut/main.py
% mkdir import_tut/game
% touch import_tut/game/__init__.py 
% mkdir import_tut/game/characters/
% touch import_tut/game/characters/player.py  
% echo "def get_player_info():\n\tprint('I am the main player')" >> import_tut/game/characters/player.py 
% echo "import game.characters.player\n\ngame.characters.player.get_player_info()" >> import_tut/main.py 
% python import_tut/main.py 
I am the main player
```

import_tut/main.py
```py
import game.characters.player

game.characters.player.get_player_info()
```

game/characters/player.py
```py
def get_player_info():
	print('I am the main player')
```