# Manim-Tutorial
A tutorial for manim, a mathematical animation engine made by 3b1b for Python. 
## Requirements
* Python 3.7 (I managed to run it on version 3.6.5, so I'm guessing 3.6 and above works)
* Linux 
## Table of Contents
* [Installations](#Installations)
  * [Common Problems](#Common-Problems)
* [Running Manim Projects](#Running-Manim-Projects)
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

## Running-Manim-Projects

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
