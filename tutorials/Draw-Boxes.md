In this tutorial, we're going to start drawing things on the screen.

## Starting Up

Do you remember how we start a program for LÖVE?

Make a folder (maybe name it Box) and make a main.lua file.

```Lua
function love.load()
end

function love.update(dt)
end

function love.draw()
end
```

Fill your main.lua with that, and then we'll start adding to it.


## Starting Box

Instead of posting all the code, below is just the part you need to change. This will happen a lot, but we'll try to keep you on track with what is added and what's changed.

So in `love.draw`, add this line in the middle.

```Lua
function love.draw()
   love.graphics.rectangle("fill", 50, 50, 50, 50)
end
```
Run the program. Check it out, you've drawn a square. This is just the start.


## Building Up

Alright, we're going to change this code around a bit. Instead of putting in the numbers directly, let's start using variables.

Make your main.lua look like the below.

```Lua
function love.load()
   x = 50
   y = 50
   width = 50
   height = 50
end

function love.update(dt)
end

function love.draw()
   love.graphics.rectangle("fill", x, y, width, height)
end
```

Run this, and you get the same thing.

Now, let's go a step further.

```Lua
function love.load()
   box = {
      x = 50,
      y = 50,
      width = 50,
      height = 50
   }
end

function love.update(dt)
end

function love.draw()
   love.graphics.rectangle("fill", box.x, box.y, box.width, box.height)
end
```
What you see here is Lua's table, its only data object. They're very handy and flexible.

Tables are made with the curly braces ({}), as you see in `love.load`. This is one way you can make a table. Those aren't the only changes here though. Look in `love.draw`. There, you'll see that the table's name was added to all the variables. That's how you use the variables inside the table.

The code still runs the same way.

## Two Boxes

Let's add another box. We'll change the name of the first one so they're `box1` and `box2`.

```Lua
function love.load()
   box1 = {
      x = 50,
      y = 50,
      width = 50,
      height = 50
   }
   
   box2 = {
      x = 200,
      y = 200,
      width = 50,
      height = 50
   }
end

function love.update(dt)
end

function love.draw()
   love.graphics.rectangle("fill", box1.x, box1.y, box1.width, box1.height)
   love.graphics.rectangle("fill", box2.x, box2.y, box2.width, box2.height)
end
```
Can you see how tables are handy? We can give both boxes their own variables and not lose track of them.

## Color

How about we add some color to these boxes? Edit the `love.draw` function like so.

```Lua
function love.draw()
   love.graphics.setColor(255,0,0)
   love.graphics.rectangle("fill", box.x, box.y, box.width, box.height)
   love.graphics.setColor(0,255,0)
   love.graphics.rectangle("fill", box2.x, box2.y, box2.width, box2.height)
end
```
Red and green boxes on screen. Nice. We just had to put in our program what color to use before it draws each box.

In computers, all colors are created with 3 base colors: red, green, and blue. That might be different than how it works in art class, but that's a whole other story. Here are some example colors.

|  Color  |  Red  | Green | Blue |
| ------- | ----- | ----- | ---- |
| Black   | 0     | 0     | 0    |
| White   | 255   | 255   | 255  |
| Red     | 255   | 0     | 0    | 
| Lime    | 0     | 255   | 0    |
| Blue    | 0     | 0     | 255  |
| Yellow  | 255   | 255   | 0    |
| Cyan    | 0     | 255   | 255  |
| Magenta | 255   | 0     | 255  |
| Silver  | 192   | 192   | 192  |
| Gray    | 128   | 128   | 128  |
| Maroon  | 128   | 0     | 0    |
| Olive   | 128   | 128   | 0    |
| Green   | 0     | 128   | 0    |
| Purple  | 128   | 0     | 128  |
| Teal    | 0     | 128   | 128  |
| Navy    | 0     | 0     | 128  |

Okay, so they're red and _lime_ green squares, but same idea.

Just like before, we're going to get a bit creative here with tables.

```Lua
function love.load()
   box1 = {
      x = 50,
      y = 50,
      width = 50,
      height = 50
   }
   
   box2 = {
      x = 200,
      y = 200,
      width = 50,
      height = 50
   }
   
   red = {
      red = 255,
      green = 0,
      blue = 0
   }
   
   lime = {
      red = 0,
      green = 255,
      blue = 0
   }
end

function love.update(dt)
end

function love.draw()
   love.graphics.setColor(red.red, red.green, red.blue)
   love.graphics.rectangle("fill", box1.x, box1.y, box1.width, box1.height)
   love.graphics.setColor(lime.red, lime.green, lime.blue)
   love.graphics.rectangle("fill", box2.x, box2.y, box2.width, box2.height)
end
```

Between the table and these new color tables, hopefully colors are a bit clearer for you.

We're not done messing with things this way yet though. We can make drawing the squares simpler than that. Let's do it!

First, we're going to add on a new function. Add it right down at the end.

```Lua
function drawBox(color, box)
   love.graphics.setColor(color.red, color.green, color.blue)
   love.graphics.rectangle("fill", box.x, box.y, box.width, box.height)
end
```
With that made, we can change `love.draw` like this.

```Lua
function love.draw()
   drawBox(red, box1)
   drawBox(green, box2)
end
```

Look at the code. It's very clean. To draw a box, we use the new `drawBox` function. The `drawBox` function works by setting the color and drawing the box to the x, y, width, and height it has. Make sense?


## What's Next?

Let's get moving with some [Simple Movement](https://github.com/MelCoderDojo/love/wiki/Simple-Movement)!
