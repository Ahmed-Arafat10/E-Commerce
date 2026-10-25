# Section 3 — HTML Lists & Links

**Course:** HTML & CSS Basics — BIS  
**Topic:** `<ul>`, `<ol>`, `<li>`, nested lists, `<a>` (anchor links), and inline vs. block elements  
**Practical exercise:** 15 minutes maximum

## Learning outcomes

By the end of this section, you should be able to:

- Create an unordered (bulleted) list and an ordered (numbered) list.
- Add individual items to either type of list.
- Create a nested unordered list (a list inside a list item).
- Create links to another website, another HTML page, and a specific section on the same page.
- Create email, phone, and download links.
- Open an external link in a new browser tab safely.
- Distinguish between inline and block elements and predict how they appear on a page.

---

## 1. `<ul>` — Unordered List

**Definition:** `<ul>` creates a list of items where the **order does not matter**. Browsers normally display bullet
points.

```html
<h2>Our activities</h2>
<ul>
    <li>Workshops</li>
    <li>Student projects</li>
    <li>Networking</li>
</ul>
```

**Use it for:** Features, activities, categories, or other items without a required sequence.

## 2. `<ol>` — Ordered List

**Definition:** `<ol>` creates a list of items where the **order matters**. Browsers normally display numbers (1, 2,
3, ...).

```html
<h2>How to join</h2>
<ol>
    <li>Fill in the form.</li>
    <li>Check your email.</li>
    <li>Attend the first meeting.</li>
</ol>
```

**Use it for:** Instructions, steps, rankings, or sequences.

## 3. `<li>` — List Item

**Definition:** `<li>` represents **one item** inside a `<ul>` or `<ol>`.

```html

<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

**Important:** `<li>` belongs inside a list. Choose `<ul>` or `<ol>` based on whether item order is meaningful.

### Quick comparison

| Tag    | Meaning        | Default appearance           |
|--------|----------------|------------------------------|
| `<ul>` | Unordered list | Bullets                      |
| `<ol>` | Ordered list   | Numbers                      |
| `<li>` | One list item  | One bullet or numbered entry |

---

## 4. Nested `<ul>` — List Inside a List

**Definition:** A **nested list** is a list placed **inside an `<li>`** of another list. It helps organize subcategories
or related details under a main item.

```html
<h2>Our Activities</h2>
<ul>
    <li>
        HTML Workshops
        <ul>
            <li>HTML Basics</li>
            <li>HTML Lists and Links</li>
            <li>HTML Forms</li>
        </ul>
    </li>
    <li>
        Student Projects
        <ul>
            <li>Personal Portfolio</li>
            <li>E-Commerce Website</li>
        </ul>
    </li>
    <li>Networking Events</li>
</ul>
```

**What you'll see:** Main activities appear as bullets; their sub-activities appear as **indented bullets**, often with
a different bullet style.

**Important:** Place the inner `<ul>` **inside its parent `<li>`**, before that item's closing `</li>`.

---

## 5. `<a>` — Anchor (Link)

**Definition:** `<a>` creates a **clickable link**. The `href` attribute specifies the link's destination.

**Basic syntax:**

```html
<a href="https://example.com">Visit Example</a>
```

There are not separate HTML anchor tags for each link type. The **value of `href`** (and sometimes other attributes)
determines what the link does.

### Common anchor link types

| Link type                               | Example                                            | What happens                                                     |
|-----------------------------------------|----------------------------------------------------|------------------------------------------------------------------|
| **External website (absolute URL)**     | `<a href="https://developer.mozilla.org/">MDN</a>` | Opens a website using its full URL.                              |
| **Another local page (relative URL)**   | `<a href="about.html">About us</a>`                | Opens `about.html` in the same folder.                           |
| **Section on the same page (fragment)** | `<a href="#contact">Go to contact</a>`             | Jumps to the element with `id="contact"`.                        |
| **Email link**                          | `<a href="mailto:club@example.com">Email us</a>`   | Opens a configured email app.                                    |
| **Phone link**                          | `<a href="tel:+201000000000">Call us</a>`          | Opens a calling app on supported devices.                        |
| **Download link**                       | `<a href="index.html" download>Download page</a>`  | Requests a download instead of normal navigation when supported. |

### Opening a link in a new tab

Use `target="_blank"` for a new tab or window

```html
<a href="https://developer.mozilla.org/" target="_blank">
    Learn HTML on MDN
