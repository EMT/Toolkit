Chrome Pro Tips
===============

In the console type 

`document.designMode = "on"`

This makes the page easily editable (useful for changing text for screenshots etc). You can make a bookmarklet to toggle this mode on and off by highlighting the following and dragging to the bookmarks bar:

`javascript:(function () {if (document.documentElement.contentEditable === false || document.designMode === "off") {document.body.contentEditable='true';document.designMode='on';void 0;} else if (document.documentElement.contentEditable === true || document.designMode === "on") {document.body.contentEditable='false';document.designMode='off';void 0;}})();`

###Keyboard Shortcuts


<kbd>cmd</kbd>+<kbd>W</kbd> to close the current tab

<kbd>cmd</kbd>+<kbd>T</kbd> to open new tab

<kbd>cmd</kbd>+<kbd>shift</kbd>+<kbd>T</kbd> to open most recently closed tab

<kbd>cmd</kbd>+<kbd>opt</kbd>+<kbd>I</kbd> to open dev tools

<kbd>cmd</kbd>+<kbd>L</kbd> to select the URL at the top of the browser