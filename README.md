# GUI-Music-Player-Using-Python
The GUI Music Player using Python is an interactive application where user can simply control it by clicking on the buttons. To build this project in python we need to create an interface first with the help of tkinter() package. Next, using mixer module in pygame package we are going to control the execution of song.
# import all the required packages
from tkinter import *
from pygame import mixer
import os

# Creating interface or root window
root=Tk()

# To make the size of the window static
root.resizable(0,0)

# To Insert a title to the created root window
root.title('Music Player')

# Function to play the song
def play():
    currentsong=playlist.get(ACTIVE)
    mixer.music.load(currentsong)
    mixer.music.play()

# Function to pause the song which is currently playing
def pause():
    mixer.music.pause()

# Function to resume the song which has paused
def resume():
    mixer.music.unpause()


# Function to stop the currently playing song
def stop():
    mixer.music.stop()

# Intilaizing the mixer module
mixer.init()

# Creating a listbox where the list of songs are going to be displayed
playlist = Listbox(root, selectmode=SINGLE, bg="black", fg="white", font=('arial', 15), width=30)
playlist.grid(columnspan=4)

# Specifying the path from where the list of songs need to displayed on the root window
os.chdir = os.chdir(r"C:\\Users\Music")
songs = os.listdir()
for s in songs:
    playlist.insert(END, s)

# Creating button which is used to control the play,pause,resume and stop the song
playbtn = Button(root, text="Play", command=play,bg='yellow',fg='blue')
playbtn.grid(row=1, column=0)

pausebtn = Button(root, text="Pause", command=pause,bg='yellow',fg='red')
pausebtn.grid(row=1, column=1)

Resumebtn = Button(root, text="Resume", command=resume,bg='yellow',fg='green')
Resumebtn.grid(row=1, column=2)

stopbtn = Button(root, text="Stop", command=stop,bg='red',fg='black')
stopbtn.grid(row=1, column=3)

# To execute the output window
mainloop()
