---
layout: post
hide: True
title: Basics of HTML Guide
description: An introduction to basic HTML, and resources to learn more.
type: ccc
permalink: /basics/html
author: Rohan Juneja
---

{% include nav_basics.html %}


# How does HTML work?
- Similar function to Markdown, identifies how stuff should be displayed
- HTML is based on tags `<tagname>content</tagname>`
  - Note the "/" on the ending tag
- See a markdown to html example below

Markdown
```md
# This is a title
```
HTML
```html
<h1>This is a title</h1>
```

# Attributes
- Tags can have additional info in attributes
- Attributes are in the following format below

```html
<tagname attribute_name="attribute_value" another_attribute="another_value"></tagname>
```

# Some useful tags to know that are similar to markdown
Image Tag - Markdown

```md
![describe image](link to image)
```

Image Tag - HTML

```html
<!-- no content so no end tag, width/height is optional (in pixels) -->
<img alt="describe image" src="link to image" width="100" height="200">
```

Link Tag - Markdown

```md
[link text](link)
```

Link Tag - HTML

```html
<a href="link">link text</a>
```

Bolded Text - Markdown

```md
**Bolded Text**
```

Bolded Text - HTML

```md
<strong>Bolded Text</strong>
```

Italic Text - Markdown

```md
*Italic Text*
```

Italic Text - HTML

```md
<i>Italic Text</i>
```

# Some new useful tags to know (not really in markdown)
P tag (just represeants a paragraph/normal text)

```html
<p>This is a paragraph</p>
```

Button

```html
<button>some button text</button>
```

Div (groups together related content)

```html
<!-- first information -->
<div>
    <!-- notice how tags can be put INSIDE eachother -->
    <p>This is the first paragarph of section 1</p>
    <p>This is the second paragraph of section 1</p>
</div>

<!-- second information -->
<div>
    <!-- notice how tags can be put INSIDE eachother -->
    <p>This is the first paragarph of section 2</p>
    <p>This is the second paragraph of section 2</p>
</div>
```



# Resources
- https://www.w3schools.com/html/default.asp
- I will show a demo of how to find information on this website
