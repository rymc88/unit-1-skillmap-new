# Lab 1.2: Sprites in the Corners

## Overview @unplugged

```ghost
let mySprite = sprites.create(img`.`, SpriteKind.Player)
mySprite.sayText(":)")
game.showLongText("", DialogLayout.Bottom)
```

In this lab, you will learn to:

- Add multiple sprites to your project.
- Make different sprite kinds.

![Overview](https://raw.githubusercontent.com/rymc88/unit-1-skillmap-new/master/img/overview-1-2.png)

## Hero Sprite

Let's create the first sprite of the project.

**Step 1:** Add your first ``||sprites:sprite||`` to the project. 
This will be your [***hero sprite***](# hero "The hero sprite represents the player.")
so give it an appropriate name. 

--------------------

**Step 2:** Draw an image for your ``||variables(sprites): heroSprite||``. Keep your image simple for now.
You can always come back and improve it later.

--------------------

**Step 3:** Place your ``||variables(sprites): heroSprite||`` in one of the corners of the screen using the
``||sprites:set position||`` block.

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
heroSprite.setPosition(0, 0)
```

## Enemy Sprite

Now, let's add a second sprite to your project.

**Step 1:** Drag a new ``||sprites:sprite||`` block into your 
project's ``||loops:on start||`` block. This will be your ``||variables(sprites): enemySprite||``
so give it an appropriate name.

--------------------

**Step 2:** Draw an image for your ``||variables(sprites): enemySprite||``. 

--------------------

**Step 3:** Set the Sprite Kind to ``||sprites: "Enemy"||``.

--------------------

**Step 4:** Place your ``||variables(sprites): enemySprite||`` in the corner opposite your hero sprite.

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
heroSprite.setPosition(0, 0)
// @highlight
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
// @highlight
enemySprite.setPosition(0, 0)
```



## Food Sprite

You now know how to add multiple sprites to your MakeCode Arcade projects.
Add another sprite to the project. 

**Step 1:** This will be the ``||variables(sprites):foodSprite||`` 
so give it an appropriate name.

--------------------

**Step 2:** Draw an image for your ``||variables(sprites):foodSprite||``.

--------------------

**Step 3:** Set the Sprite Kind to ``||sprites: "Food"||``.

--------------------

**Step 4:** Place your ``||variables(sprites):foodSprite||`` in one of the remaining empty corners.

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
// @highlight
foodSprite.setPosition(40, 90)
```

## Projectile Sprite

Add the last sprite to your project. 

**Step 1:** This will be the ``||variables(sprites): projectileSprite||``
so give it an appropriate name.

--------------------

**Step 2:** Draw an image for your ``||variables(sprites): projectileSprite||``.

--------------------

**Step 3:** Set the Sprite Kind to ``||sprites: "Projectile"||``.

--------------------

**Step 4:** Place your ``||variables(sprites): projectileSprite||`` in the last empty corner.

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
heroSprite.setPosition(0, 0)
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
enemySprite.setPosition(0, 0)
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
foodSprite.setPosition(0, 0)
// @highlight
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
// @highlight
projectileSprite.setPosition(0, 0)
```

## The Story

Now, we need a story! Your project contains four characters.
Construct a story that involves these four sprite types.

Include a [***synopsis***](# synopsis "A brief summary.") of the the story at the beginning of the game.
Use either a ``||sprites: say ":)"|`` block **and/or** 
``||game: show long text "___" ||`` block.

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
heroSprite.setPosition(0, 0)
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
enemySprite.setPosition(0, 0)
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
foodSprite.setPosition(0, 0)
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
projectileSprite.setPosition(0, 0)
// @highlight
heroSprite.sayText(":)")
// @highlight
game.showLongText("", DialogLayout.Bottom)
```