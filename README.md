
import tkinter as tk
import random

score = 0
time_left = 30

def move_button():
    x = random.randint(20, 350)
    y = random.randint(80, 300)
    button.place(x=x, y=y)

def catch():
    global score
    score += 1
    score_label.config(text=f"Очки: {score}")
    move_button()

def timer():
    global time_left
    time_left -= 1
    time_label.config(text=f"Час: {time_left}")

    if time_left > 0:
        root.after(1000, timer)
    else:
        button.place_forget()
        result_label.config(text=f"Гру завершено! Очки: {score}")

root = tk.Tk()
root.title("Лови квадрат")
root.geometry("400x400")
root.resizable(False, False)
root.config(bg="lightblue")

title = tk.Label(
    root,
    text="ЛОВИ КВАДРАТ!",
    font=("Arial", 20, "bold"),
    bg="lightblue"
)
title.pack(pady=10)

score_label = tk.Label(
    root, text="Очки: 0",
    font=("Arial", 14), bg="lightblue"
)
score_label.pack()

time_label = tk.Label(
    root, text="Час: 30",
    font=("Arial", 14), bg="lightblue"
)
time_label.pack()

button = tk.Button(
    root,
    text="ЛОВИ!",
    bg="red",
    fg="white",
    font=("Arial", 12, "bold"),
    command=catch
)
button.place(x=150, y=150)

result_label = tk.Label(
    root, text="",
    font=("Arial", 14, "bold"),
    bg="lightblue"
)
result_label.pack(side="bottom", pady=15)

root.after(1000, timer)
root.mainloop()
