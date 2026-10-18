

https://github.com/user-attachments/assets/05cd4670-466a-49f5-a308-71f1b6ced463

# Book & Notes Vault

A personal reading tracker and book catalog built with vanilla HTML, CSS, and JavaScript. 
Built as an individual summative assignment exploring accessible design, regex validation, and state persistence without external frameworks or libraries.

- **Author:** Lilian
- **Theme:** Book & Notes Vault
- **Live GitHub Pages URL:** [https://kamikazililian236.github.io/Books-Vaults/](https://kamikazililian236.github.io/Books-Vaults/)
- **Demo Video (Unlisted):** [Paste Your YouTube / Drive Link Here]

---

# Project Overview & Design Wireframes

The app was planned with mobile-first accessibility in mind, helping readers log books, track reading milestones, filter by genre, and search using live regular expressions.

## Early Wireframe & UI Sketches
<!-- Put your sketch images inside the assets folder and link them here -->
![Wireframe Desktop & Mobile](./assets/wireframe-sketch.png)


# Core Features
- **Curated Reading Dashboard:** Real-time statistics including total books read, total pages completed, books added this week, and a spotlight showcase for your current favorite book.
- **My Library Catalog:** Clean records view with inline expandable book details (synopsis and cover art), status toggling (`To Read`, `Reading`, `Read`), and inline edit/delete actions.
- **Safe Regex Search & Highlighting:** Real-time search powered by dynamic regex compilation wrapped in `try/catch` to safely catch invalid patterns, with matched text wrapped in accessible `<mark>` tags.
- **Form Validation with Real-time Feedback:** Strict input checks ensuring clean database records with inline error messages.
- **Reading Goal Tracker with ARIA Live Announcements:** A reading target system that announces status changes politely (`aria-live="polite"`) when approaching the goal, and assertively (`aria-live="assertive"`) when the target is reached or exceeded.
- **Data Persistence & Portable Backup:** Automatically synchronizes state to `localStorage` with JSON export and import capabilities.
- **Responsive Layout:** Designed mobile-first with smooth transitions across mobile (360px), tablet (768px), and desktop (1024px+).



# Regex Catalog

| Rule | Validation / Target | Regular Expression Pattern | Example Valid Input | Example Rejected Input |
|------|---------------------|----------------------------|---------------------|------------------------|
| **1. Title / Author** | Disallows leading/trailing spaces & collapse double spaces | `/^\S(?:.*\S)?$/` | `Clean Architecture` | ` Clean Architecture ` |
| **2. Page Count** | Positive integers only (> 0, no decimals) | `/^[1-9]\d*$/` | `432` | `-5`, `0`, `12.5` |
| **3. Date Added** | Strict ISO calendar format (YYYY-MM-DD) | `/^\d{4}-(0[1-9]\|1[0-2])-(0[1-9]\|[12]\d\|3[01])$/` | `2026-10-10` | `2026/10/10`, `10-10-2026` |
| **4. Tag / Category** | Letters, spaces, and hyphens | `/^[A-Za-z]+(?:[ -][A-Za-z]+)*$/` | `Web Dev`, `Sci-Fi` | `Tag@#$`, `Tech-` |
| **5. Advanced Regex** | Back-reference detecting repeated words/surnames | `/\b(\w+)\s+\1\b/i` | Catches `"Martin Martin"`, `"The The"` | Clean single words |



# Keyboard Navigation Map

The app is fully operable without a mouse:
- `Tab`: Move forward through interactive links, form inputs, and buttons.
- `Shift + Tab`: Move backward through elements.
- `Enter` / `Space`: Activate buttons, toggles, and drawer items.
- `Escape`: Instantly close the mobile navigation drawer.
- Visible focus rings (`:focus-visible`) ensure clear orientation across all elements.



# Accessibility (a11y) Notes
- **Semantic Landmarks:** Proper document structure using `<header>`, `<nav>`, `<main>`, `<aside>`, `<section>`, and `<footer>`.
- **Form Labels:** Every `<input>` and `<select>` is explicitly bound to a `<label for="...">`.
- **Screen Reader Announcements:** The reading milestone tracker uses `role="status"` and `aria-live` regions to announce goal updates.
- **Skip Link:** A visible skip-to-content link is present at the top of the page.
- **Contrast:** High contrast text on warm background passing WCAG AA standards.



# How to Run the Automated Unit Tests
1. Download or clone this repository to your machine.
2. Double-click **`tests.html`** or open it inside Chrome, Firefox, or Edge.
3. The test suite will automatically execute unit assertions for all regex validation rules, safe compiler handling, and dashboard statistics calculations.
