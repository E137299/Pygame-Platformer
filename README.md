# Pygame Platformer

In this project, you will create a 2D platform game using Pygame and object-oriented programming.

The game world scrolls left and right as the player moves. The player can:

* Walk left and right
* Jump onto platforms
* Fall if they miss the land

The world also contains **enemy characters** that:

* Walk back and forth on platforms
* Turn around at platform edges
* Never fall off the land


## Program Requirements

### General

* Use **Pygame**
* Use **at least 4 custom classes**
* Use `pygame.sprite.Sprite` for all game objects
* Use **sprite groups** to organize objects
* The screen must scroll when the player moves
* Enemies must patrol platforms without falling

---

## Required Classes

---
## `Land` (or `Scenery`) Class

### Purpose

Represents non-player objects that scroll when the player moves (sky, ground, platforms).


### Instance Variables

| Variable | Description                     |
| -------- | ------------------------------- |
| `image`  | Image loaded from a file        |
| `rect`   | Rectangle representing position |
| `x`, `y` | Position values                 |
| `speed`  | Scroll speed                    |

### Required Methods

#### `__init__(self, image_path, x, y, speed)`

* Loads an image
* Positions it on the screen
* Sets scrolling speed

#### `move_left(self)`

* Moves the object left
* Used when the player moves right

#### `move_right(self)`

* Moves the object right
* Used when the player moves left

---

## `Player` Class

### Purpose

Represents the user-controlled character.


### Instance Variables

| Variable     | Description             |
| ------------ | ----------------------- |
| `image`      | Current animation image |
| `rect`       | Player position         |
| `x`, `y`     | Player coordinates      |
| `moveY`      | Vertical movement value |
| `direction`  | `"left"` or `"right"`   |
| `jump_count` | Controls jump height    |
| `index`      | Animation frame index   |

### Required Methods

#### `__init__(self, x, y)`

* Loads all player images
* Sets initial position and state

#### `move_left(self)`

* Updates image and direction
* Moves player left

#### `move_right(self)`

* Updates image and direction
* Moves player right

#### `jump(self, land_group)`

* Moves the player upward
* Uses `jump_count` to limit jump height
* Displays jumping image

#### `gravity(self)`

* Pulls player downward
* Causes player to fall if not touching land
* Ends the game if the player falls off the screen

#### `stand(self)`

* Sets player to idle image

---

##  `Enemy` Class

### Purpose

Represents an enemy that **walks back and forth on platforms** without falling off. The enemy kills the player if the two touch.


### Instance Variables

| Variable    | Description               |
| ----------- | ------------------------- |
| `image`     | Enemy sprite              |
| `rect`      | Enemy position            |
| `x`, `y`    | Coordinates               |
| `speed`     | Horizontal movement speed |
| `direction` | `"left"` or `"right"`     |

### Required Methods

#### `__init__(self, x, y)`

* Loads enemy image
* Sets starting position
* Chooses initial direction

#### `move(self, land_group)`

* Moves enemy left or right
* Reverses direction when:

  * Reaching the edge of a platform
  * About to step off land

#### `check_ground(self, land_group)`

* Returns `True` if enemy is still on land
* Used to prevent falling

 Enemies must **never fall off platforms**

---

## Required Sprite Groups

Students must create and use:

| Group Name    | Purpose                    |
| ------------- | -------------------------- |
| `background`  | Sky or scenery             |
| `land`        | Ground and platforms       |
| `enemies`     | All enemy sprites          |
| `scenery`     | Combined scrolling objects |
| `all_sprites` | Everything drawn to screen |

---

## Required Game Loop Behavior

The main loop must:

* Handle quit events
* Respond to keyboard input
* Scroll scenery when the player moves
* Apply gravity when the player is not on land
* Move enemies every frame
* Check for collisions between the player and the enemies.
* Draw all sprites
* Control frame rate using `clock.tick()`



