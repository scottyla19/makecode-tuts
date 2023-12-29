# Free Throw Tutorial
### @explicitHints true
```customts
namespace SpriteKind {
    export const hoop = SpriteKind.create()
}


```
## Step 1: Draw your basketball court

You will need to do some initial setup including drawing your own basketball court as the background of your ``||scene||`` and setting the start score and timer.
Add the following to your code, then click the artist's palette to the left of the line of code to draw your court.


```python 
scene.set_background_image(img(""" """))
info.start_countdown(20)
info.set_score(0)
```

## Step 2: Add the player

Add your player to the game by adding a ``||sprite||`` variable and naming it ``myPlayer``. Remember to make it a ``||SpriteKind.player||`` and choose the image using the palette icon.
You'll also need to ``||Sprite.set_position||`` to be on the bottom-left of the screen, ``||Sprite.set_velocity||`` to be horizontal only, and make the player bounce off the walls using ``||Sprite.set_bounce_on_wall||``.

```python
myPlayer : Sprite = None
myPlayer = sprites.create(img(""" """), SpriteKind.player)
myPlayer.set_position(0, 128)
myPlayer.set_velocity(50, 0)
myPlayer.set_bounce_on_wall(True)
```

## Step 3: Make the hoop
Add a hoop to the game by adding a ``||sprite||`` variable and naming it ``myHoop``. Remember to make it a ``||SpriteKind.hoop||`` and draw the hoop using the palette icon.
Don't forget to ``||Sprite.set_position||`` in the top center of the screen.

```python
myPlayer : Sprite = None
myPlayer = sprite.create(img(""" """), SpriteKind.hoop)
myHoop.set_position(80, 15)
```

## Step 4: Allow the player to shoot
Have the player shoot a ``||SpiteKind.projectile||`` when the user presses the ``A`` button.
You will need to `def`ine a function to pass as the call back from the ``||controller.A.on_event||`` for the ``A`` button.
Don't forget to draw a basketball for the projectile sprite using the palette on this line.

```python
def on_event_pressed():
    sprites.create_projectile_from_sprite(img(""" """), myPlayer, 0, -100)
controller.A.on_event(ControllerButtonEvent.PRESSED, on_event_pressed)
```

## Step 5: Count made shots
You will need to increment (increase by 1) the ``||score||`` when your projectile ``||sprites.on_overlap||``s the ``||SpriteKind.hoop||``.
We will ``def``ine a function to handle the overlap that will update the score and destroy the projectile using a fun effect.

```python
def on_on_overlap(sprite, otherSprite):
    info.change_score_by(1)
    sprite.destroy(effects.fountain)
sprites.on_overlap(SpriteKind.projectile, SpriteKind.hoop, on_on_overlap)
```


    
