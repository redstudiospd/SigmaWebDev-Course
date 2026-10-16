CSS BOX MODEL — QUICK REVISION

Every HTML element is treated as a box. From the inside out:

Content: The actual text, image, or other material inside the element.
Padding: Space between the content and the border. The element's background
         extends through the padding.
Border:  The line surrounding the content and padding.
Margin:  Space outside the border, separating the element from others.
         The element's background does not extend into the margin.

WIDTH AND HEIGHT

With the default box-sizing: content-box:
  Total width  = content width + left/right padding + left/right borders
  Total height = content height + top/bottom padding + top/bottom borders

Margins add space outside that total.

With box-sizing: border-box:
  The declared width and height include the content, padding, and border.
  Margins are still outside and are not included.

MARGIN COLLAPSE

For adjacent vertical block elements, positive margins may collapse:
the gap is usually the larger margin, not the sum.
For example, a 25px bottom margin beside a 35px top margin usually creates
a 35px gap, not a 60px gap.

BASIC CSS EXAMPLE

.box {
  padding: 10px;
  border: 2px solid blue;
  margin: 5px;
  box-sizing: border-box;
}

