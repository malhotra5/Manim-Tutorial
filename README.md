# Manim-Tutorial
A tutorial for manim, a mathematical animation engine made by 3b1b for Python. 
## Requirements
* Python 3.7 (I managed to run it on version 3.6.5, so I'm guessing 3.6 and above works)
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
* [YOUR GO TO GUIDE FOR EVERYDAY USE!!](#GO-TO-GUIDE)
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
### Basics

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
## Acknowledgements
* 3 Blue 1 Brown: The creator of this engine who uses it for creating cool math videos. Visit his YouTube channel and manin repo at 
  * https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw
  * https://github.com/3b1b/manim
* Todd Zimmerman: Made a documentation for manim that is outdated and works on Python 2.7. Visit it at
  * https://talkingphysics.wordpress.com/2018/06/11/learning-how-to-animate-videos-using-manim-series-a-journey/
