# Typing APL

## About the glyphs
APL is distinguished by its use of symbols to represent primitive functions and operators. It does not take long to get used to typing these glyphs, and there are some different methods available to suit your preference.

## Learn the meaning of glyphs and how to type them
- <span class="logo-youtube">:fontawesome-brands-youtube:</span> [APL Mnemonics video]()

## Keyboard layout diagrams
Keyboard layouts can vary between operating systems, locales (country and language-specific layouts) and operating systems.

Dyalog APL's standard UK English layout is as follows:

```
┌────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬─────────┐
│¬ ⌺ │! ⌶ │" ⍫ │£ ⍒ │$ ⍋ │% ⌽ │^ ⍉ │& ⊖ │* ⍟ │( ⍱ │) ⍲ │_ ! │+ ⌹ │Backspace│
│` ⋄ │1 ¨ │2 ¯ │3 < │4 ≤ │5 = │6 ≥ │7 > │8 ≠ │9 ∨ │0 ∧ │- × │= ÷ │         │
├────┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬──────┤
│Tab    │Q   │W   │E ⍷ │R   │T ⍨ │Y   │U   │I ⍸ │O ⍥ │P ⍣ │{ ⍞ │} ⍬ │Enter │
│       │q ? │w ⍵ │e ∊ │r ⍴ │t ~ │y ↑ │u ↓ │i ⍳ │o ○ │p * │[ ← │] → │      │
├───────┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┐     │
│Caps    │A   │S   │D   │F   │G   │H   │J ⍤ │K ⌸ │L ⌷ │: ≡ │@ ≢ │~   │     │
│Lock    │a ⍺ │s ⌈ │d ⌊ │f _ │g ∇ │h ∆ │j ∘ │k ' │l ⎕ │; ⍎ │' ⍕ │#   │     │
├──────┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴──┬─┴────┴─────┤
│Shift │| ⊣ │Z ⊆ │X   │C   │V   │B   │N   │M   │< ⍪ │> ⍙ │? ⍠ │Shift       │
│      │\ ⊢ │z ⊂ │x ⊃ │c ∩ │v ∪ │b ⊥ │n ⊤ │m | │, ⍝ │. ⍀ │/ ⌿ │            │
├──────┴┬───┴─┬──┴───┬┴────┴────┴────┴────┴────┴┬───┴──┬─┴────┼─────┬──────┤
│Ctrl   │Win  │Alt   │                          │Alt Gr│Win   │Menu │Ctrl  │
│       │     │      │                          │      │      │     │      │
└───────┴─────┴──────┴──────────────────────────┴──────┴──────┴─────┴──────┘
```

Several international keyboard layouts exist with charts available from [the dfns website](https://dfns.dyalog.com/n_keyboards.htm).

## Input methods
**TODO:** how much to include here and what to link to other resources?

The IDE for Microsoft Windows and cross-platform RIDE both come with a language bar at the top of the session.

Users can click on glyphs in [the language bar](), or type directly both in and out of the APL session to enter glyphs.

A prefix key is a key which doesn't output anything by itself, but once pressed may cause . On TryAPL, for example, the prefix key is to the left of the <kbd>1</kbd> key (backtick <kbd>\`</kbd> on US and UK keyboards). <kbd>\`</kbd> followed by <kbd>a</kbd> gives `⍺` (alpha).

A shifting key is a key which, while held, allows an APL glyph to be output by pressing a different key. With the default Dyalog IME

More information

### Microsoft Windows

#### Default input methods
The Dyalog Unicode IME for Microsoft Windows uses <kbd>Ctrl</kbd> as the shifting key, but also allows input using a prefix key. These can be configured via the IDE for Microsoft Windows as described in the [Dyalog for Microsoft Windows UI Guide]().

!!!Note Known issues with the Dyalog IME
	The Dyalog IME might not work with certain [Universal Windows Platform]() (UWP) applications. Other issues.

The Dyalog Unicode IME

[APLAutoHotKey]() is an application which can be used to create [AutoHotKey]() scripts which enable the typing of APL glyphs using a variety of shifting keys on Microsoft Windows. Both APLAutoHotKey and AutoHotKey come bundled with installations of Dyalog version 19.0.

### macOS

### Linux

#### Wayland
At the time of writing, GNOME Wayland is the default desktop environment for Ubuntu and Fedora Linux. The APL keyboard layout is not available in the keyboard settings by default, and must be made available.

##### Using GNOME Tweaks
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

##### Using the command line
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

#### XKB on XWindows

### Alternative input methods

More information about

### Language bar

### Prefix key input

### Shifting key input

## How to set up APL keyboard input
- [APL Wiki page on Typing Glyphs]()
- [Section 2.2.5 of Mastering Dyalog APL](https://mastering.dyalog.com/Getting-Started.html#typing-apl-glyphs)

## APL Fonts
The de-facto standard APL font is the [APL385 Unicode font](http://apl385.com/fonts/index.htm) by Adrian Smith. This font is freely available in the public domain and is installed alongside standard installations of Dyalog APL.

The [APL Wiki page on fonts](https://aplwiki.com/wiki/Fonts) lists more fonts with good support for APL characters.
