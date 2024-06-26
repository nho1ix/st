# Modified version of Luke's build of st - the simple (suckless) terminal <a href="https://hits.seeyoufarm.com"><img alt="visits" align="right" src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fnho1ix%2Fst&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false"/></a>

The [suckless terminal (st)](https://st.suckless.org/) with some additional
features that make it literally the best terminal emulator ever:

## Unique features (using dmenu)

+ **follow urls** by pressing `win-l`
+ **copy urls** in the same way with `win-y`
+ **copy the output of commands** with `win-o`

## Bindings for

+ **scrollback** with `win-↑/↓` or `win-pageup/down` or `shift` while scrolling the
  mouse.
+ OR **vim-bindings**: scroll up/down in history with `win-k` and `win-j`.
  Faster with `win-u`/`win-d`.
+ **zoom/change font size**: same bindings as above, but holding down shift as
  well. `win-home` returns to default
+ **copy text** with `win-c`, **paste** is `win-v` or `shift-insert`

## Pretty stuff

+ Compatibility with `Xresources` and `pywal` for dynamic colors.
+ Default [gruvbox](https://github.com/morhetz/gruvbox) colors otherwise.
+ Transparency/alpha, which is also adjustable from your `Xresources`.
+ Default font is system "mono" at 14pt, meaning the font will match your
  system font.

## Other st patches

+ Boxdraw
+ Ligatures
+ font2
+ updated to latest version 0.8.5

## Installation for newbs

You should have xlib header files and libharfbuzz build files installed.

```
git clone https://github.com/LukeSmithxyz/st
cd st
sudo make install
```

Obviously, `make` is required to build. `fontconfig` is required for the
default build, since it asks `fontconfig` for your system monospace font. It
might be obvious, but `libX11` and `libXft` are required as well. Chances are,
you have all of this installed already.

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the
`$LIBS` before compiling.

Be sure to have a composite manager (`xcompmgr`, `picom`, etc.) running if you
want transparency.

## How to configure dynamically with Xresources

For many key variables, this build of `st` will look for X settings set in
either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these
files to load the settings.

For example, you can define your desired fonts, transparency or colors:

```
*.font:	Liberation Mono:pixelsize=12:antialias=true:autohint=true;
*.alpha: 0.9
*.color0: #111
...
```

The `alpha` value (for transparency) goes from `0` (transparent) to `1`
(opaque). There is an example `Xdefaults` file in this respository.

### Colors

To be clear about the color settings:

- This build will use gruvbox colors by default and as a fallback.
- If there are Xresources colors defined, those will take priority.
- But if `wal` has run in your session, its colors will take priority.

Note that when you run `wal`, it will negate the transparency of existing windows, but new windows will continue with the previously defined transparency.

## Contact

- Luke Smith <luke@lukesmith.xyz>
- [https://lukesmith.xyz](https://lukesmith.xyz)
