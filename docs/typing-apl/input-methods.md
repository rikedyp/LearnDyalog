# Input methods

## Input method types

### Language bar
Both the Dyalog IDE for Microsoft Windows and the Remote IDE on all platforms come with a [language bar](https://mastering.dyalog.com/Getting-Started.html#the-language-bar) which you can click to enter glyphs into the session. Hovering the mouse over the language bar shows a tooltip with information about that glyph. The tooltip includes what to type to enter that glyph using your keyboard, except when using AutoHotKey on Windows.

### Prefix key input
A prefix key, also known as a dead key, is a key which doesn't output anything by itself, but once pressed then the next key press may output an alternative character.

On TryAPL, for example, the prefix key is to the left of the <kbd>1</kbd> key (backtick <kbd>\`</kbd> on US and UK keyboards). For example, <kbd>\`</kbd> followed by <kbd>a</kbd> gives `⍺` (alpha).

### Shifting key input
A shifting key is a key which, while held, allows an APL glyph to be output by pressing a different key. With the default Dyalog IME <kbd>Ctrl</kbd> is the shifting key. For example, pressing <kbd>Ctrl+i</kbd> produces `⍳` (iota).

## Microsoft Windows

### Dyalog Unicode IME

The Dyalog Unicode IME for Microsoft Windows uses <kbd>Ctrl</kbd> as the shifting key, but also allows input using a prefix key. These can be configured via the IDE for Microsoft Windows as described in the [Dyalog for Microsoft Windows UI Guide]().

!!!Note Known issues with the Dyalog IME
	The Dyalog IME might not work with some Universal Windows Platform (UWP) applications. There is also a [forum thread about known issues with the Dyalog IME](https://forums.dyalog.com/viewtopic.php?f=14&t=661).

The Dyalog Unicode IME

### AutoHotKey

[APLAutoHotKey](https://github.com/Dyalog/APLAutoHotKey) is an application which can be used to create [AutoHotKey](https://www.autohotkey.com/) scripts which enable the typing of APL glyphs using a variety of shifting keys on Microsoft Windows. Both APLAutoHotKey and AutoHotKey come bundled with installations of Dyalog version 19.0.

## macOS
!!!Note
	Installations of Dyalog for macOS come with fonts and a [prefix input method](#prefix-key-input) ready to use. The following instructions enable typing APL even outside of Dyalog.

To install fonts on macOS, place the downloaded **.ttf** file in the **/Library/Fonts/** directory.

To enable keyboard mappings, 

To enter Dyalog glyphs, the keyboard key mappings must be enabled. To enable these keyboard key mappings on macOS, the appropriate **DyalogAlt.keylayout** and **DyalogAlt.icns** files for your locale must be downloaded and installed in the **/Library/Keyboard Layouts** directory. To download a zip file containing these files, click on the relevant flag (if the country you require is not available, or you want to customise one of these layouts, then please [refer to this forum post](https://forums.dyalog.com/viewtopic.php?f=22&t=1900&p=7559#p7559)):

**Download**

## Linux

!!!Note
	Shifting key input on Linux only works with a single natural language layout. This is because the APL keyboard is itself implemented as a full language layout, and the switching mechanism can only switch between one default layout and one additional layout.

### Wayland
At the time of writing, GNOME Wayland is the default desktop environment for Ubuntu and Fedora Linux. The APL keyboard layout is not available in the keyboard settings by default, and must be made available.

#### Using GNOME Tweaks
You can enable the APL keyboard and set a shifting key via the **GNOME-Tweaks** tool, which must be installed separately:

On Ubuntu:
```
sudo apt install gnome-tweaks
```

On Fedora:
```
sudo dnf install gnome-tweaks
```

1. Start **GNOME-Tweaks**
1. Under **Keyboard & Mouse**, turn on **Show Extended Input Sources**.
1. Click **Additional Layout Options** and choose one of the "(while pressed)" options 
1. To enable the APL keyboard, in the main settings, go to the **Keyboard** options, click the <btn>+</btn> button under **Input Sources** and add the APL layout.

#### Using the command line
If you are comfortable using a terminal, you can enable shifting key input of APL glyphs as follows:

Make the APL keyboard layout available as an input source:

```
gsettings set org.gnome.desktop.input-sources show-all-sources true
```

Enable the APL keyboard by adding it to the currently available input sources:

1. List the current input source

	```
	gsettings get org.gnome.desktop.input-sources sources
	```

	Example output: `[('xkb', 'gb')]`

1. Add `'apl'` to the input sources

	```
	gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'gb'), ('xkb', 'apl')]"
	```

To enable shifting key input, set the `xkb-options`. You may have some set already. To see the current xkb-options:

```
gsettings get org.gnome.desktop.input-sources xkb-options
```

Example output: `['lv3:ralt_switch']`
 
In this case, append the shifting key `grp` option with a *key*_switch value [see possible shifting keys](#available-shifting-keys-on-linux):

```
gsettings set org.gnome.desktop.input-sources xkb-options "['lv3:ralt_switch', 'grp:win_switch']"
```

### XKB on XWindows
Set APL as an additional shifting key layout using the `setxkbmap` command:

```
setxkbmap -layout gb,apl -variant ,dyalog -option grp:caps_swich
```

### Available shifting keys on Linux
The possible shifting key values are found in `/usr/share/X11/xkb/rules/evdev.lst` under the `options` group.

```
cat /usr/share/X11/xkb/rules/evdev.ls | grep "grp"
```

### Raspberry Pi
When installing [Dyalog on the Raspberry Pi](https://www.dyalog.com/), (or any other Debian-based Linux distribution), the fonts and keyboard mappings are automatically installed and enabled.

### Other window managers and older Linux versions
More information about installing and configuring Dyalog keyboard support for various window managers (such as Unity) can be found on the [Dyalog forums](https://www.dyalog.com/forum/viewtopic.php?f=20&t=210) or by [emailing us](mailto:support@dyalog.com?subject=Keyboard%20support%20on%20Linux%20distributions).

## Alternative input methods
There is more information about [typing glyphs on the APL Wiki](https://aplwiki.com/wiki/Typing_glyphs).

## Documentation
The [![](https://www.dyalog.com/uploads/images/General/pdf_24.png)Dyalog for UNIX Installation and Configuration Guide](https://docs.dyalog.com/latest/Dyalog for UNIX Installation and Configuration Guide.pdf) includes detailed instructions for:

- configuring the terminal window for Dyalog keyboard support (global per user per UI)
- generating APL glyphs through the PuTTY terminal emulator by installing the Dyalog Unicode IME and APL385 font
