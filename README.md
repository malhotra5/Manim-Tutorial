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
* [YOUR GO TO GUIDE FOR EVERYDAY USE!!]()
* [Further Work](#Further-Work)
* [Acknowledgements](#Acknowledgements)
## Installations
This installation and guide is meant for linux users. We will start by installing prerequisites. 

Lets first get the repo for manim, using:

    git clone https://github.com/3b1b/manim.git

We will start with installing some system requirements: Cairo, Latex, ffmpeg and sox. 

Install by running the following commands on the terminal: 

    sudo apt install SystemReq
    
Some additional installations are mentioned below

    sudo apt-get install libcairo2-dev libjpeg-dev libgif-dev 
    sudo apt install texlive-latex-base texlive-full texlive-fonts-extra
Phew! This will be the last isntallation for additional python modules. Run this in the terminal 
  
    python3 -m pip install -r requirements.txt
    
### Common-Problems
* Problem #1: Cairo System requirement 
People are sometimes unable to install cairo through the terminal. But, it is possible to install it using the Python.

        pip3 install pycairo
* Problem #2: **Exception: Latex error converting to dvi. See log output above or the log file**
This error can be frustrating. Especially when you don't know what to isntall. But if you followed my installation guide, this error is not due to missing a system requirement. Rather, there is a problem with the code.

* Problem #3: **No module named manim** 
This error occurs when you use the command to run a manim project when your not in the parent directory. Make sure that your current directory is in manim, and no other sub directory. 
## Running-Manim-Projects
Easy way to test whether all your installations are working is by running the command below
    
    python3 -m manim example_scenes.py SquareToCircle -pl
    
If it worked, then congratulations! Now you can run manim programs and get started with making animations. 
Now, this will be the general command to run all manim projects

    python3 -m manim pythonFile.py className -args

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
``` 
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

    python3 -m manim fileName.py Shapes -pl
    
**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/AYCJHLIlbW0/0.jpg)](https://www.youtube.com/watch?v=AYCJHLIlbW0)

### Shapes

```
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

In this code, I specifically included an example that I ran across when using manim. Look at this line of code that is included above too.

    pointers.append(Line(ORIGIN, np.array([cos(pi/180*360/8*i),sin(pi/180*360/8*i), 0]),color=YELLOW))
    
I am appending mobjects into an list. This way I can manipulate the mobjects in the list. However, some manim methods such as *FadeOut()* can't take multiple mobjects at once. This makes it hard to do multiple tasks with less lines of code. Some methods do however take multiple mobjects. 

For example: self.add() took the list. However, you have to unpack the list first. 

    self.add(*pointers)
    
Here, mobjects in the list pointers, we unpacked and passed as arguments to *add()*. Notice the syntax for doing so. We put * before the list.   

Last note. If you realized, the base class of the class above was *Scene*. This is provided by manim. Using it, we can access methods pertaining to manim. Manim also has many other base classes that we can use. If you realize, the lines of code below come from the base class. 

    self.add()
    self.play()

There are other bases classes we will explore for making Graphs, 3D Scenes,etc. 

**Click for results on YouTube:** 

[![Youtube video link](https://img.youtube.com/vi/kFCliVVACp4/0.jpg)](https://www.youtube.com/watch?v=kFCliVVACp4)

### Text

**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/3pxIVQxlpRQ/0.jpg)](https://www.youtube.com/watch?v=3pxIVQxlpRQ)

### Math-Equations

**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/k9U4VjqTyPA/0.jpg)](https://www.youtube.com/watch?v=k9U4VjqTyPA)

### Graphing

**Click for results on YouTube:**

[![Youtube video link](https://img.youtube.com/vi/6IyImPGDVUc/0.jpg)](https://www.youtube.com/watch?v=6IyImPGDVUc)

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
## GO-TO-GUIDE!

## Further-Work
I am missing a lot of aspects behind this powerful library after reverse engineering manim. There are things such as 3D scenes that still need to be documented. But hopefully this guide will cater to your basic needs. 
## Acknowledgements
* 3 Blue 1 Brown: The creator of this engine who uses it for creating cool math videos. Visit his YouTube channel and manin repo at 
  * https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw
  * https://github.com/3b1b/manim
* Todd Zimmerman: Made a documentation for manim that is outdated and works on Python 2.7. Visit it at
  * https://talkingphysics.wordpress.com/2018/06/11/learning-how-to-animate-videos-using-manim-series-a-journey/
