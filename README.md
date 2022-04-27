# Ducky Script Cheatsheet


------

## Overview

Ducky Script is a simple scripting language for automating keypresses. It was originally developed for [USB Rubber Ducky](https://shop.hak5.org/products/usb-rubber-ducky-deluxe).

This guide gives an concise overview of Ducky Script. For more information, [see this page](https://github.com/hak5darren/USB-Rubber-Ducky/wiki/Duckyscript).

Official documentation of Ducky Script, [see this page](https://docs.hak5.org/usb-rubber-ducky-1/the-ducky-script-language/ducky-script-quick-reference)

## Examples

Ducky Script is very easy and straightforward to write, you basically just tell it what key to press!

Let's take a look at some examples first:

### Open Task Manager

```
CONTROL SHIFT ESC
```

### Open a webpage on windows

```
WINDOWS r
DELAY 400
STRING https://www.youtube.com/watch?v=dQw4w9WgXcQ
ENTER
```

### Save a webpage then close it

```
CONTROL s
DELAY 600
ENTER
DELAY 600
CONTROL w
```

## Syntax Details

* One command per line. **`Each line has a 256 character limit!`**

* 1000 milliseconds = 1 second.

* Check out the [sample profiles](https://github.com/dekuNukem/duckyPad/tree/master/sample_profiles) for more examples.

## List of Commands

[REM](#REM)

[DEFAULTDELAY](#DEFAULTDELAY)

[DEFAULTCHARDELAY](#DEFAULTCHARDELAY)

[DELAY](#DELAY)

[STRING](#STRING)

[REPEAT](#REPEAT)

[Special Keys](#Special-Keys)

[Mouse Buttons](#Mouse-Buttons)

[MOUSE_MOVE](#MOUSE_MOVE-X-Y)

[MOUSE_WHEEL](#MOUSE_WHEEL-X)

[KEYDOWN / KEYUP](#KEYDOWN--KEYUP)

[SWCOLOR](#SWCOLOR)

[DP_SLEEP](#DP_SLEEP)

[PREV_PROFILE / NEXT_PROFILE](#PREV_PROFILE--NEXT_PROFILE)

[GOTO_PROFILE](#GOTO_PROFILE)

[HOLD](#HOLD-experimental)

[LOOP](#LOOP-experimental)

-----

### REM

`REM` is comment, any line starting with `REM` is ignored.

### DEFAULTDELAY

`DEFAULTDELAY` specifies how long (in milliseconds) to wait between **`each line of command`**.

If unspecified, `DEFAULTDELAY` is 18ms in duckyPad.

```
DEFAULTDELAY 100

REM duckyPad will wait 100ms between each subsequent command
```

### DEFAULTDELAYFUZZ X

Adds an additional random delay from 0 to X milliseconds after `each line of command`, can be used to make typing more human-like.

Set to 0 to disable.

### DEFAULTCHARDELAY

`DEFAULTCHARDELAY` specifies how long (in milliseconds) to wait between each **`key stroke`**.

If unspecified, `DEFAULTCHARDELAY` is 18ms in duckyPad.

```
DEFAULTCHARDELAY 50

REM duckyPad will wait 50ms between each key stroke
```

### DEFAULTCHARDELAYFUZZ X

Adds an additional random delay from 0 to X milliseconds after `each key stroke`, can be used to make typing more human-like.

Set to 0 to disable.

### DELAY

`DELAY` creates a momentary pause in script execution. Useful for waiting for UI to catch up.

```
DELAY 1000

REM waits 1000 milliseconds, or 1 second
```

### STRING

`STRING` types out whatever after it **`as-is`**.

```
STRING Hello world!!!

REM types out "Hello world!!!"
```

### REPEAT

Repeats the last command **`n`** times.

```
STRING Hello world
REPEAT 10

REM types out "Hello world" 11 times (1 original + 10 repeats)
```

### Special Keys

duckyScript also supports a bunch of special keys:

```
CTRL / RCTRL
SHIFT / RSHIFT
ALT / RALT
WINDOWS / RWINDOWS
COMMAND / RCOMMAND (mac)
OPTION / ROPTION (mac)
ESC
ENTER
UP
DOWN
LEFT
RIGHT
SPACE
BACKSPACE
TAB
CAPSLOCK
PRINTSCREEN
SCROLLLOCK
PAUSE
BREAK
INSERT
HOME
PAGEUP
PAGEDOWN
DELETE
END
MENU
POWER

F1
F2
F3
F4
F5
F6
F7
F8
F9
F10
F11
F12
F13
F14
F15
F16
F17
F18
F19
F20
F21
F22
F23
F24

(media keys)
MK_VOLUP
MK_VOLDOWN
MK_MUTE
MK_PREV
MK_NEXT
MK_PP (play/pause)
MK_STOP

(numpad keys)
NUMLOCK
KP_SLASH
KP_ASTERISK
KP_MINUS
KP_PLUS
KP_ENTER
KP_0
KP_1
KP_2
KP_3
KP_4
KP_5
KP_6
KP_7
KP_8
KP_9
KP_DOT
KP_EQUAL
```

Those special keys can be used on their own:

`WINDOWS`

...or can be combined with a character to form shortcuts:

`WINDOWS s`

...or can be combined with other special keys:

`WINDOWS SHIFT s`

------

* Type the key names as-is in **`ALL CAPS`**.

* **`UP TO 6 KEYS`** can be pressed simultaneously.

