# Section 4 — HTML Tables, Images & CSS Basics

**Course:** HTML & CSS Basics — BIS  
**Topics:** HTML tables, `<img>`, three ways to add CSS, and basic CSS text properties  
**Practical exercise:** 15 minutes maximum

## Learning outcomes

By the end of this section, you should be able to:

- Build a table using rows, header cells, and data cells.
- Add an image and describe it using alternative text.
- Explain the difference between **inline**, **internal**, and **external** CSS.
- Write basic CSS rules using selectors, properties, and values.
- Style text using color, font, alignment, spacing, and decoration properties.
- Combine HTML and CSS in a small BIS Student Club webpage.

---

## 1. HTML Tables

**Definition:** An HTML table displays **tabular data** in rows and columns, such as a timetable, product price list, or
student grades.

### Main table tags

| Tag         | Meaning           | What it does                                     |
|-------------|-------------------|--------------------------------------------------|
| `<table>`   | Table             | Contains the entire table.                       |
| `<tr>`      | Table row         | Creates one row.                                 |
| `<th>`      | Table header cell | Creates a heading cell; usually bold by default. |
| `<td>`      | Table data cell   | Creates a regular data cell.                     |
| `<caption>` | Table caption     | Provides a title or description for the table.   |
| `<thead>`   | Table head        | Groups the header rows.                          |
| `<tbody>`   | Table body        | Groups the main data rows.                       |
| `<tfoot>`   | Table foot        | Groups summary rows, when needed.                |

### Example: BIS workshop schedule

```html

<table>
    <caption>BIS Workshop Schedule</caption>
    <thead>
    <tr>
        <th>Workshop</th>
        <th>Day</th>
        <th>Room</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>HTML Basics</td>
        <td>Sunday</td>
        <td>Lab 1</td>
    </tr>
    <tr>
        <td>CSS Basics</td>
        <td>Tuesday</td>
        <td>Lab 2</td>
    </tr>
    </tbody>
</table>
```

**How to read it:** The `<table>` contains rows (`<tr>`). Each row contains cells: `<th>` for a heading or `<td>` for
data.

**Important:** Browsers do not automatically draw visible borders around every cell. We will add borders using CSS in
the practical exercise. Use tables for **data**, not for arranging the entire page layout.

### Optional: Merge cells with `colspan` and `rowspan`

- `colspan="2"` makes a cell span **two columns**.
- `rowspan="2"` makes a cell span **two rows**.

```html

  <table>
      <tr>
          <th colspan="2">BIS Courses</th>
      </tr>
      <tr>
          <td>HTML</td>
          <td>CSS</td>
      </tr>
  </table>
```

---

## 2. `<img>` — Image

**Definition:** The `<img>` element displays an image on a webpage. It is a **void element**, meaning it does not have a
closing `</img>` tag.

### Basic syntax

```html
<img src="club.jpg" alt="BIS students attending a workshop">
```

| Attribute | Purpose                                                                       | Example                        |
|-----------|-------------------------------------------------------------------------------|--------------------------------|
| `src`     | Specifies the image file location or URL.                                     | `src="club.jpg"`               |
| `alt`     | Describes the image if it cannot be seen or loaded; useful for accessibility. | `alt="Students at a workshop"` |
| `width`   | Sets the image's displayed width (in CSS pixels).                             | `width="400"`                  |
| `height`  | Sets the image's displayed height (in CSS pixels).                            | `height="200"`                 |

### Relative path vs. absolute URL

**Local image (relative path):**

```html
<img src="images/club.jpg" alt="BIS Student Club group photo" width="400">
```

This expects an `images` folder next to your HTML file and a `club.jpg` file inside it.

**Online image (absolute URL):**

```html
<img
        src="https://placehold.co/480x180/png?text=BIS+Student+Club"
        alt="Placeholder banner with the words BIS Student Club"
        width="480"
        height="180"
>
```

