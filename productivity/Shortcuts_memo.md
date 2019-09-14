## Shortcuts Memo

### Chrome (on Mac)

* Recover a recently closed page/tab - `Command + Shift + T`
* Open a new tab - `Command + T`
* Close current tab - `Command + W`
* Add cursor to the search bar - `Command + L`
* Jump to a specific tab - `Command + 1` through `Command + 8`
* Jump to last tab - `Command + 9`
* Jump to next open tab - `Command + Option + Left`
* Jump to previous open tab - `Command + Option + Right`
* Move tab to new window (there's no direct way to do this via shortcut, you can achieve a similar effect as follows)
    * Select the address bar - `Command + L`
    * Open current tab in new window - `Shift + Enter`

For all shortcuts, refer to [Chrome keyboard shortcuts](https://support.google.com/chrome/answer/157179?hl=en)

### IDEA/PyCharm/WebStorm/AndroidStudio/...

* Run Anything - Double `Control`
* Search Everywhere - Double `Shift`
* Find Action - `Shift + Command + A`
* Find a
    * class - `Command + O`
    * file - `Shift + Command + O`
    * symbol - `Option + Command + O`
* Select
    * next tab - `Shift + Command + ]`
    * previous tab - `Shift + Command + [`
* Extend or shrink selection - `Option + Up/Down`
* Highlight usages in a file - `Shift + Command + F7`
* View recent files - `Command + E`
* View recently edited files - `Command + Shift + E`
* Collapse/Expand code blocks - `Command +/-`
* Reformat code - `Command + Option + L`
* Move 
    * statement up/down - `Shift + Command + Up/Down`
    * line up/down - `Shift + Option + Up/Down`
    * note, `move statement` cannot move a line out of its function, while `move line` could, refer to [IntelliJ IDEA: Move line?](https://stackoverflow.com/a/8362822) for details
* File Structure - `Command + F12`

For details, refer to [Mastering IntelliJ IDEA keyboard shortcuts](https://www.jetbrains.com/help/idea/mastering-keyboard-shortcuts.html)

### Visual Studio Code

* Command Palette - `Shift + Command + P`
* Format Document - `Shift + Option + F`
* Go to Symbol in File (just as `File Structure` in `IDEA`) - `Shift + Command + O`
* Open Recent Files - `Control + R`

For details, refer to [Visual Studio Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)

### iTerm

Make shortcuts `Option + Left`/`Option + Right` enable in iTerm

* Open the iTerm preferences by `Command + ,`
* Navigate to `Profiles` -> `Keys`
* Add/update the following keybinding to your profile
    * `Command + Left` - Send Hex Codes: `0x1b 0x62`
    * `Command + Right` - Send Hex Codes: `0x1b 0x66`

> That should give you the desired behavior not just in ZSH, but also if you SSH into a server running BASH, irb/pry, node etc.

Alias

* List all alias - `$ alias`
* For all git aliases, refer to [Cheatsheet](https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet)

For details, refer to [Looking for ALT+LeftArrowKey solution in zsh](https://stackoverflow.com/a/31328973)

### Terminal Commands (on Mac)

Frequently used commands in terminal

* Find text string in files
    * `$ mdfind -onlyin ./ "TEXT_YOU_WANT_SEARCH"`
        * Note that, it is [not working in hidden directories recursively](https://superuser.com/questions/732571/mdfind-onlyin-not-working-in-hidden-directories-recursvily-how-to-use-it-prope)
    * `$ grep -r TEXT_YOU_WANT_SEARCH ./`
        * Actually, you can almost [search anything with grep](Find anything with grep)
* Display file contents
    * `$ less`
        * `g` - go to the first line
        * `G` - go to the last line
    * difference between `more` and `less`
        * `less` command is faster because it does not load the entire file at once

For details, refer to 
* [How to find files with certain text in the Terminal](https://superuser.com/questions/162999/how-to-find-files-with-certain-text-in-the-terminal/163002)
[Unix Less Command: 10 Tips for Effective Navigation](https://www.thegeekstuff.com/2010/02/unix-less-command-10-tips-for-effective-navigation)

### All Applicable

* Open the preferences of the current application - `Command + ,`
* Make current window full screen or not - `Control + Command + F`
* Go to parent directory - `Command + Up`
* Minimize the front window - `Command + M`
* Minimize all windows of the front window - `Option + Command + M`
* Hide all other apps except for the front - `Option + Command + H`

For all shortcuts on mac, refer to [Mac keyboard shortcuts](https://support.apple.com/en-us/HT201236)
