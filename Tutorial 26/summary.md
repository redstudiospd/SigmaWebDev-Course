CSS OVERFLOW: QUICK REVISION NOTES

Note: I couldn't retrieve the video's transcript, so I can't confirm
its exact wording or examples. These notes cover the requested sections
with concise standard CSS definitions.


1. INTRODUCTION (0:00)

Overflow happens when an element's content is larger than the space
available inside its box. The CSS overflow property controls how that
extra content is handled.


2. SIGMA WEB DEVELOPER COURSE INTRO (0:28)

Course introduction/context. The main topic in this lesson is how CSS
handles content that does not fit inside an element.


3. OVERFLOW PROPERTY (0:38)

The overflow property controls content that spills beyond an element's
box. Overflow is commonly caused by constrained width or height.

  .box {
    width: 200px;
    height: 100px;
    overflow: auto;
  }

Common values:

  visible
    Default. Content can extend outside the box.

  hidden
    Clips overflowing content. It is not shown, though it may still be
    scrollable programmatically or brought into view by focus.

  scroll
    Clips overflowing content and provides scrolling controls,
    whether or not scrolling is needed.

  auto
    Adds scrolling controls when content actually overflows.

  clip
    Clips overflowing content and does not provide scrolling.

You can control each direction separately:

  overflow-x: auto;  /* horizontal overflow */
  overflow-y: hidden; /* vertical overflow */

Quick memory:
  visible = let it spill
  hidden  = cut it off
  scroll  = allow scrolling
  auto    = scroll only when needed
  clip    = cut it off without scrolling

Use overflow-x and overflow-y when horizontal and vertical content
need different behavior. <citation src="1,2"></citation>


4. CONCLUSION (7:31)

Choose an overflow value based on what should happen to content that
does not fit: show it, clip it, or let users scroll to it. Use auto
when scrollbars should appear only when necessary.

<citation src="1,2"></citation>