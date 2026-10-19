# Section 2: HTML Document Structure and Text Formatting

**Course:** BIS --- HTML & CSS Basics\
**Estimated time:** 10--15 minutes\
**Level:** Beginner

## Learning objectives

By the end of this lesson, you should be able to:

-   Describe the basic structure of an HTML document.
-   Explain the roles of `<html>`, `<head>`, `<title>`, and `<body>`.
-   Use heading tags (`<h1>` to `<h6>`) and paragraphs.
-   Format text using bold, italic, and underline elements.
-   Distinguish between block-level and inline elements.

------------------------------------------------------------------------

## 1. Basic HTML tags

### `<html>`

**Definition:** The root element that contains the entire HTML document.
The `lang` attribute can identify the page's language.

``` html
<html lang="en">
  <!-- The page's HTML goes here -->
</html>
```

### `<head>`

**Definition:** Contains information *about* the page, such as its
title, character encoding, and links to CSS files. Most of this
information does not appear in the main page content.

``` html
<head>
  <meta charset="UTF-8">
  <title>My First Web Page</title>
</head>
```

### `<title>`

**Definition:** Sets the page title shown in the browser tab. It belongs
inside `<head>`, not inside `<body>`.

``` html
<title>Student Club Page</title>
```

### `<body>`

**Definition:** Contains the content people see on the web page, such as
headings, paragraphs, and other page elements.

``` html
<body>
  <h1>Welcome!</h1>
  <p>This is my first web page.</p>
</body>
```

### A complete HTML document

These tags work together. A typical HTML page starts with
`<!DOCTYPE html>`, which tells the browser to use modern HTML standards.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My First Web Page</title>
</head>
<body>
  <h1>Welcome to My Page</h1>
  <p>I am learning HTML.</p>
</body>
</html>
```

------------------------------------------------------------------------

## 2. Heading tags: `<h1>` to `<h6>`

**Definition:** Heading tags organize content into a clear hierarchy.
`<h1>` is the main heading, while `<h2>` through `<h6>` represent nested
levels of headings. Browsers usually display lower-level headings in
smaller text, but headings should be chosen for structure---not just for
their size.

``` html
<h1>Campus Community</h1>
<h2>Clubs and Activities</h2>
<h3>Art Club</h3>
<h4>Weekly Meetings</h4>
<h5>What to Bring</h5>
<h6>Additional Notes</h6>
```

**Tip:** Most short pages only need an `<h1>` and a few `<h2>` or `<h3>`
headings. Use heading levels in a logical order.

------------------------------------------------------------------------

## 3. Paragraphs: `<p>`

**Definition:** The `<p>` tag marks a paragraph of text. Browsers
normally add space before and after paragraphs.

``` html
<p>Our campus offers activities for students with different interests.</p>
<p>Everyone is welcome to suggest a new activity.</p>
```

Use a new `<p>` element for a separate paragraph instead of adding many
spaces manually.

------------------------------------------------------------------------

## 4. Bold, italic, and underline

### Bold or strong importance: `<strong>`

**Definition:** `<strong>` marks text as important. Browsers usually
display it in bold.

``` html
<p><strong>Registration closes on Friday.</strong></p>
```

### Italic or emphasis: `<em>`

**Definition:** `<em>` marks text that should receive emphasis. Browsers
usually display it in italic.

``` html
<p>You can <em>also</em> join the club online.</p>
```

### Underline: `<u>`

**Definition:** `<u>` marks text with a visual underline. Use it
sparingly because underlined text can be mistaken for a link.

``` html
<p>Please read the <u>meeting guidelines</u>.</p>
```

**Note:** You may also see `<b>` and `<i>`. They are valid HTML tags for
drawing attention to text visually, while `<strong>` and `<em>`
communicate importance or emphasis in the meaning of the content.

------------------------------------------------------------------------

## 5. Inline tags vs. block-level tags

HTML elements behave in different ways by default.

### Block-level behavior

A block-level element typically starts on a new line and takes up the
available width.

Examples from this lesson: `<h1>`--`<h6>` and `<p>`.

``` html
<h2>Upcoming Events</h2>
<p>Join us for a campus clean-up.</p>
<p>Bring a reusable water bottle if you have one.</p>
```

Each heading or paragraph appears as its own block.

### Inline behavior

An inline element typically stays within the current line of text and
takes up only the space it needs.

Examples from this lesson: `<strong>`, `<em>`, and `<u>`.

``` html
<p>Everyone is <strong>welcome</strong>, and beginners are <em>encouraged</em> to join.</p>
```

The formatted words stay inside the paragraph instead of starting
separate lines.

**Remember:** These are the elements' default behaviors. CSS can change
how an element is displayed.

------------------------------------------------------------------------

# Practical Activity: Create an Inclusive Campus Club Page

**Time limit:** 15 minutes\
**Goal:** Build a simple page inviting students to join a campus club.
You can choose any club that interests you---such as coding, reading,
gaming, sports, art, accessibility, or environmental action.

## Instructions

1.  Create a file named `club-page.html`.
2.  Add the basic HTML structure: `<!DOCTYPE html>`, `<html>`, `<head>`,
    `<title>`, and `<body>`.
3.  Add one `<h1>` for the page title.
4.  Use at least two heading levels from `<h2>` to `<h6>` to organize
    the information.
5.  Write two paragraphs using `<p>`.
6.  Use `<strong>` for an important detail, `<em>` for emphasis, and
    `<u>` to underline a short phrase.
7.  Include at least one inline element inside a paragraph and at least
    two block-level elements.
8.  Save the file and open it in a browser.

## Starter code

Replace the example club and details with your own ideas. Keep the page
respectful and welcoming to students with different backgrounds,
abilities, schedules, and levels of experience.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Campus Club</title>
</head>
<body>
  <h1>Welcome to the Campus Art Club</h1>

  <p>We make art, share ideas, and learn from one another.</p>

  <h2>Who Can Join?</h2>
  <p>
    <strong>Everyone is welcome.</strong>
    You do not need previous experience, and
    <em>your ideas matter</em>.
  </p>

  <h3>When We Meet</h3>
  <p>We meet on Thursdays after class. Check the campus noticeboard for updates.</p>

  <p>Please read the <u>club guidelines</u> before your first meeting.</p>
</body>
</html>
```

## Completion checklist

Before you finish, check each item:

-   [ ] My page includes `<!DOCTYPE html>`, `<html>`, `<head>`,
    `<title>`, and `<body>`.
-   [ ] I used at least one heading and two paragraphs.
-   [ ] I used `<strong>`, `<em>`, and `<u>`.
-   [ ] I used inline elements inside a paragraph.
-   [ ] I can identify the block-level elements on my page.
-   [ ] I changed the example to reflect a club or interest of my
    choice.

## Quick review

1.  Which tag controls the text shown in the browser tab?
2.  Which tag contains the visible page content?
3.  Why should headings be used in a logical order?
4.  In the example below, which elements are inline?

``` html
<p>Learning is <strong>for everyone</strong> and <em>takes practice</em>.</p>
```

**Answers:** 1. `<title>` 2. `<body>` 3. To organize content into a
meaningful hierarchy 4. `<strong>` and `<em>`
