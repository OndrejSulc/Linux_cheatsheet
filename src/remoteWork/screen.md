# REMOTE WORK


## Screen

Start a screen session
```
screen
```

Proper size of screen (usually for serial port) - add line line in `/etc/profile`
```
shopt -s checkwinsize
```

Some terminal issues fixed with 
```
TERM=screen
```

Connect to serial port with baud rate (bits/s) 115200
```
screen /dev/ttyS1 115200
```

Start named screen session
>screen -S session_name

Shortcuts to manage single screen session
```
Ctrl+a c      Create a new window (with shell).
Ctrl+a "      List all windows.
Ctrl+a 0      Switch to window 0 (by number).
Ctrl+a A      Rename the current window.
Ctrl+a S      Split current region horizontally into two regions.
Ctrl+a |      Split current region vertically into two regions.
Ctrl+a tab    Switch the input focus to the next region.
Ctrl+a Ctrl+a Toggle between the current and previous windows
Ctrl+a Q      Close all regions but the current one.
Ctrl+a X      Close the current region.
Ctrl+a X      Close the current region.

```

Detach from screen session
>Ctrl+a d

Detach and terminate session
>Ctrl+d

List screens
>screen -ls

Restore screen "10835.session_name"
>screen -r 10835


## Nano editor

Install nano
>sudo apt-get install nano

Open file using nano
>nano filename

Options:
```
-w       Opens the file in a standard format - does not wrap text to fit screen

```

Shortcuts:
```
Command	Explanation
CTRL + A	Lets you jump to the beginning of the line.
CTRL + E	Lets you to jump to the end of the line.
CTRL + Y	Scrolls page down.
CTRL + V	Scrolls page up.
CTRL + G	A Help window will pop out and show you all the available commands.
CTRL + O	To save the file. Nano will ask you to edit or verify the desired file name.
CTRL + W	Search for a specified phrase in your text. Press ALT + W to search for the same phrase again.
CTRL + K	It cuts the entire selected line to the cut buffer (similar to clipboard).
CTRL + U	To paste the text from the cut buffer into the selected line.
CTRL + J	Justifies the current paragraph.
CTRL + C	Shows the current cursor position in the text (line/column/character).
CTRL + R	Opens a file and inserts it at the current cursor position.
CTRL + X	To exit Nano text editor. It prompts a save request if you made any changes to the file.
CTRL + \	Replaces string or a regular expression.
CTRL + T	Invokes the spell checker, if available.
CTRL + _	Lets you go to the specified line and column number.
ALT + A	To select text. You can combine this command with CTRL + K to cut a specific part of the text to the cut buffer.
```

<div style="page-break-after: always;"></div>
