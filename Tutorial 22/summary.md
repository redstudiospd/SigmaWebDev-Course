CSS UNITS: QUICK REVISION NOTES

1. PX (0:31)

px means CSS pixels. It is a fixed-size CSS unit, not necessarily one
physical pixel on the device. It is useful when you want a specific,
predictable size, such as a thin border.

Example:
  .box {
    width: 200px;
    border: 1px solid black;
  }

Because px sizes do not scale with the surrounding font size, using
them for every text size can make a design less adaptable to a user's
text-size preferences.


2. VW (4:01)

vw means viewport width. The viewport is the visible area of the
browser window.

  1vw = 1% of the viewport width
  50vw = half the viewport width
  100vw = the full viewport width

Example:
  .banner {
    width: 80vw;
  }

vw is useful for sizing elements relative to the screen width.
It is not the same as %: percentages are usually relative to a
containing element, while vw is relative to the viewport.


3. VH (7:31)

vh means viewport height.

  1vh = 1% of the viewport height
  100vh = the viewport height

Example:
  .hero {
    min-height: 100vh;
  }

vh can be useful for full-height sections. On mobile devices, browser
interface bars can affect the visible viewport height. Newer units
such as svh, lvh, and dvh can help when a layout needs to account for
changing mobile viewport sizes.


4. REM AND EM (8:16)

rem means root em. It is relative to the font size of the root
element, usually <html>.

If the root font size is 16px:
  1rem = 16px
  2rem = 32px

Example:
  h1 {
    font-size: 2rem;
  }

em is relative to a font size in the element's context:
  For font-size, em is based on the parent element's font size.
  For other properties, such as padding, em is based on the element's
  own font size.

Example:
  .card {
    font-size: 1.25em;
    padding: 1em;
  }

Quick difference:
  rem uses the root font size, so it is consistent throughout the page.
  em depends on the local font-size context and can compound in nested
  elements.

Both units can help text and spacing scale with font settings.


5. VMIN AND VMAX (13:38)

vmin and vmax are based on the viewport's width and height.

  1vmin = 1% of the smaller viewport dimension
  1vmax = 1% of the larger viewport dimension

Example:
  .square {
    width: 50vmin;
    height: 50vmin;
  }

vmin is useful when an element should fit within the smaller screen
dimension. vmax sizes relative to whichever viewport dimension is
larger.


6. MORE UNITS (16:41)

% (percentage)
A relative value usually based on the relevant size of the containing
element. For example, width: 50% generally means half the containing
block's width.

  .inner {
    width: 50%;
  }

ch
Based on the width of the "0" character in the current font. Often
useful for limiting text line length.

  .text {
    max-width: 60ch;
  }

ex
Based on the font's x-height, approximately the height of lowercase
letters such as x. Less commonly used.

cm, mm, in, pt, pc
Physical or print-oriented units:
  cm = centimeters
  mm = millimeters
  in = inches
  pt = points
  pc = picas

They are generally more useful for print than screen layouts.

General reminders:
  A CSS length usually has no space between its number and unit:
    16px, 1.5rem
  Zero can usually be written without a unit:
    margin: 0;


7. CONCLUSION (25:43)

Choose a unit based on what the size should relate to:

  px     specific CSS-pixel size
  vw/vh  viewport width or height
  rem    root font size
  em     local font-size context
  vmin   smaller viewport dimension
  vmax   larger viewport dimension
  %      containing element or property context

For responsive designs, combine units thoughtfully. For example,
rem can keep text scalable, while max-width can prevent a layout from
growing too wide.

Reference notes: CSS unit definitions and relationships.
<citation src="1,4"></citation>
