# Guess-num
# Description: This is a simple guess num game .
# There are 10 attempts .
# Author : Dina Maher (FCAI) .

# import libraries
from tkinter import *
import random

# The number of attempts
attempts = 10
answer = 45   # The correct ans

# Check the answer
def check_answer():
    global attempts
    global text

    attempts -= 1
    guess = int(entry_window.get())

    # If The number guessed is correct
    if answer == guess:
        text.set("You win! Congratulations!!")
        btn_check.pack_forget()

    # If The attempts are over
    elif attempts == 0:
        text.set("Game Over!! You are out of attempts!")
        btn_check.pack_forget()

    # If incorrect low num
    elif guess < answer:
        text.set("Incorrect! You have " + str(attempts) + " attempts remaining - Go Higher!!")

    # If incorrect high num
    elif guess > answer:
        text.set("Incorrect! You have " + str(attempts) + " attempts remaining - Go Lower!!")

    return

# Create the borders of the window and the title
Guess = Tk()
Guess.title("Guess The Number")
Guess.geometry("500x200")

# Create the label of the window
label = Label(Guess,text='Guess The Number between [1:100]',foreground = "black",font = ("Arial",18))
label.pack()

# Create the entry of the window
entry_window = Entry(Guess,width = 45,borderwidth = 6,background= "white",foreground = "black")
entry_window.pack()

# Create the button of the check
btn_check = Button(Guess,text = "PLAY",foreground = "white" ,background = "black",width = 15,command = check_answer)
btn_check.pack()

# Create the button of the quit
btn_quit = Button(Guess,text = "EXIT",foreground = "white" ,background = "black",width = 15,command = Guess.destroy)
btn_quit.pack()

# Start Text
text = StringVar()
text.set("You have 10 attempts! Good Luck!!")

# Attempts Text
guess_attempts = Label(Guess,textvariable = text,font = ("Arial",15))
guess_attempts.pack()

Guess.mainloop()
