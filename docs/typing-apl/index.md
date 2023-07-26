# Typing APL

## About the glyphs
APL is distinguished by its use of symbols to represent primitive functions and operators. It does not take long to get used to typing these glyphs, and there are some different methods available to suit your preference.

## Learn the meaning of glyphs and how to type them
<span class="logo-youtube">:fontawesome-brands-youtube:</span> [But How Will I Remember All Those Squiggles? – APL Mnemonics](https://dyalog.tv/APLSeeds23/?v=qZtb4XOLdkI)

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

For Linux distributions that have Dyalog keyboard support included with the distribution, a diagram showing the keyboard layout can be found in the **/usr/share/X11/xkb/symbols/apl** file.

Diagrams showing more keyboard layouts can be found on the [keyboard layout page of the dfns website](https://dfns.dyalog.com/n_keyboards.htm).

## APL Fonts
The de-facto standard APL font is the [APL385 Unicode font](http://apl385.com/fonts/index.htm) by Adrian Smith. This font is freely available in the public domain and is installed alongside standard installations of Dyalog APL.

The [APL Wiki page on fonts](https://aplwiki.com/wiki/Fonts) lists more fonts with good support for APL characters.

<div id="glyphs">
← ↑ → ↓ + - × ÷ * ⍟ ⌹ ○ ! ? | ⌈ ⌊ ⊥ ⊤ ⊣ ⊢ = ≠ ≤ < > ≥ ≡ ≢ ∨ ∧ ⍱ ⍲ ⊂ ⊃ ⊆ ⊇ ⌷ ⍋ ⍒ ⍳ ⍸ ∊ ⍷ ∪ ∩ ~ / \ ⌿ ⍀ , ⍪ ⍴ ⌽ ⊖ ⍉ ¨ ⍨ ⍣ . ∘ ⍤ ⍥ @ ⍞ ⎕ ⍠ ⌸ ⌺ ⌶ ⍎ ⍕ ⋄ ⍝ ⍺ ⍵ ∇ ∆ & ¯ ⍬
</div>

<style>
	#glyphs {
		font-family: APL;
		line-height: 1em;
		font-size: 8em;
		position: fixed;
		top: 0; left: 0;
		z-index: -1;
		opacity: 3%;
		width: 100vw;

	}
</style>
