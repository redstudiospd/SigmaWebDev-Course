CSS LIST STYLING: QUICK REVISION NOTES

Note: I couldn't retrieve the video's transcript, so I can't verify its
exact wording or examples. These notes cover the listed topics and use
standard CSS definitions.


1. INTRODUCTION (0:00)

HTML lists are useful for grouping related items. Use <ul> for an
unordered list, <ol> for an ordered list, and <li> for each list item.
CSS changes how the list looks without changing its meaning.


2. SIGMA WEB DEVELOPER COURSE INTRO (0:37)

Course introduction/context. The lesson focuses on styling lists and
using a list to build a navigation bar.


3. LIST STYLING (0:47)

list-style-type changes the bullet or numbering style.

  ul {
    list-style-type: square;
  }

  ol {
    list-style-type: upper-roman;
  }

list-style-position controls where the marker sits:
  outside: marker sits outside the item's text area (default)
  inside: marker sits within the item's text area

list-style is shorthand for setting marker type, position, and image.

To remove the default marker:

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

Removing the margin and padding also removes the browser's default
space around the list. <citation src="1,4"></citation>


4. USING AN IMAGE AS LIST STYLE (5:55)

list-style-image replaces the usual bullet with an image.

  ul {
    list-style-image: url("bullet.png");
  }

A fallback marker can be set with list-style-type in case the image
cannot load:

  ul {
    list-style-type: square;
    list-style-image: url("bullet.png");
  }

The image's size and alignment can be difficult to control with
list-style-image. For more control, use a custom marker or a
background image. <citation src="1,2,4"></citation>


5. CREATING A NAVBAR USING A LIST (8:04)

A navigation bar can be marked up as a list because its links are
a group of related destinations. Use <nav> to identify the navigation
section, then use CSS to arrange and style the list.

HTML:

  <nav>
    <ul class="navbar">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>

CSS:

  .navbar {
    display: flex;
    gap: 16px;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .navbar a {
    display: block;
    padding: 8px 12px;
    text-decoration: none;
  }

Flexbox arranges the list items in a row. The gap adds space between
them. Displaying links as blocks gives them a larger, easier-to-click
area. <citation src="5"></citation>


6. CONCLUSION (9:15)

Use list-style-type to choose markers, list-style-position to place
them, and list-style-image to use an image marker. For a navbar, keep
the semantic list structure and use CSS, often Flexbox, to arrange
and style the links.

Quick reminder:
  HTML provides the list structure.
  CSS controls its appearance and layout.