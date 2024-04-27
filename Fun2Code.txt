from PIL import ImageTk, Image
from tkinter import messagebox
import tkinter as tk
import cryptography
from cryptography.fernet import Fernet

encrypt_table = str.maketrans(
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz", "ZYXWVUTSRQPONMLKJIHGFEDCBAzyxwvutsrqponmlkjihgfedcba")

# Define a function to encrypt a message


def encrypt(message):
    return message.translate(encrypt_table)


def decrypt(ciphertext):
    return ciphertext.translate(encrypt_table)


def button_click():
    text = textbox.get("1.0", "end-1c")
    textbox.configure(bg='#f5f5f5', fg='black', font=('Arial', 12))

    # Decrypt the message
    ciphertext = encrypt(text)
    decrypted_text = decrypt(ciphertext)
    messagebox.showinfo("Message", "The Encrypted Message: " + ciphertext)


def Decryption():
    text = textbox.get("1.0", "end-1c")
    textbox.configure(bg='#f5f5f5', fg='black', font=('Arial', 12))
    # Decrypt the message
    ciphertext = encrypt(text)
    decrypted_text = decrypt(ciphertext)
    messagebox.showinfo("Message", "The Decrypted Message: " + decrypted_text)


root = tk.Tk()
root.title("GUI Example")
image = Image.open("encrypt.PNG")
photo = ImageTk.PhotoImage(image)

# Set the background image of the root window
root.configure(background='black')
background_label = tk.Label(root, image=photo)
background_label.place(relwidth=1, relheight=1)


# Define a custom font
text_font = ("Helvetica", 12)

# Create the textbox with custom font and background color
textbox = tk.Text(root, height=1, width=30, font=text_font, bg="#f0f0f0")
textbox.configure(bg='#f5f5f5', fg='black', font=('Arial', 12))

textbox.pack(pady=10)

# Create the button with custom font, background color, and border


button = tk.Button(root, text="Encrypt", font=text_font,
                   bg="#008CBA", fg="white", bd=0, command=button_click)

button.configure(bg='#007bff', fg='white', font=('Arial', 14), padx=10, pady=5)

button1 = tk.Button(root, text="Decrypt", font=text_font,
                    bg="#008CBA", fg="white", bd=0, command=Decryption)

button1.configure(bg='#007bff', fg='white',
                  font=('Arial', 14), padx=10, pady=5)


# button1.place(x=-30, y=50)
button.pack()
button1.pack()


root.mainloop()
