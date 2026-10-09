# Назва проєкту

import tkinter as tk
from tkinter import messagebox

# Налаштування гри
score = 0
clicks = 0
bonus = 1

def click_bomb():
    global score, clicks, bonus

    clicks += 1
    score += bonus

    if clicks % 10 == 0:
        bonus += 1
        messagebox.showinfo(
            "Бонус!",
            f"Тепер за клік ти отримуєш {bonus} очок!"
        )

    score_label.config(text=f"💣 Очки: {score}")
    clicks_label.config(text=f"Кліки: {clicks}")

def reset_game():
    global score, clicks, bonus

    score = 0
    clicks = 0
    bonus = 1

    score_label.config(text="💣 Очки: 0")
    clicks_label.config(text="Кліки: 0")
    bonus_label.config(text="Бонус за клік: 1")

# Створення вікна
root = tk.Tk()
root.title("Bomb Clicker")
root.geometry("400x450")
root.configure(bg="#202436")
root.resizable(False, False)

title = tk.Label(
    root,
    text="💣 BOMB CLICKER 💣",
    font=("Arial", 22, "bold"),
    fg="#ffcc33",
    bg="#202436"
)
title.pack(pady=20)

score_label = tk.Label(
    root,
    text="💣 Очки: 0",
    font=("Arial", 18, "bold"),
    fg="white",
    bg="#202436"
)
score_label.pack(pady=10)

clicks_label = tk.Label(
    root,
    text="Кліки: 0",
    font=("Arial", 14),
    fg="#bfc9e0",
    bg="#202436"
)
clicks_label.pack(pady=5)

bonus_label = tk.Label(
    root,
    text="Бонус за клік: 1",
    font=("Arial", 14),
    fg="#66ff99",
    bg="#202436"
)
bonus_label.pack(pady=5)

bomb_button = tk.Button(
    root,
    text="💣",
    font=("Arial", 65),
    command=click_bomb,
    bg="#343c58",
    fg="white",
    activebackground="#515e85",
    relief="flat",
    cursor="hand2"
)
bomb_button.pack(pady=20)

reset_button = tk.Button(
    root,
    text="🔄 Почати заново",
    font=("Arial", 13, "bold"),
    command=reset_game,
    bg="#e74c3c",
    fg="white",
    activebackground="#c0392b",
    relief="flat",
    padx=15,
    pady=8
)
reset_button.pack(pady=10)

root.mainloop()
