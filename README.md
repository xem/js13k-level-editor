js13k-level-editor
==

This projects contains a level editor specially conceived for the js13kgames.com competition.

It can be used to produce built-in levels for your js13k game.

The lite version (1.1kb gzipped) can also be included directly in your entry as a custom level editor for your game.

Feel free to fork it and adapt it to your needs.

The levels made with this editor are shareable as text or with an URL.

There's also a [tiny level reader script](http://xem.github.io/js13k-level-editor/l.js) that you can use to load custom levels from an URL.

You can join the discussion on Slack: https://js13kgames.slack.com/messages/level-editor-share/

---


Editor
--

The editor lets you pick tiles from a tileset and paste them on a blank map.

The tileset (on top) is a canvas called "a", with a context2D called "c".

It loads automatically the image {url}/t.png and the script {url}/s.js at the root of the project specified in the "URL" field.

The JS script is executed, then the png file is drawn on the canvas.

Any of these two files can be omitted (your spritesheet can be png only or js only).

Of course, these files can also be used in your game.

The editor lets you choose a tile size in px (like 16x16 or 32x32) and a level size, in tiles.

The editor creates a hash that can be used to the URL by your game (to play the level), or the level editor (to edit it).

It also outputs the map as a text block, which is a much more efficient way to store built-in levels in your zipped entry. (scroll the page to see it)

Demo (blank level):

http://xem.github.io/js13k-level-editor/editor.html

Demo (existing, editable level):

https://xem.github.io/js13k-level-editor/editor.html#@H/1%20.%22!.%22%22.%22#.%22$.%22%25.%22&.%22%27.%22..%22/.%220.%221.%222.%22A.%22B.%22C.%22D.%22E.%22F.%22G.%22G-%22F-%22E-%22D-%22C-%22B-%22@.%22?.%22%3E.%22=.%22%3C.%22;.%22:.%229.%228.%227.%226.%225.%224.%223.%223-%222-%221-%220-%22/-%22.-%224-%225-%226-%227-%228-%229-%22:-%22;-%22%3C-%22=-%22%3E-%22?-%22@-%22A-%22%27-%22&-%22%25-%22$-%22#-%22%22-%22!-%22%20-%22(-%22(.%22).%22)-%220**1*+0+:0,:1+;1,;$)$%27)$B&,B%27%3CB(%3CB)%3CB*%3CB+%3CB,%3CE,%3ED+0D,0F+0F,0E+.D*-F*-E*/E)0E(-!,1%22,2#,35,76+77*78+89*9:+9;,98))8*(7+(6,(7,(8,(9,(9+(:,(=,!%3E,!%3E+!?,!?+!?*!@,!@+!@*!@)!3$44$55$56$57$63#%254#&5#&6#&7#%27

Tileset files used by this demo:

- http://xem.github.io/js13k-level-editor/t.png
- http://xem.github.io/js13k-level-editor/t.js

---

Editor LITE
--

The lite editor can be included in your entry.

The difference with the normal editor are:

- No URL field (the tileset is necessarily in the current folder)
- No text block output
- No tile size field (the tile size is hardcoded at the end of editor.lite.html (d={t:32}). You can edit it manually.
- The source code is minified

Demo (blank level):

http://xem.github.io/js13k-level-editor/editor.lite.html

Demo (existing, editable level):

https://xem.github.io/js13k-level-editor/editor.lite.html#@H/1%20.%22!.%22%22.%22#.%22$.%22%25.%22&.%22%27.%22..%22/.%220.%221.%222.%22A.%22B.%22C.%22D.%22E.%22F.%22G.%22G-%22F-%22E-%22D-%22C-%22B-%22@.%22?.%22%3E.%22=.%22%3C.%22;.%22:.%229.%228.%227.%226.%225.%224.%223.%223-%222-%221-%220-%22/-%22.-%224-%225-%226-%227-%228-%229-%22:-%22;-%22%3C-%22=-%22%3E-%22?-%22@-%22A-%22%27-%22&-%22%25-%22$-%22#-%22%22-%22!-%22%20-%22(-%22(.%22).%22)-%220**1*+0+:0,:1+;1,;$)$%27)$B&,B%27%3CB(%3CB)%3CB*%3CB+%3CB,%3CE,%3ED+0D,0F+0F,0E+.D*-F*-E*/E)0E(-!,1%22,2#,35,76+77*78+89*9:+9;,98))8*(7+(6,(7,(8,(9,(9+(:,(=,!%3E,!%3E+!?,!?+!?*!@,!@+!@*!@)!3$44$55$56$57$63#%254#&5#&6#&7#%27

---

Level reader
--

It's a JS script containing a load_level() function, that can be used by the editor and by your game. (l.js)

It reads the hash passed in argument and stores all the important information in the object d, which is returned:

````
d = {
  t: // tile size in px
  w: // level width in tiles,
  h: // level height in tiles,
  z: // use tile zero by default
  m: // tiles used on the map:
  [
    [tile_index, x coordinate, y coordinate],
    [tile_index, x coordinate, y coordinate],
    ... // one entry for each tile of the map
  ]
}
````

Demo:

http://xem.github.io/js13k-level-editor/index.html#@H/1%20.%22!.%22%22.%22#.%22$.%22%25.%22&.%22%27.%22..%22/.%220.%221.%222.%22A.%22B.%22C.%22D.%22E.%22F.%22G.%22G-%22F-%22E-%22D-%22C-%22B-%22@.%22?.%22%3E.%22=.%22%3C.%22;.%22:.%229.%228.%227.%226.%225.%224.%223.%223-%222-%221-%220-%22/-%22.-%224-%225-%226-%227-%228-%229-%22:-%22;-%22%3C-%22=-%22%3E-%22?-%22@-%22A-%22%27-%22&-%22%25-%22$-%22#-%22%22-%22!-%22%20-%22(-%22(.%22).%22)-%220**1*+0+:0,:1+;1,;$)$%27)$B&,B%27%3CB(%3CB)%3CB*%3CB+%3CB,%3CE,%3ED+0D,0F+0F,0E+.D*-F*-E*/E)0E(-!,1%22,2#,35,76+77*78+89*9:+9;,98))8*(7+(6,(7,(8,(9,(9+(:,(=,!%3E,!%3E+!?,!?+!?*!@,!@+!@*!@)!3$44$55$56$57$63#%254#&5#&6#&7#%27

---


Structure of a map stored to URL / text
--

Maps saved as hash have the following form:

    http://(game_url)/index.html#twhzTTT...

with:

- t: String.fromCodePoint(d.t) // 1 char
- w: String.fromCodePoint(d.w) // 1 char
- h: String.fromCodePoint(d.h) // 1 char
- z: +d.z // 1 char (0 or 1)

for each tile i
- T: String.fromCodePoint(i[0])+String.fromCodePoint(i[1])+String.fromCodePoint(i[2]) // 3 chars

<br>

Maps saved as text have the following form:

````
                                        
                                        
                                        
                   %&&&'                
                   45556                
                                        
                                  ,     
                                  <     
                                  <  -  
    $  $                )       ! <  0  
                *+     7(9     !! < -/- 
                :;    7(8(9   !!! < 0.0 
 123            :;   7(((((9 !!!! < 0>0 
""""""""""    """"""""""""""""""""""""""
""""""""""    """"""""""""""""""""""""""
````

Each char represents the index of the tile used, starting from U+0020 (to have only printable characters).

The lines breaks are made with "\n" chars.

To read a tile at [x:y] in this kind of map, just use: ````map_ascii.split("\n")[y].charCodeAt(x)-32````

<br>

---

License
--

Public domain
