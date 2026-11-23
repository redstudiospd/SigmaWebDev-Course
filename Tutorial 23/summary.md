CSS DISPLAY AND LAYOUT: QUICK REVISION NOTES

Note: I couldn't retrieve the video's transcript, so these notes cover
the requested topics and fill gaps with standard CSS explanations.


1. INTRO: INLINE AND BLOCK PROPERTIES (0:35)

The display property controls how an element participates in layout
and how its child elements are arranged.

Block elements:
  Start on a new line by default.
  Usually take the full available width.
  Width and height can be set.
  Examples: <div>, <p>, <section>

Inline elements:
  Stay within the current line of text.
  Take only the space their content needs.
  Width and height generally do not apply as expected.
  Examples: <span>, <a>, <strong>

inline-block:
  Stays in the line like an inline element.
  Accepts width and height like a block element.

Example:
  .badge {
    display: inline-block;
    width: 100px;
    padding: 8px;
  }

These are default behaviors. CSS can change an element's display type.


2. DISPLAY: NONE (6:43)

display: none hides the element and removes it from the page layout.
It takes up no space, as if it were not rendered.

Example:
  .hidden {
    display: none;
  }

Use it when the element should disappear and leave no gap.

Accessibility note:
Content with display: none is normally also hidden from screen readers.
<citation src="1,2"></citation>


3. VISIBILITY (7:32)

visibility controls whether an element is visible.

  visibility: visible;  /* shown */
  visibility: hidden;  /* hidden */

visibility: hidden hides the element but keeps its space in the layout.
Other elements do not move into the empty space.

Quick difference:
  display: none       hides it and removes its space
  visibility: hidden  hides it but keeps its space

A hidden element is generally not available to screen readers or
pointer interaction. Do not use opacity: 0 as a substitute when you
need to disable interaction; transparent elements may still receive
clicks or focus.
<citation src="2"></citation>


4. FLEXBOX EXAMPLE (8:04)

Flexbox is a one-dimensional layout system. It arranges items along
a row OR a column.

Set display: flex on a parent to make its direct children flex items.

HTML:
  <div class="row">
    <div>One</div>
    <div>Two</div>
    <div>Three</div>
  </div>

CSS:
  .row {
    display: flex;
    gap: 12px;
    justify-content: space-between;
    align-items: center;
  }

Useful properties:
  flex-direction: row;       /* arrange items in a row */
  flex-direction: column;    /* arrange items in a column */
  justify-content: ...;      /* align along the main axis */
  align-items: ...;          /* align along the cross axis */
  gap: ...;                  /* space between items */

Think of flexbox for arranging items in one direction, such as a
navigation bar or a row of buttons.
<citation src="6,10"></citation>


5. GRID (9:16)

CSS Grid is a two-dimensional layout system. It can manage columns
and rows together.

Set display: grid on a parent to make its direct children grid items.

Example:
  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }

This creates three equal-width columns. 1fr means one share of the
available space.

Use Grid when you need control over both rows and columns, such as
a card layout or page structure.

Quick difference:
  Flexbox: one direction at a time
  Grid: rows and columns together
<citation src="7,8"></citation>


6. MORE RESOURCES (9:31)

For further practice, look up:
  MDN: CSS display
  MDN: Flexbox
  MDN: CSS Grid

Try changing display values and resizing the browser to see how the
layout behaves. Browser developer tools can also show flex and grid
overlays for a selected container.


7. CONCLUSION (10:24)

Use display: block, inline, or inline-block to control an element's
basic layout behavior.

Use display: none when the element should take up no space.
Use visibility: hidden when its space should remain.
Use Flexbox for one-direction layouts.
Use Grid for row-and-column layouts.

Remember: the display property controls both an element's outer
layout behavior and, with values like flex or grid, the layout of
its children. <citation src="1,6,8"></citation>