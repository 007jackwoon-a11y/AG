# AG
import tkinter as tk
from tkinter import messagebox

class ApologyApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Official Apology Terminal")
        
        # Make it fullscreen to grab attention
        self.root.attributes('-fullscreen', True)
        self.root.configure(bg="#1a1a1a")

        # Prevent closing via the 'X' button or Alt+F4
        self.root.protocol("WM_DELETE_WINDOW", self.prevent_escape)

        # Main container frame
        frame = tk.Frame(root, bg="#1a1a1a")
        frame.place(relx=0.5, rely=0.5, anchor=tk.CENTER)

        # Apology Title
        title_label = tk.Label(
            frame, 
            text="⚠️ SYSTEM ERROR: APOLOGY REQUIRED ⚠️", 
            font=("Helvetica", 24, "bold"), 
            fg="#ff4d4d", 
            bg="#1a1a1a"
        )
        title_label.pack(pady=20)

        # Apology Message (Customize this!)
        message = (
            "I am deeply, truly, and profoundly sorry for what I did.\n\n"
            "Device control has been temporarily suspended until forgiveness is granted.\n"
            "Please click the button below to restore full system functionality."
        )
        msg_label = tk.Label(
            frame, 
            text=message, 
            font=("Helvetica", 16), 
            fg="#ffffff", 
            bg="#1a1a1a", 
            justify=tk.CENTER
        )
        msg_label.pack(pady=20)

        # Forgiveness Button
        self.forgive_btn = tk.Button(
            frame, 
            text="I Forgive You ❤️", 
            font=("Helvetica", 18, "bold"), 
            bg="#28a745", 
            fg="white", 
            padx=20, 
            pady=10, 
            command=self.accept_apology
        )
        self.forgive_btn.pack(pady=30)

    def prevent_escape(self):
        # Triggers when they try to click 'X'
        messagebox.showwarning(
            "Access Denied", 
            "Nice try! You cannot escape until forgiveness is officially granted."
        )

    def accept_apology(self):
        # Success message and exit
        messagebox.showinfo(
            "System Restored", 
            "Thank you for your forgiveness! Friendship restored successfully."
        )
        self.root.destroy()

if __name__ == "__main__":
    root = tk.Tk()
    app = ApologyApp(root)
    root.mainloop()
