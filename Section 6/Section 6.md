# Section 6 — HTML Forms and `<div>`

**Topics:** HTML forms, form controls, the `<div>` element, and basic form styling

## 1. Learning objectives

By the end of this section, you should be able to:

- Explain why websites use forms.
- Create a form using inputs, labels, buttons, dropdowns, and text areas.
- Use common form attributes correctly.
- Group HTML elements with `<div>` and style those groups with CSS classes.
- Build a simple registration form.

---

## 2. What is a form?

An **HTML form** collects information from a user, such as a name, email address, or selected option. Examples include
login, registration, search, feedback, and contact forms.

The `<form>` element groups the fields and provides a way to submit their values.

```html
<form action="#" method="get">
    <!-- Form fields go here -->
</form>
```

| Attribute | Meaning                                    | Example                           |
|-----------|--------------------------------------------|-----------------------------------|
| `action`  | Where the form data is sent when submitted | `action="/register"`              |
| `method`  | How the browser sends the data             | `method="get"` or `method="post"` |

**GET vs POST (beginner level):**

- **GET:** Usually used for searches and filters. Submitted values can appear in the URL.
- **POST:** Commonly used to send registration or login information to a server. It does **not** encrypt data by itself;
  real websites should use HTTPS.

> **Important:** HTML can display and submit a form, but it does not automatically save information or create user
> accounts. A real submission requires a working server or other form-handling service. The examples in this lesson are
> for front-end practice only.

---

## 3. Form elements

### 3.1 `<label>` — Describe an input

A label tells the user what to enter. The `for` attribute should match the input's `id` so clicking the label focuses
that input.

```html
<label for="studentName">Student name:</label>
<input type="text" id="studentName" name="studentName">
```

### 3.2 `<input>` — Collect short values

The `type` attribute controls the kind of input shown.

| Input type | Purpose                                      | Example          |
|------------|----------------------------------------------|------------------|
| `text`     | One line of text                             | Student name     |
| `email`    | Email address, with basic browser validation | Student email    |
| `password` | Hides characters while typing                | Account password |
| `number`   | Numeric value                                | Age              |
| `date`     | Date picker (browser-dependent)              | Event date       |
| `radio`    | Choose **one** option from a group           | Study level      |
| `checkbox` | Choose a yes/no option or multiple options   | Agree to rules   |

Examples:

```html
<input type="text" name="fullName" placeholder="Enter your name" required>
<input type="email" name="email" required>
<input type="number" name="age" min="16" max="60">
<input type="date" name="eventDate">
```

**Common attributes:**

| Attribute     | Purpose                                                                     |
|---------------|-----------------------------------------------------------------------------|
| `type`        | Specifies the input type                                                    |
| `id`          | Uniquely identifies an element; connects it to its label                    |
| `name`        | The key used for the field when the form is submitted                       |
| `value`       | The value submitted for a selected option, or the initial value of an input |
| `placeholder` | A short hint inside an input; **not a replacement for a label**             |
| `required`    | Prevents normal form submission until the field is completed                |
| `min` / `max` | Limit valid numeric or date values where applicable                         |

### 3.3 Radio buttons — Choose one

Radio inputs belong to the same group when they share a `name`. Give each option a different `value`.

```html
<input type="radio" id="first" name="year" value="first" required>
<label for="first">First year</label>

<input type="radio" id="second" name="year" value="second">
<label for="second">Second year</label>
```

### 3.4 Checkboxes — Tick an option

```html
<input type="checkbox" id="updates" name="updates" value="yes">
<label for="updates">Send me event updates</label>
```

A checkbox is usually submitted only when it is checked.

### 3.5 `<select>` and `<option>` — Dropdown list

```html
<label for="track">Choose a track:</label>
<select id="track" name="track" required>
    <option value="">-- Select a track --</option>
    <option value="html">HTML</option>
    <option value="css">CSS</option>
</select>
```

### 3.6 `<textarea>` — Longer messages

Use `<textarea>` for multi-line input. Its starting text goes **between the tags**, not in a `value` attribute.

```html
<label for="message">Your message:</label>
<textarea id="message" name="message" rows="4" placeholder="Write here..."></textarea>
```

### 3.7 `<button>` — Submit the form

```html
<button type="submit">Register</button>
```

`type="submit"` submits the form. `type="button"` is a regular button, generally used with JavaScript.

---

## 4. What is a `<div>`?

The `<div>` element is a **block-level container** used to group other HTML elements.

- It has **no special meaning** on its own.
- It helps organize page sections or form fields.
- It is often given a `class` or `id` so CSS can style the group.
- By default, a `<div>` begins on a new line and takes the available width.

```html
<div class="form-group">
    <label for="city">City:</label>
    <input type="text" id="city" name="city">
</div>
```

