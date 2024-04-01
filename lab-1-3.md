
# Lab 1.3: Moving Sprites

## Overview @unplugged

Sprites are important entities in MakeCode Arcade, but they can be boring
if they only stay in one place.

In this lab, you will learn how to:

- Move sprites at a certain speed and direction.
- Make a sprite follow another sprite.
- Make a sprite bounce off the edges of the screen.

![Overview](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/overview-1-3.gif)

## Hero Sprite Movement

Add the correct block to your project so the player can control the
``||variables(sprites):heroSprite||`` with the directional pad.

**Step 1:** Go into the  ``||controller:Controller||`` drawer. 

-------------------------------

**Step 2:** Drag and place the ``||controller:move with buttons||`` 
block under your ``||variables(sprites):heroSprite||`` block.

-------------------------------

**Step 3:** Change ``||variables:mySprite||`` in the ``||controller:move||``
block to your ``||variables(sprites):heroSprite's||`` name.

```blocks
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
// @highlight
controller.moveSprite(heroSprite)
```

## Keep Sprite on Screen @unplugged

While the player can control the hero sprite, the player
can also cause the sprite to leave the screen.

![Sprite Stay](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/sprite-stay.gif)

This could be confusing to the player, so let's restrict the movement 
of the hero sprite so that it stays on the screen.

## Stay in Screen Block

From the ``||sprites:Sprites||`` drawer, add a 
``||sprites:set stay in screen ON||``
block to your project. 

~hint Reminder!
Don't forget to change mySprite
to the name of your hero sprite.
hint~

```blocks
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
// @highlight
heroSprite.setStayInScreen(true)
```

## The Chase is On! @unplugged

Another way to move sprites around the screen is to 
make one sprite follow another. 

![Srpite Follow](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/sprite-follow.gif)

In our project, let's have the enemy chase the hero.

## Follow Block

From the ``||sprites:Sprites||`` drawer, add a 
``||sprites:set follow||`` block to your project.

Change the sprite names appropriately. 

Think about about which sprite is chasing, and which sprite is being chased.

~hint Reminder!
Make sure the set follow block comes after setting
your heroSprite and enemySprite.
hint~

~hint Hint
Adjust the follow speed by clicking on the plus icon.
hint~

```blocks
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
// @highlight
enemySprite.follow(heroSprite)
```

## Velocity @unplugged

![Sprite Velocity](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/sprite-velocity.png)

## Sprite Velocity

Let's have the ``||variables(sprite):foodSprite||`` and 
``||variables(sprites):projectileSprite||`` move in opposite directions. 

**Step 1:** From the ``||sprites:Sprites||`` drawer, add two
``||sprites:set velocity to vx "50" vy "50"||``
blocks to your project.

-------------------------------

**Step 2:** Try different numbers for *vx* and *vy*.

~hint Make a Sprite Move
- North (Up)
- South (Down)
- East (Right)
- West (Left)
- Northeast
- Southeast
- Southwest
- Northwest
hint~

```blocks
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
enemySprite.follow(heroSprite, 100)
let foodSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 8 8 8 8 8 8 8 8 1 
    1 8 8 1 1 1 1 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 1 1 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 8 8 8 8 8 8 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Food)
foodSprite.setPosition(40, 90)
// @highlight
foodSprite.setVelocity(0, 0)
let projectileSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 7 7 7 7 7 7 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 f 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 7 7 7 7 7 7 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Projectile)
projectileSprite.setPosition(120, 30)
// @highlight
projectileSprite.setVelocity(0, 0)
```

## Bouncy Ball
Now, let's add a fifth ``||sprites:sprite||`` to your project. In these instructions,
it will be called a ``||variables(sprites):bouncyBall||``. You might come up with 
a different name depending on the story for your game.

**Step 1:** Add a new ``||sprites:sprite||`` to your
project.

-------------------------------

**Step 2:** Give the ``||sprites:sprite||`` the name ``||variables(sprites):bouncyBall||``.

-------------------------------

**Step 3:** Draw a ball for your ``||sprites:sprite||``.

-------------------------------

**Step 4:** Set its kind to a *new* ``||sprites:kind of "Ball"||``.

-------------------------------

**Step 5:** Give the ball a specific ``||sprites:velocity||``.

```blocks
namespace SpriteKind {
    export const Ball = SpriteKind.create()
}
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
enemySprite.follow(heroSprite, 100)
let foodSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 8 8 8 8 8 8 8 8 1 
    1 8 8 1 1 1 1 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 1 1 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 8 8 8 8 8 8 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Food)
foodSprite.setPosition(40, 90)
foodSprite.setVelocity(0, 0)
let projectileSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 7 7 7 7 7 7 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 f 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 7 7 7 7 7 7 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Projectile)
projectileSprite.setPosition(120, 30)
projectileSprite.setVelocity(0, 0)
let bouncyBall = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 9 9 9 9 9 9 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f 9 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 9 9 9 9 9 9 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Ball)
// @highlight
bouncyBall.setVelocity(0, 0)
```

## Keep Bouncy Ball On Screen

Let's keep the ball on the screen. We just learned about a 
block that keeps a sprite on the screen, so let's use that one.

**Step 1:** Add the appropriate block to your project.

-----------------------------

**Step 2:** Change the ``||variables:name||`` of the sprite in the block to
match the ``||variables(sprites):bouncyBall||`` sprite's name.