The online placeholder requires an internet connection. In a real project, use an image you have permission to publish.

**Good practice:** Write meaningful `alt` text for informative images. If an image is purely decorative, `alt=""` can be
appropriate. Preserve image proportions to avoid stretching; later, CSS can help make images responsive.

---

## 3. What Is CSS?

**CSS** stands for **Cascading Style Sheets**. HTML defines the **content and structure** of a webpage, while CSS
controls its **appearance**: colors, fonts, spacing, borders, and layouts.

A basic CSS rule contains a **selector** and one or more **property: value** declarations:

```css
p {
    color: blue;
    font-size: 18px;
}
```

- `p` is the **selector**: select paragraph elements.
- `color` and `font-size` are **properties**: what to style.
- `blue` and `18px` are **values**: how to style it.
- A semicolon (`;`) separates declarations.

> **Terminology:** CSS uses the word **properties** (not HTML attributes) for `color`, `font-size`, etc. HTML attributes
> include `src`, `href`, and `alt`.

---

## 4. Three Ways to Add CSS to HTML

### A. Inline CSS — `style` attribute

**Definition:** CSS written directly on a single HTML element using its `style` attribute.

```html
<p style="color: green; font-weight: bold;">
    Registration is open!
</p>
```

**Use it for:** Quick demonstrations or one-off styles. It is harder to maintain when used repeatedly across a website.

### B. Internal CSS — `<style>` element

**Definition:** CSS written inside a `<style>` element, normally in the page's `<head>`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Internal CSS Example</title>
    <style>
        h1 {
            color: navy;
            text-align: center;
        }
    </style>
</head>
<body>
<h1>BIS Student Club</h1>
</body>
</html>
```

**Use it for:** Styles specific to one HTML page.

### C. External CSS — `<link>` element

**Definition:** CSS stored in a separate `.css` file and connected to an HTML page using `<link>` inside `<head>`.

**`index.html`:**

```html

<head>
  <meta charset="UTF-8">
  <title>External CSS Example</title>
  <link rel="stylesheet" href="assets/css/style.css">