</a>
```

> **Good practice:** Use meaningful link text, such as **Read club information**, rather than **Click here**. Also, an
> on-page anchor like `href="#contact"` needs a matching `id="contact"` in the document.

---

## 6. Inline vs. Block Elements

Elements have different **default display behaviors** in the browser.

| Type               | Default behavior                                                                  | Examples from this lesson               |
|--------------------|-----------------------------------------------------------------------------------|-----------------------------------------|
| **Block element**  | Starts on a new line and normally fills the available width.                      | `<h1>`, `<h2>`, `<p>`, `<ul>`, `<ol>`   |
| **Inline element** | Flows within the current line of text and only takes the space its content needs. | `<a>`, `<strong>`, `<em>`, `<b>`, `<i>` |
| **List item**      | Has a special `list-item` display, with a bullet or number.                       | `<li>`                                  |

### Example

```html
<h2>Block element: a heading</h2>
<p>Block element: a paragraph with an
    <a href="about.html">inline link</a> inside it.
</p>
<p>Another paragraph starts on a new line.</p>
```

**Remember:** An `<a>` link usually appears *within* the surrounding sentence without starting a new line. A `<p>` or
`<ul>` normally starts on a new line. These are **default** behaviors; later, CSS can change how elements are displayed.

---

# Practical Exercise — Build a BIS Student Club Page (15 minutes)

**Goal:** Build a small two-page website using lists, **nested `<ul>`**, and common anchor link types. Identify block
and inline elements on the page.

**What you need:** A code editor (such as VS Code) and a web browser. **No CSS or JavaScript required.**

### Step 1 — Create the files (2 minutes)

Create a folder called `bis-student-club`, then create two files inside it:

```text
bis-student-club/
├── index.html
└── about.html
```

### Step 2 — Write `index.html` (8 minutes)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BIS Student Club</title>
</head>
<body>
<h1>BIS Student Club</h1>
<p>Welcome to our club website!</p>

<p><a href="#join">Jump to How to Join</a></p>

<h2>Our Activities</h2>
<ul>
    <li>
        HTML Workshops
        <ul>
            <li>HTML Basics</li>
            <li>HTML Lists and Links</li>
            <li>HTML Forms</li>
        </ul>
    </li>
    <li>
        Student Projects
        <ul>
            <li>Personal Portfolio</li>
            <li>E-Commerce Website</li>
        </ul>
    </li>
    <li>Networking Events</li>
</ul>

<h2 id="join">How to Join</h2>
<ol>
    <li>Read our <a href="about.html">club information</a>.</li>
    <li>Email <a href="mailto:club@example.com">the club team</a>.</li>
    <li>Attend your first event.</li>
</ol>

<p>
    Learn more at
    <a href="https://developer.mozilla.org/en-US/docs/Web/HTML"
       target="_blank" rel="noopener noreferrer">MDN Web Docs</a>.
</p>

<p>Example phone link: <a href="tel:+201000000000">0100 000 0000</a></p>
<p><a href="index.html" download="bis-club-page.html">Download this page</a></p>
</body>
</html>
```

### Step 3 — Write `about.html` (3 minutes)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>About the BIS Student Club</title>
</head>
<body>
<h1>About Our Club</h1>
<p>We learn web development and build projects together.</p>
<p><a href="index.html">Back to Home</a></p>
</body>
</html>
```

### Step 4 — Open and test the website (2 minutes)

Open `index.html` in your browser and confirm:

- [ ] The activities appear with **bullets**, and the joining steps appear with **numbers**.
- [ ] Workshop topics and project examples are **nested, indented bullets** under their parent activity.
- [ ] **Jump to How to Join** takes you to that heading.
- [ ] **Club information** opens `about.html`; **Back to Home** returns to `index.html`.
- [ ] **MDN Web Docs** opens in a new tab.
- [ ] The heading `<h2>` starts on a new line (block), while the `<a>` link sits within a paragraph or list item
  (inline).
- [ ] The email, phone, and download links have the expected behavior when supported by your browser/device.

**Note:** `club@example.com` and the phone number are examples, not real club contact details. Email and phone links
depend on the apps installed on your device. Browser support and local-file behavior can affect downloads.

---

## Quick recap

- `<ul>`: list where order does **not** matter.
- `<ol>`: list where order **does** matter.
- `<li>`: one item inside either list.
- **Nested `<ul>`:** a sublist inside a parent `<li>`.
- `<a href="...">`: link to a destination or action.
- `href="#id"`: jump to an element with that `id`.
- `target="_blank"`: open a link in a new tab or window.
- **Block vs. inline:** blocks normally start new lines; inline elements flow within text. (`<li>` has special
  `list-item` display.)

**Optional challenge:** Add another activity with its own nested `<ul>`, and add one more step to the ordered list.
