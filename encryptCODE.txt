from PIL import ImageTk, Image
from tkinter import messagebox
import tkinter as tk


# Define the encryption key
key = 5

# Define a function to encrypt a message


def encrypt(message):
    ciphertext = ""
    for letter in message:
        if letter.isalpha():
            if letter.isupper():
                Base = ord('A')
            else:
                Base = ord('a')

            ciphertext += chr((ord(letter) - Base + key) % 26 + Base)

        else:
            # Leave non-alphabetic characters as-is
            ciphertext += letter

    return ciphertext

# Define a function to decrypt a message


def decrypt(ciphertext):
    plaintext = ""
    for letter in ciphertext:
        if letter.isalpha():
            if letter.isupper():
                Base = ord('A')
            else:
                Base = ord("a")

            plaintext += chr((ord(letter) - Base - key) % 26 + Base)

        else:
            # Leave non-alphabetic characters as-is
            plaintext += letter

    return plaintext


def button_click():
    print("Function Three GUI")
    text = textbox.get("1.0", "end-1c")
    ciphertext = encrypt(text)
    decrypted_text = decrypt(ciphertext)
    messagebox.showinfo("Encrypted", "The Encrypted Message: " + ciphertext)


def Decryptiom():
    text = textbox.get("1.0", "end-1c")
    ciphertext = encrypt(text)
    decrypted_text = decrypt(ciphertext)
    messagebox.showinfo(
        "Decrypted", "The Decrypted Message: " + decrypted_text)


root = tk.Tk()
root.title("Encryption Project")
image = Image.open("enc.PNG")
photo = ImageTk.PhotoImage(image)

# Set the background image of the root window
background_label = tk.Label(root, image=photo)
background_label.place(relwidth=1, relheight=1)
# Define a custom font
text_font = ("Helvetica", 12)

# Create the textbox with custom font and background color
textbox = tk.Text(root, height=1, width=30, font=text_font, bg="#DDD")
textbox.pack(pady=10)

# Create the button with custom font, background color, and border
button = tk.Button(root, text="Encrypt", font=text_font,
                   bg="#008CBA", fg="white", bd=0, command=button_click)

button1 = tk.Button(root, text="Decrypt", font=text_font,
                    bg="#008CBA", fg="white", bd=0, command=Decryptiom)
button.pack()
button1.pack()

root.mainloop()
