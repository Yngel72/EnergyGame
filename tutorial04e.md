### @activities true

```template

namespace SpriteKind {
    export const Renewable = SpriteKind.create()
}

namespace myTiles {
    //% blockIdentity=images._tile
    export const tile0 = img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `
}

info.onCountdownEnd(function () {
    if (info.score() < 20) {
        game.over(false)
    } else {
        game.over(true)
    }
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    otherSprite.destroy()
    info.changeScoreBy(1)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Renewable, function (sprite, otherSprite) {
    tiles.placeOnRandomTile(otherSprite, assets.tile`transparency16`)
    info.changeScoreBy(1)
})
let offshoreWind: Sprite = null
let energy: Sprite = null
tiles.setTilemap(tiles.createTilemap(
            hex`3200320000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010101010101010101000000000000000000000000000000000000000000000000000000000000000000000000000000000001010101010101010101010100000000000000000000000000000000000000000000000000000000000000000000000000000101010101010101010101010101010100000000000000000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101010000000000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101010000000000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000000000101010101010101010101010101010101010100000000000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101010000000000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101010100000000000000000000000000000000000000000000000000000000000101010101010101010101010101010101010101010000000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000101010101010101010101010101010101010101010100000000000000000000000000000000000000000000000000000000010101010101010101010101010101010101010101010000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101010101000000000000000000000000000000000000000000000000000000000001010101010101010101010101010101010101010100000000000000000000000000000000000000000000000000000000000101010101010101010101010101010101010101000000020202020202020000000000000000000000000000000000000000000101010101010101010101010101010101010100000202020202020202020202020000000000000000000000000000000000000101010101010101010101010101010101000202020202020202020202020202020000000000000000000000000000000000000001010101010101010101010101010202020202020202020202020202020202000000000000000000000000000000000000000000000000000001010101010102020202020202020202020202020202020202000000000000000000000000000000000000000000000000000000000000000202020202020202020202020202020202020202000000000000000000000000000000000000000000000000000000000000020202020202020202020202020202020202020200000000000000000000000000000000000000000000000000000000000002020202020202020202020202020202020202020200000000000000000000000000000000000000000000000000000000000202020202020202020202020202020202020202020000000000000000000000000000000000000000000000000000000002020202020202020202020202020202020202020202000000000000000000000000000000000000000000000000000000020202020202020202020202020202020202020202020200000000000000000000000000000000000000000000000000000202020202020202020202020202020202020202020202020200000000000000000000000000000000000000000000000000020202020202020202020202020202020202020202020202020000000000000000000000000000000000000000000000000202020202020202020202020202020202020202020202020202000000000000000000000000000000000000000000000000020202020202020202020202020202020202020202020202020200000000000000000000000000000000000000000000000002020202020202020202020202020202020202020202020202020000000000000000000000000000000000000000000000020202020202020202020202020202020202020202020202020200000000000000000000000000000000000000000000000002020202020202020202020202020202020202020202020202020000000000000000000000000000000000000000000000000002020202020202020202020202020202020202020202020000000000000000000000000000000000000000000000000000000202020202020202020202020202020202020202020202000000000000000000000000000000000000000000000000000000000202020202020202020202020202020202020202020000000000000000000000000000000000000000000000000000000000000002020202020202020202020202020202020000000000000000000000000000000000000000000000000000000000000000000000000202020202020202020202000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000`,
            img`
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
            `,
            [myTiles.tile0,sprites.castle.tilePath5,sprites.castle.tileGrass1],
            TileScale.Sixteen
        ))

scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . f f f . f f f f . f f f . 
    f f f f f c c c c f f f f f 
    f f f f b c c c c b f f f f 
    f f f c 3 c c c c 3 c f f f 
    . f 3 3 c c c c c c 3 3 f . 
    . f c c c c 4 4 c c c c f . 
    . f f c c 4 4 4 4 c c f f . 
    . f f f b f 4 4 f b f f f . 
    . f f 4 1 f d d f 1 4 f f . 
    . . f f d d d d d d f f . . 
    . . e f e 4 4 4 4 e f e . . 
    . e 4 f b 3 3 3 3 b f 4 e . 
    . 4 d f 3 3 3 3 3 3 c d 4 . 
    . 4 4 f 6 6 6 6 6 6 f 4 4 . 
    . . . . f f f f f f . . . . 
    . . . . f f . . f f . . . . 
    `, SpriteKind.Player)
if (Math.percentChance(20)) {
    tiles.placeOnRandomTile(mySprite, sprites.castle.tilePath5)
} else {
    tiles.placeOnRandomTile(mySprite, sprites.castle.tileGrass1)
}
controller.moveSprite(mySprite)
scene.cameraFollowSprite(mySprite)
for (let index = 0; index < 100; index++) {
    energy = sprites.create(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . f f f f . . . . . 
        . . . . . . f f 5 5 f . . . . . 
        . . . . . . f 5 5 f f . . . . . 
        . . . . . f f 5 f f . . . . . . 
        . . . . f f 5 5 f f f . . . . . 
        . . . . f 5 5 5 5 5 f . . . . . 
        . . . . f f f f 5 5 f . . . . . 
        . . . . . . f 5 5 f f . . . . . 
        . . . . . f f 5 f f . . . . . . 
        . . . . . f 5 f f . . . . . . . 
        . . . . . f f f . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, SpriteKind.Food)
    if (Math.percentChance(80)) {
        tiles.placeOnRandomTile(energy, sprites.castle.tilePath5)
    } else {
        tiles.placeOnRandomTile(energy, sprites.castle.tileGrass1)
    }
}
for (let index = 0; index < 200; index++) {
    offshoreWind = sprites.create(img`
        . . . . . . . . . . 8 8 . . . . 
        . . . . . . . . . . 1 8 8 . . . 
        . . . . . . . 8 8 8 . 1 8 8 . . 
        . . . . . . . 8 1 8 8 . 1 8 . . 
        . . . . . . . 1 . 1 8 . . 8 . . 
        . . . . . . . . 8 8 8 . . 8 . . 
        . 8 8 8 8 8 8 8 1 1 1 . 8 8 . . 
        . 1 1 1 1 1 1 1 . . . 8 8 1 . . 
        . . 8 8 8 8 8 8 8 8 8 1 1 . . . 
        . . 1 1 1 1 1 1 1 1 1 . . . . . 
        . 8 8 8 8 8 8 8 8 8 8 . . . . . 
        . 1 1 1 1 1 1 1 1 1 1 8 8 . . . 
        . . 8 8 8 8 8 8 8 8 . 1 8 8 . . 
        . . 1 1 1 1 1 1 1 8 . . 1 8 . . 
        . . . . . . . . 8 8 . . . 8 . . 
        . . . . . . . . 1 1 . 8 8 1 . . 
        `, SpriteKind.Renewable)
    tiles.placeOnRandomTile(offshoreWind, assets.tile`transparency16`)
}
info.startCountdown(10)

```
# Animations - Bring your player character to life
## Introduction
### Introduction @unplugged

A little bit of extra code will help bring your player character to life. Click continue to learn how to do it. 

### Step 1
For the animation to play correctly, we need to force the game to update around three times per second.
For this, we need the block ``||Game.on game update every 500 ms||``. Get one from the ``||Game.Game||`` menu (under "Advanced") and change 500 to 300 ms.

```blocks
game.onUpdateInterval(300, function () {})
```

### Step 2

Now we need to play one animation per direction of movement. For this we need an ``||Logic.if-then-else||`` block from the ``||Logic.Logic||`` menu. Get one and place it inside your ``||Game.on game update every 300 ms||`` block.

```blocks
game.onUpdateInterval(300, function () {
    // @highlight
    if (true) {
	
} else {
	
}
})
```

### Step 3
CLick the little "+" sign in the lower left corner of your new ``||Logic.if-then-else||`` block until you have 5 gaps in your block. 
You now have what you need to set up an animation for each direction and for when you're standing still.

```blocks
game.onUpdateInterval(300, function () {
    // @highlight
    if (true) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```

### Step 4
Let's make your character walk to the left. 
Get a hexagonal ``||Controller.is A button pressed||`` block from the ``||Controller||`` menu and place it inside the topmost hexagon in the ``||Logic.if-then-else||`` block. Click the tiny downwards arrow to the left of where it says button "A" in the hexagon and choose "left" from the drop-down menu.

```blocks
game.onUpdateInterval(300, function () {
    // @highlight
    if (controller.left.isPressed()) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
```

### Step 5
Get an ``||Animation.animate mySprite frames interval||`` block from the ``||Animation.Animation||`` menu (under "Advanced") and place it inside the topmost gap of your ``||Logic.if-then-else||`` block.
```blocks
game.onUpdateInterval(300, function () {
    if (controller.left.isPressed()) {
        // @highlight
        animation.runImageAnimation(
        mySprite,
        [img`
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            `],
        500,
        false
        )
    } else if (false) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```
### Step 6
Change where it says 500 ms to 100 ms in the ``||Animation.animate mySprite||`` block and make sure it says ``||Animation.loop OFF||``at the bottoom of the block.

```blocks
game.onUpdateInterval(300, function () {
    if (controller.left.isPressed()) {
        // @highlight
        animation.runImageAnimation(
        mySprite,
        [img`
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            `],
        100,
        false
        )
    } else if (false) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
```
### Step 7
Click the grey square in the ``||Animation.animate mySprite||`` block. Choose "gallery" in the middle of the top of the screen. Notice how some of the thumbnails have small film icons at the bottom right? Hold your mouse pointer over these thumbnails to see the animation. Find your player character and click the animation where your character is walking towards the left.

```blocks
game.onUpdateInterval(300, function () {
    if (controller.left.isPressed()) {
        // @highlight
        animation.runImageAnimation(
        mySprite,
        [img`
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f e 4 4 c c c f f f f . 
            . f f e 4 4 f b f 4 4 f f . 
            . . f f d d f 1 4 d 4 f . . 
            . . . f d d d d 4 f f f . . 
            . . . f e 4 4 4 e e f . . . 
            . . . f 3 3 3 e d d 4 . . . 
            . . . f 3 3 3 e d d e . . . 
            . . . f 6 6 6 f e e f . . . 
            . . . . f f f f f f . . . . 
            . . . . . . f f f . . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f c 4 4 c c c f f f f . 
            . f f f 4 4 f b f 4 4 f f . 
            . . f f d d f 1 4 d 4 f . . 
            . . . f d d d e e f f f . . 
            . . . f e 4 e d d 4 f . . . 
            . . . f 3 3 e d d e f . . . 
            . . f f 6 6 f e e f f f . . 
            . . f f f f f f f f f f . . 
            . . . f f f . . . f f . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f c 4 4 c c c f f f f . 
            . f f f 4 4 f b f 4 4 f f . 
            . . f c d d f 1 4 d 4 f f . 
            . . . f d d d d 4 f f f . . 
            . . . f e 4 4 4 e d d 4 . . 
            . . . f 3 3 3 3 e d d e . . 
            . . f f 6 6 6 6 f e e f . . 
            . . f f f f f f f f f f . . 
            . . . f f f . . . f f . . . 
            `],
        100,
        false
        )
    } else if (false) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
```
### Step 8
Repeat step 5 through 7 for the three remaining directions. Remember to choose the correct animation and to set the time to 100 ms.
Inside the final gap of your ``||Logic.if-then-else||`` block, place a ``||Sprites.set mySprite image to||`` block and choose the gallery image where your player character is facing you.
```blocks
let mySprite: Sprite = null
game.onUpdateInterval(300, function () {
    if (controller.left.isPressed()) {
        animation.runImageAnimation(
        mySprite,
        [img`
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f e 4 4 c c c f f f f . 
            . f f e 4 4 f b f 4 4 f f . 
            . . f f d d f 1 4 d 4 f . . 
            . . . f d d d d 4 f f f . . 
            . . . f e 4 4 4 e e f . . . 
            . . . f 3 3 3 e d d 4 . . . 
            . . . f 3 3 3 e d d e . . . 
            . . . f 6 6 6 f e e f . . . 
            . . . . f f f f f f . . . . 
            . . . . . . f f f . . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f c 4 4 c c c f f f f . 
            . f f f 4 4 f b f 4 4 f f . 
            . . f f d d f 1 4 d 4 f . . 
            . . . f d d d e e f f f . . 
            . . . f e 4 e d d 4 f . . . 
            . . . f 3 3 e d d e f . . . 
            . . f f 6 6 f e e f f f . . 
            . . f f f f f f f f f f . . 
            . . . f f f . . . f f . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . . . . f f f f f . f f f . 
            . . . f f c c c c f f f f f 
            . . f c c c c c c b f f f f 
            . . f c c c c c c 3 c f f f 
            . f c c c c c c c c 3 3 f . 
            . f c c 4 c c c c c f f f . 
            . f f c 4 4 c c c f f f f . 
            . f f f 4 4 f b f 4 4 f f . 
            . . f c d d f 1 4 d 4 f f . 
            . . . f d d d d 4 f f f . . 
            . . . f e 4 4 4 e d d 4 . . 
            . . . f 3 3 3 3 e d d e . . 
            . . f f 6 6 6 6 f e e f . . 
            . . f f f f f f f f f f . . 
            . . . f f f . . . f f . . . 
            `],
        100,
        false
        )
    } else if (controller.up.isPressed()) {
        animation.runImageAnimation(
        mySprite,
        [img`
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c c c c c c c f . 
            . f f c c c c c c c c f f . 
            . f f f c c c c c c f f f . 
            . f f f f f f f f f f f f . 
            . . f f f f f f f f f f . . 
            . . e f f f f f f f f e . . 
            . e 4 f f f f f f f f 4 e . 
            . 4 d f 3 3 3 3 3 3 c d 4 . 
            . 4 4 f 6 6 6 6 6 6 f 4 4 . 
            . . . . f f f f f f . . . . 
            . . . . f f . . f f . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c c c c c c f f . 
            . f f c c c c c c c c f f . 
            . f f c c c c c c f f f f . 
            . f f f f f f f f f f f f . 
            . . f f f f f f f f f f . . 
            . . e f f f f f f f f e . . 
            . . e f f f f f f f f 4 e . 
            . . 4 f 3 3 3 3 3 e d d 4 . 
            . . e f f f f f f e e 4 . . 
            . . . f f f . . . . . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f f c c c c c c c c c f . 
            . f f c c c c c c c c f f . 
            . f f f f c c c c c c f f . 
            . f f f f f f f f f f f f . 
            . . f f f f f f f f f f . . 
            . . e f f f f f f f f e . . 
            . e 4 f f f f f f f f e . . 
            . 4 d d e 3 3 3 3 3 f 4 . . 
            . . 4 e e f f f f f f e . . 
            . . . . . . . . f f f . . . 
            `],
        100,
        false
        )
    } else if (controller.right.isPressed()) {
        animation.runImageAnimation(
        mySprite,
        [img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f f . . . . 
            f f f f f c c c c f f . . . 
            f f f f b c c c c c c f . . 
            f f f c 3 c c c c c c f . . 
            . f 3 3 c c c c c c c c f . 
            . f f f c c c c c 4 c c f . 
            . f f f f c c c 4 4 c f f . 
            . f f 4 4 f b f 4 4 f f f . 
            . f f 4 d 4 1 f d d c f . . 
            . . f f f 4 d d d d f . . . 
            . . 4 d d e 4 4 4 e f . . . 
            . . e d d e 3 3 3 3 f . . . 
            . . f e e f 6 6 6 6 f f . . 
            . . f f f f f f f f f f . . 
            . . . f f . . . f f f . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f f . . . . 
            f f f f f c c c c f f . . . 
            f f f f b c c c c c c f . . 
            f f f c 3 c c c c c c f . . 
            . f 3 3 c c c c c c c c f . 
            . f f f c c c c c 4 c c f . 
            . f f f f c c c 4 4 c f f . 
            . f f 4 4 f b f 4 4 f f f . 
            . . f 4 d 4 1 f d d f f . . 
            . . f f f e e d d d f . . . 
            . . . f 4 d d e 4 e f . . . 
            . . . f e d d e 3 3 f . . . 
            . . f f f e e f 6 6 f f . . 
            . . f f f f f f f f f f . . 
            . . . f f . . . f f f . . . 
            `,img`
            . f f f . f f f f f . . . . 
            f f f f f c c c c f f . . . 
            f f f f b c c c c c c f . . 
            f f f c 3 c c c c c c f . . 
            . f 3 3 c c c c c c c c f . 
            . f f f c c c c c 4 c c f . 
            . f f f f c c c 4 4 e f f . 
            . f f 4 4 f b f 4 4 e f f . 
            . . f 4 d 4 1 f d d f f . . 
            . . f f f 4 d d d d f . . . 
            . . . f e e 4 4 4 e f . . . 
            . . . 4 d d e 3 3 3 f . . . 
            . . . e d d e 3 3 3 f . . . 
            . . . f e e f 6 6 6 f . . . 
            . . . . f f f f f f . . . . 
            . . . . . f f f . . . . . . 
            `],
        100,
        false
        )
    } else if (controller.down.isPressed()) {
        animation.runImageAnimation(
        mySprite,
        [img`
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c 4 4 c c c c f . 
            . f f c c 4 4 4 4 c c f f . 
            . f f f b f 4 4 f b f f f . 
            . f f 4 1 f d d f 1 4 f f . 
            . . f f d d d d d d f f . . 
            . . e f e 4 4 4 4 e f e . . 
            . e 4 f b 3 3 3 3 b f 4 e . 
            . 4 d f 3 3 3 3 3 3 c d 4 . 
            . 4 4 f 6 6 6 6 6 6 f 4 4 . 
            . . . . f f f f f f . . . . 
            . . . . f f . . f f . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c 4 4 c c c c f . 
            . f f c c 4 4 4 4 c c f f . 
            . f f f b f 4 4 f b f f f . 
            . f f 4 1 f d d f 1 4 f f . 
            . . f f d d d d d 4 e f e . 
            . f e f f b b b e d d 4 e . 
            . e 4 f b 3 3 3 e d d e . . 
            . . . f 6 6 6 6 f e e . . . 
            . . . f f f f f f f . . . . 
            . . . f f f . . . . . . . . 
            `,img`
            . . . . . . . . . . . . . . 
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c 4 4 c c c c f . 
            . f f c c 4 4 4 4 c c f f . 
            . f f f b f 4 4 f b f f f . 
            . f f 4 1 f d d f 1 4 f f . 
            . e f e 4 d d d d d f f . . 
            . e 4 d d e b b b f f e f . 
            . . e d d e 3 3 b e f 4 e . 
            . . . e e f 6 6 6 6 f . . . 
            . . . . f f f f f f f . . . 
            . . . . . . . . f f f . . . 
            `],
        100,
        false
        )
    } else {
        // @highlight
        mySprite.setImage(img`
            . f f f . f f f f . f f f . 
            f f f f f c c c c f f f f f 
            f f f f b c c c c b f f f f 
            f f f c 3 c c c c 3 c f f f 
            . f 3 3 c c c c c c 3 3 f . 
            . f c c c c 4 4 c c c c f . 
            . f f c c 4 4 4 4 c c f f . 
            . f f f b f 4 4 f b f f f . 
            . f f 4 1 f d d f 1 4 f f . 
            . . f f d d d d d d f f . . 
            . . e f e 4 4 4 4 e f e . . 
            . e 4 f b 3 3 3 3 b f 4 e . 
            . 4 d f 3 3 3 3 3 3 c d 4 . 
            . 4 4 f 6 6 6 6 6 6 f 4 4 . 
            . . . . f f f f f f . . . . 
            . . . . f f . . f f . . . . 
            `)
    }
```
### Step 9
Congratulations! That's all of it! Now you know how to make your character move in a more life like fashion.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>

