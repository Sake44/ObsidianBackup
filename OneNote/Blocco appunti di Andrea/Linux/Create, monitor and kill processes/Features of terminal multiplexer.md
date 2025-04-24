# Introduction

In electronics, a multiplexer (or mux) is a device that allows for multiple inputs to be connected to a single output. Thus, a terminal multiplexer gives us the ability to switch between different inputs as required. Although not exactly the same, screen and tmux share a series of common features:

• Any successful invocation will result in at least a session which — in turn — will include at least a window. Windows contain programs.
• Windows can be split into regions or panes — which can aid in productivity when working with various programs simultaneously.
• Ease of control: to run most commands, they use a key combination — the so-called command
prefix or command key — followed by another character.
• Sessions can be detached from their current terminal (that is, programs are sent to the
background and continue to run). This guarantees complete execution of programs no matter if
we accidentally close a terminal, experience an occasional terminal freeze or even remote
connection loss.
• Socket connection.
• Copy mode.
• They are highly customizable.

## Gnu Screen

Creation of GNU Screen in 1987: emulate multiple independent VT100 screens on a single physical terminal.

### Windows
#GNU Screen is invoked just by typing screen into the terminal. Screen’s command prefix is **Ctrl + a**.
To see all windows at the bottom of the terminal display, type: Ctrl + a - w. 
```bash
#!/bin/bash
0*$ bash

# Example output
# To create a new screen type: Ctrl + a - c

0-$ bash 1*$ bash
```

To rename a #screen, we can: Ctrl + a - A and write the new window name.
To create another window but provide it a name from the start: 
```
screen -t <screen name>
```
You can move between windows in different ways:
• By using Ctrl + a - n (go to next window) and Ctrl + a - p (go to previous window).
• By using Ctrl + a - number (go to window number number).
• By using Ctrl + a - " to see a list of all windows. You can move up and down with the arrow keys and select the one you want with Enter. 

While working with windows it is **important** to remember the following:
• Windows run their programs completely independent of each other.
• Programs will continue to run even if their window is not visible
To remove a window, simply terminate the program running in it (once the last window is
removed, screen will itself terminate). Alternatively, use **Ctrl + a - k** while in the window you want to remove.

### Regions
#screen can divide a terminal screen up into multiple regions in which to accommodate windows.
These divisions can be either horizontal ( Ctrl + a - S ) or vertical ( Ctrl + a - | ).
To move to the new region, type Ctrl + a - Tab. 

**Important** aspects to keep in mind when working with regions are:
• You move between regions by typing Ctrl + a - Tab .
• You can terminate all regions except the current one with Ctrl + a - Q .
• You can terminate the current region with Ctrl + a - X .
• Terminating a region does not terminate its associated window.

### Sessions
So far we have played with a few windows and regions, but all belonging to the same and only session. It is time to start playing with sessions.To see a list of all sessions, type: 
```bash
#!/bin/bash
screen -list 
# or 
screen -ls
```

#### Session Detachment
For a number of reasons you may want to detach a screen session from its terminal:
• To let your computer at work do its business and connect remotely later from home.
• To share a session with other users.
You detach a session with the key combination **Ctrl + a - d**.

#### Copy & Paste: Scrollback Mode
GNU Screen features a #copy or #scrollback mode. Once entered, you can move the cursor in the current window and through the contents of its history using the arrow keys.

The steps to follow are:
1. Enter copy/scrollback mode: Ctrl + a - [ .
2. Move to the beginning of the piece of text you want to copy using the arrow keys.
3. Mark the beginning of the piece of text you want to copy: Space.
4. Move to the end of the piece of text you want to copy using the arrow keys.
5. Mark the end of the piece of text you want to copy: Space.
6. Go to the window of your choice and paste the piece of text: Ctrl + a - ] .
#### Customization of screen
The system-wide configuration file for screen is /etc/screenrc. Alternatively, a user-level
~/.screenrc can be used. The file includes four main configuration sections:
- SCREEN SETTINGS: You can define general settings by specifying the directive followed by a space and the value as in: defscrollback 1024.
- SCREEN KEYBINDINGS: This section is quite interesting as it allows you to redefine keybindings that perhaps interfere with your everyday use of the terminal.
- TERMINAL SETTINGS
- STARTUP SCREENS

### Tmux
#tmux was released in 2007. Although very similar to screen, it includes a few notable differences:
• **Client-server model**: the server supplies a number of sessions, each of which may have a
number of windows linked to it that can, in turn, be shared by various clients.
• Interactive selection of sessions, windows and clients via menus.
• The same window can be linked to a number of sessions.
• Availability of both vim and Emacs key layouts.
• UTF-8 and 256-colour terminal support.

#### Windows
tmux can be invoked by simply typing tmux at the command prompt. You will be shown a shell prompt and a status bar at the bottom of the window:
```
[0] 0:bash*                                           "debian" 18:53 27-Aug-19
```
You can assign session and window names when invoking tmux: 
```
tmux new -s "LPI" -n "Window zero"
```

tmux’s command prefix is **Ctrl + b** . To create a new window, just type Ctrl + b - c.
You can rename a window with **Ctrl + b -** , . When prompted, supply the new name and
hit Enter:
```
(rename-window) Window one
```
You can have all windows displayed for selection with Ctrl + b - w (use the arrow keys to move up and down and enter to select):
```
(0)0: Window zero- "debian"
(1)1: Window one* "debian"
```

#### Panes
The window-splitting facility of screen is also present in #tmux. The resulting divisions are not called regions but #panes, though. The most important difference between regions and panes is that the latter are complete #pseudo-terminals linked to a window. This means that killing a pane will also kill its pseudo-terminal and any associated programs running within.
Important pane commands:
Ctrl + b - ↑ , ↓ , ← , → move between panes.
Ctrl + b - ; move to the last active pane.
Ctrl + b - Ctrl + arrow key resize pane by one line.
Ctrl + b - Alt + arrow key resize pane by five lines.
Ctrl + b - { swap panes (current to previous).
Ctrl + b - } swap panes (current to next).
Ctrl + b - z zoom in/out panel.
Ctrl + b - t tmux displays a fancy clock inside the pane (kill it by pressing q).
Ctrl + b - ! turn pane into window.

#### Sessions
To list sessions in tmux you can use Ctrl + b - s, alternatively you can type: 
```
tmux ls
```

You can switch sessions with **Ctrl + b - s**. To kill a session, you can use the command: 
```
tmux kill-session -t SESSION-NAME
```

#### Customization of tmux
The configuration files for #tmux are typically located at /etc/tmux.conf and ~/.tmux.conf.
There is also the possibility of starting #tmux with the -f switch to supply an alternate configuration file. You can find a tmux configuration file example located at /usr/share/doc/tmux/example_tmux.conf