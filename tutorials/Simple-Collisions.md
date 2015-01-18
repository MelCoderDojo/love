This is the third and final part of the Boxes tutorials. It comes after [Simple Movement](https://github.com/MelCoderDojo/love/wiki/Simple-Movement).

In this one, we're going to make it so the boxes run into each other instead of sliding passed each other. For this, we're going to use bump.lua by kikito.

## Setting Up

Download bump.lua by right/second clicking [here](https://raw.githubusercontent.com/MelCoderDojo/love/master/libraries/bump.lua/bump.lua) and choosing to Save As (or something similar).

Once you get that, put the file in the folder with your main.lua file.

## Adding to Code

It doesn't take too much work to make bump.lua work with our boxes.

```Lua
function love.load()
   box1 = {
      x = 50,
      y = 50,
      width = 50,
      height = 50,
      speed = 300
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
   
   green = {
      red = 0,
      green = 255,
      blue = 0
   }
   
   bump = require "bump"
   world = bump.newWorld()
   world:add(box1, box1.x, box1.y, box1.width, box1.height)
   world:add(box2, box2.x, box2.y, box2.width, box2.height)
end
```

To use a file outside of main.lua, we need to use `require "name"`. In this case, the file is bump.lua, so `require "bump"` is what we need to use. Often, we don't set this to a variable, doing `require "name"` instead of `name = require "name"` or similar. This is just how bump.lua works.

In the `world = bump.newWorld()` line, we are setting up a place bump.lua can keep track of everything. It might help to think of it like a map with movable pieces that help you keep track of everything. It's not the real thing, but it helps.

With `world:add`, we are adding both boxes. It works like this.

```Lua
world:add(thing, left, top, width, height)
```

We have to give it the whole item first off, in this case being either box1 or box2. The `left` is for what the left side is in x, and then the `top` is for the top for `y`. Because we're already working with boxes, which are set up that way, we already have all this figured out without anything extra.

## Fixing Movement

We have to make some adjustments to how we move box1 around. We were directly changing the position with our code, but we need to make sure first that we can even move to that spot.

```Lua
function love.update(dt)
   local goalX, goalY

   if love.keyboard.isDown("right") then
      goalX = box1.x + box1.speed * dt
   end
   
   if love.keyboard.isDown("left") then
      goalX = box1.x - box1.speed * dt
   end
   
   if love.keyboard.isDown("down") then
      goalY = box1.y + box1.speed * dt
   end
   
   if love.keyboard.isDown("up") then
      goalY = box1.y - box1.speed * dt
   end
   
   goalX = goalX or box1.x
   goalY = goalY or box1.y
   box1.x, box1.y = world:move(box1, goalX, goalY)
   
end
```

What we've done is create `goalX` and `goalY`. We put the new `x` and `y` we would have in there for now.

The end may seem a bit confusing, and that might be because some special Lua stuff is happening here.

For both `goalX = goalX or box1.x` and `goalY = goalY or box1.y`, a certain problem is being fixed. If you don't move, or move in just one direction, at least one (`goalX` or `goalY`) will be empty. If one is empty, we set it to the last value (`box1.x` or `box1.y`). If you didn't move, it's the same as before, right? Right.

This or that? If not this, then it's that. That's the idea.

Last, we have `box1.x, box1.y = world:move(box1, goalX, goalY)`. With this, we feed into the `world` for bump.lua where we want to put box1. It'll tell us where box1 will be, whether it just passes back `goalX` and `goalY` because there were no problems, or if we get something different because box1 crashes into something else in the `world` (in our case, box2).

It's a bit much to swallow, but try it out and see it in action.
