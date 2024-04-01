# Lab 1.5: Eat Some More!

## Overview @unplugged

You will be adding additional enemy features and a bonus items
to the game from the previous lab.

![Overview](https://github.com/rymc88/Lab-1-5/blob/master/img/overview.gif?raw=true)

In this lab, you will learn to:
- Detect collisions between different sprites.
- Destroy a sprite with effects.
- Set and update player lives.

## Starting Out

Your player doesn't have to start with only 3 lives. You can change the
number of lives they start with. More lives allow the game to last longer, 
while fewer lives make it trickier to play.

**Step 1:** From the ``||info:Info||`` drawer, add a ``||info:set life to "3"||`` block to 
your ``||loops:on start||`` block. 

**Step 2:** Change the number of lives to make the game work the way you want.

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
enemySprite.setPosition(randint(8, 152), randint(8, 112))
enemySprite.setVelocity(randint(-100, 100), randint(-100, 100))
enemySprite.setBounceOnWall(true)
// @highlight
info.setLife(5)
```

## New Kinds of Food

Different kinds of sprites can do different things. We'll add a new kind of sprite
which, when "eaten" by the player, gives them an extra life.

**Step 1:** From the ``||game: Game||`` drawer, add an ``||game: on game update every "500" ms||``
block to your project. Set the time from `500` to `10000` ms.

~hint Reminder
1000 millisecond = 1 second
hint~

------------------------------

**Step 2:** From the ``||sprites: Sprites||`` drawer, add a ``||sprites: sprite of kind "extraLife"||``
to the new ``||game: on game update||`` block. 

-----------------------------

**Step 3:** Name this ``||variables: sprite||`` whatever you want and select
any image.

----------------------------

**Step 4:** From the ``||sprites: Sprites||`` drawer, add a ``||sprites: set position||``
block to your new ``||game: on game update||`` block. Set the position to be ``||math: random||``.

---------------------------

**Step 5:** From the ``||sprites: Sprites||`` drawer, add a ``||sprites: set velocity||``
block to your new ``||game: on game update||`` block. Set the velocity to be ``||math: random||``.

```blocks
namespace SpriteKind {
    export const extraLife = SpriteKind.create()
}
let lifeSprite: Sprite = null
game.onUpdateInterval(10000, function () {
    lifeSprite = sprites.create(img`
        . . 1 1 . . . 1 1 . . 
        . 1 2 2 1 . 1 2 2 1 . 
        1 2 3 2 2 1 2 2 2 2 1 
        1 2 3 2 2 2 2 2 2 2 1 
        1 2 2 2 2 2 2 2 2 2 1 
        . 1 2 2 2 2 2 b 2 1 . 
        . . 1 2 2 2 b 2 1 . . 
        . . . 1 2 2 2 1 . . . 
        . . . . 1 2 1 . . . . 
        . . . . . 1 . . . . . 
        `, SpriteKind.extraLife)
    lifeSprite.setPosition(randint(8, 152), randint(8, 112))
    lifeSprite.setVelocity(randint(-20, 20), randint(-20, 20))
```

## Player Overlaps Extra Life

Add a new ``||sprites: on overlaps||`` block to your game. Set it so it will
run when a ``||variables: sprite||`` ``||sprites: of kind "Player"||`` with
an ``||variables: otherSprite||`` ``||sprites: of kind "extraLife"||``. 

Then add blocks so: 
- The ``||variables:lifeSprite||`` is destroyed.
- ``||info:Lives||`` are increased by 1.

## Special Effects

Whenever sprites are destroyed, you can add an effect that makes it more
interesting. Make the following changes:

**Step 1:** Find the ``||sprites: on overlaps||`` block between the Player and Food sprites.

-----------------------------

**Step 2:** Click the plus sign at the end of the ``||sprites:destroy||`` block.

--------------------------

**Step 3:** Select an ``||sprites:effect||`` that makes sense to you and the duration you want.

--------------------------

**Step 4:** Make a similar change when an Extra Life sprite is eaten by the Player.

```blocks
namespace SpriteKind {
    export const extraLife = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.extraLife, function (sprite, otherSprite) {
    // @highlight
    sprites.destroy(otherSprite, effects.hearts, 500)
    info.changeLifeBy(1)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    // @highlight
    sprites.destroy(otherSprite, effects.smiles, 1000)
    info.changeScoreBy(1)
})
```

## Auto-Destruct Sequence!

Sprites continue to move even when they aren't visible on the screen. If they are
moving and never come back, you can destroy them automatically.

**Step 1:** From the ``||sprites: Sprites||`` drawer, add a ``||sprites: set auto destroy OFF||``
block to the ``||game: on game update||`` block where you create the ``||variables:lifeSprite||.

--------------------

**Step 2:** Set the ``||variables(sprites): mySprite||`` field to the name of the 
``||variables:lifeSprite||`` you are creating. 

---------------------

**Step 3:** Change OFF to ``||loops(sprites): ON||``.

Now whenever an extraLife sprite leaves the screen without being eaten, it will
automatically be destroyed.

```blocks
namespace SpriteKind {
    export const extraLife = SpriteKind.create()
}
let lifeSprite: Sprite = null
game.onUpdateInterval(10000, function () {
    lifeSprite = sprites.create(img`
        . . 1 1 . . . 1 1 . . 
        . 1 2 2 1 . 1 2 2 1 . 
        1 2 3 2 2 1 2 2 2 2 1 
        1 2 3 2 2 2 2 2 2 2 1 
        1 2 2 2 2 2 2 2 2 2 1 
        . 1 2 2 2 2 2 b 2 1 . 
        . . 1 2 2 2 b 2 1 . . 
        . . . 1 2 2 2 1 . . . 
        . . . . 1 2 1 . . . . 
        . . . . . 1 . . . . . 
        `, SpriteKind.extraLife)
    lifeSprite.setPosition(randint(8, 152), randint(8, 112))
    lifeSprite.setVelocity(randint(-20, 20), randint(-20, 20))
    // @highlight
    lifeSprite.setFlag(SpriteFlag.AutoDestroy, true)
```

## See Sprites Destroyed

You can see how often the sprites are destroyed.

**Step 1:** From the ``||sprites: Sprites||`` drawer, add an ``||sprites: on destroyed of kind "Player"||``
block. Change the kind to ``||sprites: "extraLife"||``.

--------------------

**Step 2:** Add a ``||sprites: sprite say||`` block to this event handler and make your
``||variables:enemySprite||`` say "Bye!".

-------------------

**Step 3:** Click the plus sign and set the duration to "500" ms, so it flashes
"Bye!" every time an ``||variables:lifeSprite||`` is destroyed.

```blocks
namespace SpriteKind {
    export const extraLife = SpriteKind.create()
}
sprites.onDestroyed(SpriteKind.extraLife, function (sprite) {
    enemySprite.sayText("Bye!", 500, true)
})
let enemySprite: Sprite = null
```

## Enemies Get Hungry, Too! @unplugged

Every time the Enemy eats Food or Extra Life, the player's score should go down!

![Enemy Overlaps Food & Life](https://github.com/rymc88/Lab-1-5/blob/master/img/enemy-overlaps-food-life.gif?raw=true)

## Let the Enemy Eat

Add a new ``||sprites: on overlaps||`` block to your project. Set
it so it will run when a ``||variables: sprite||`` ``||sprites: of kind "Enemy"||``
overlaps with an ``||variables: otherSprite||`` ``||sprites: of kind "Food"||``.

Then add blocks so:
- The ``||variables: foodSprite||`` is destroyed with some effect. This should be different from
the effect when a Player eats the Food.
- The player's ``||info: score||`` is reduced.

## No Extra Life for You!

Add a new ``||sprites: on overlaps||`` block to your project. Set
it so it will run when a ``||variables: sprite||`` ``||sprites: of kind "Enemy"||``
overlaps with an ``||variables: otherSprite||`` ``||sprites: of kind "extraLife"||``.

Then add blocks so:
- Destroy the ``||variables: lifeSprite||`` with an effect. This should be 
a different from when a Player eats the Extra Life.
- The player's ``||info: score||`` is reduced.

## Bonus Additions

Of course, there are a lot of other things you can do with your game. 
For some bonus points, here are some things you can add:

- Add other new sprite kinds to do different things in your game.
- Add other Food sprites which act the same but have different pictures.
- Design your own sprites or backgrounds.