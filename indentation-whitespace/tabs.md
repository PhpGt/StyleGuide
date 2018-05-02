# Tabs

## Use the tab character for indentation

Tabs visually indicate the current block's level of indentation, assisting readability by being set to a particular column width. A tab character's width can be dynamically set, while consistently maintaining a single level of indentation.

There is no need to define a tab width as part of this styleguide, as every text editor is easily configurable to change the width of a tab character without affecting the source code itself. Tabs are originally 8 characters wide, still being so within terminal emulators and web browsers, and due to this styleguide avoiding many levels of indentation, 8 character wide tabs seem a perfectly acceptable width to use. However, this decision is left to the developer to set in their editor. Very commonly a tab width of 4 characters is used.

Using tabs allows tab stops to be respected. Tab characters that follow word characters on a line will automatically grow and shrink to the width of the next tab stop. Adding or removing characters before a tab will never break the tab stops. When changing the contents of the line before a tab, subsequent tab stops are kept aligned. Example: aligning array value assignments.

Programmers who can't change their personal coding style from spaces to tabs can use any decent editor to automatically convert between spaces and tabs to ensure the code is being committed in the same style as the guidelines for the repository.

Other justifications for tabs:

+ The tab character already exists specifically for indentation.
+ It's impossible to semi-indent something using tab characters.
+ Navigating indented code using the cursor keys is respected when using tab characters.

Arguments and rebuttals:

+ "Indenting with spaces means my code will look the same everywhere". Yes, that's exactly the point in using tabs. It is down to the developer to decide on their preferred tab width, as indentation size should not affect the code layout in any way.
+ "Spaces allow consistency in laying out code horizontally". They do, but this styleguide doesn't promote horizontal formatting of code.
