````
# Section 6 — HTML Forms, `<div>`, HTML5, and JavaScript

**Topics:** HTML forms, form controls, `action` and HTTP methods (GET/POST), the `<div>` element, HTML5, and the `<script>` tag

## 1. Learning objectives

By the end of this section, you should be able to:

- Explain why websites use forms.
- Create a form using inputs, labels, buttons, dropdowns, and text areas.
- Use common form attributes correctly.
- Group HTML elements with `<div>` and style those groups with CSS classes.
- Explain how `action`, `method="get"`, and `method="post"` work.
- Add basic JavaScript to an HTML page with the `<script>` tag.
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

**We will explain `action`, GET, and POST in more detail in Section 3.**

> **Important:** HTML can display and submit a form, but it does not automatically save information or create user
> accounts. A real submission requires a working server or other form-handling service. The examples in this lesson are
> for front-end practice only.

---

## 3. Form `action` and HTTP methods (`GET` / `POST`)

When a user clicks a submit button, the browser creates an **HTTP request** to send form values to a destination.

- **`action`** answers: **Where** will the form be submitted?
- **`method`** answers: **How** will the form data be sent?
- Each form input needs a **`name`** attribute to be included in the submitted data.

### 3.1 The `action` attribute

`action` specifies the URL or server route that receives the submission.

```html
<form action="/register" method="post">
    <input type="text" name="studentName" required>
    <button type="submit">Register</button>
</form>
```

Here, `/register` is the destination. It is **only an example**: the form works with real data only when a server handles that URL.

- `action="/search"`: submits to the `/search` path on the same website.
- `action="https://example.com/register"`: submits to the specified URL (example only).
- If `action` is omitted, the form normally submits to the current page's URL.
- `action="#"` is often used as a placeholder in classroom demos; it does **not** save the data.

### 3.2 `method="get"` — Data in the URL

`GET` is commonly used for **searches and filters**. The browser usually adds named form values to the URL as a query string.

```html
<form action="/search" method="get">
    <label for="query">Search:</label>
    <input type="text" id="query" name="q" required>
    <button type="submit">Search</button>
</form>
```

If the user types `html`, the resulting URL might look like:

```text
https://example.com/search?q=html
```

Here, `q` comes from the input's **`name`**, and `html` is the submitted value. The actual page requires a working `/search` route.

### 3.3 `method="post"` — Data in the request body

`POST` is commonly used for **registrations, login forms, and sending or updating information**. Normal HTML form values are sent in the HTTP request body, not appended to the URL as GET query parameters.

```html
<form action="/register" method="post">
    <label for="fullName">Full name:</label>
    <input type="text" id="fullName" name="fullName" required>

    <label for="emailAddress">Email:</label>
    <input type="email" id="emailAddress" name="email" required>

    <button type="submit">Register</button>
</form>
```

**Important:** POST does **not** automatically make form data secure or encrypted. Use **HTTPS** when sending sensitive information. Both GET and POST require server-side handling if you want to store or process the data.

### 3.4 GET vs POST at a glance

| Feature | GET | POST |
|---------|-----|------|
| Common purpose | Search or retrieve information | Submit, create, or update information |
| Where the form values go | Usually in the URL query string | Usually in the request body |
| Easy to bookmark a search | Yes | Not in the same way |
| Suitable for passwords | No | With HTTPS and proper server-side security |
| Needs a server to process data | Yes, for a real application | Yes, for a real application |

> **Remember:** `action` = **where** to send; `method` = **how** to send; `name` = **the key** for each submitted value.

---

## 4. Form elements

### 4.1 `<label>` — Describe an input

A label tells the user what to enter. The `for` attribute should match the input's `id` so clicking the label focuses
that input.

```html
<label for="studentName">Student name:</label>
<input type="text" id="studentName" name="studentName">
```

### 4.2 `<input>` — Collect short values

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

### 4.3 Radio buttons — Choose one

Radio inputs belong to the same group when they share a `name`. Give each option a different `value`.

```html
<input type="radio" id="first" name="year" value="first" required>
<label for="first">First year</label>

<input type="radio" id="second" name="year" value="second">
<label for="second">Second year</label>
```

### 4.4 Checkboxes — Tick an option

```html
<input type="checkbox" id="updates" name="updates" value="yes">
<label for="updates">Send me event updates</label>
```

A checkbox is usually submitted only when it is checked.

### 4.5 `<select>` and `<option>` — Dropdown list

```html
<label for="track">Choose a track:</label>
<select id="track" name="track" required>
    <option value="">-- Select a track --</option>
    <option value="html">HTML</option>
    <option value="css">CSS</option>
</select>
```

### 4.6 `<textarea>` — Longer messages

Use `<textarea>` for multi-line input. Its starting text goes **between the tags**, not in a `value` attribute.

```html
<label for="message">Your message:</label>
<textarea id="message" name="message" rows="4" placeholder="Write here..."></textarea>
```

### 4.7 `<button>` — Submit the form

```html
<button type="submit">Register</button>
```

`type="submit"` submits the form. `type="button"` is a regular button, generally used with JavaScript.

