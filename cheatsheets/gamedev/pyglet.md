# Pyglet

Installation
```
$ pip install pyglet
````

# Writing Pyglet Application

Hello World:
```python
import pyglet

window = pyglet.window.Window()

label = pyglet.text.Label('Hello, world',
                          font_name='Times New Roman',
                          font_size=36,
                          x=window.width//2, y=window.height//2,
                          anchor_x='center', anchor_y='center')
                          
@window.event
def on_draw():
    window.clear()
    label.draw()
    
pyglet.app.run()
```
### Image Viewing
```python
# Most games and applications will need to load and display images on 
# the screen. In this example we’ll load an image from the application’s 
# directory and display it within the window:
import pyglet

window = pyglet.window.Window()
image = pyglet.resource.image('kitten.jpg')

@window.event
def on_draw():
    window.clear()
    image.blit(0, 0)

pyglet.app.run()

# The blit() method draws the image. The arguments (0, 0) tell 
# pyglet to draw the image at pixel coordinates 0, 0 in the window (the lower-left corner).
```

### Handling mouse and keyboard events

```python
from pyglet.window import key

@window.event
def on_key_press(symbol, modifiers):
    if symbol == key.A:
        print('The "A" key was pressed.')
    elif symbol == key.LEFT:
        print('The left arrow key was pressed.')
    elif symbol == key.ENTER:
        print('The enter key was pressed.')
```
### Music Playing
```python
import pyglet

music = pyglet.resource.media('music.mp3')
music.play()

pyglet.app.run()
```

# Windowing

```python
# If the Window constructor is called with no arguments, defaults will be assumed for all parameters:
# However we can do many things with the windows

# Full screen windows
window.set_fullscreen(False)
window.set_fullscreen(True)


# Size and Position
window = pyglet.window.Window(1280, 720)


# Resizeablity
window = pyglet.window.Window(resizable=True)

@window.event
def on_resize(width, height):
    print('The window was resized to %dx%d' % (width, height))


# Minimum and Maximum sizing:
window.set_minimum_size(320, 200)
window.set_maximum_size(1024, 768)


# Caption
window = pyglet.window.Window(caption='Initial caption')
window.set_caption('A different caption')


# Icon
window = pyglet.window.Window()
icon1 = pyglet.image.load('16x16.png')
icon2 = pyglet.image.load('32x32.png')
window.set_icon(icon1, icon2)

```

# Working with keyboard

```python
# pyglet has support for low-level keyboard input suitable 
# for games as well as locale- and device-independent Unicode text entry.

# There are two keyboard events (press and release)
def on_key_press(symbol, modifiers):
    pass

def on_key_release(symbol, modifiers):
    pass
    
# Defined key symbols
key.A
key.B
key.C
...

key._1
key._2
key._3
...

key.ENTER or key.RETURN
key.SPACE
key.BACKSPACE
key.DELETE
key.MINUS
key.EQUAL
key.BACKSLASH

key.LEFT
key.RIGHT
key.UP
key.DOWN
key.HOME
key.END
key.PAGEUP
key.PAGEDOWN

key.F1
key.F2
...

# KEYs on numberpad
key.NUM_1
key.NUM_2
...
key.NUM_EQUAL
key.NUM_DIVIDE
key.NUM_MULTIPLY
key.NUM_SUBTRACT
key.NUM_ADD
key.NUM_DECIMAL
key.NUM_ENTER
```
### Remembering key state
```python
from pyglet.window import key

window = pyglet.window.Window()
keys = key.KeyStateHandler()
window.push_handlers(keys)

# Check if the spacebar is currently pressed:
if keys[key.SPACE]:
    pass
```

# Working with mouse

```python
# All mouse events are dispatched by the window which receives the event from 
# the operating system. Typically this is the window over which the mouse cursor 
# is, however mouse exclusivity and drag operations mean this is not always the case.

# Mouse motion event
def on_mouse_motion(x, y, dx, dy):
    pass

# The x and y parameters give the coordinates of the mouse pointer, 
# relative to the bottom-left corner of the window.

# Many games are not concerned with the actual position of the mouse cursor, 
# and only need to know in which direction the mouse has moved. For example, the 
# mouse in a first-person game typically controls the direction the player looks, 
# but the mouse pointer itself is not displayed.

# The dx and dy parameters are for this purpose: they give the distance the mouse 
# travelled along each axis to get to its present position. This can be computed naively by 
# storing the previous x and y parameters after every mouse event,
def on_mouse_press(x, y, button, modifiers):
    pass

def on_mouse_release(x, y, button, modifiers):
    pass

def on_mouse_drag(x, y, dx, dy, buttons, modifiers):
    pass
```
### Changing the mouse cursor
```python
# Visibility of the mouse
win = pyglet.window.Window()
win.set_mouse_visible(False)
win.set_mouse_visible(True)

# Changing the curosr
cursor = win.get_system_mouse_cursor(win.CURSOR_HELP)
win.set_mouse_cursor(cursor)
```
### Mouse Exclusivity

```python
# It is possible to take complete control of the mouse for your own 
# application, preventing  it being used to activate other applications. 
# This is most useful for immersive games such as first-person shooters
win = pyglet.window.Window()
win.set_exclusive_mouse(True)
```

# Shapes

```python
# The shapes module is a simplified option for creating and manipulating 
# colored shapes. This includes rectangles, circles, and lines. Shapes can 
# be resized, positioned, and rotated where applicable, and their color and 
# opacity can be changed. All shapes are implemented using OpenGL primitives

# Various shapes can be constructed with a specific position, size, and color:
circle = shapes.Circle(x=100, y=150, radius=100, color=(50, 225, 30))
square = shapes.Rectangle(x=200, y=200, width=200, height=200, color=(55, 55, 255))

circle.opacity = 120

# The size of Shapes can also be adjusted after creation:
square.width = 200
circle.radius = 99


# Anchor points
# For Circles, the default anchor point is the center of the circle. For 
# Rectangles, it is the bottom left corner. Depending on how you need to 
# position your Shapes, this can be changed.
rectangle = shapes.Rectangle(x=400, y=400, width=100, height=50)
rectangle.anchor_x = 50
rectangle.anchor_y = 25
# or, set at the same time:
rectangle.anchor_position = 50, 25

# The rectangle is then rotated around it's anchor point:
rectangle.rotation = 45
```

# Images

pyglet provides functions for loading and saving images in various formats using native operating system services. If the Pillow library is installed, many additional formats can be supported. Loaded images can be efficiently provided to OpenGL as a texture

If you’ve done any game or graphics programming, you’re probably familiar with the concept of “sprites”. pyglet also provides an efficient and comprehensive Sprite class, for displaying images on the screen with an optional transform (such as scaling and rotation)

# Graphics

# Sound and Video

# Application Resources

# The pyglet event framework

# Creating an OpenGL context

# The OpenGL interface

# The application event loop

# Displaying text

...

# Keeping track of time

...
