This is part 2 of the Boxes tutorials. This comes after [Draw Boxes](https://github.com/MelCoderDojo/love/wiki/Draw-Boxes).

## Movement

Let's get moving! Now, we finally put `love.update` to work with our first box.

```Lua   
function love.update(dt)
   if love.keyboard.isDown("right") then
      box1.x = box1.x + 5
   end
   
   if love.keyboard.isDown("left") then
      box1.x = box1.x - 5
   end
end
```

Check it out! Moving square! Nice.

This movement isn't entirely smooth though, especially on slower computers. We can fix that by playing with `dt` (delta time).

When you play with `dt`, you're often dealing with fractions of a second, so we need to set a speed that's at least in the hundreds. OTherwise, it'll be really slow.

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
end

function love.update(dt)
   if love.keyboard.isDown("right") then
      box1.x = box1.x + box1.speed * dt
   end
   
   if love.keyboard.isDown("left") then
      box1.x = box1.x - box1.speed * dt
   end
end
```

There we go, some nice and smooth speed. While we're at it, why don't we add in moving up and down?

```Lua
function love.update(dt)
   if love.keyboard.isDown("right") then
      box1.x = box1.x + box1.speed * dt
   end
   
   if love.keyboard.isDown("left") then
      box1.x = box1.x - box1.speed * dt
   end
   
   if love.keyboard.isDown("down") then
      box1.y = box1.y + box1.speed * dt
   end
   
   if love.keyboard.isDown("up") then
      box1.y = box1.y - box1.speed * dt
   end
end
```

If you look closely, you'll see that going down gets a `+` while up gets a `-`. Why is that?

```
  -------------- x
 |
 |
 |
 |
 y
```

In many 2D video games, x and y work like this. (0,0), the starting point or origin, is in the upper left corner. That makes the y-axis get bigger as you go down the screen instead of up. It's just starting the graph a different way.


## Drawing Order

As you might have notice, the red square goes _underneath_ the green square. It just has to do with the order the two are drawn in. Like with a painting, if you draw one thing first, the next thing you draw in that spot will cover up what was there.

Play with the two and see.

### Green in Front
```Lua
function love.draw()
   drawBox(red, box1)
   drawBox(green, box2)
end
```

### Red in Front
```Lua
function love.draw()
   drawBox(green, box2)
   drawBox(red, box1)
end
~~~

This is important to keep in mind. Not just for making things look how you want when moving, but always.

## What's Next?

How about making it so the boxes can't pass through each other? Next is [Simple Collisions](https://github.com/MelCoderDojo/love/wiki/Simple-Collisions)
