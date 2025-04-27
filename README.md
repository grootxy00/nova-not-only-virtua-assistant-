# nova-not-only-virtua-assistant-
#this is for my personanl assistant like jarvis a ai devloped by tony stark 
import datetime
import webbrowser
import speech_recognition as sr
import pyttsx3
import tkinter as tk

# Initialize speech engine
engine = pyttsx3.init()

# Function to talk (output speech)
def talk(text):
    engine.say(text)
    engine.runAndWait()

# Function to listen for voice input
def listen():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        audio = recognizer.listen(source)
    try:
        command = recognizer.recognize_google(audio)
        print(f"You said: {command}")
        return command.lower()
    except sr.UnknownValueError:
        print("Sorry, I couldn't understand that.")
        return ""
    except sr.RequestError:
        print("Sorry, there was an error with the speech service.")
        return ""

# Function to update the text output in the GUI
def update_output(text):
    output_text.set(text)

# Nova's brain
def run_nova():
    command = listen()
    
    if "nova" in command:
        response = "Ohh, Ram Ram boss, Mahakal ki Jai!"
        update_output(response)
        talk(response)
    
    elif "time" in command:
        time = datetime.datetime.now().strftime('%I:%M %p')
        response = f"Current time is {time}"
        update_output(response)
        talk(response)
    
    elif "your name" in command:
        response = "My name is Nova, at your service."
        update_output(response)
        talk(response)
    
    elif "how are you" in command:
        response = "I am operating at full efficiency, thank you."
        update_output(response)
        talk(response)
    
    # --- Search Functionality ---
    elif "search for" in command:
        search_query = command.replace("search for", "").strip()
        if "google" in command:
            response = f"Searching Google for {search_query} boss."
            update_output(response)
            talk(response)
            webbrowser.open(f"https://www.google.com/search?q={search_query}")
        elif "stackoverflow" in command:
            response = f"Searching StackOverflow for {search_query} boss."
            update_output(response)
            talk(response)
            webbrowser.open(f"https://stackoverflow.com/search?q={search_query}")
        else:
            response = "I can search on Google or StackOverflow. Please specify."
            update_output(response)
            talk(response)
    
    # --- Website Commands ---
    elif "open youtube" in command:
        response = "Opening YouTube for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.youtube.com")
    
    elif "open google" in command:
        response = "Opening Google for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.google.com")
    
    elif "open stackoverflow" in command:
        response = "Opening StackOverflow for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.stackoverflow.com")
    
    elif "open github" in command:
        response = "Opening GitHub for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.github.com")
    
    elif "open python docs" in command:
        response = "Opening Python documentation for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://docs.python.org/3/")
    
    elif "open twitter" in command:
        response = "Opening Twitter for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.twitter.com")
    
    elif "open wikipedia" in command:
        response = "Opening Wikipedia for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.wikipedia.org")
    
    elif "open reddit" in command:
        response = "Opening Reddit for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.reddit.com")
    
    elif "open facebook" in command:
        response = "Opening Facebook for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.facebook.com")
    
    elif "open amazon" in command:
        response = "Opening Amazon for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.amazon.com")
    
    elif "play music" in command:
        response = "Opening YouTube for you boss."
        update_output(response)
        talk(response)
        webbrowser.open("https://www.youtube.com/results?search_query=music+playlist")
    
    elif "stop" in command or "goodbye" in command:
        response = "Goodbye. Shutting down Nova."
        update_output(response)
        talk(response)
        exit()
    
    else:
        response = "I didn't understand. Please say again."
        update_output(response)
        talk(response)

# Create a window using Tkinter
window = tk.Tk()
window.title("Nova - Your Assistant")

# Set the window size
window.geometry("400x300")

# Set up the output text display
output_text = tk.StringVar()
output_label = tk.Label(window, textvariable=output_text, font=("Arial", 14), wraplength=350, justify="center")
output_label.pack(pady=50)

# Start the Nova assistant
update_output("Nova is ready to assist.")
talk("Nova is ready to assist.")

# Run Nova in the background and start listening
window.after(1000, run_nova)

# Start the Tkinter main loop
window.mainloop()
