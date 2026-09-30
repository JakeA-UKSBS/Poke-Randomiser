https://jakea-uksbs.github.io/Poke-Randomiser/


# Poke-Randomiser

A Pokémon draft battler for playing friends. Draft a team of random Pokémon, roll random abilities for them, build your sets, then fight a best-of-3.

**Play it here:** https://jakea-uksbs.github.io/Poke-Randomiser/

## Game modes

| Mode | Draft pool |
| --- | --- |
| **Standard Bo3** | Any fully evolved Pokémon with a competitive set (420 Pokémon) |
| **Mega Bo3** | Legendaries, Mythicals and Mega Evolutions only (152 Pokémon). Megas start already Mega Evolved and don't need a Mega Stone. |

You can play against:

- **Friend on this device**: pass the phone or laptop back and forth. Screens between turns hide each player's choices.
- **Online friend**: one player creates a room and shares the code or link, the other joins.
- **Vs CPU**: a simple computer opponent, mainly for trying things out.

## Rules

### 1. Draft

- You draft **7 Pokémon** over 7 rounds. Each round offers **3 random Pokémon**; pick one.
- Pokémon with several forms (Arceus types, Rotom appliances, regional forms, Megas) take a single slot in the pool. If you pick one, you choose the form when you choose its ability.
- You can't be offered a Pokémon you've already drafted.

### 2. Ability roll

- Every Pokémon you draft rolls **3 random abilities from any Pokémon**, not just its own. Keep one.
- An ability already on your team won't be offered again, so all 7 of your abilities are different.
- You get **one reroll per draft**, which swaps the 3 on offer for 3 new ones. Save it for a bad roll.
- Wonder Guard, Huge Power and Pure Power are banned from the rolls.

### 3. Team builder

For each Pokémon, set:

- **4 moves**: starts from Showdown's Random Battle movepool. Tick "Show full learnset" for everything it can learn.
- **Item**
- **Tera type**
- **EVs and nature**: pick a preset such as fast physical or special wall.

A Pokémon holding a **Mega Stone** Mega Evolves in battle instead of Terastallizing. Mega Evolving replaces its rolled ability with the Mega's own. Only one Mega per side can evolve in a game.

Teams can be saved in your browser and reused, or copied as Showdown text.

### 4. The match

- Best of 3. **First to 2 wins takes the match.**
- Before each game, both players pick **6 of their 7** in lineup order. Your first pick leads.
- **Lose a game and you ban one of the winner's Pokémon.** It sits out for the rest of the match.
- All Pokémon are **level 50**, using Gen 9 mechanics.
- Each player can Terastallize once per game. Tap Terastallize, then pick a move.

## How online play works

1. Pick a game mode, choose **Online friend**, enter your name and click **Create room**.
2. Send your friend the 5-letter code, or use **Copy link** to send a link that fills the code in for them.
3. Your friend opens the site, enters their name and clicks **Join room**. The room creator's game mode is used.
4. You both draft and build at the same time on your own devices. Bring picks, move choices and bans happen privately on each device.

Under the hood, the two browsers connect directly with [PeerJS](https://peerjs.com/) (WebRTC), so there's no game server. Both browsers run the same battle from a shared random seed and send each other only their choices, which keeps them in sync turn by turn. Each side runs its own copy of the game, so it works on trust between friends and isn't cheat-proof.

If the connection drops, a red banner appears. Start a new room from the home screen.

## How it's built

- **Battle engine:** [Pokémon Showdown](https://github.com/smogon/pokemon-showdown)'s simulator, via the [pkmn/ps](https://github.com/pkmn/ps) packages. It's bundled into `engine.js` together with Showdown's Gen 9 Random Battle sets, which provide the default movesets. Damage, abilities, items, Tera and Mega Evolution all behave as they do on Showdown.
- **Sprites:** from [PokéAPI's sprites](https://github.com/PokeAPI/sprites), embedded in `sprites.js`.
- **Page:** a single `index.html` with no build step or framework. It's plain HTML, CSS and JavaScript, so GitHub Pages serves it as-is.

| File | What it is |
| --- | --- |
| `index.html` | The whole game: draft, builder, battle UI, online play |
| `engine.js` | Showdown battle engine and data (about 7 MB) |
| `sprites.js` | Pokémon sprites (about 1 MB) |

To update the site, replace the files and push to `main`. GitHub Pages redeploys in a minute or two.

## Credits

Pokémon and all related names and images are © Nintendo, Game Freak and The Pokémon Company. This is a non-commercial fan project for playing with friends and isn't affiliated with or endorsed by them. The battle engine is Pokémon Showdown (MIT licence) via pkmn/ps. Sprites come from PokéAPI.