---

## 5. What is a `<div>`?

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

## 6. What Is HTML5?

**HTML5** is the modern version of HTML (HyperText Markup Language), used to **structure content on web pages**.

HTML5 introduced useful features that make websites more **meaningful, accessible, and easier to develop**, including:

- **Semantic elements** that describe the purpose of page content.
- **Improved forms** with new input types and built-in validation.
- **Multimedia elements** such as `<audio>` and `<video>`.

> **Remember:** HTML builds the **structure**, CSS controls the **appearance**, and JavaScript adds **interactivity**.

## 7. The HTML5 Document Structure

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

## 8. Semantic HTML5 Elements

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

### 8.1 Before and After: `<div>` vs. Semantic HTML

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

## 9. HTML5 Improvements to Forms

HTML5 also made forms easier to create and validate.

### 9.1 Newer Input Types

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

## 10. The `<script>` tag — Adding JavaScript to HTML

HTML gives the page its **structure**, CSS gives it **style**, and JavaScript can make it **interactive**. The `<script>` tag tells the browser to load or run JavaScript code.

### 10.1 Internal JavaScript

Write JavaScript **inside** a `<script>` tag. For a simple page, putting the script near the end of `<body>` means the HTML elements above it already exist when the script runs.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Script Example</title>
</head>
<body>
    <h1>BIS Student Club</h1>
    <p id="message">Welcome!</p>
    <button type="button" id="greetBtn">Click me</button>

    <script>
        document.getElementById("greetBtn").addEventListener("click", function () {
            document.getElementById("message").textContent = "Hello, BIS students!";
        });
    </script>
</body>
</html>
```

**What happens?** Clicking the button changes the paragraph text **without reloading the page**.

- `document.getElementById("greetBtn")` finds the button using its `id`.
- `addEventListener("click", ...)` runs code when the button is clicked.
- `textContent` changes the text inside an element.

### 10.2 External JavaScript

You can keep JavaScript in a separate `.js` file and connect it using the `src` attribute.

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>External JavaScript</title>
    <script src="script.js" defer></script>
</head>
<body>
    <h1>BIS Student Club</h1>
    <p id="message">Welcome!</p>
    <button type="button" id="greetBtn">Click me</button>
</body>
</html>
```

**script.js** (in the same folder as `index.html`)

```javascript
document.getElementById("greetBtn").addEventListener("click", function () {
    document.getElementById("message").textContent = "Hello, BIS students!";
});
```

- `src="script.js"` points to the external JavaScript file.
- `defer` makes this external script run after the HTML has been parsed.
- Use **either** JavaScript inside `<script>...</script>` **or** an external script through `src` for that tag.

> **Form tip:** `type="submit"` submits a form using its `action` and `method`. A button with `type="button"` does **not** submit the form automatically and is useful for JavaScript demos.

---

## 11. HTML5 quick review

1. What does `<!DOCTYPE html>` do?
2. What is the difference between `<div>` and `<section>`?
3. Which element should contain the page's main content?
4. Name two HTML5 input types.
5. Does HTML5 replace CSS or JavaScript? Why not?

**Key takeaway:** HTML5 provides clear page structure and improved form controls. Use **semantic tags for meaning** and
**`<div>` for generic grouping and layout**.

## 12. Forms, HTTP, and JavaScript review questions

1. What is the purpose of the `<form>` element?
2. What is the difference between `id` and `name` on an input?
3. Why do radio buttons in one group need the same `name`?
4. When should you use `<textarea>` instead of `<input type="text">`?
5. What is the benefit of wrapping form fields inside `<div class="form-group">`?
6. Can HTML alone save a form submission to a database? Why or why not?
7. What does the `action` attribute specify?
8. Which method normally places submitted form values in the URL: GET or POST?
9. Does POST encrypt submitted values by itself?
10. What is the difference between `<script>...</script>` and `<script src="script.js" defer></script>`?
11. When should you use `type="button"` instead of `type="submit"`?

````

---

## 13. Practice exercise — BIS Workshop Registration (15 minutes)

Create an **`index.html`** page with a workshop registration form and a JavaScript greeting button.

1. Add a heading: **BIS Workshop Registration**.
2. Place your form inside a `<div class="form-container">`.
3. Include labeled fields for **student name**, **email**, and **workshop track** (a dropdown with HTML and CSS options).
4. Give each input a `name` and add `required` where appropriate.
5. Use `<form action="/register" method="post">` and a **Register** submit button. The URL is an example; no server is provided in this exercise.
6. Outside the form, add a **Say Hello** button with `type="button"` and a paragraph with `id="greeting"`.
7. Use an internal `<script>` tag to change the paragraph to **"Welcome to the BIS workshop!"** when the button is clicked.
8. Add a little CSS to give the form container some padding, a border, and spacing between fields.

**Try this after finishing:** Make a separate search form using `action="/search"` and `method="get"`. Observe the query string when it is submitted (the destination page may not exist in your practice setup).

**Self-check:** Your labels connect to inputs, the submit button uses the form's `action`/`method`, and clicking **Say Hello** updates text without submitting the form.
