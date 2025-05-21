## About

**BashUI** is a lightweight toolkit for building styled terminal dialogs in Bash.

It includes framed boxes, user input prompts, list selections, text formatting, and customizable visual styles — everything you need to create clean, informative, or interactive command-line interfaces.

![Demo of BashUI](assets/demo-bashui.gif)

## Features

* Framed one-line and multi-line boxes with 16 border styles
* User input prompts with optional timeout and default answers
* List selection menus with automatic numbering and sorting
* Customizable text styles (bold, color, background, blink...)
* Automatic text wrapping, alignment, and indentation
* Modular functions you can reuse in your own scripts
* Single-file script for ease of use
* No dependencies beyond Bash (v4+) and standard Unix tools

## Installation

Clone the repository and use BashUI as a standalone CLI utility:

```bash
git clone https://github.com/jpfleury/bashui.git
path/to/bashui/bashui box "Thank you for using BashUI!"
```

## Usage

BashUI provides three main commands:

```bash
bashui box <text> [text_style] [border_style] [newline_before] [newline_after]

bashui input <mode> [description] [question] [empty_is_valid] [indent_question] [timeout_s] [text_style] [border_style]

bashui title <text> <level> [text_style] [border_style] [newline_before] [newline_after]
```

Run `bashui --help` to see all options and detailed examples.

### Compatibility

* Requires Bash 4 or higher
* Uses standard Unix tools: `awk`, `sed`, `fold`, `tput`

## Examples to get started

Simple one-line box:

```bash
bashui box "Operation completed successfully"
bashui box "Operation completed successfully" success
```

Two-line informative box:

```bash
bashui box "Backup~~~The operation finished without errors."
```

Two-line box for errors:

```bash
bashui box "Database error~~~Connection timed out on db-server-01." error
bashui box "Database error~~~Connection timed out on db-server-01." error_bg
```

User confirmation ("No" by default):

```bash
answer=$(bashui input yN "Delete all files?")

if [[ $answer == "y" ]]; then
	echo "Proceeding with deletion..."
fi
```

User confirmation ("Yes" by default):

```bash
answer=$(bashui input Yn "Restart the server now?")

if [[ $answer == "y" ]]; then
	echo "Restarting..."
fi
```

Selection list:

```bash
selected=$(bashui input list $'Choose a database engine:\nSQLite\nPostgreSQL\nMySQL')

echo "You selected $selected"
```

Title display:

```bash
bashui title "Setup complete" 2 success
```

## License

Author: Jean-Philippe Fleury <https://github.com/jpfleury>
Copyright © Jean-Philippe Fleury, 2021-2025

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
