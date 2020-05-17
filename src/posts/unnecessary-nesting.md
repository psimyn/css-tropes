---
title: Unnecessary nesting
date: '2020-05-14'
tags:
  - css
---

I see this quite commonly in SCSS. Related classes get grouped under their parent namespace. For example:

```scss
.modal {
  .modal-header {
    font-size: 3rem;
  }
}
```

The problem is that when you want a different sized header. The specificity battle has already begun:

```scss
.header--small {
  font-size: 1.5rem;
}
```

You have a few options here.

Adding a modal-specific override

```scss
.modal {
  .modal-header--small {
    font-size: 1.5rem;
  }
}
```

Make your modifier class more specific. A common and terrible way:

```scss
.header--small {
  font-size: 1.5rem !important;
}
```

A still-not-great-but-less-terrible way:

```scss
.header--small.header--small {
  font-size: 1.5rem;
}
```

The ideal solution is to not unnecessarily nest! You can organise your rules with different files.

```scss
.modal {
  // stuff related to the modal itself
}

.modal-header {
  font-size: 3rem;
}
```

Just because you _can_ nest with preprocessors doesn't mean that you should. There is also currently a [CSS Nesting Spec Draft](https://drafts.csswg.org/css-nesting-1/) that I do not look forward to at all.

