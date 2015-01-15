## Note
This is currently unfinished.

* love.[draw](#draw)
* love.errhand
* love.focus
* love.gamepadaxis
* love.gamepadpressed
* love.gamepadreleased
* love.joystickadded
* love.joystickaxis
* love.joystickhat
* love.joystickpressed
* love.joystickreleased
* love.joystickremoved
* love.keypressed
* love.keyreleased
* love.load
* love.mousefocus
* love.mousepressed
* love.mousereleased
* love.quit
* love.resize
* love.run
* love.textinput
* love.threaderror
* love.update
* love.visible

## love.<a name="draw">draw</a>

Callback function used to draw on the screen every frame.

```Lua
love.draw()
```

## love.errhand <a name="errhand"></a>

The error handler, used to display error messages.

```Lua
love.errhand( msg )
```
| Variable |   Type   |     Description     |
| -------- | -------- | ------------------- |
| msg      |  string  | The error message.  |

## love.focus

Callback function triggered when window receives or loses focus.

```Lua
love.focus( f )
```
| Variable |   Type   |     Description     |
| -------- | -------- | ------------------- |
| f        | boolean  | Window focus.       |

## love.gamepadaxis

Called when a Joystick's virtual gamepad axis is moved.

```Lua
love.gamepadaxis( joystick, axis )
```
| Variable |     Type     |        Description        |
| -------- | ------------ | ------------------------- |
| joystick | Joystick     | The joystick object.      |
| axis     | GamepadAxis  | The virtual gamepad axis. |

## love.gamepadpressed

Called when a Joystick's virtual gamepad button is pressed.

```Lua
love.gamepadpressed( joystick, button )
```
| Variable |     Type      |        Description          |
| -------- | ------------- | --------------------------- |
| joystick | Joystick      | The joystick object.        |
| button   | GamepadButton | The virtual gamepad button. |

## love.gamepadreleased

Called when a Joystick's virtual gamepad button is released.

```Lua
love.gamepadreleased( joystick, button )
```
| Variable |     Type      |         Description         |
| -------- | ------------- | --------------------------- |
| joystick | Joystick      | The joystick object.        |
| button   | GamepadButton | The virtual gamepad button. |

## love.joystickadded

Called when a Joystick is connected.

This callback is also triggered after love.load for every Joystick which was already connected when the game started up.

```Lua
love.joystickadded( joystick )
```
| Variable |     Type     |              Description              |
| -------- | ------------ | ------------------------------------- |
| joystick | Joystick     | The newly connected Joystick object.  |

## love.joystickaxis

Called when a joystick axis moves.

```Lua
love.joystickaxis( joystick, axis, value )
```
| Variable |     Type     |        Description        |
| -------- | ------------ | ------------------------- |
| joystick | Joystick     | The joystick object.      |
| axis     | number       | The axis number.          |
| value    | number       | The new axis value.       |

## love.joystickhat

Called when a joystick hat direction changes.

```Lua
love.joystickhat( joystick, hat, direction )
```
|  Variable  |     Type     |        Description        |
| ---------- | ------------ | ------------------------- |
| joystick   | Joystick     | The joystick object.      |
| hat        | number       | The hat number.           |
| direction  | JoystickHat  | The new hat direction.    |

## love.joystickpressed

Called when a joystick button is pressed.

```Lua
love.joystickpressed( joystick, button )
```
| Variable |     Type     |        Description        |
| -------- | ------------ | ------------------------- |
| joystick | number       | The joystick number.      |
| button   | number       | The button number.        |

## love.joystickreleased

Called when a joystick button is released.

```Lua
love.joystickreleased( joystick, button )
```
| Variable |     Type     |        Description        |
| -------- | ------------ | ------------------------- |
| joystick | number       | The joystick number.      |
| button   | number       | The button number.        |

## love.joystickremoved

Called when a Joystick is disconnected.

```Lua
love.joystickremoved( joystick )
```
| Variable |     Type     |              Description              |
| -------- | ------------ | ------------------------------------- |
| joystick | Joystick     | The now-disconnected Joystick object. |

## love.keypressed

Callback function triggered when a key is pressed.

Key repeat needs to be enabled with love.keyboard.setKeyRepeat for repeat keypress events to be received.

```Lua
love.keypressed( key, isrepeat )
```
| Variable |     Type     |              Description                |
| -------- | ------------ | --------------------------------------- |
| key      | KeyConstant  | Character of the key pressed.           |
| isrepeat | boolean      | Whether this keypress event is a repeat. The delay between key repeats depends on the user's system settings. |

## love.keyreleased

Callback function triggered when a key is released.

```Lua
love.keyreleased( key )
```
| Variable |     Type     |              Description              |
| -------- | ------------ | ------------------------------------- |
| key      | KeyConstant  | Character of the key released.        |

## love.load

This function is called exactly once at the beginning of the game.

```Lua
love.load( arg )
```
| Variable |     Type     |                Description                |
| -------- | ------------ | ----------------------------------------- |
| arg      | table        | Command line arguments given to the game. |

## love.mousefocus

Callback function triggered when window receives or loses mouse focus.

```Lua
love.mousefocus( f )
```
| Variable |     Type     |                Description                |
| -------- | ------------ | ----------------------------------------- |
| f        | boolean      | Window mouse focus.                       |

## love.mousepressed

Callback function triggered when a mouse button is pressed.

```Lua
love.mousepressed( x, y, button )
```
| Variable |      Type      |                Description                |
| -------- | -------------- | ----------------------------------------- |
| x        | number         | Mouse x position.                         |
| y        | number         | Mouse y position.                         |
| button   | MouseConstant  | Mouse button pressed.                     |

## love.mousereleased

Callback function triggered when a mouse button is released.

```Lua
love.mousereleased( x, y, button )
```
| Variable |      Type      |                Description                |
| -------- | -------------- | ----------------------------------------- |
| x        | number         | Mouse x position.                         |
| y        | number         | Mouse y position.                         |
| button   | MouseConstant  | Mouse button released.                    |

## love.quit

Callback function triggered when the game is closed.

```Lua
r = love.quit()
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| r        | boolean        | Abort quitting. If true, do not close the game. |

## love.resize

Called when the window is resized, for example if the user resizes the window, or if love.window.setMode is called with an unsupported width or height in fullscreen and the window chooses the closest appropriate size.

Calls to love.window.setMode will only trigger this event if the width or height of the window after the call doesn't match the requested width and height. This can happen if a fullscreen mode is requested which doesn't match any supported mode, or if the fullscreen type is 'desktop' and the requested width or height don't match the desktop resolution.

```Lua
love.resize( w, h )
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| w        | number         | The new width.                                  |
| h        | number         | The new height.                                 |

## love.run

The main function, containing the main loop. A sensible default is used when left out.

```Lua
love.run()
```

## love.textinput

Called when text has been entered by the user. For example if shift-2 is pressed on an American keyboard layout, the text "@" will be generated.

```Lua
love.textinput( text )
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| text     | string         | The UTF-8 encoded unicode text.                 |

## love.threaderror

Callback function triggered when a Thread encounters an error.

```Lua
love.threaderror( thread, errorstr )
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| thread   | Thread         | The thread which produced the error.            |
| errorstr | string         | The error message.                              |

## love.update

Callback function used to update the state of the game every frame.

```Lua
love.update( dt )
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| dt       | number         | Time since the last update in seconds.          |

## love.visible

Callback function triggered when window is minimized/hidden or unminimized by the user.

```Lua
love.visible( v )
```
| Variable |      Type      |                   Description                   |
| -------- | -------------- | ----------------------------------------------- |
| v        | boolean        | Window visibility.                              |

Data

The superclass of all data.

Functions

Data:getSize

Data:getString

Supertypes

Object

Data:getSize

Gets the size of the Data.

size = Data:getSize()
size	number	The size of the Data in bytes.

Data:getString

Gets the full Data as a string.

data = Data:getString()
data	string	The raw data.

Drawable

Superclass for all things that can be drawn on screen. This is an abstract type that can't be created directly.

Supertypes

Object

Object

The superclass of all LÖVE types.

Functions

Object:type

Object:typeOf

Object:type

Gets the type of the object as a string.

type = Object:type()
type	string	The type as a string.

Object:typeOf

Checks whether an object is of a certain type. If the object has the type with the specified name in its hierarchy, this function will return true.

b = Object:typeOf( name )
b	boolean	True if the object is of the specified type, false otherwise.
name	string	The name of the type to check for.
