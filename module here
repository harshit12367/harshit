# typeprint.py
import sys
import time
import builtins
import random
import os
import threading
import pygame

# Initialize pygame mixer
pygame.mixer.init()

# Save the original print function
original_print = builtins.print

# Enable ANSI colors in Windows
if os.name == 'nt':
    os.system('')

# Color Codes
colors = [
    "\033[91m",  # Red
    "\033[92m",  # Green
    "\033[93m",  # Yellow
    "\033[94m",  # Blue
    "\033[95m",  # Magenta
    "\033[96m",  # Cyan
]

reset_color = "\033[0m"

# Typing effect settings
typing_speed = 0.03  # Typing delay between characters
sound_file = "typing-18347.mp3"  # Your sound file

def play_key_sound():
    try:
        sound = pygame.mixer.Sound(sound_file)
        sound.play()
    except Exception as e:
        original_print(f"Sound error: {e}")

def type_effect(text):
    color = random.choice(colors)

    for char in text:
        sys.stdout.write(f"{color}{char}{reset_color}")
        sys.stdout.flush()
        threading.Thread(target=play_key_sound).start()
        time.sleep(typing_speed)

    original_print()  # New line

def custom_print(*args, **kwargs):
    text = " ".join(str(arg) for arg in args)
    type_effect(text)

# Override the default print
builtins.print = custom_print
