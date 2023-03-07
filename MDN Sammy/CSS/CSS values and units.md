tags: #css 

###### absolute length units
- the following are all absolute length units - they are not relative to anything else, and are generally considered to always be the same size
- Most of these units are more useful when used for print, rather than screen output

|Unit | Name | Equivalent to |
| ----|------|-------------|
|`cm` | centimeters | 1cm = 37.8px|
|`mm` | milimeters | 1mm = 1/10th of 1cm|
|`Q` | quarter milimeters | 1q = 1/40th of 1cm|
|`in` | inches | 1in = 2.54cm = 90px |
|`pc` | picas | 1pc = 1/6th of 1in |
| `pt` | points | 1pt = 1/72nd of 1in|
| `px` | pixels | 1px = 1/96th of 1in|

###### relative length units
- relative length units are relative to something else, perhaps the size of the parent element's font, or the size of the viewport

| Unit | Relative to |
|------|-------------|
| `em` | font size of the parent, in the case of typographical properties like `font-size`, and the font size of the element itself, in the case of other properties like `width` |
|`ex` | x-height of the element's font |
| `ch` | the advance measure (width) of the glyph 'O' of the element's font |
| `rem` | font size of the root element |
| `lh` | line height of the element |
| `rlh` | line height of the root element |
| `vw` | 1% of the viewport's width |
| `vh` | 1% of the viewport's height |
|`vmin` | 1% of the viewport's smaller dimension |
|`vmax` | 1% of the viewport's larger dimension |
| `vb` | 1% of the size of the initial containing block in the direction of the root element's `block axis`|
| `vi` | 1% of the size of the initial containing block in the direction of the root element's `inline axis`|
|`svw`, `svh` | 1% of the small viewport's width and height, respectively |
| `lvw`, `lvh` | 1% of the large viewport's width and height, respectively |
|`dvw`, `dvh` | 1% of the dynamic viewport's width and height, respectively |
###### ems and rems
- the `em` unit means 'my parent element's font-size' in the case of _typography_. So each successive level of nesting gets progressively larger, as each, for example, has its font size set to `1.3em` - 1.3 times its parent's font size
``` css
li {

	font-size:1.3em;
}
```
- the `rem` unit menas 'The root element's font-size (`<html>`)'
###### HSL and HSLA values
- The `hsl()` function accepts hue, saturation, and lightness values, which are used to distinguish between the 16.7 millions colors
- **hue** -> the base shade of the color. this takes a value between 0 and 360, representing the angles around a color wheel
- **saturation** -> this takes a value from 0-100%, where 0 is no color (it will appear as a shade of grey), and 100% is full color saturation
- **lightness** -> This takes a value from 0–100%, where 0 is no light (it will appear completely black) and 100% is full light (it will appear completely white)







