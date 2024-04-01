# Lab 1.4: Eat It All!

## Overview @unplugged

Today you will write a game where the player must eat all the food which
appears, while avoiding an enemy that bounces around the screen!

![Overview](https://github.com/rymc88/Lab-1-4/blob/master/img/overview.gif?raw=true)

In this lab, you will learn to:

- Detect collisions between different sprites.
- Make sprites appear in random locations.
- Adjust the score and player lives.

## Every 3 Seconds

You will first learn how to make sprites appear regularly at random
locations using the ``||game:on game update every "x" ms||`` and
``||math:pick random||``.

**Step 1:** From the ``||game:Game||`` drawer, add an
``||game:on game update every "500" ms||`` to your project.

-------------------------------

**Step 2:** Change time from `500` ms to `3000` ms in the ``||game:on game update||`` block.

-------------------------------

**Step 3:** From the ``||sprites:Sprite||`` drawer, add a ``||sprites:sprite of kind "Food"||``
to the ``||game:on game update every "3000" ms"||`` block.

-------------------------------

**Step 4:** Name this ``||variables(sprites):sprite||`` whatever you want and
select any image from the gallery you would like.

```blocks
let foodSprite: Sprite = null
game.onUpdateInterval(3000, function () {
    foodSprite = sprites.create(img`
        . . . . . . b b b b . . . . . . 
        . . . . . . b 4 4 4 b . . . . . 
        . . . . . . b b 4 4 4 b . . . . 
        . . . . . b 4 b b b 4 4 b . . . 
        . . . . b d 5 5 5 4 b 4 4 b . . 
        . . . . b 3 2 3 5 5 4 e 4 4 b . 
        . . . b d 2 2 2 5 7 5 4 e 4 4 e 
        . . . b 5 3 2 3 5 5 5 5 e e e e 
        . . b d 7 5 5 5 3 2 3 5 5 e e e 
        . . b 5 5 5 5 5 2 2 2 5 5 d e e 
        . b 3 2 3 5 7 5 3 2 3 5 d d e 4 
        . b 2 2 2 5 5 5 5 5 5 d d e 4 . 
        b d 3 2 d 5 5 5 d d d 4 4 . . . 
        b 5 5 5 5 d d 4 4 4 4 . . . . . 
        4 d d d 4 4 4 . . . . . . . . . 
        4 4 4 4 . . . . . . . . . . . . 
        `, SpriteKind.Food)
})
```

## Start Wherever

Now, let's give the ``||variables(sprites):foodSprite||`` a random position
on the screen.

**Step 1:** From the ``||sprites:Sprites||`` drawer, add a ``||sprites:set position||``
block to ``||game:on game update||``.

--------------------------

**Step 2:** From the ``||math:Math||`` drawer, add a ``||math:pick random "0" to "10"||``
to your project.

--------------------------

**Step 3:** Connect it to the "X" entry in your ``||sprites:set position||`` block.
Set the numbers to `8` and `152`.

--------------------------

**Step 4:** Add a second ``||math:pick random||`` block to the "Y" entry in your
``||sprites:set position||`` block. Set the numbers to `8` and `112`.

```blocks
let foodSprite: Sprite = null
game.onUpdateInterval(3000, function () {
    foodSprite = sprites.create(img`
        . . . . . . b b b b . . . . . . 
        . . . . . . b 4 4 4 b . . . . . 
        . . . . . . b b 4 4 4 b . . . . 
        . . . . . b 4 b b b 4 4 b . . . 
        . . . . b d 5 5 5 4 b 4 4 b . . 
        . . . . b 3 2 3 5 5 4 e 4 4 b . 
        . . . b d 2 2 2 5 7 5 4 e 4 4 e 
        . . . b 5 3 2 3 5 5 5 5 e e e e 
        . . b d 7 5 5 5 3 2 3 5 5 e e e 
        . . b 5 5 5 5 5 2 2 2 5 5 d e e 
        . b 3 2 3 5 7 5 3 2 3 5 d d e 4 
        . b 2 2 2 5 5 5 5 5 5 d d e 4 . 
        b d 3 2 d 5 5 5 d d d 4 4 . . . 
        b 5 5 5 5 d d 4 4 4 4 . . . . . 
        4 d d d 4 4 4 . . . . . . . . . 
        4 4 4 4 . . . . . . . . . . . . 
        `, SpriteKind.Food)
    // @highlight
    foodSprite.setPosition(randint(8, 152), randint(8, 112))
})
```

## Hero Sprite

From the ``||sprites:Sprites||`` drawer, add a ``||sprites:sprite of kind "Player"||``
to your ``||loops:on start||`` block. 

Name it whatever you want and select whatever image
you want. Then add blocks so the Player:

- Starts in the middle of the screen.
- Stays on the screen.
- Moves with the buttons.

```blocks
let heroSprite = sprites.create(img`
    . . . . . . f f f f . . . . . . 
    . . . . f f f 2 2 f f f . . . . 
    . . . f f f 2 2 2 2 f f f . . . 
    . . f f f e e e e e e f f f . . 
    . . f f e 2 2 2 2 2 2 e e f . . 
    . . f e 2 f f f f f f 2 e f . . 
    . . f f f f e e e e f f f f . . 
    . f f e f b f 4 4 f b f e f f . 
    . f e e 4 1 f d d f 1 4 e e f . 
    . . f e e d d d d d d e e f . . 
    . . . f e e 4 4 4 4 e e f . . . 
    . . e 4 f 2 2 2 2 2 2 f 4 e . . 
    . . 4 d f 2 2 2 2 2 2 f d 4 . . 
    . . 4 4 f 4 4 5 5 4 4 f 4 4 . . 
    . . . . . f f f f f f . . . . . 
    . . . . . f f . . f f . . . . . 
    `, SpriteKind.Player)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
```

## Enemy Sprite

From the ``||sprites:Sprites||`` drawer, add a ``||sprites:sprite of kind "Enemy"||``
to your ``||loops:on start||`` block. 

Name it whatever you want and select whatever image
you want. Then add blocks so the Enemy:

- Starts in a random location.
- Moves with a random velocity.
- Bounces off the edges of the screen.

```blocks
let heroSprite = sprites.create(img`
    . . . . . . f f f f . . . . . . 
    . . . . f f f 2 2 f f f . . . . 
    . . . f f f 2 2 2 2 f f f . . . 
    . . f f f e e e e e e f f f . . 
    . . f f e 2 2 2 2 2 2 e e f . . 
    . . f e 2 f f f f f f 2 e f . . 
    . . f f f f e e e e f f f f . . 
    . f f e f b f 4 4 f b f e f f . 
    . f e e 4 1 f d d f 1 4 e e f . 
    . . f e e d d d d d d e e f . . 
    . . . f e e 4 4 4 4 e e f . . . 
    . . e 4 f 2 2 2 2 2 2 f 4 e . . 
    . . 4 d f 2 2 2 2 2 2 f d 4 . . 
    . . 4 4 f 4 4 5 5 4 4 f 4 4 . . 
    . . . . . f f f f f f . . . . . 
    . . . . . f f . . f f . . . . . 
    `, SpriteKind.Player)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
// @highlight
let enemySprite = sprites.create(img`
    ........................
    ........................
    ........................
    ........................
    ..........ffff..........
    ........ff1111ff........
    .......fb111111bf.......
    .......f11111111f.......
    ......fd11111111df......
    ......fd11111111df......
    ......fddd1111dddf......
    ......fbdbfddfbdbf......
    ......fcdcf11fcdcf......
    .......fb111111bf.......
    ......fffcdb1bdffff.....
    ....fc111cbfbfc111cf....
    ....f1b1b1ffff1b1b1f....
    ....fbfbffffffbfbfbf....
    .........ffffff.........
    ...........fff..........
    ........................
    ........................
    ........................
    ........................
    `, SpriteKind.Enemy)
// @highlight
enemySprite.setPosition(randint(8, 152), randint(8, 112))
// @highlight
enemySprite.setVelocity(randint(-100, 100), randint(-100, 100))
// @highlight
enemySprite.setBounceOnWall(true)
```
## Sprite Collisions @unplugged

When two sprites are drawn so that one overlaps the other, it is called a
**sprites collision**.

![Sprite Collision](https://github.com/rymc88/Lab-1-4/blob/master/img/sprite-collisions.gif?raw=true)

Sprites collisions are an important part of all games. Without them, nothing
happens in a game.


## Player Overlaps Enemy

Add an ``||sprites:on sprite overlaps||`` block to your game. 

**Step 1:** Set it so it will run when a ``||variables:sprite||`` ``||sprites: of kind "Player"||``
overlaps with an ``||variables:otherSprite||`` ``||sprites: of kind "Enemy"||``.

----------------------------

**Step 2:** Drag the red ``||variables:otherSprite||`` block from the top of the
``||sprites:overlaps||`` block and connect it to ``||variables:mySprite||``
space in the ``||sprites:set position||`` & ``||sprites:set velocity||`` block.

----------------------------

**Step 3:** The ``||variables:otherSprite||`` (which is the ``||variables:enemySprite||``)
moves to a new ``||math:random||`` position with a new ``||math:random||`` velocity.

![Player Overlaps Enemy](https://github.com/rymc88/Lab-1-4/blob/master/img/player-overlaps-enemy.png?raw=true)

## Player Overlaps Food

Add another ``||sprites:on sprite overlaps||`` block to your game.

**Step 1:** Set it so it will run when a ``||variables:sprite||`` ``||sprites:of kind "Player"||``
overlaps with an ``||variables:otherSprite||`` ``||sprites:of kind "Food"||``.

-----------------------------

**Step 2:** Drag the red ``||variables:otherSprite||`` block from the top of the
``||sprites:overlaps||`` block and connect it to ``||variables:mySprite||``
space in the ``||sprites:destroy||`` block.

------------------------------

The ``||variables:otherSprite||`` (which is the ``||variables:foodSprite||``)
will be destroyed when the Player collides with it.

![Player Overlaps Food](https://github.com/rymc88/Lab-1-4/blob/master/img/player-overlaps-food.png?raw=true)

## Part 3: Points & Lives @unplugged

So far, your game has a player, an enemy, and some food to eat.

![Overlaps Completed](https://github.com/rymc88/Lab-1-4/blob/master/img/overlaps-completed.gif?raw=true)

Now let's add some scoring and lives.

## Lose A Life

Let's make the player lose a life when they collide with the enemy.

From the ``||info:Info||`` drawer, find the ``||info:change life by "-1"||``
block and add it to the appropriate ``||sprites:on overlaps||`` block.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    otherSprite.setPosition(randint(8, 152), randint(8, 112))
    otherSprite.setVelocity(randint(-100, 100), randint(-100, 100))
    // @highlight
    info.changeLifeBy(-1)
})
```

## Score A Point

Now, let's increase the score when the player collides with some food.

From the ``||info:Info||`` drawer, find the ``||info:change score by "1"||``
block and add it to the appropriate ``||sprites:on overlaps||`` block.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    // @highlight
    info.changeScoreBy(1)
```

## Bonus Additions

Here are some things you can add to your game which can make it more interesting
and personal.

- Make both the Player and Enemy relocate when they collide.
- Have the Player lose points if the Enemy collides with Food.
- Play a sound when the Enemy and Player collide, and when the
Player and Food collide.
- Design your own sprites.
- Add a background

What else can you think of?

```ghost
    music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
    music.play(music.createSong(hex`00780004080200`), music.PlaybackMode.UntilDone)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    music.play(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
    music.stopAllSounds()
```