# CSS Position Property — Tutorial 28

> **Revision notes based on the video transcript.** The main definitions and explanations follow the instructor's examples. A short **Extra clarification** section fills in a few details that the video does not fully explain.

## 1. What does `position` do?

The CSS `position` property controls how an element is placed in a document. It works with offset properties such as `top`, `right`, `bottom`, and `left`.

It is also important when arranging elements on top of one another with `z-index`.

```css
.element {
  position: relative;
  top: 3px;
}
```

This moves the element 3 pixels down from its normal position.

## 2. The five position values

### `position: static`

- **Definition:** The default position of every element.
- The element stays in the normal document flow, in the place its HTML layout gives it.
- `top`, `right`, `bottom`, `left`, and `z-index` do not reposition a statically positioned element in the usual way.

```css
.box {
  position: static;
}
```

**Remember:** Static = normal/default layout.

### `position: relative`

- **Definition:** The element is positioned relative to its original position.
- Use `top`, `right`, `bottom`, or `left` to shift it from that original position.
- The element's original space is still reserved in the document flow. Other elements do not move into that space.
- A relatively positioned element can also be used as the positioning reference for an absolutely positioned descendant.

```css
.box {
  position: relative;
  top: 10px;
  left: 20px;
}
```

**Remember:** Relative = move from its own original position; its original space remains.

### `position: absolute`

- **Definition:** The element is taken out of the normal document flow and positioned relative to its nearest positioned ancestor.
- A positioned ancestor means an ancestor whose `position` is not `static` (for example, `relative`, `absolute`, `fixed`, or `sticky`).
- If no such ancestor exists, it is normally positioned relative to the initial containing block (often described simply as the page/viewport area).
- Use `top`, `right`, `bottom`, and `left` to place it.

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  left: 0;
}
```

Here, `.child` is placed at the top-left of `.parent`.

**Remember:** Absolute = removed from normal flow; positioned relative to the nearest suitable ancestor.

### `position: fixed`

- **Definition:** The element is positioned relative to the viewport in the usual case.
- It stays at the same screen position while the page is scrolled.
- It is useful for elements that should remain visible, such as a floating help button or a fixed navigation control.

```css
.box {
  position: fixed;
  bottom: 20px;
  right: 20px;
}
```

**Remember:** Fixed = stays in the same viewport position while scrolling (in the usual case).

### `position: sticky`

- **Definition:** The element behaves like a normally positioned element until the scroll reaches a specified offset; then it sticks in place within its scrolling area.
- You generally need to specify an offset such as `top: 0` for the sticky effect to happen.
- It is useful for navigation bars or section headings that stick near the top while scrolling.

```css
.navbar {
  position: sticky;
  top: 0;
}
```

**Remember:** Sticky = normal at first, then sticks when you scroll to its threshold.

## 3. `fixed` vs `sticky`

| Fixed | Sticky |
|---|---|
| Stays at the specified viewport position from the start. | Scrolls normally until it reaches its offset. |
| Does not reserve its normal space in the document flow. | Keeps its space in the normal flow. |
| Commonly used for floating controls. | Commonly used for sticky navigation bars and headings. |

**Quick memory trick:**
- **Fixed:** fixed to the screen.
- **Sticky:** sticks only after you scroll to it.

## 4. The offset properties

These work with positioned elements:

- `top`: distance from the top.
- `right`: distance from the right.
- `bottom`: distance from the bottom.
- `left`: distance from the left.

For `relative`, the offsets shift the element away from its original position. For `absolute` and `fixed`, they help determine its placement relative to its containing block. For `sticky`, an offset such as `top` sets the sticking threshold.

```css
.box {
  position: absolute;
  top: 10px;
  left: 15px;
}
```

## 5. `z-index`

- **Definition:** `z-index` controls the stacking order of overlapping elements.
- Within the same stacking context, a higher `z-index` is generally displayed in front of a lower one.
- For the positioned elements demonstrated in the video, set a non-static position (such as `relative`) before using `z-index`.

```css
.box-one {
  position: relative;
  z-index: 2;
}

.box-two {
  position: relative;
  z-index: 1;
}
```

Here, `.box-one` appears in front of `.box-two` if they overlap and are in the same stacking context.

**Remember:** Higher `z-index` = closer to the front, but stacking contexts can affect comparisons.

## 6. Important rule: how `absolute` finds its reference

When an absolutely positioned element needs a reference:

1. It checks its parent.
2. If that parent is not a suitable positioned ancestor, it checks the next ancestor.
3. It continues upward until it finds the nearest suitable ancestor.
4. If none is found, it uses the initial containing block.

Example:

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  left: 0;
}
```

The child is positioned relative to `.parent`, not the whole page.

The video also points out that certain properties on an ancestor can establish a containing block for positioned descendants even when that ancestor has `position: static`. The examples mentioned are:

- `transform`
- `filter`
- `perspective`

This is an important exception to remember.

## 7. Extra clarifications for accurate revision

These details make the video explanations more precise:

- **Relative does not remove an element from the flow.** Its visual position changes, but its original layout space remains.
- **Absolute does remove an element from the flow.** Following elements lay out as though the absolutely positioned element were not there.
- **Fixed is usually viewport-relative**, but an ancestor with certain properties (such as `transform`) can make it use that ancestor as its containing block instead.
- **Sticky needs room and a scroll context.** It may not stick as expected if an ancestor's overflow/scrolling setup or the available space prevents it.
- **`z-index` is affected by stacking contexts.** A child with a very large `z-index` cannot necessarily appear above an element outside its parent's stacking context.
- **Small `z-index` correction:** the video presents non-static positioning as necessary for `z-index`. That is a useful rule for positioned elements, but it is not universal: flex and grid items can also use `z-index` without a non-static `position`.

## 8. Quick comparison table

| Value | Positioned relative to | In normal flow? | Moves with page scroll? |
|---|---|---:|---|
| `static` | Normal document flow | Yes | Yes |
| `relative` | Its original position | Yes | Yes |
| `absolute` | Nearest suitable containing block | No | Usually yes |
| `fixed` | Usually the viewport | No | No, in the usual case |
| `sticky` | Normal flow, then its scroll container's scrolling area | Yes | Until it sticks; then stays within its sticky limits |

## 9. One-minute revision

- `static` → default; normal flow; offsets do not reposition it.
- `relative` → shifts from its original position; keeps its original space.
- `absolute` → removed from normal flow; uses the nearest suitable ancestor as its reference.
- `fixed` → usually stays at the same place on the screen while scrolling.
- `sticky` → behaves normally first, then sticks after reaching an offset.
- `z-index` → controls which overlapping element appears in front, subject to stacking contexts.
- `top`, `right`, `bottom`, `left` → offset/placement properties used with positioned elements.

## 10. Small practice check

1. Which position value is the default?
2. Which value moves an element from its original position but keeps its original space?
3. Which value removes an element from normal document flow?
4. Which value usually keeps an element in the same screen position while scrolling?
5. Which value behaves normally first and sticks after reaching an offset?
6. What does `z-index` control?
7. Which ancestor does an absolutely positioned element use as its reference?