```blocks
namespace SpriteKind {
    export const Ball = SpriteKind.create()
}
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
enemySprite.follow(heroSprite, 100)
let foodSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 8 8 8 8 8 8 8 8 1 
    1 8 8 1 1 1 1 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 1 1 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 8 8 8 8 8 8 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Food)
foodSprite.setPosition(40, 90)
foodSprite.setVelocity(0, 0)
let projectileSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 7 7 7 7 7 7 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 f 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 7 7 7 7 7 7 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Projectile)
projectileSprite.setPosition(120, 30)
projectileSprite.setVelocity(0, 0)
let bouncyBall = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 9 9 9 9 9 9 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f 9 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 9 9 9 9 9 9 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Ball)
bouncyBall.setVelocity(0, 0)
// @highlight
bouncyBall.setStayInScreen(true)
```

## Not So Bouncy, Ball @unplugged

That's a little better, but the ball is not vey bouncy.

![Not Bouncy Ball](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/no-bouce-ball.gif)

Let's try something else.

## Bounce on Wall Block

**Step 1:** Delete the block that you just added that keeps the ball on the screen.

~hint Hint!
One way to delete a block is to select it. Notice the yellow border
around the block. Once you see this, prees the Backspace or Delete key
on your keyboard
hint~

----------------------------

**Step 2:** In its place, add a ``||sprites:set bounce on wall ON||``
block.

----------------------------

**Step 3:** Change the ``||variables:name||`` of the sprite in the block to
match the ``||variables(sprites):bouncyBall||`` sprite's name.

Wait for the simulator to restart, then watch the ball. How does it act now?

```blocks
namespace SpriteKind {
    export const Ball = SpriteKind.create()
}
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
enemySprite.follow(heroSprite, 100)
let foodSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 8 8 8 8 8 8 8 8 1 
    1 8 8 1 1 1 1 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 1 1 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 8 8 8 8 8 8 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Food)
foodSprite.setPosition(40, 90)
foodSprite.setVelocity(0, 0)
let projectileSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 7 7 7 7 7 7 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 f 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 7 7 7 7 7 7 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Projectile)
projectileSprite.setPosition(120, 30)
projectileSprite.setVelocity(0, 0)
let bouncyBall = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 9 9 9 9 9 9 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f 9 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f 9 9 f 9 9 1 
    1 9 9 f f f f 9 9 1 
    1 9 9 9 9 9 9 9 9 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Ball)
bouncyBall.setVelocity(0, 0)
// @highlight
bouncyBall.setBounceOnWall(true)
```

## Bouncy Ball Mania

Now, let's add a bunch of bouncy balls to our project. Instead of having them
appear all at once at the start of the game, though, we'll add them gradually.

**Step 1:** From the ``||game:Game||`` drawer, drag an 
``||game:on game update every "500" ms||``
block and drop it on a blank area of your canvas.

--------------------------------

**Step 2:** Move the blocks that create the bouncy ball out of your 
``||loops:on start||`` block and into the new 
``||game:on game update||`` block. 

--------------------------------

**Step 3:** Change the number in the ``||game:on game update||`` from `500` ms to 
`5000` ms (5 seconds).

```blocks
namespace SpriteKind {
    export const Ball = SpriteKind.create()
}
let bouncyBall: Sprite = null
let heroSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 2 2 2 2 2 2 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 1 1 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 1 2 2 1 2 2 1 
    1 2 2 2 2 2 2 2 2 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Player)
heroSprite.setPosition(40, 30)
controller.moveSprite(heroSprite)
heroSprite.setStayInScreen(true)
let enemySprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 5 5 5 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f 5 5 5 5 5 1 
    1 5 5 f f f f 5 5 1 
    1 5 5 5 5 5 5 5 5 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Enemy)
enemySprite.setPosition(120, 90)
enemySprite.follow(heroSprite, 100)
let foodSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 8 8 8 8 8 8 8 8 1 
    1 8 8 1 1 1 1 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 1 1 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 1 8 8 8 8 8 1 
    1 8 8 8 8 8 8 8 8 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Food)
foodSprite.setPosition(40, 90)
foodSprite.setVelocity(0, 0)
let projectileSprite = sprites.create(img`
    . 1 1 1 1 1 1 1 1 . 
    1 7 7 7 7 7 7 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 f 7 7 1 
    1 7 7 f f f f 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 f 7 7 7 7 7 1 
    1 7 7 7 7 7 7 7 7 1 
    . 1 1 1 1 1 1 1 1 . 
    `, SpriteKind.Projectile)
projectileSprite.setPosition(120, 30)
projectileSprite.setVelocity(0, 0)
// @highlight
game.onUpdateInterval(5000, function () {
    bouncyBall = sprites.create(img`
        . 1 1 1 1 1 1 1 1 . 
        1 9 9 9 9 9 9 9 9 1 
        1 9 9 f f f f 9 9 1 
        1 9 9 f 9 9 f 9 9 1 
        1 9 9 f f f 9 9 9 1 
        1 9 9 f 9 9 f 9 9 1 
        1 9 9 f 9 9 f 9 9 1 
        1 9 9 f f f f 9 9 1 
        1 9 9 9 9 9 9 9 9 1 
        . 1 1 1 1 1 1 1 1 . 
        `, SpriteKind.Ball)
    bouncyBall.setVelocity(0, 0)
    bouncyBall.setBounceOnWall(true)
})
```

## Update your Story

You have a new character (or, at least a new sprite) in your project.
Update the story for your project to reflect the addition of the 
new sprite.
