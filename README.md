# RouteTwo
(derived from entrpntr & Dabomstew's versions, derived from RouteOne by HRoll)

### -- TABLE OF CONTENTS --
1. [LATEST CHANGES]
2. [CONFIG FILE]
3. [PRELIMINARY NOTES FOR ROUTE FILES]
4. [MAKING A ROUTE FILE]
   1. [Comments]
   2. [Generic display]
      1. [Money]
	  2. [Stats]
   3. [Player Pokemon utility]
      1. [Player Pokemon]
	  2. [Battle items]
	  3. [Player money]
	  4. [Badges]
	  5. [Battle Tower]
   4. [Battles]
      1. [Trainers]
	  2. [Wild encounters]
	  3. [Battle options]
5. [KNOWN ISSUES]
6. [TODOS]
7. [CONTACT INFO AND ACKNOWLEDGEMENTS]
   1. [Communities]
   2. [Coders]
### -- --


#### 1. LATEST CHANGES
Syntax:
`[YYYY/MM/DD]`  
**► Compatibility-breaking update.**  

○ Usual update.


`[2020/11/18]`  
**► Renamed move PSYCHICM into PSYCHIC.**  

○ Updated Glacierbadge Special Defense bug.  
○ Added item buying/selling mechanics with commands `buy`, `sell`.  
○ Added weather handling in battles with option `-weather`.  
○ Added Special Attacks aliases options `-xspatk`, `-xspatks` for respectively `-xspc`, `-xspcs`.  
○ Added Special Defense boosts (for Amnesia, etc.) with options `-xspdef`, `yspdef`, `xspdefs`, `yspdefs`.  
○ `returnpower` now bounds the value between `1` and `102`.  

○ Added XML formatting file for Notepad++ route files in `xml/` .


`[2020/11/08]`  
**► Changed held item syntax. `pinkbowflag`, `charcoalflag`, etc. are obsolete.**  

○ Added primal money management with commands `money`, `addmoney`, `spendmoney`.  
○ Added Amulet Coin handling with commands `setamuletcoin`, `unsetamuletcoin`.



`[2020/10/22\]`  
○ Imported n-shot damage calculation from RouteOne.  
○ Added config file flag `includeCrits` under `[util]`.  

○ Fixed Struggle damage calculation.


`[2020/10/18\]`
○ Added held item removal with command `unequip`.
○ Added all species-specific stat-boosting items (listed below).
○ Added remaining type-boosting items (listed below).
○ Added Reflect handling in battles with options `-xreflect`, `-yreflect`.
○ Added Light Screen handling in battles with options `-xlightscreen`, `-ylightscreen`.


#### -- --


#### 2. CONFIG FILE

First, you should set the options in config.ini. Make sure the game option is set to `gold`, `silver` or `crystal`, and that you have set the right game.
Then, set your starting pokemon's species, level, and IVs under `[poke]`.
Under `[files]`, you'll want to enter the file names of your desired input file and output file destination.
The options under `[util]` should generally be set to true, unless you really don't want to know how many X items/rarecandies/stat boosting items you used.

\[More advanced: to use more than one config file, you can use the command line option `java -jar <RouteTwo filename> <config filename>`.\]

#### -- --


#### 3. PRELIMINARY NOTES FOR ROUTE FILES

`"command"` : Every command will be put between quotation marks. You SHOULD NOT be writing these quotation marks in your routing files.  
`"alias"` : An alias refers to a shorter name for a given command.  
`"CoMMAnd"` : Every command is case-incensitive. You can capitalize at will.  
- The convention from the initial release is to keep commands lowercase, and names/moves/etc uppercase.  
- You can disobey this convention at will.  
- For readability purposes, the commands here will display some uppercase letters.   
`<ARGUMENT>` : When using angle brackets, it refers to a mandatory argument. You SHOULD NOT be writing these brackets in your routing files.  
`\[ARGUMENT\]` : when using square brackets, it refers to an optional argument. You can omit it if you don't need it. You SHOULD NOT be writing these brackets in your routing files.  

#### -- --


#### 4. MAKING A ROUTE FILE

##### 4.1 - COMMENTS
  `"//"` : Starts a comment. Either at the start of a line or at the end of instructions.  
           Used as documentation for the reader/router.  

##### 4.2 - GENERIC DISPLAY
###### 4.2.1 - Money :
  `"money"` : Displays the current Player money.  
  
###### 4.2.2 - Stats :
  `"ranges"` : Displays a table of the main Pokemon stats for all DV values.  
  `"stats"`  : Displays the main Pokemon stats as they are in the Pokemon menu.  
  
  **Stats options :**
  `"-b"` : Add to account for stat badge boosts.  

##### 4.3 - PLAYER POKEMON UTILITY
###### 4.3.1 - Player Pokemon :
  `"evolve <SPECIES>"` : Changes your Pokemon to `SPECIES`.  
  alias: `"e"`           Example : `evolve FERALIGATR`  
  
  `"learnMove <MOVE>"` : Learns move `MOVE`. `MOVE` is written with only letters (no spaces, no dashes, no underscores, etc.)  
  alias: `"lm"`          Example : `learnmove THUNDERBOLT`  
  
  `"unlearnMove <MOVE>"` : Unlearns move `MOVE`. `MOVE` is written with only letters (no spaces, no dashes, no underscores, etc.)  
  alias: `"um"`            Example : `unlearnmove LEER`  
  
  `"rareCandy"` : Uses a Rare Candy to your Pokemon.  
  alias: `"rc"`  
  
  `"hpup"`      : Uses an HP Up to your Pokemon.  
  `"protein"`   : Uses a Protein to your Pokemon.  
  `"iron"`      : Uses an Iron to your Pokemon.  
  `"calcium"`   : Uses a Calcium to your Pokemon.  
  `"carbos"`    : Uses a Carbos to your Pokemon.  
  
  `"returnPower <NUM>"` : Sets power NUM to Return. NUM wil be capped between `0` and `102`.  
  
###### 4.3.2 - Battle items :
  `"unequip"` : Unequips any held item.  
  
  These commands equip the desired **species-boosting** item.  
  Commands          Species         Boosted stats              Multiplier  
  `"lightBall"`   : Pikachu         Special Attack             x2  
  `"metalPowder"` : Ditto           Defense & Special Defense  x1.5  
  `"thickClub"`   : Cubone/Marowak  Attack                     x2  

  These commands equip the desired **type-boosting** item.  
  Commands           Boosted  
  `"blackBelt"`    : Fighting  
  `"blackGlasses"` : Dark  
  `"charcoal"`     : Fire  
  `"dragonScale"`  : Dragon (in Gen2, it's not the Dragon Fang due to a code error)  
  `"hardStone"`    : Rock  
  `"magnet"`       : Electric  
  `"metalcoat"`    : Steel  
  `"miracleSeed"`  : Grass  
  `"mysticWater"`  : Water  
  `"neverMeltIce"` : Ice  
  `"pinkBow"`      : Normal  
  `"poisonBarb"`   : Poison  
  `"polkadotBow"`  : Normal  
  `"sharpBeak"`    : Flying  
  `"silverPowder"` : Bug  
  `"softSand"`     : Ground  
  `"spellTag"`     : Ghost  
  `"twistedSpoon"` : Psychic  
  
###### 4.3.3 - Player money :
  `"buy <ITEM> \[QUANTITY\]"`  : Buys `ITEM` `QUANTITY` times. `ITEM` only in letters.  
  `"sell <ITEM> \[QUANTITY\]"` : Sells `ITEM` `QUANTITY` times.  
    NOTE : this only affects money, since there it is no inventory management.  
    Example : `buy XATTACK 46 // Smeargle route`  
  
  `"addMoney <NUM>"` : Adds `NUM` to player's money.  
                     Example : `addmoney 5000`  

  `"spendMoney <NUM>"` : Spends `NUM` money.  
                       Example : `spendmoney 350`  

  These commands don't affect your currently held item.  
  `"setAmuletCoin"`   : Activates the Amulet Coin effect (doubling money).  
  `"unsetAmuletCoin"` : Deactivates the Amulet Coin effect.  
    Note : You can both activate Amulet Coin and have an item equipped.  
           If your main Pokemon holds the Amulet Coin, the desired RouteTwo instructions are :  
           `unequip // unequips current held item`  
           `setAmuletCoin // activates Amulet Coin, still no held item`  
      
###### 4.3.4 - Badges :
  These commandes gives you the desired badge without fighting its Gym Leader.  
  This is useful when you route Pokemon you don't acquire/catch straight away.  
  Commands           Gym Leader  Stat boost  Type boost  
  `"zephyrbadge"`  : Falkner     Attack      Flying  
  `"hivebadge"`    : Bugsy       -           Bug  
  `"plainbadge"`   : Whitney     Speed       Normal  
  `"fogbadge"`     : Morty       -           Ghost  
  `"stormbadge"`   : Chuck       -           Fighting  
  `"mineralbadge"` : Jasmine     Defense     Steel  
  `"glacierbadge"` : Pryce       Special\*   Ice       (\*game has a Special Defense bug)  
  `"risingbadge"`  : Clair       -           Dragon  
  `"boulderbadge"` : Brock       -           Rock  
  `"cascadebadge"` : Misty       -           Water  
  `"thunderbadge"` : Surge       -           Electric  
  `"rainbowbadge"` : Erika       -           Grass  
  `"soulbadge"`    : Janine      -           Poison  
  `"marshbadge"`   : Sabrina     -           Psychic  
  `"volcanobadge"` : Blaine      -           Fire  
  `"earthbadge"`   : Blue        -           Ground  
  
###### 4.3.5 - Battle Tower :
  `"battletowerflag"` : Activates battle tower mode. You CAN'T deactivate it afterwards.  
                     (gets rid of badge boosts within battles)  
  
##### 4.4 - BATTLES
###### 4.4.1 - Trainers :
  `"0x<NUM>"` : Triggers a trainer battle against the trainer with index `NUM`.  
  `"<NAME>"`  : Triggers a trainer battle against the trainer with name `NAME`.  
  
###### 4.4.2 - Wild encounters :
  `"L<NUM> <SPECIES>"` : Triggers a wild battle against a level `NUM` `SPECIES` with perfect DVs.  
  
  **Wild encounters options :**  
  `"<ATK> <DEF> <SPD> <SPC>"` : Gives DVs `ATK DEF SPD SPC` to the wild encounter.  
    Example : `L30 GYARADOS 15 10 10 10`  
  `"-trainer"` : Sets the wild encounter as a trainer Pokemon. Mainly gives access to the x1.5 experience multiplier.  
  alias: `"-t"`  
  
  `"-wild"`     : Sets the wild encounter as wild. A wild encounter is wild by default, this option can be omitted.  
  alias: `"-w"`  
      
###### 4.4.3 - Battle options :
  For all battle options, `x` refers to the player, `y` refers to the enemy.  
  Any option starting with `-x` can be written starting with `-y` to have the same effect on the enemy team.  
  
  `"-xitems <ATK>/<DEF>/<SPD>/<SPC>\[/ACC\]"` : Sets `ATK` X Attacks, `DEF` X Defends, etc.  
  alias: `"-x"`  Example : `RED -xitems 2/0/1/0 // sets 2 X Attacks & 1 X Speed`  

  `"-xatk <NUM>"`   : Sets `NUM` X Attacks for the entire fight.  
  `"-xdef <NUM>"`   : Sets `NUM` X Defends for the entire fight.  
  `"-xspd <NUM>"`   : Sets `NUM` X Speeds for the entire fight.  
  `"-xspatk <NUM>"` : Sets `NUM` X Specials for the entire fight.  
  alias: `"-xspc"`    Only applies to Special Attack.  
  `"-xspdef <NUM>"` : Boosts Special Defense `NUM` times. Useful for Amnesia, etc.  
  `"-xacc"`         : Sets an X Accuracy.  
    Example : `LANCE -xspd 1 -xspc 2 // sets 1 X Speed & 2 X Specials forthe entire fight`  
  
  `"-xatks <FIRST>\[/SECOND...\]"`   : Sets `FIRST` X Attacks for the 1st Pokemon, `SECOND` X Attacks for the 2nd, etc.  
  `"-xdefs <FIRST>\[/SECOND...\]"`   : Sets `FIRST` X Defends for the 1st Pokemon, `SECOND` X Defends for the 2nd, etc.  
  `"-xspds <FIRST>\[/SECOND...\]"`   : Sets `FIRST` X Speeds for the 1st Pokemon, `SECOND` X Speeds for the 2nd, etc.  
  `"-xspatks <FIRST>\[/SECOND...\]"` : Sets `FIRST` X Specials for the 1st Pokemon, `SECOND` X Specials for the 2nd, etc.  
  alias: `"-xspcs"`                  Only applies to Special Attack.  
  `"-xspdefs <FIRST>\[/SECOND...\]"` : Applies `FIRST` Special Defense boosts for the 1st Pokemon, `SECOND` Special Defense boosts for the 2nd, etc.  
    NOTE : Any missing value in the above syntaxes defaults to 0.  
    Example : `MORTY -xspds 0/1/1/1 // Sets up an X Speed on second Pokemon`  

  `"-bbs <ATK>/<DEF>/<SPD>/<SPC>"` : Sets up manual badge boosts. Useless for Gen2.  

  `"-sxp <NUM>"` : Divides all earned experience by `NUM`.  
  `"-sxps <FIRST>\[/SECOND...\]"` : Divides first enemy Pokemon experience by `FIRST`, the second by `SECOND`, etc.  
    NOTE : Any missing value in the above formula defaults to `1`.  
    Example : `CLAIR -sxps 1/2 // Doesn't change 1st Dragonair earned exp, divides 2nd Dragonair earned exp by 2, doesn't change remaining Pokemon earned exp.`  
 
  `"-weather <FIRST>\[/SECOND...\]"` : Sets the weather for the battle, or each enemy Pokemon.  
                                   Arguments should be NONE/RAIN/SUN/SANDSTORM (NONE can be replaced by 0).  
    Example : `ERIKA -weather NONE/NONE/SUN/SUN // Victreebel uses Sunny Day`  

  `"-xreflect <FIRST>\[/SECOND...\]"`    : Sets up Reflect for the player.  
  `"-xlightscreen <FIRST>\[/SECOND...\]"` : Sets up Light Screen for the player.  
                                       Arguments should be 0 or 1 (inactive or active).  
    Example : `SABRINA -yreflect 1/1/1 // Espeon uses Reflect`  

  `"-order <FIRST>\[/SECOND...\]"` : Switches the enemy team order. Useful for good AI trainers who send stronger Pokemon first against yours.  
    Example : `"BROCK -order 1/2/4/5/3 // Sends Graveler, Rhyhorn, Onix, Omastar, Kabutops. Initial order(desired order): Graveler(1), Rhyhorn(2), Omastar(4), Kabutops(5), Onix(3)`  

  `"-lvranges"`  : Outputs player Pokemon stats when a level up occurs during a battle.  
  `"-lvrangesb"` : Outputs player Pokemon stats accounting for badge boosts when a level up occurs during a battle.  

  `"-verbose <LEVEL>"` : Activates output for the desired battle.  
  alias: `"-v"`          Level should be NONE/SOME/ALL/EVERYTHING or 0/1/2/3.  
    NOTE : `-v 0` is equivalent to skipping output for the battle.  
	
#### -- --


#### -- 5. KNOWN ISSUES --
(from original RouteTwo)  

○ Some moves don't properly display damage or show falsified damage. This includes 1hit moves/fixed damage moves.  
○ Multi-hit moves only show the damage per 1 hit.  
○ This documentation was written without spell check. Kappa  

#### -- --


#### -- 6. TODOS --
(from original RouteTwo)  


○ Fix move damage displays for weird moves, like Dragon Rage.  
○ Add ability to indicate that a battle's EXP is split between some number of pokemon.  
○ Add ability to preserve move slot orders.  
○ Add ability to print strings into output.  

#### -- --


#### -- 7. CONTACT INFO AND ACKNOWLEDGEMENTS --

##### 7.1 - COMMUNITIES
[`PokemonSpeedruns` Discord server (archived)](https://discord.gg/0UUw8zDe2hWlwRsm)  

[`Gen 1-3 Pokemon Speedrunning` Discord server](https://discord.gg/NjQFEkc)  

##### 7.2 - CODERS
[`HRoll`](https://github.com/HRoll) [(2)](http://twitch.tv/hroll) - for making the original RouteOne which contributes 80% of the code for this  
 
[`Mountebank`](http://twitch.tv/mountebank) - for contributing to the development of the original RouteOne  

[`SpeedRunsLive`](http://speedrunslive.com) - for inspiration/awesome races  

[`Dabomstew`](https://github.com/Dabomstew) - for porting RouteOne to fit Gen 2  

[`entrpntr`](https://github.com/entrpntr) - for the attention to details and the various ideas  


#### -- --