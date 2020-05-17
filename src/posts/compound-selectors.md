---
title: Compound selectors
date: '2020-05-17'
tags:
  - css
  - selectors
---

Often an accompanied by excessive nesting, compound selectors are the result of either too much cleverness or the endless pursuit of DRYness.

```scss
.hello {
  &-world {
    color: green;
  }
}
```

This does save a little typing, but usually not worth the loss of searchability or readability. It's easy to miss the space and think it's a nested selector

```scss
.hello {
  &-world {
    color: green;
  }

  & -world {
    color: red;
  }
}
```

It is more acceptable to do this inside loops, i.e. for generating a list of colors or responsive modifiers

```scss
@each $class, $color in $colors {
  .#{$class} {
    color: $color;
  }
}
```

Or for any kind of larger scale util generation this is fine. But don't use it save writing out the prefix of your classname - you will come to regret it later. I did.
