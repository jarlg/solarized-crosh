solarized-crosh
===============

configuration for using solarized theme with crosh

If you are running ChromeOS, have a minimal chroot installed (no X), are working with it using mostly tmux/screen + editor of choice + other terminal tools, then this is a quick guide to set crosh up to properly use the solarized colorscheme. We do this by configuring crosh through the javascript console (ctrl+shift+j).

First (optional?) set crosh to 256 color mode by opening crosh, and entering the javascript console. Set ```$TERM```:

```javascript
term_.prefs_.set('environment', { TERM: "xterm-256color" })
```
(not sure about the importance of this step, and ```screen-256color``` could probably work the same. I use tmux, and it's working with this.) 


Secondly, set ```$TERM``` for your chroot session, in your .bashrc, .zshenv, whatever..
 
```bash
export TERM=screen-256color
```
or ```xterm-256color``` if you aren't using tmux/screen.


Thirdly, (optional) it's a good idea to force tmux into 256 color mode, so I have it aliased (.zshenv):

```bash
alias tmux="tmux -2"
```


Now, we need to configure the colors for crosh: 

```javascript
base03 =     "#002b36";
base02 =     "#073642";
base01 =     "#586e75";
base00 =     "#657b83";
base0 =      "#839496";
base1 =      "#93a1a1";
base2 =      "#eee8d5";
base3 =      "#fdf6e3";
yellow =     "#b58900";
orange =     "#cb4b16";
red =        "#dc322f";
magenta =    "#d33682";
violet =     "#6c71c4";
blue =       "#268bd2";
cyan =       "#2aa198";
green =      "#859900";

term_.prefs_.set('color-palette-overrides',
        [ base02 , red     , green  , yellow,
        blue     , magenta , cyan   , base2,
        base03   , orange  , base01 , base00,
        base0    , violet  , base1  , base3 ]);
```
This overrides the default color-palette with the palette I've found to match with the solarized "dark" colorscheme. It doesn't fit perfectly with the light one, but it's just some tweaks away.

## Customizing crosh
I havent' really found any good lookup of how to customize crosh, but here are some useful things. ```'...'``` usually means you can put some CSS-readable value, f.ex. ```'#bababa'```.

Change foreground, background or cursor color: ```term_.prefs_.set('foreground-color', '...')```

Blinking cursor? ```term_.prefs_.set('cursor-blink', false)```

Screwed something up?  Globally undo everything you changed: ```term_.prefs_.resetAll()```


## Related useful stuff

* [tmux solarized config](https://github.com/seebi/tmux-colors-solarized)
* [solarized main repo](https://github.com/altercation/solarized)

## Screenshots

![screenshot1](https://raw.github.com/jarlg/solarized-crosh/master/ss1.png)
