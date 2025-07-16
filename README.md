# password-generator
import tkinter as tk
import string
import random
from tkinter import messagebox

def generate_password():
    try:
        length = int(length_entry.get())
        if length < 4:
            result_label.config(text="❌ Minimum 4 characters required!")
            return

        characters = string.ascii_letters + string.digits + string.punctuation
        password = ''.join(random.choice(characters) for _ in range(length))
        result_label.config(text=f"🔐 Password:\n{password}")
    except ValueError:
        result_label.config(text="❌ Enter a valid number!")

# GUI setup
root = tk.Tk()
root.title("Password Generator")
root.geometry("300x250")
root.resizable(False, False)

tk.Label(root, text="Password Generator", font=("Arial", 16)).pack(pady=10)

tk.Label(root, text="Enter password length:", font=("Arial", 12)).pack()
length_entry = tk.Entry(root, width=10, font=("Arial", 12))
length_entry.pack(pady=5)

tk.Button(root, text="Generate", font=("Arial", 12), command=generate_password).pack(pady=10)

result_label = tk.Label(root, text="", font=("Arial", 12), wraplength=250, justify="center", fg="green")
result_label.pack(pady=10)

root.mainloop()
