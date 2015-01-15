#Introduction

It's traditional to start a brand new code experience with printing out "Hello world!" That's what we're going to do, but you can have some fun with it.

#Let's Do It!

Make a new folder for your project named "Hello World". Make a file named "main.lua" inside of it. Put the code written below in the file.

```Lua
function love.draw()
   love.graphics.print("Hello world!")
end
```

See the indentation? That can be either 3 or 4 spaces. Pick which number you want and always follow it.

Anyway, save and run your program! (If you don't know how, ask us for help!)

#Some Modifications

We're going to make this a little fancier, adding color and changing how big the text is and where it's at.

```Lua
function love.load()
   local myfont = love.graphics.newFont(45)
   love.graphics.setFont(myfont)

   love.graphics.setColor(0,0,0)
   love.graphics.setBackgroundColor(255,255,255)
end

function love.draw()
   love.graphics.print("Hello world!", 100, 100)
end
```

Try that one out!

#Random Coloring

This is a fun one. We're going to make the text randomly change color. It's a little complicated, but try it out!

```Lua
function love.load()
   local myfont = love.graphics.newFont(45)
   love.graphics.setFont(myfont)

   love.graphics.setColor(0,0,0)
   love.graphics.setBackgroundColor(255,255,255)
   
   timer = 0
   timerLimit = 3
end

function love.update(dt)
   timer = timer + dt
   if timer >= timerLimit then
      randnum = math.random(3)
      if randnum == 1 then
         love.graphics.setColor(255,0,0)
      elseif randnum == 2 then
         love.graphics.setColor(0,255,0)
      else
         love.graphics.setColor(0,0,255)
      end
      
      timer = 0
   end
end

function love.draw()
   love.graphics.print("Hello world!", 100, 100)
end
```

Do you understand what's going on?

#Basic Structure

You've done a very simple (and colorful) Hello World program. You now know a LÖVE program's three basic parts: load, update, and draw.

When you start a LÖVE project, you usually start from this.
```Lua
function love.load()
end

function love.update(dt)
end

function love.draw()
end
```

Though you may make many different files, you will set them up very similarly.

##love.load()
This is where things for the game are set up. It is like how you have to gather up your ingredients and other materials before you start a recipe. You have to set up first.

##love.update(dt)
This handles all of the “regular” code while you run. Controlling what happened, what to do next. The dt is important, meaning "delta time" or "how much time has changed." Most of all that is actually happening is happening here.

##love.draw()
This handles how things are drawn to the screen.
