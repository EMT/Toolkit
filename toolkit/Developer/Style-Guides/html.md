# HTML Style Guide

Always use UTF-8 in your editor

Always use `<meta charset="utf-8">`

Always use HTML5: `<!DOCTYPE html>`

Don’t use the `type` attribute when including styles or scripts

All block elements on a newline:

```
<ul>
    <li>Item</li>
</ul>
```

Inline elements inline:

```
<p><strong>Hello<strong> world</p>
```

Indentation: 4 spaces, no tabs:

```
<div>
    <ul>
        <li>Item</li>
    </ul>
</div>
```

Indent templating logic:

```
<div>
    <ul>
        <?php foreach ($items as $item) { ?>
            <li><?= $item ?></li>
        <?php } ?>
    </ul>
</div>
```

Lowercase for everything: `<img src="">` not `<IMG SRC="">`

No trailing whitespace

Don’t use entity references unless replacing special HTML characters: `©` not `&copy;`

Don’t close void elements: `<br>` not `<br />` and `<img src="">` not `<img src="" />`

Do close elements with optional closing tags, for readability

Use double quotes for attributes: `<img src="">` not `<img src=''>`

Write semantic HTML

Test HTML using the W3C validator

Use multimedia fallbacks, eg., img alt

Comment code where it’s helpful


