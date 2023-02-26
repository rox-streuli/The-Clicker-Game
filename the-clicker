# THE CLICKER

# Estimated time
# 30-45 minutes
#
# Level of difficulty
# Medium
#
# Objectives
# Learn practical skills related to:
#
#   writing event handlers and assigning them to widgets using the bind()
#   method,

#    managing widgets with the grid manager,

#    using the after() and after_cancel() methods.

# Scenario

# We want you to write a simple but challenging game, which can help
# many people to improve their perception skills and visual memory.
# We'll call the game The Clicker as clicking is what we expect from the player.
#
# The Clicker's board consists of 25 buttons and each of the buttons
# contains a random number from range 1..999. Note: each number is different!
#
# Below the board there is a timer which initially shows 0. The
# timer starts when the user clicks the board for the first time.
#
# We expect the player to click all the buttons in the order imposed
# by the numbers - from the lowest to the highest one. Additional
# rules say that:
#
#   the properly clicked button changes the button's state to DISABLED
#   (it greys the button out)

#    the improperly clicked button shows no activity,

#   the timer increases its value every second,

#    when all the buttons are greyed out (i.e., the player has completed
#    his/her task) the timer stops immediately.
#
# Hint: consider using the <Button-1> event instead of setting the
# command button property - it may simplify your code.

import tkinter as tk
from random import randint


def tic_toc():
    global seconds, after_id
    if clock_on:
        seconds += 1
        clock_label["text"] = str(seconds)
        after_id = clock_label.after(1000, tic_toc)


def click(event):
    global clock_on
    if not clock_on:
        clock_on = True
        clock_label.after(1000, tic_toc)
    button_clicked = event.widget
    number_clicked = int(button_clicked["text"])
    if number_clicked == numbers[0]:
        button_clicked.config(state=tk.DISABLED)
        del numbers[0]
    if len(numbers) == 0:
        clock_on = False
        clock_label.after_cancel(after_id)


window = tk.Tk()
window.title("Clicker")
window.minsize(300, 200)

numbers = []
for i in range(25):
    num = randint(1, 999)
    while num in numbers:
        num = randint(1, 999)
    numbers.append(num)

for i in range(25):
    new_button = tk.Button(window, text=str(numbers[i]), width=10, bg="green")
    new_button.grid(column=i // 5, row=i % 5)
    new_button.bind("<Button-1>", click)

numbers.sort()
seconds = 0

clock_label = tk.Label(window, text="Time: "+str(seconds),
                       font=("Arial", "14", "bold"), bg="orange")
clock_label.grid(row=5, column=0, columnspan=5)
clock_on = False

window.mainloop()
