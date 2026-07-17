+++
title = "test markdown page"
description = "test markdown page"
+++

Table of contents:

* [Heading 1](#heading-1)
* [Heading 2](#heading-2)
* [Heading 3](#heading-3)
* [Heading 4](#heading-4)
* [Heading 5](#heading-5)
* [Heading 6](#heading-6)
* [Everything else I can think of](#others)

***

# Heading 1

words words words words words words words words words words words words words words words words words words words words

## Heading 2

words words words words words words words words words words words words words words words words words words words words

### Heading 3

words words words words words words words words words words words words words words words words words words words words

#### Heading 4

words words words words words words words words words words words words words words words words words words words words

##### Heading 5

words words words words words words words words words words words words words words words words words words words words

###### Heading 6

words words words words words words words words words words words words words words words words words words words words

---

# Everything else that I can think of {#others}

When writing we sometimes need all sorts of fun text decorations like **bold** or *italics* or _italics with underscores_ or ~~strikethrough~~. Any others???

---

> Block quote words words words words words words words words words words words words words words words words words words words words words words words words words words words

> > Block quote words words words words words words words words words words words words words words words words words words words words words words words words words words words

> > > Block quote words words words words words words words words words words words words words words words words words words words words words words words words words words words

---

Footnote 1 [^1]

Footnote 2 [^2]

Footnote 3 [^3]

---

- one
- kind
    - type
    - variation
- of
- list

* one
* kind
    * type
    * variation
* of
* list

1. one
2. kind
    1. type
    2. variation
3. of
4. list

1) one
2) kind
    1) type
    2) variation
3) of
4) list

100. this
101. list
102. starts
103. at
104. one-hundred

---

(copied from [this page](https://raw.githubusercontent.com/fullpipe/markdown-test-page/refs/heads/master/test-page.md))

| Table Heading 1 | Table Heading 2 | Center align    | Right align     | Table Heading 5 |
| :-------------- | :-------------- | :-------------: | --------------: | :-------------- |
| Item 1          | Item 2          | Item 3          | Item 4          | Item 5          |
| Item 1          | Item 2          | Item 3          | Item 4          | Item 5          |
| Item 1          | Item 2          | Item 3          | Item 4          | Item 5          |
| Item 1          | Item 2          | Item 3          | Item 4          | Item 5          |
| Item 1          | Item 2          | Item 3          | Item 4          | Item 5          |

---

Code can be written as a single-line thing like this: `$ hello world` or like this:

```
# this is totally fake code for testing

import flags;
import os;
import time;

fn main() {
    let flags = flags.collect();

    println!("Connecting to {} at {}", flags.name, flags.server_address);
    println!("10%");
    os.sleep(1 * time.second);
    println!("50%");
    os.sleep(1 * time.second);
    println!("You've hacked {}", flags.name);
}
```

---

Task list:

- [x] Make website
- [x] Write articles
- [ ] ??????
- [ ] Profit

---

Pictures are already tested in another file, [here](@/2025-02-01-pictures.md).

---

[^1]: Made you look!
[^2]: Made you look!
[^3]: Made you look!