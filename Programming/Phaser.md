# Image and Sprites

```js
this.load.image('image_key', 'filepath');
```

load an image in the cache (must be called during preload).

```js
this.add.image(x_value, y_value, 'image_key');
```

add an image (must be called during create).

```js
const sprite_object = this.add.sprite(x_value, y_value, 'image_key');
```

add a sprite from the provided image key (must be called during create).

```js
game_object.setOrigin(x_value, y_value);
```

set the anchor point for the game object _(value between 0 and 1)_.

# Audio

```js
this.load.audio('sound_key', 'filepath');
```

load a sound in the cache (must be called during preload).

```js
const sound_object = this.sound.add('sound_key');
```

add a sound (must be called during create).

```js
sound_object.play();
```

play a sound.

# Scene

```js
this.scene.restart();
```

restart the current scene.

```js
game_object.destroy();
```

remove a game object from the scene.

```js
this.scene.start('scene_key');
```

start a scene.

```js
this.scene.stop('scene_key');
```

stop a scene.

# Physics

## Configuration

```js
    physics: {
        default: 'arcade',
        arcade: {
            gravity: { y: gravity_value },
            debug: true
        }
    }
```

add physics/gravity to the game (must be added to the config object).

## Physics objects

```js
const sprite_object = this.physics.add.sprite(x_value, y_value, 'image_key');
```

add a sprite that will follow the physics of the game.

```js
const group_object = this.physics.add.staticGroup();
```

add a group of static objects.

```js
const group_object = this.physics.add.group();
```

add a group of physics enabled objects.

```js
const sprite_object = group.create(x_value, y_value, 'image_key');
```

add a sprite to the group.

## Movements

```js
physics_object.setCollideWorldBounds(true);
```

keep the physics object within the world bounds.

```js
this.physics.add.collider(physics_object_1, physics_object_2 [, callback]);
```

add a collider between two physics objects.

```js
this.physics.add.overlap(physics_object_1, physics_object_2 [, callback]);
```

add an overlap between two physics objects.

```js
physics_object.setVelocityX(x_value);
```

set the horizontal velocity of the physics object.

## Interactions

```js
physics_object.body.touching.<collision_direction>;
```

`True` when physics object is colliding with a body (static or not) in a given direction.
Values for direction are `none`, `up`, `down`, `left`, `right`.

# Inputs

## Game object interactions

```js
game_object.setInteractive();
```

enable gameObject interactions.

```js
game_object.on('event_value', () => { /* Code here */ });
```

Add an event listener to the gameObject.
Event can be `pointerup`, `pointerdown`, `pointerover` or `pointerout`.

## Key press events

```js
this.input.keyboard.on('event_value', () => { /* Code here */ });
```

add a key event handler.
Event can be `keydown-<key>` or `keyup-<key>`.

```js
const cursors_object = this.input.keyboard.createCursorKeys();
```

add a keyboard event listener.

```js
cursors_object.<cursor_key>.isDown
```

check if a specific cursor key is down.
Cursor key can be `up`, `down`, `left`, `right`, `shift` or `space`.

# Events

```js
this.time.addEvent({
    callback: () => { /* Code here */ },
    delay: value_in_ms,
    callbackScope: this,
    loop: true
});
```

add an event after `value_in_ms` ms and call `callback_function`. Loop when `loop` is `true`.

# Animations

## Sprite sheets

```js
this.load.spritesheet('spritesheet_key', 'filepath', 
    { frameWidth: width_value, frameHeight: height_value });
```

load a sprite sheet in the cache.

```js
this.anims.create({
    key: 'animation_key',
    frames: this.anims.generateFrameNumbers('spritesheet_key'.
        { start: start_value, end: end_value }),
    frameRate: frame_rate_value,
    repeat: -1
});
```

generate the animation provided.

```js
sprite_object.anims.play('animation_key' [, ignore_if_playing]);
```

play specified animation.

```js
sprite_object.flipX = true;
```

flip the direction of the sprite.

```js
sprite_object.anims.pause();
```

pause the animations for a sprite.

```js
this.anims.pauseAll();
```

pause all animations.

## Tweens

```js
const tween_object = this.tweens.add({
    targets: sprite_object,
    target_property: target_value,
    ease: 'easing_value',
    duration: value_in_ms,
    repeat: -1,
    yoyo: true,
    onStart: () => { /* Code here */ },
    onComplete: () => { /* Code here */ },
    onRepeat: () => { /* Code here */ },
    onYoyo: () => { /* Code here */ }
});
```

create a frame to frame transition.

```js
tween_object.play();
```

play the animation.

```js
tween_object.stop();
```

stop the animation.

# Camera

```js
this.cameras.main.setBounds(x_value, y_value, width_value, height_value);
```

set the bounds of the camera.

```js
this.physics.world.setBounds()
```

set the bounds of the physics world (best to match the camera bounds).

```js
this.camera.main.startFollow(target_object [, true, speed_value_for_x, speed_value_for_y, offset_x_value, offset_y_value]);
```

set the camera to follow the target object. Speed value is between 0 and 1.

```js
this.cameras.main.shake(duration_value_in_ms [, intensity_value, false, 
    (camera, progress) => { /* Code here */ }, callback_context]);
```

shake the camera.

```js
this.camera.main.fade(duration_value_in_ms [, red_value, green_value, blue_value, false, 
    (camera, progress) => { /* Code here */ }, callback_context]);
```

apply a fade transition from transparent to the provided color.

```js
game_object.setScrollFactor(x_value, y_value);
```

set the influence of the movement of a camera upon this game object.

# Documentation

| Links |
| --- |
| [Phaser Official](https://docs.phaser.io) |
| [Notes from Phaser](https://rexrainbow.github.io/phaser3-rex-notes/docs/site/) |
