js13k-level-editor
==

This projects contains a level editor specially conceived for the js13kgames.com competition.

It can be used to produce built-in levels for your js13k game.

It's super small (1.02kb gzipped), so you can also include it in your entry and use it as a custom level editor for your game.

Feel free to fork it and adapt it to your needs.

There's also a level reader that you can use directly in your game to load built-in or custom levels.

Join the discussion on: https://js13kgames.slack.com/messages/level-editor-share/

---


Editor
--

The editor lets you pick tiles from a spritesheet and paste them on a blank map.

The spritesheet (on the left) is a canvas called "a", with a context2D called "c".

It loads automatically the file /s.png and the script /s.js at the root of the project. The png file is drawn on the canvas, then the JS script is executed.

Any of these two files can be omitted (your spritesheet can be png only or js only).

Of course, these files can also be used in your game.

The editor lets you choose a tile size (8x8, 16x16, 32x32, 64x64, ...) and a level size (width and height, counted in tiles).

The editor outputs a hash that can be appended to the URL of the level reader (in order to load and use it), or the URL of the level editor (in order to edit it)

Demo (blank level):

http://xem.github.io/js13k-level-editor/editor.html

Demo (existing, editable level):

http://xem.github.io/js13k-level-editor/editor.html#@@%C2%84%C2%84#!%22$!%22%25!%22&!%22!!%22%22!%22%27!%22(!%22)!%22*!%22+!%22,!%22-!%22-%22%22-#%22-$%22-%25%22-&%22-%27%22-(%22-)%22%25)%22$)%22#)%22%22)%22!)%22!(%22!%27%22!&%22!%25%22!$%22!#%22!%22%22&)!%27)!()!))!*)!+)!,)!+$$+%25$*&%22+&%22,&%22#(%20

Spritesheets used by this demo:

- http://xem.github.io/js13k-level-editor/s.png
- http://xem.github.io/js13k-level-editor/s.js

---

Level reader
--

It's a JS script that's used by the editor and by your game. (r.js, 162b)

It reads the URL's hash and puts all the data of the level in the variable "d":

````
d = {
  w: // tile width in px,
  h: // tile height in px,
  W: // level width in tiles,
  H: // level height in tiles,
  T: // tiles used on the map:
  [
    [tile_index, x coordinate, y coordinate],
    [tile_index, x coordinate, y coordinate],
    ... // one entry for each tile of the map
  ]
}
````

Demo:

http://xem.github.io/js13k-level-editor/index.html#@@%C2%84%C2%84#!%22$!%22%25!%22&!%22!!%22%22!%22%27!%22(!%22)!%22*!%22+!%22,!%22-!%22-%22%22-#%22-$%22-%25%22-&%22-%27%22-(%22-)%22%25)%22$)%22#)%22%22)%22!)%22!(%22!%27%22!&%22!%25%22!$%22!#%22!%22%22&)!%27)!()!))!*)!+)!,)!+$$+%25$*&%22+&%22,&%22#(%20

---


Structure of a level's URL
--

Hashes have the following form:

    http://(game_url)/index.html#whWHTTT...

with:

- w: String.fromCodePoint(tile width in px) // 1 char
- h: String.fromCodePoint(tile height in px // 1 char
- W: String.fromCodePoint(level width in tiles) // 1 char
- H: String.fromCodePoint(level height in tiles) // 1 char
- T: String.fromCodePoint(tile index)+String.fromCodePoint(tile coord X)+String.fromCodePoint(tile coord Y) // 3 chars
- T: ... repeat for all the tiles of the map


---

License
--

Public domain
