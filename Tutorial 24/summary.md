CSS SHADOWS, OUTLINES, AND ROUNDED CORNERS

Note: I couldn't retrieve the video's transcript, so I can't verify its
exact wording or examples. These concise notes cover the requested
sections using standard CSS definitions.


1. INTRODUCTION (0:00)

This lesson covers CSS shadows and outlines, plus border-radius and
outline-offset as related styling properties.


2. SIGMA WEB DEVELOPER COURSE INTRO (0:27)

Course introduction/context. The topics below are the CSS concepts
to remember from this lesson.


3. SHADOWS (0:37)

text-shadow adds a shadow to text.

Syntax:
  text-shadow: horizontal-offset vertical-offset blur-radius color;

Example:
  h1 {
    text-shadow: 2px 2px 4px gray;
  }

box-shadow adds a shadow around an element's box.

Syntax:
  box-shadow: horizontal-offset vertical-offset blur spread color;

Example:
  .card {
    box-shadow: 2px 4px 8px 1px gray;
  }

The offsets move the shadow horizontally and vertically.
Blur makes it softer. Spread grows or shrinks it.
Use inset to place the shadow inside the box:

  .card {
    box-shadow: inset 0 0 6px gray;
  }

A box-shadow does not take up layout space. Multiple shadows can be
listed with commas. <citation src="3"></citation>


4. OUTLINES (8:13)

An outline is a line drawn around an element, outside its border.
It can be set with the outline shorthand:

  .button {
    outline: 2px solid blue;
  }

An outline does not take up layout space, so it does not change the
element's dimensions or move nearby content.

Difference:
  border   is part of the element's box and can affect layout size
  outline  is drawn outside the border and does not affect layout size

Outlines are often used to show keyboard focus. Keep a visible focus
indicator so keyboard users can tell which element is selected.
<citation src="1"></citation>


5. CONCLUSION (10:28)

Use text-shadow for text and box-shadow for element boxes.
Use outlines for an outer visual indicator, such as keyboard focus.
Use border-radius to round corners and outline-offset to adjust the
space between an element and its outline.


6. SIGMA OUTRO (12:48)

Course/video closing. No additional CSS property is introduced here.


ADDITIONAL: BORDER-RADIUS

border-radius rounds the corners of an element's border edge.

Example:
  .card {
    border-radius: 12px;
  }

A larger radius makes corners more rounded. A value of 50% can create
a circle when the element is square.

You can round individual corners with properties such as
border-top-left-radius. <citation src="2"></citation>


ADDITIONAL: "BORDER-OFFSET"

CSS does not have a standard border-offset property. The likely
intended property is outline-offset.

outline-offset sets the distance between an element's outline and its
border edge:

  .button {
    outline: 2px solid blue;
    outline-offset: 4px;
  }

A positive value moves the outline outward. A negative value moves it
inward. <citation src="5"></citation>