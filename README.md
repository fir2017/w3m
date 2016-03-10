# w3m

This is my modified/patched version of **[w3m](http://w3m.sourceforge.net)**.

Based on: version **0.5.3.git20160228**

git://anonscm.debian.org/collab-maint/w3m.git#commit=692e2c04a0e7e216b670eab6133d68818260d5e8

The following commands/options were added:

* yankcommand *(for copying urls to the clipboard)*
* mediaplayercommand *(for playing linked videos with a media player)*

This way you can use individual keymaps for these commands, you don't need to use the `EXTERN` command prefixed with a number.

## Installation

For Arch Linux, clone this repository, go to the cloned directory and run `makepkg -si`.

*Note: The package is named `w3m-spcmd` and it conflicts with the default `w3m` package. Check the PKGBUILD and feel free to modify it as you wish.*

For other distros you need to extract the archive and install manually from source. The files are already modified/patch, but I included the `diff` files if you want to patch the original files for yourself.

## Usage

### yank (copy url to the clipboard)

Just set the `yankcommand` in **~/.w3m/config** (or use the options page in w3m itself)

* example yank command: 

`sh -c 'printf %s "$0" | xsel -b'`

* or with notification: 

`sh -c 'printf %s "$0" | xsel -b && notify-send "w3m" "URL yanked!"'`

Set the key binding in **~/.w3m/keymap**

```
keymap y YANK_LINK
keymap Y YANK_PAGE
```

To copy the link/url under the cursor or the current page url to the clipboard.

### mediaplayer

The same thing with the `mediaplayercommand`

In **~/.w3m/config**

`mediaplayercommand mpv`

In **~/.w3m/keymap**

```
keymap m MEDIAPLAYER_LINK
keymap M MEDIAPLAYER_PAGE
```

This way you can invoke the selected media player (`mpv` in this case) to play the selected url or the current page url. Handy for browsing youtube and playing videos.

*Note: to play videos with a media player, you need to install [youtube-dl](https://github.com/rg3/youtube-dl)*


## Other tips for w3m

You can browse the mobile version of youtube with this url: `https://m.youtube.com/?app=m`

The problem is, if you search for something it will redirect the browser to desktop version of youtube. To avoid this you can set w3m's user agent to a mobil browser's user agent. 

For example, in **~/.w3m/config**

`user_agent Opera/9.80 (S60; SymbOS; Opera Mobi/SYB-1107071606; U; en) Presto/2.8.149 Version/11.10`

*Note: If you use a modern mobile browser's user agent (e.g.: some Android or iPhone user agent) youtube might not load, instead it warns you to turn on the javascript.*

## License

* w3m uses MIT license
* my patches/modifications are also MIT licensed