```css
.form-group {
    margin-bottom: 12px;
}
```

**`class` vs `id`:** A class can be reused on many elements (e.g., `class="form-group"`). An `id` should be unique on
the page (e.g., `id="city"`). In CSS, `.form-group` selects a class and `#city` selects an ID.

**`<div>` vs semantic tags:** Use meaningful HTML elements such as `<header>`, `<nav>`, `<main>`, `<section>`, and
`<footer>` when they describe the content. Use `<div>` when you simply need a general-purpose grouping container.

## 1. What Is HTML5?

**HTML5** is the modern version of HTML (HyperText Markup Language), used to **structure content on web pages**.

HTML5 introduced useful features that make websites more **meaningful, accessible, and easier to develop**, including:

- **Semantic elements** that describe the purpose of page content.
- **Improved forms** with new input types and built-in validation.
- **Multimedia elements** such as `<audio>` and `<video>`.

> **Remember:** HTML builds the **structure**, CSS controls the **appearance**, and JavaScript adds **interactivity**.

## 2. The HTML5 Document Structure

Start an HTML5 page with the following structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First HTML5 Page</title>
</head>
<body>
<h1>Welcome to HTML5</h1>
<p>This page uses HTML5.</p>
</body>
</html>
```

**Explanation:**

| Code                         | Purpose                                                       |
|------------------------------|---------------------------------------------------------------|
| `<!DOCTYPE html>`            | Tells the browser to use standards mode for an HTML document. |
| `<html lang="en">`           | Indicates that the page's language is English.                |
| `<meta charset="UTF-8">`     | Supports characters from many languages.                      |
| `<meta name="viewport" ...>` | Helps the page display correctly on mobile devices.           |
| `<title>`                    | Sets the text shown in the browser tab.                       |

## 3. Semantic HTML5 Elements

A **semantic element** clearly describes the role of its content to developers, browsers, and assistive technologies.

| Element     | Purpose                                                      |
|-------------|--------------------------------------------------------------|
| `<header>`  | Introductory content for a page or section.                  |
| `<nav>`     | A section of navigation links.                               |
| `<main>`    | The primary content of the page (typically one per page).    |
| `<section>` | A thematic group of related content, usually with a heading. |
| `<article>` | Self-contained content, such as a news post or blog article. |
| `<aside>`   | Related but secondary content, such as a sidebar.            |
| `<footer>`  | Closing information for a page or section.                   |

### Before and After: `<div>` vs. Semantic HTML

A `<div>` is a **generic container**. It is useful for grouping elements and styling them with CSS, but it does not
explain what the content means.

**Generic `<div>`:**

```html
<div class="header">
    <h1>BIS Student Club</h1>
</div>
<div class="navigation">
    <a href="#join">Join Us</a>
</div>
```

**Semantic HTML5:**

```html
<header>
    <h1>BIS Student Club</h1>
</header>
<nav>
    <a href="#join">Join Us</a>
</nav>
```

Both versions can look identical when styled with CSS, but semantic tags make the page structure clearer. They can help
**accessibility and search engines understand the page**; they do not automatically guarantee better SEO rankings.

> **When should you use `<div>`?** Use it when you need a container for layout or styling and no more meaningful
> semantic element fits.

## 4. HTML5 Improvements to Forms

HTML5 also made forms easier to create and validate.

### Newer Input Types

```html
<form action="/register" method="post">
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <label for="age">Age:</label>
    <input type="number" id="age" name="age" min="16" max="60">

    <label for="date">Workshop Date:</label>
    <input type="date" id="date" name="date">

    <button type="submit">Register</button>
</form>
```

- `type="email"` checks whether the value looks like an email address.
- `type="number"` allows numeric input; `min` and `max` specify allowed limits.
- `type="date"` lets users select a date (the interface depends on the browser).
- `required` prevents submitting the form while that field is empty.

**Important:** Browser validation improves the user experience, but applications still need **server-side validation**
when receiving submitted data.

## 5. Quick Review

1. What does `<!DOCTYPE html>` do?
2. What is the difference between `<div>` and `<section>`?
3. Which element should contain the page's main content?
4. Name two HTML5 input types.
5. Does HTML5 replace CSS or JavaScript? Why not?

**Key takeaway:** HTML5 provides clear page structure and improved form controls. Use **semantic tags for meaning** and
**`<div>` for generic grouping and layout**.

## 6. Quick review questions

1. What is the purpose of the `<form>` element?
2. What is the difference between `id` and `name` on an input?
3. Why do radio buttons in one group need the same `name`?
4. When should you use `<textarea>` instead of `<input type="text">`?
5. What is the benefit of wrapping form fields inside `<div class="form-group">`?
6. Can HTML alone save a form submission to a database? Why or why not?
