# type: "label"

`label` is designed to display text:

```js
{
  type: "label",
  props: {
    text: "Hello, World!",
    align: $align.center
  },
  layout: function(make, view) {
    make.center.equalTo(view.super)
  }
}
```

It shows `Hello, World!` on the screen.

# props

Prop | Type | Read/Write | Description
---|---|---|---
text | string | rw | text content
font | $font | rw | font
textColor | $color | rw | text color
shadowColor | $color | rw | shadow color
align | $align | rw | alignment
lines | number | rw | lines, 0 means no limit
autoFontSize | boolean | rw | adjust font size automatically