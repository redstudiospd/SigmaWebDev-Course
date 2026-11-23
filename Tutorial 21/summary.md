CSS SPECIFICITY, CASCADE, AND BEST PRACTICES

1. WHAT IS SPECIFICITY IN CSS (1:21)

Specificity is the selector's priority score. When multiple CSS rules
that apply to the same element set the same property, specificity helps
determine which value is used.

For the common selector types, specificity is counted as:
  ID – CLASS – TYPE

  ID selector        #profile             1-0-0
  Class selector     .highlight           0-1-0
  Type selector      p                    0-0-1

Count each selector type, then compare the totals from left to right.
The first column that differs decides the winner.

Example:
  #intro { color: blue; }       /* 1-0-0 */
  .note { color: red; }         /* 0-1-0 */

If both rules apply to the same element, #intro wins because its ID
column is higher.

More examples:
  p                 = 0-0-1
  .card p           = 0-1-1
  #main .card p     = 1-1-1

If specificity is tied, the cascade uses later rules in source order
(after the other cascade conditions have been considered).

Quick memory:
  ID beats class; class beats type.
  Compare the columns left to right, not as one ordinary number.

GAP-FILL:
Attribute selectors such as [type="text"] and pseudo-classes such as
:hover count in the class column. Pseudo-elements such as ::before
count in the type column. The universal selector * adds no specificity.


2. EXPLORING DIFFERENT CLASSES (1:58)

An element can have more than one class. Separate class names with
spaces in the HTML class attribute:

  <p class="notice important">Read this notice.</p>

This element has both the notice and important classes.

Separate selectors with no space to target an element that has BOTH
classes:

  .notice.important {
    color: red;
  }

A space between selectors means a descendant relationship:

  .notice .important {
    color: red;
  }

This targets an element with class="important" inside an element
with class="notice".

Do not mix up:
  .one.two   = one element has both classes
  .one .two  = an element with class two is inside an element with class one

Classes are reusable, so they are generally useful for styling groups
of elements.


3. CASCADE ALGORITHM IN CSS (2:36)

The cascade is the process the browser uses to decide which CSS value
applies when declarations conflict.

A beginner-friendly way to think through a conflict:

  1. Check which rules actually match the element and property.
  2. Compare importance and origin, including whether !important is used.
  3. Compare cascade layer priority, if layers are used.
  4. Compare selector specificity.
  5. If still tied, later source order generally wins.

Example of source order deciding a tie:

  p { color: green; }
  p { color: purple; }

Both selectors have the same specificity, so the later declaration
makes the paragraph purple.

Important:
Specificity is only one part of the cascade. A higher-specificity
selector does not automatically win if another cascade factor, such
as importance or layer priority, takes precedence.
!important changes priority; it does not add points to specificity.

When a style does not apply as expected, inspect the element with
browser developer tools. They show matching styles and commonly mark
overridden declarations.


4. BEST PRACTICES IN CSS (18:06)

  • Prefer reusable classes for styling.
  • Keep selectors short and easy to understand.
  • Avoid unnecessary IDs and deeply nested selectors; they can make
    styles harder to override.
  • Avoid !important for routine styling. It can make future changes
    and debugging more difficult.
  • Use clear, consistent class names.
  • If a style is unexpectedly overridden, inspect the element and
    check the matching rules before adding more specificity.
  • Keep related styles organized so the intended cascade is easy to follow.

Example of a simple, reusable class:

  .card-title {
    font-size: 1.25rem;
    color: navy;
  }

Use specificity only as much as needed. Higher specificity is not
automatically better; simpler rules are usually easier to maintain.


5. CONCLUSION (19:25)

Specificity helps resolve conflicts between matching CSS selectors.
For common selectors, remember:

  ID > class > type

The cascade also considers other factors, including importance,
origin, layers, and source order. Use reusable classes, simple
selectors, and developer tools to keep styles predictable.

References for the specificity and cascade details:
<citation src="2,3"></citation>