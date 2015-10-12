# Sass Style Guide

Follow this: https://github.com/necolas/idiomatic-css with some additions and exceptions

Always use UTF-8 in your editor

Omit leading 0: `.8em` not `0.8em` and `.3s` not `0.3s`

Use RGB color syntax: `rgb(255,255,255)` not `fff` or `ffffff` — for compatibility and improved readability when used with with `rgba()`

Avoid IDs for styles where possible

## Naming conventions

Name classes (and IDs) based on an element’s purpose: `.search-form`

If the class doesn’t apply to an element with a soecific purpose, give it a generic name, rather than a presentational one: `.btn-alt` not `.btn-green` and `.btn-important` not `.btn-large`

Separate words in class/ID names with hypens: `.search-form` not `.searchform`, `.searchForm` or `.search_form`

Make class/ID names descriptive but not too long

## Media Queries

We usually don’t target any specific devices or widths — we let the layout dictate the break-points for media queries instead. When looking at a Sass file, we’re going to want to find out what a specific element does and where it’s styles come from. Using the old method of grouping media queries at the bottom of the file, we have to find an element’s base rules, then find media queries applied to it in another part of the file. We can avoid this because Sass allows us to place media queries inside rules, creating self-contained rules that describe all of the styles for an element at all screen widths:

```
.page-title {
	font-size: 1em;
	text-align: left;
	padding: 5%;

	@media all and (min-width: 600px) {
		font-size: 2em;
		text-align: center;
		padding: 1em;
	}
}
```
