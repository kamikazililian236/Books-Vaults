# Book & Notes Vault

A personal reading tracker and book catalog built with vanilla HTML, CSS and JavaScript (no frameworks). Built as an individual summative assignment (Building Responsive UI).

- **Author:** Lilian
- **Theme:** Book & Notes Vault
- **Live GitHub Pages URL:** [https://kamikazililian236.github.io/Books-Vaults/](https://kamikazililian236.github.io/Books-Vaults/)
- **Demo Video (Unlisted):** [https://youtu.be/eXt_e5BpbW8](https://youtu.be/eXt_e5BpbW8)

---

## Project Overview

Book & Notes Vault helps a reader keep a quiet space for every book: log books, mark what is being read, search the collection, and back up the data as a JSON file.

## Wireframes & UI Sketches

<img width="850" height="1280" alt="Wireframe 1" src="https://github.com/user-attachments/assets/a3ca7377-7ddd-469d-9d83-9dbf1afe59b7" />
<img width="916" height="1280" alt="Wireframe 2" src="https://github.com/user-attachments/assets/35ef8fa0-60fd-419e-a10f-644bb83741c9" />
<img width="838" height="1280" alt="Wireframe 3" src="https://github.com/user-attachments/assets/a7f8495c-ec4a-4fea-a528-3a8c282383a2" />

---

## Pages

| Page | What it does |
|------|--------------|
| **Home** | Welcome screen with a spotlight card showing the book currently being read |
| **Dashboard** | Current read, number of books read, books added this week, and a favorite book showcase card |
| **My Library** | Table of all books (cards on mobile) with search, sort, tag and status filters |
| **Add / Edit Book** | Form to add a new book or edit an existing one, with optional cover upload |
| **Settings** | Save an annual reading goal and a personal reading note |
| **About** | Purpose of the app and who made it |

## Features

- **Library catalog:** 10 seeded books, with inline expandable details (cover and synopsis) per book.
- **Add, edit and delete:** Edit fills the form with the book's data. Delete asks for confirmation first.
- **Status toggle:** Click a book's status to cycle `To Read` → `Reading` → `Read`.
- **Search with optional regex:** Searches title, author and tag. Two checkboxes switch on **Regex filter** and **Case sensitive**.
- **Filters and sorting:** Filter by tag and by status. Sort by title.
- **Cover upload:** Choose an image from your device; it is stored with the book.
- **Persistence:** All changes are saved automatically to `localStorage`, so data stays after a refresh.
- **JSON export / import:** Export downloads `vault_books_export.json`. Import loads a JSON file and rejects files that are not a list of books.
- **Responsive layout:** Table on desktop, card list on mobile, with a slide-out navigation drawer.
- **Navigation:** Back button, breadcrumb, and page links that work with the browser's back button.

## Data Model

Each book is stored like this:

```json
{
  "id": 1,
  "title": "The Midnight Library",
  "author": "Matt Haig",
  "pages": 288,
  "tag": "Fiction",
  "date": "2026-10-08",
  "status": "Reading",
  "isFavorite": false,
  "cover": "./assets/the-midnight-library.jpg",
  "coverImage": "./assets/the-midnight-library.jpg",
  "synopsis": "Between life and death there is a library where shelves go on forever."
}
```

`seed.json` holds the starting collection. If nothing is saved yet, the app loads these books.

---

## Regex Catalog

The search box compiles the typed pattern with `new RegExp(...)` inside a `try/catch`, so an invalid pattern never crashes the app. It simply shows no results. Turn on **Regex filter** to use these:

| Pattern | What it finds | Example match |
|---------|---------------|---------------|
| `^The` | Titles, authors or tags that start with "The" | The Book Thief, The Island |
| `Drama\|Mystery` | Either word (the bar means OR) | Books tagged Drama or Mystery |
| `^fiction$` | An exact tag | Fiction |
| `\b(\w+)\s+\1\b` | **Advanced:** a repeated word (back-reference) | "The The" |
| `(` | Invalid pattern (edge case) | No results, no crash |

With **Case sensitive** on, `^the` finds nothing because the titles start with a capital T.

## Keyboard Map

All controls are native buttons, links, inputs and dropdowns, so the app can be used without a mouse:

| Key | Action |
|-----|--------|
| `Tab` / `Shift + Tab` | Move forward / backward through buttons, links and form fields |
| `Enter` | Press a button or link (open the menu, open My Library, View, Edit) |
| `Space` | Tick a checkbox (Regex filter, Case sensitive, Favorite) |
| `Arrow keys` | Change the choice in the Sort, Tag and Status dropdowns |

## Accessibility Notes

- Semantic structure with `<header>`, `<nav>`, `<main>`, `<section>` and `<aside>`, and `lang="en"` on the page.
- Form fields use `<label for="...">` bound to their inputs.
- Icon-only buttons have `aria-label` text (back, menu, close).
- Delete asks for confirmation to prevent accidents.

## How to Run

1. Clone or download this repository.
2. Open the folder in VS Code and run **Live Server** on `index.html`, or open the live site above.
3. To run the tests, open `tests.html` in a browser.

## Project Structure

```
index.html      main page
Styles/         base.css, layout.css, components.css
scripts/        main.js
assets/         book covers and images
seed.json       10 starting books
tests.html      browser tests
```

## Planned Improvements

- Inline error messages and regex validation rules on the Add Book form.
- Highlight search matches with `<mark>`.
- Skip-to-content link and `aria-live` messages for the reading goal.
- Close the navigation drawer with the `Escape` key.
- Split `main.js` into modules (storage, validation, search, UI).
