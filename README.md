# Manim-Tutorial
A tutorial for manim, a mathematical animation engine made by 3b1b for Python. 
## Requirements
* Python 3.7 (I managed to run it on version 3.6.7, so I'm guessing 3.6 and above works)
* Linux 
## Table of Contents
* [Installations](#Installations)
  * [Common Problems](#Common-Problems)
* [Running Manim Projects](#Running-Manim-Projects)
  * [What ClassName means](#classNames)
  * [What are the possible args](#Args)

* [Tutorial!](#Tutorial)
  * [Basics, Getting Started](#Basics)
  * [Shapes](#Shapes)
  * [Text](#Text)
  * [Math Equations](#Math-Equations)
  * [Graphing](#Graphing)
* [YOUR GO TO GUIDE FOR EVERYDAY USE!!](#GO-TO-GUIDE)
* [Exploring the repo](#Exploring-the-Repo)
  * [ManimLib](#ManimLib)
    * [Animation](#Animations)
    * [Mobject](#Mobjects)
      * [Types](#Types)
    * [Scene](#Scenes)
    * [Utils](#Utils)
  * [Media](#Media)
  * [Old_Projects](#Old_Projects)
* [Putting it together](#Putting-it-together)
* [Further Work](#Further-Work)
* [Acknowledgements](#Acknowledgements)
## Installations
This installation and guide is meant for linux users. We will start by installing prerequisites. 

Lets first get the repo for manim, using:
``` bash
    git clone https://github.com/3b1b/manim.git
```

We will start with installing some system requirements: Cairo, Latex, ffmpeg and sox. 

Install by running the following commands on the terminal: 

``` bash
    sudo apt install SystemReq
```

Some additional installations are mentioned below
``` bash
    sudo apt-get install libcairo2-dev libjpeg-dev libgif-dev 
    sudo apt install texlive-latex-base texlive-full texlive-fonts-extra
```
Phew! This will be the last isntallation for additional python modules. Run this in the terminal 
``` bash
    python3 -m pip install -r requirements.txt
```

### Common-Problems
* Problem #1: Cairo System requirement 
People are sometimes unable to install cairo through the terminal. But, it is possible to install it using the Python.
``` bash
        pip3 install pycairo
```

* Problem #2: **Exception: Latex error converting to dvi. See log output above or the log file**
This error can be frustrating. Especially when you don't know what to isntall. But if you followed my installation guide, this error is not due to missing a system requirement. Rather, there is a problem with the code.

* Problem #3: **No module named manim** 
This error occurs when you use the command to run a manim project when your not in the parent directory. Make sure that your current directory is in manim, and no other sub directory. 
## Running-Manim-Projects
Easy way to test whether all your installations are working is by running the command below
```bash
    python3 -m manim example_scenes.py SquareToCircle -pl
```

If it worked, then congratulations! Now you can run manim programs and get started with making animations. 
Now, this will be the general command to run all manim projects
```python
    python3 -m manim pythonFile.py className -args
```

**NOTE 1**: Your videos that you make are saved in the folder called *media*. \
**NOTE 2**: The command for running the manim programs should only be run in the parent directory. 
 
### classNames
Manim programs have a certain structure. The Python program file requires you to make classes for all your series of animations. If you make more than a few classes, you have to run commands for every class you make. Seperate videos are made for every class.  
### Args
Args are a list of arguements that can be stated when running the program. The most important agruements and it's explanations are provided in the [GO TO GUIDE.](#GO-TO-GUIDE)
I recommend to look at it later, and start with the tutorial.
## Tutorial!
Finally we can start. In this tutorial, we will learn by doing. 
### Basics
``` python
from big_ol_pile_of_manim_imports import *

class Shapes(Scene):
    def construct(self):
        ######Code######
        #Making shapes
        circle = Circle()
        square = Square()
        triangle=Polygon(np.array([0,0,0]),np.array([1,1,0]),np.array([1,-1,0]))

        #Showing shapes
        self.play(ShowCreation(circle))
        self.play(FadeOut(circle))
        self.play(GrowFromCenter(square))
        self.play(Transform(square,triangle))
```

We will break this into parts: 
* Import: The import in this code is the import we will use in all manim projects. It has almost all the imports we will ever require
* Class: For running animations, you have to make a class that has a base class from manim. 
  * Method: The construct method is special to manim. Manim calls on construct for creating animations. Therefore, every class that runs manim has to have this method. 
* Code: You don't have to fully understand how the code works yet. But you can see that you first define your animations, and then you display it. You can experiment with the order in which you define and display.

**NOTE**: If you recall, to run this animation, you would run the following in the terminal - 
```bash
    python3 -m manim fileName.py Shapes -pl
```
**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/AYCJHLIlbW0/0.jpg)](https://www.youtube.com/watch?v=AYCJHLIlbW0)

### Shapes

```python
from big_ol_pile_of_manim_imports import *
from math import cos, sin, pi

class Shapes(Scene):
    def construct(self):
        #######Code#######
        #Making Shapes
        circle = Circle(color=YELLOW)
        square = Square(color=DARK_BLUE)
        square.surround(circle)

        rectangle = Rectangle(height=2, width=3, color=RED)
        ring=Annulus(inner_radius=.2, outer_radius=1, color=BLUE)
        ring2 = Annulus(inner_radius=0.6, outer_radius=1, color=BLUE)
        ring3=Annulus(inner_radius=.2, outer_radius=1, color=BLUE)
        ellipse=Ellipse(width=5, height=3, color=DARK_BLUE)

        pointers = []
        for i in range(8):
            pointers.append(Line(ORIGIN, np.array([cos(pi/180*360/8*i),sin(pi/180*360/8*i), 0]),color=YELLOW))

        #Showing animation
        self.add(circle)
        self.play(FadeIn(square))
        self.play(Transform(square, rectangle))
        self.play(FadeOut(circle), FadeIn(ring))
        self.play(Transform(ring,ring2))
        self.play(Transform(ring2, ring))
        self.play(FadeOut(square), GrowFromCenter(ellipse), Transform(ring2, ring3))
        self.add(*pointers)
        self.wait(2)
```
After looking at a lot of pieces of code in this tutorial, you will eventually familiarize yourself with manim. So lets start!

Our focus is going to shift from understanding the structure of our code, to understanding the code itself. The first import statement imports many of the classes we will use. 

The section for making shapes creates shapes that can be used in manim. You can define it's size, color,etc. 
You will see some methods such as *surround* or *FadeOut*, we wil classify them later. The code is simple enough to read, most of it looks like English. 

The section for showing the animaton displays the shapes, as specified in the code. Let's look at the what the code offers.

**Shapes:** The shapes defined in manim are known as mobjects. Manim has this classification for objects other than shapes. Keep reading for the formal definition of a mobject. 
* Square
* Circle 
* Rectangle
* Lines
* Annulus

**Animations:** These are animations that apply to objects known as mobjects. Mobjects are objects defined by manim. Manim creates these objects specifically, so that you can apply any animations or other special manim methods to them. 
* FadeIn 
* Transform 
* FadeOut
* GrowFromCenter

**Adding:**
These are some of the methods for adding mobjects or playing Animations on mobjects. Note: If you play an animation, you don't have to add it to the screen. The animation does it for you. 
* Play
* Add

In this code, I specifically included an example that I found useful to know. 
``` python
    pointers.append(Line(ORIGIN, np.array([cos(pi/180*360/8*i),sin(pi/180*360/8*i), 0]),color=YELLOW))
```
I am appending mobjects into an list. This way I can manipulate the mobjects in the list. However, some manim methods such as *FadeOut()* can't take multiple mobjects at once. This makes it hard to do multiple tasks with less lines of code. We will take a look at a way to overcome that problem later. Although, some methods do however take multiple mobjects. 

For example: self.add() took the list. However, you have to unpack the list first. 
```python
    self.add(*pointers)
```
Here, mobjects in the list pointers, we unpacked and passed as arguments to *add()*. Notice the syntax for doing so. We put * before the list.   

Last note. If you realized, the base class of the class above was *Scene*. This is provided by manim. Using it, we can access methods pertaining to manim. Manim also has many other base classes that we can use. If you realize, the lines of code below come from the base class. 
```python
    self.add()
    self.play()
```
There are other bases classes we will explore for making Graphs, 3D Scenes,etc. 

**Click for results on YouTube:** 

[![Youtube video link](https://img.youtube.com/vi/kFCliVVACp4/0.jpg)](https://www.youtube.com/watch?v=kFCliVVACp4)

### Text

```python
from big_ol_pile_of_manim_imports import *

class makeText(Scene):
    def construct(self):
        #######Code#######
        #Making text
        first_line = TextMobject("Manim is fun")
        second_line = TextMobject("and useful")
        final_line = TextMobject("Hope you like it too!", color=BLUE)
        color_final_line = TextMobject("Hope you like it too!")

        #Coloring
        color_final_line.set_color_by_gradient(BLUE,PURPLE)

        #Position text
        second_line.next_to(first_line, DOWN)

        #Showing text
        self.wait(1)
        self.play(Write(first_line), Write(second_line))
        self.wait(1)
        self.play(FadeOut(second_line), ReplacementTransform(first_line, final_line))
        self.wait(1)
        self.play(Transform(final_line, color_final_line))
        self.wait(2)
```

Hopefully, most of the code makes sense. In this section I'll introduce a new mobject known as TextMobject. It is used to store text. It is particulary useful because it helps you position text on the screen and you can use the animation *write()*. 

I also included a nice coloring tool, *set_color_by_gradient*. You can pass constants in Manim such as *BLUE* or *PURPLE*. To pass a custom color you can specify the hex code of the color instead of using Manim color constants. 

TextMobjects will be used later on to write good looking math equations. 

**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/3pxIVQxlpRQ/0.jpg)](https://www.youtube.com/watch?v=3pxIVQxlpRQ)

### Math-Equations

```python

from big_ol_pile_of_manim_imports import *

class Equations(Scene):
    def construct(self):
        #Making equations
        first_eq = TextMobject("$$J(\\theta) = -\\frac{1}{m} [\\sum_{i=1}^{m} y^{(i)} \\log{h_{\\theta}(x^{(i)})} + (1-y^{(i)}) \\log{(1-h_{\\theta}(x^{(i)}))}] $$")
        second_eq = ["$J(\\theta_{0}, \\theta_{1})$", "=", "$\\frac{1}{2m}$", "$\\sum\\limits_{i=1}^m$", "(", "$h_{\\theta}(x^{(i)})$", "-", "$y^{(i)}$", "$)^2$"]

        second_mob = TextMobject(*second_eq)

        for i,item in enumerate(second_mob):
            if(i != 0):
                item.next_to(second_mob[i-1],RIGHT)

        eq2 = VGroup(*second_mob)

        des1 = TextMobject("With manim, you can write complex equations like this...")
        des2 = TextMobject("Or this...")
        des3 = TextMobject("And it looks nice!!")

        #Coloring equations
        second_mob.set_color_by_gradient("#33ccff","#ff00ff")

        #Positioning equations
        des1.shift(2*UP)
        des2.shift(2*UP)

        #Animating equations
        self.play(Write(des1))
        self.play(Write(first_eq))
        self.play(ReplacementTransform(des1, des2), Transform(first_eq, eq2))
        self.wait(1)

        for i, item in enumerate(eq2):
            if (i<2):
                eq2[i].set_color(color=PURPLE)
            else:
                eq2[i].set_color(color="#00FFFF")

        self.add(eq2)
        self.wait(1)
        self.play(FadeOutAndShiftDown(eq2), FadeOutAndShiftDown(first_eq), Transform(des2, des3))
        self.wait(2)

```
Here, we will  look at very important concepts that will help when using Manim. 

That looks long, but it's very simple. Here I have provided 2 ways of making equation and displaying it to the screen. If you remember, we installed some latex system requirements. We will use LaTex to make our equations look nice. 

LaTex will take it's own tutorial. However, you don't need to know a lot of LaTex. I will introduce some rules that will help you write any math equation. Notice that equations are specified in TextMobjects. 

**LaTex:** When making an equation, the general rule is to put a *$* at the start and end of the text. For example:
```python
text = TextMobject("This is text") #Normal text
equation = TextMobject("$X$") #This is an equation X
```

Now for the fun part. In LaTex, you can represent symbols using a backslash and a keyword. THis include theta, alpha, summation, etc. In Manim, it is similar. 

```python
theta = TextMobject("$\\theta$")
```
Notice, in Manim, you specify symbols by putting 2 backslash before the keyword. 

Finally, the I will introduce the syntax for adding subscripts and superscripts. Here is the syntax for superscripts. 

```python
superScript_equation = TextMobject("$r^{\\theta}$")
```

The ^ symbol signifies superscript. We put the symbol theta as the superscript. Also, when specifying superscript the {} brackets are not displayed in the equation. They help group all the elements you want to add to the superscript. 

For subscripts, it is similar. 

```python
subScript_equation = TextMobject("$\\theta_{1}$")
```

This is theta subscript 1. The _ signifies subscript. Like usual, the {} brackets aren't displayed in the equation. 

Now, we will look at a complex way of writing equations using VGroup. 

**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/k9U4VjqTyPA/0.jpg)](https://www.youtube.com/watch?v=k9U4VjqTyPA)

### Graphing

```python
from big_ol_pile_of_manim_imports import *
import math

class Graphing(GraphScene):
    CONFIG = {
        "x_min": -5,
        "x_max": 5,
        "y_min": -4,
        "y_max": 4,
        "graph_origin": ORIGIN,
        "function_color": WHITE,
        "axes_color": BLUE
    }

    def construct(self):
        #Make graph
        self.setup_axes(animate=True)
        func_graph=self.get_graph(self.func_to_graph,self.function_color)
        graph_lab = self.get_graph_label(func_graph, label = "x^{2}")

        func_graph_2=self.get_graph(self.func_to_graph_2,self.function_color)
        graph_lab_2 = self.get_graph_label(func_graph_2, label = "x^{3}")

        vert_line = self.get_vertical_line_to_graph(1,func_graph,color=YELLOW)

        x = self.coords_to_point(1, self.func_to_graph(1))
        y = self.coords_to_point(0, self.func_to_graph(1))
        horz_line = Line(x,y, color=YELLOW)

        point = Dot(self.coords_to_point(1,self.func_to_graph(1)))

        #Display graph
        self.play(ShowCreation(func_graph), Write(graph_lab))
        self.wait(1)
        self.play(ShowCreation(vert_line))
        self.play(ShowCreation(horz_line))
        self.add(point)
        self.wait(1)
        self.play(Transform(func_graph, func_graph_2), Transform(graph_lab, graph_lab_2))
        self.wait(2)


    def func_to_graph(self, x):
        return (x**2)

    def func_to_graph_2(self, x):
        return(x**3)
```


Here is the default dictionary Manim uses for graphing. 
```python

CONFIG = {
"x_min": -1,
"x_max": 10,
"x_axis_width": 9,
"x_tick_frequency": 1,
"x_leftmost_tick": None, # Change if different from x_min
"x_labeled_nums": None,
"x_axis_label": "$x$",
"y_min": -1,
"y_max": 10,
"y_axis_height": 6,
"y_tick_frequency": 1,
"y_bottom_tick": None, # Change if different from y_min
"y_labeled_nums": None,
"y_axis_label": "$y$",
"axes_color": GREY,
"graph_origin": 2.5 * DOWN + 4 * LEFT,
"exclude_zero_label": True,
"num_graph_anchor_points": 25,
"default_graph_colors": [BLUE, GREEN, YELLOW],
"default_derivative_color": GREEN,
"default_input_color": YELLOW,
"default_riemann_start_color": BLUE,
"default_riemann_end_color": GREEN,
"area_opacity": 0.8,
"num_rects": 50,
}

```


**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/6IyImPGDVUc/0.jpg)](https://www.youtube.com/watch?v=6IyImPGDVUc)

## GO-TO-GUIDE!
Click the link below for the guide.  

## Exploring-the-Repo

### ManimLib
#### Animations
#### Mobjects
##### Types
#### Scenes
#### Utils

### Media
### Old_Projects

## Putting-it-together


[Manim Resource Guide](https://github.com/malhotra5/Manim-Guide)

## Further-Work
I am missing a lot of aspects behind this powerful library after reverse engineering manim. There are things such as 3D scenes that still need to be documented. But hopefully this guide will cater to your basic needs. 
## Acknowledgements
* 3 Blue 1 Brown: The creator of this engine who uses it for creating cool math videos. Visit his YouTube channel and manin repo at 
  * https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw
  * https://github.com/3b1b/manim
* Todd Zimmerman: Recently made a new documentation made in Python3.7. Visit it at
  * https://talkingphysics.wordpress.com/tag/manim/