</head>
```

**`assets/css/style.css`:**

```css
body {
    font-family: Arial, sans-serif;
    color: #333333;
}
```

**Use it for:** Most projects, especially when multiple webpages share the same design.

### Quick comparison

| CSS type     | Where the CSS is written                       | Main advantage                   |
|--------------|------------------------------------------------|----------------------------------|
| **Inline**   | In an element's `style="..."`                  | Fast for one element.            |
| **Internal** | Inside `<style>` in the HTML file              | Convenient for one page.         |
| **External** | In a separate `.css` file linked with `<link>` | Reusable and easier to maintain. |

**Important:** If rules conflict, CSS uses the **cascade** (including importance, specificity, and source order) to
decide which style applies. In basic cases, an inline style takes priority over normal internal/external rules. Internal
CSS does **not** always override external CSS; the selector and rule order also matter.

---

## 5. Basic CSS Properties for Text

| CSS property      | What it changes               | Example                           |
|-------------------|-------------------------------|-----------------------------------|
| `color`           | Text color                    | `color: darkblue;`                |
| `font-family`     | Font type                     | `font-family: Arial, sans-serif;` |
| `font-size`       | Text size                     | `font-size: 18px;`                |
| `font-weight`     | Text thickness (e.g., bold)   | `font-weight: bold;`              |
| `font-style`      | Normal or italic text         | `font-style: italic;`             |
| `text-align`      | Horizontal text alignment     | `text-align: center;`             |
| `text-decoration` | Underline, line-through, etc. | `text-decoration: underline;`     |
| `text-transform`  | Changes letter capitalization | `text-transform: uppercase;`      |
| `line-height`     | Spacing between lines         | `line-height: 1.6;`               |
| `letter-spacing`  | Spacing between letters       | `letter-spacing: 1px;`            |

### Example

```html
<p class="welcome">Welcome to the BIS Student Club!</p>
```

```css
.welcome {
    color: darkblue;
    font-family: Arial, sans-serif;
    font-size: 20px;
    font-weight: bold;
    font-style: italic;
    text-align: center;
    text-decoration: underline;
    text-transform: uppercase;
    line-height: 1.6;
    letter-spacing: 1px;
}
```

**Remember:** `.welcome` selects elements with `class="welcome"`. By comparison, `p` selects **all** paragraph elements.
The example demonstrates every property, but a real design usually applies only the styles that are needed.

---

# Practical Exercise — BIS Student Club Events Page (15 minutes)

**Goal:** Create a webpage with a **workshop table**, an **image**, and **all three CSS methods**. Style text using
basic CSS properties.

**What you need:** VS Code (or another text editor), a browser, and an internet connection to load the sample online
image.

### Step 1 — Create the project files (2 minutes)

Create a folder called `bis-club-events` containing:

```text
bis-club-events/
├── index.html
└── style.css
```

### Step 2 — Write `index.html` (7 minutes)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BIS Student Club Events</title>

  <!-- External CSS -->
  <link rel="stylesheet" href="assets/css/style.css">

  <!-- Internal CSS -->
  <style>
    h1 {
      color: navy;
      text-align: center;
    }
  </style>
</head>
<body>
<h1>BIS Student Club Events</h1>

<!-- Inline CSS -->
<p style="color: darkgreen; font-weight: bold;">
  Registration is now open!
</p>

<img
        src="https://placehold.co/480x180/png?text=BIS+Student+Club"
        alt="Placeholder banner with the words BIS Student Club"
        width="480"
        height="180"
>

<h2>Upcoming Workshops</h2>
<table>
  <caption>November Workshop Schedule</caption>
  <thead>
  <tr>
    <th scope="col">Workshop</th>
    <th scope="col">Day</th>
    <th scope="col">Room</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>HTML Basics</td>
    <td>Sunday</td>
    <td>Lab 1</td>
  </tr>
  <tr>
    <td>CSS Basics</td>
    <td>Tuesday</td>
    <td>Lab 2</td>
  </tr>
  <tr>
    <td>Mini Project</td>
    <td>Thursday</td>
    <td>Lab 3</td>
  </tr>
  </tbody>
</table>

<p class="note">Seats are limited. Join early!</p>
</body>
</html>
```

### Step 3 — Write `assets/css/style.css` (4 minutes)

```css
body {
    font-family: Arial, sans-serif;
    color: #333333;
    line-height: 1.6;
}

p {
    font-size: 16px;
}

h2 {
    text-transform: uppercase;
    letter-spacing: 1px;
}

.note {
    font-style: italic;
    text-decoration: underline;
}

img {
    max-width: 100%;
    height: auto;
}

table {
    border-collapse: collapse;
    width: 100%;
    max-width: 600px;
}

th, td {
    border: 1px solid gray;
    padding: 8px;
    text-align: left;
}

caption {
    font-weight: bold;
}
```

**New helper properties:** `border` draws table cell borders; `padding` adds space inside cells;
`border-collapse: collapse` combines neighboring borders; `max-width` limits an element's width. These are not text
properties, but they make the table and image easier to view.

### Step 4 — Open and test (2 minutes)

Open `index.html` in a browser, then confirm:

- [ ] A BIS Student Club banner image appears (internet connection required).
- [ ] The image has an `alt` description in the HTML source.
- [ ] The schedule has a caption, three column headings, and three data rows.
- [ ] Table cell borders appear after connecting `assets/css/style.css`.
- [ ] The main heading is **navy and centered** (**internal CSS**).
- [ ] “Registration is now open!” is **dark green and bold** (**inline CSS**).
- [ ] The text uses **Arial**, and the second heading is **uppercase** (**external CSS**).
- [ ] The final note appears *italic* and <u>underlined</u> (**external CSS**).