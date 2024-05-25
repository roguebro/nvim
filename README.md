## Vim and Neovim as an Open World Text Adventure

About OWTA's:

https://github.com/roguebro/roguebro/blob/main/owta.md

## Setup

Vim or Neovim can be easily installed in many Linux-distro's with the package managers.
They are usually launched with `vim` and `nvim` respectively.

Some distro's will by default link `vi` to `vim`.
But often initially `vi` is a very minimal original vi-clone.

Current versions:

- vim 9+
- neovim 0.9+

On macOS `vim` is available by default.

Installation on Windows can be more complex. Look for (non-)official pre-compiled binaries.
As an additional complexity factor, it depends if you run them from a GUI or from within a terminal.
It might be more interesting to `ssh` into a (Linux/BSD)-system.

Once launched, check which version you have:

    :version

## Start Exploring

This OWTA is not meant for absolute beginners, however - in typical OWTA-fashion - its goal is to learn which features and configuration options are available by navigating the help-system and using various methods of completion.

However, beginners should probably start with the basics of *modal editing* and *motions*. Use

    :Tutor

The tutor and following help-topics should make you understand some basic concepts:

    :h operator
    :h motion
    :h :w

And some more advanced concepts like searching and substituting (perhaps with regular expressions):

    :h :s
    :h /

Learn about window-management and understand what buffers are:

    :h window
    :buffers
    :bn
    :bp

Learn to use help effectively and understand some patterns, as arbitrarily demonstrated here:

    :h ctrl-x
    :h i_ctrl-o
    :h 'textwidth'

A big part of the OWTA-way is to become aware of your surroundings.
Imagine being dropped inside a (n)vim with perhaps a zillion plugins and scripts active.
How can you possibly know what functionality is available?
These internal commands might be worth trying and reading help about:

    :command
    :set
    :option
    :map
    :register

Some of them can be made more helpful by prefixing them with `verbose`:

    :verbose command
    :set
    :setlocal
    :verbose map

An interesting example: suffixing an option with `?` to view it's contents:

    :set path?
    :set runtimepath?
    :set cursorline?

Or setting and unsetting (boolean) options:

    :set cursorline
    :echo &cursorline
    :set nocursorline
    :echo &cursorline

It might be worthwhile to start Vim without any scripts or plugins loaded (`vim -u NONE`) and repeat some of the previous explorations.

Exploring the standard plugins and scripts that are usually included in a vim-distribution can be a treasure trove to discover features or better understand downloadable plugins.

    :set path?
    :set runtimepath?
    :echo $VIMRUNTIME

Another trove is to start vim with maximum debug logging and afterwards read through the created logfile:

    vim -V99logfile1.txt
    vim -u NONE -V99logfile2.txt

Finally, here's a possible exploration-path that can provide you with some interesting finds:

- open a new empty buffer
- enter insert mode (`i`)
- use `CTRL-R =` to write the expression to insert the runtimepath into the buffer: `&runtimepath`
- use a replacement to have each path on its own line: `:s/,/\r/g`
- put the cursor on the front of each path and use `gf` to jump to the directory and explore the files and directories with netrw, use `CTRL-O` to jump back
- alternatively, put the cursor on the end of a path and enter insert mode (`a`) and use file-completion: `ctrl-x ctrl-f`
- the subdirectories from the standard runtime directory can be considered hints to features and command, such as
    - `:h runtime`
    - `:h compiler`
    - `:h autoload`

