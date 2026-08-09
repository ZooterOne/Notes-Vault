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

# Game Objects

```js
game_object.setOrigin(x_value, y_value);
```

set the anchor point for the game object _(value between 0 and 1)_.

```js
game_object.setTint(color_value);
```

set the tint for this game object.

```js
game_object.setDepth(depth_value);
```

set the depth for this game object. Default is _0_.

# Containers

```js
container_object = this.add.container([x_value, y_value, []]);
```

add a container.

```js
container_object(game_object | [game_objects]);
```

add game objects to the container.

```js
game_object = container_object.getAt(index_value);
```

get a game_object from the container.

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

```js
sprite_object = group_object.getFirstDead(true, x_value, y_value, 'image_key', 0, true);
```

get or create a sprite object from the group when possible.

```js
sprite_object.setActive(false).setVisible(false);
```

disable sprite object from the group.

```js
physics_object.disableBody(set_active_to_false, set_visible_to_false);
```

stop and disable physics object body.

## Movements

```js
physics_object.setVelocityX(x_value);
```

set the horizontal velocity of the physics object.

```js
const velocity_vector = this.physics.velocityFromRotation(angle_in_radians, speed_value);
```

get the velocity vector from an angle and speed.

```js
this.physics.moveTo(physics_object, x_value, y_value, speed_value);
```

move a physics object towards a target.

## Interactions

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

```js
const space_key = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.SPACE);
```

add specific key event listener.

## Mouse events

```js
this.input.once(Phaser.Input.Events.POINTER_DOWN, () => { /* Code here */ });
```

add pointer down event handler.

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
    frames: this.anims.generateFrameNumbers('spritesheet_key',
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

```js
sprite_object.once(Phaser.Animations.Events.ANIMATION_COMPLETE, () => { /* Code here */ });
```

run code once animation has completed.

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

## Particles

```js
const particles_object = this.add.particles('image_key', {
    x: { 
        min: min_value, 
        max: max_value },
    y: y_value,
    lifespan: value_in_ms,
    speedX: speed_value,
    speedY: { 
        min: min_value, 
        max: max_value },
    scale: { 
        start: start_value, 
        end: end_value },
    quantity: quantity_value,
    blendMode: 'ADD'
});
```

create a particles emitter object.

```js
particles_object.set<Property>(value);
```

update the particles emitter.

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
this.cameras.main.fade(duration_value_in_ms [, red_value, green_value, blue_value, false, 
    (camera, progress) => { /* Code here */ }, callback_context]);
```

apply a fade transition from transparent to the provided color.

```js
this.cameras.main.fadeOut(duration_value_in_ms [, red_value, green_value, blue_value,
    (camera, progress) => { /* Code here */ }, callback_context]);
```

apply a fade out transition to the provided color.

```js
this.cameras.main.once(Phaser.Cameras.Scene2D.Events.FADE_OUT_COMPLETE, () => { /* Code here */ });
```

run code once fade out has completed.

```js
game_object.setScrollFactor(x_value, y_value);
```

set the influence of the movement of a camera upon this game object.

# Data storage

```js
const value = this.registry.get(`key_value`);
```

get value from the registry.

```js
this.registry.set('key_value', value);
```

set value to the registry.

```js
const value_data = localStorage.getItem('key_value');
const value = JSON.parse(value_data)?.value ?? 0;
```

get value stored on disc.

```js
localStorage.setItem('key_value', JSON.stringify({ value: value}));
```

set value to store on disc.

# Documentation

| Links |
| --- |
| [Phaser Official](https://docs.phaser.io) |
| [Notes from Phaser](https://rexrainbow.github.io/phaser3-rex-notes/docs/site/) |
