# bashed

`bashed` is a command-line text editor written in Bash. In terms of functionality, it's comparable to Windows Notepad or an HTML `<textarea>`.

## Features

* **Standard cursor movement controls**
  * Move the cursor using the arrow keys, <key>Home</key>, and <key>End</key>
  * Move by words by holding <key>Ctrl</key>*
* **Select text** by holding <key>Shift</key>*
* **Clipboard functionality:** cut, copy, and paste

_*Not supported in the Linux console, because it does not report modifier keys._

## Limitations

* No undo
* No search
* No line wrap
* Can only edit one file at a time

## System Requirements

* About 30 KB free disk space
* Linux console, or an XTerm-compatible terminal emulator
* Bash shell, version 4+ _(note: tested on 5.0.17)_
* GNU coreutils (`cat`, `tr`, `stty`)
* ncurses (`tput`, `reset`)
* `xclip` to use the X selection as the clipboard (optional)

## Usage

Download and run the [bashed](bashed) script.

```console
$ curl -O https://raw.githubusercontent.com/justinyaodu/bashed/master/bashed
$ chmod +x bashed
$ ./bashed my-file.txt
```

## Configuration

User preferences may be configured in `~/.bashedrc`, which is simply a Bash script sourced by `bashed`. This is probably a security risk, but `bashed` is not designed for serious usage anyway :)

## Performance

Bash is not known for being particularly fast. To achieve acceptable performance, `bashed`:

* Uses Bash built-ins whenever possible
* Avoids subshells by using global variables to return values from functions
* Only redraws the parts of the display that changed since the last frame
