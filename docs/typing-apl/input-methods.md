# Input methods
**TODO:** how much to include here and what to link to other resources?

The IDE for Microsoft Windows and cross-platform RIDE both come with a language bar at the top of the session.

Users can click on glyphs in [the language bar](), or type directly both in and out of the APL session to enter glyphs.

A prefix key is a key which doesn't output anything by itself, but once pressed may cause . On TryAPL, for example, the prefix key is to the left of the <kbd>1</kbd> key (backtick <kbd>\`</kbd> on US and UK keyboards). <kbd>\`</kbd> followed by <kbd>a</kbd> gives `⍺` (alpha).

A shifting key is a key which, while held, allows an APL glyph to be output by pressing a different key. With the default Dyalog IME

More information

## Microsoft Windows

The Dyalog Unicode IME for Microsoft Windows uses <kbd>Ctrl</kbd> as the shifting key, but also allows input using a prefix key. These can be configured via the IDE for Microsoft Windows as described in the [Dyalog for Microsoft Windows UI Guide]().

!!!Note Known issues with the Dyalog IME
	The Dyalog IME might not work with some [Universal Windows Platform]() (UWP) applications. There is also a [forum thread about known issues with the Dyalog IME](https://forums.dyalog.com/viewtopic.php?f=14&t=661).

The Dyalog Unicode IME

---

[APLAutoHotKey](https://github.com/Dyalog/APLAutoHotKey) is an application which can be used to create [AutoHotKey]() scripts which enable the typing of APL glyphs using a variety of shifting keys on Microsoft Windows. Both APLAutoHotKey and AutoHotKey come bundled with installations of Dyalog version 19.0.

## macOS

## Linux

### Wayland
At the time of writing, GNOME Wayland is the default desktop environment for Ubuntu and Fedora Linux. The APL keyboard layout is not available in the keyboard settings by default, and must be made available.

#### Using GNOME Tweaks
You can enable the APL keyboard and set a shifting key via the **GNOME-Tweaks** tools, which must be installed separately:

On Ubuntu:
```
sudo dnf install gnome-tweaks
```

On Fedora:
```
sudo apt install gnome-tweaks
```

1. Under **Keyboard & Mouse**, turn on **Show Extended Input Sources**.
1. Click **Additional Layout Options** and choose one of the "(while pressed)" options 
1. To enable the APL keyboard, in the main settings, go to the **Keyboard** options, click the <btn>+</btn> button under **Input Sources** and add the APL layout.

#### Using the command line
If you are comfortable using a terminal, you can enable shifting key input of APL glyphs as follows:

 by running the following command in a terminal:

```
gsettings set org.gnome.desktop.input-sources show-all-sources true
```

To enable the APL keyboard, add it to the currently available input sources.

1. List the current input source
	```
	> gsettings get org.gnome.desktop.input-sources sources
	[('xkb', 'gb')]
	```
1. Add `'apl'` to the input sources
	```
	> gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'gb'), ('xkb', 'apl')]"
	```

To enable shifting key input, set the `xkb-options`:

You may have some set already. Too see the current xkb-options:

```
> gsettings get org.gnome.desktop.input-sources xkb-options
['lv3:ralt_switch']
```
 
In this case, append the shifting key `grp` option with a *key*_switch value. The possible values are found in `/usr/share/X11/xkb/rules/evdev.ls` under the `options` group.

```
cat /usr/share/X11/xkb/rules/evdev.ls | grep "grp"
```

```
gsettings set org.gnome.desktop.input-sources xkb-options "['lv3:ralt_switch', 'grp:win_switch']"
```

!!!Note
	Shifting key input on Linux only works with a single natural language layout. This is because the APL keyboard is itself implemented as a full language layout, and the switching mechanism can only switch between one default layout and one additional layout.

### XKB on XWindows

## Alternative input methods
There is more information about [typing glyphs on the APL Wiki](https://aplwiki.com/wiki/Typing_glyphs).