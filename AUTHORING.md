# Authoring Guide — Adding a Learning Path

A complete, step-by-step walkthrough for adding your own learning path to the CCA
Coding Club **Learn** pages. No coding on the website is required — you only add
files to **this** repo and push.

If you just want the field reference, see [README.md](README.md). This document
is the friendly, start-to-finish version.

## Contents

1. [How it all fits together](#1-how-it-all-fits-together)
2. [Before you start](#2-before-you-start)
3. [Step 1 — Plan your path](#step-1--plan-your-path)
4. [Step 2 — Register the path in `paths.json`](#step-2--register-the-path-in-pathsjson)
5. [Step 3 — Create the path folder and `path.json`](#step-3--create-the-path-folder-and-pathjson)
6. [Step 4 — Position your nodes on the canvas](#step-4--position-your-nodes-on-the-canvas)
7. [Step 5 — Write a lesson (`node.md`)](#step-5--write-a-lesson-nodemd)
8. [Step 6 — Add a challenge](#step-6--add-a-challenge)
9. [Step 7 — Preview it locally](#step-7--preview-it-locally)
10. [Step 8 — Commit and push](#step-8--commit-and-push)
11. [Hosting a path in a different repo](#hosting-a-path-in-a-different-repo)
12. [Customizing the look](#customizing-the-look)
13. [Troubleshooting](#troubleshooting)
14. [Final checklist](#final-checklist)

---

## 1. How it all fits together

A learning path is a small graph of **nodes**. Each node is either a **lesson**
or a **challenge**. Nodes are connected by **edges** that define the order — a
node stays *locked* until everything pointing to it is complete.

Three kinds of files describe all of this:

```text
paths.json                 ← the master list (one entry per path → one card)
<path-id>/
  path.json                ← the graph: which nodes exist, their order & layout
  <node-id>/
    node.md                ← the actual lesson/challenge content (Markdown)
```

The flow a learner sees:

```text
Learn page          Path page                 Node page
(paths.json)   →    (<path-id>/path.json)  →   (<path-id>/<node-id>/node.md)
 path cards         the SVG node graph         the lesson, "Mark complete"
```

Progress is saved in the learner's browser (localStorage), keyed by your path id
and node ids — which is why **ids must never change once published**.

---

## 2. Before you start

You'll need:

- **Write access** to this repo (or fork it and open a pull request).
- Comfort editing **JSON** and **Markdown** in a text editor.
- That's it. No build step, no framework.

Two rules that save pain later:

- **Never rename an `id`** (path id or node id) after people have started a path —
  it silently wipes their saved progress.
- **Never delete `.nojekyll`** from the repo root. Without it, GitHub turns your
  `node.md` files into HTML and the site can't load them.

---

## Step 1 — Plan your path

Sketch it on paper first. Decide:

1. **The path:** a title, a one-line description, and an emoji icon
   (e.g. 🐍 Python, 🌿 Git, 🎮 Game Dev).
2. **The nodes:** a short list of lessons, in order, ending in a challenge or two.
3. **The order:** which nodes must be done before others unlock.

Example plan for a path called **`html-basics`**:

| Order | Node id      | Type      | Title              |
| ----- | ------------ | --------- | ------------------ |
| 1     | `intro`      | lesson    | What is HTML?      |
| 2     | `tags`       | lesson    | Tags & Elements    |
| 3     | `links`      | lesson    | Links & Images     |
| 4     | `build-page` | challenge | Build a Profile    |

Pick short, lowercase, hyphenated ids (`build-page`, not `Build Page`).

---

## Step 2 — Register the path in `paths.json`

`paths.json` (in the repo root) is an array. Add one object for your path. This
is what controls the **card** on the Learn page.

```json
[
  {
    "id": "git-basics",
    "title": "Git Basics",
    "icon": "🌿",
    "description": "Learn version control: repositories, commits, and your first contribution.",
    "nodeCount": 3
  },
  {
    "id": "html-basics",
    "title": "HTML Basics",
    "icon": "🌐",
    "description": "Build your first web page from scratch.",
    "nodeCount": 4
  }
]
```

| Field         | Required | What it does                                                        |
| ------------- | -------- | ------------------------------------------------------------------- |
| `id`          | yes      | Folder name + URL slug. Lowercase, hyphenated. **Never change it.** |
| `title`       | yes      | Heading on the card and path page.                                  |
| `icon`        | no       | An emoji. Defaults to 📘 if you leave it out.                       |
| `description` | no       | One-line blurb on the card.                                         |
| `nodeCount`   | no       | Number shown in the card's "0 / N complete" label. Match your node count. |
| `source`      | no       | Only if the content lives in a *different* repo — see [below](#hosting-a-path-in-a-different-repo). |

> Watch the commas — `paths.json` is strict JSON. No trailing comma after the
> last entry, and every string in double quotes.

---

## Step 3 — Create the path folder and `path.json`

Make a folder named exactly your `id` (e.g. `html-basics/`) and put a `path.json`
inside it. This file defines the **graph**: the nodes and the edges between them.

```json
{
  "id": "html-basics",
  "title": "HTML Basics",
  "nodes": [
    { "id": "intro",      "type": "lesson",    "title": "What is HTML?",   "x": 380, "y": 110 },
    { "id": "tags",       "type": "lesson",    "title": "Tags & Elements", "x": 380, "y": 300 },
    { "id": "links",      "type": "lesson",    "title": "Links & Images",  "x": 380, "y": 490 },
    { "id": "build-page", "type": "challenge", "title": "Build a Profile", "x": 380, "y": 690 }
  ],
  "edges": [
    { "from": "intro", "to": "tags" },
    { "from": "tags",  "to": "links" },
    { "from": "links", "to": "build-page" }
  ]
}
```

**Nodes** — each one needs:

| Field   | What it does                                                          |
| ------- | -------------------------------------------------------------------- |
| `id`    | Matches the node's folder name. Used in the URL and in progress.     |
| `type`  | `"lesson"` (diamond shape) or `"challenge"` (rounded rectangle).     |
| `title` | Shown inside the node on the graph.                                  |
| `x`,`y` | Pixel position on the canvas (next step explains how to choose them). |

**Edges** — each `{ "from": A, "to": B }` means *"B unlocks when A is complete."*

- A node with **no incoming edges** is available from the very start.
- A node with several incoming edges unlocks only when **all** of them are done.
- This lets you do branches and merges, not just straight lines.

```text
        intro                     intro
          |              vs       /     \
        tags                  variables  loops
          |                       \     /
        links                    challenge   ← needs BOTH done
```

---

## Step 4 — Position your nodes on the canvas

The graph is drawn on a fixed **760 (wide) × 810 (tall)** canvas. `x` grows to
the right, `y` grows **downward**. The horizontal centre is **x = 380**.

Node sizes (so you can space them without overlap):

| Type        | Shape   | Half-width | Half-height |
| ----------- | ------- | ---------- | ----------- |
| `lesson`    | diamond | 75         | 55          |
| `challenge` | rect    | 110        | 28          |

A safe, good-looking recipe:

- **Single column:** keep every node at `x: 380`, and step `y` by ~180–200
  (e.g. 110, 300, 490, 690). This is the easiest layout and always looks tidy.
- **A branch:** put the two siblings at `x: 200` and `x: 560`, same `y`.
- **Keep a margin:** stay roughly within `x` 120–640 and `y` 70–760 so labels
  and lock/check icons don't get clipped.

You don't need to be exact — open the path locally (Step 7) and nudge the numbers
until it looks right.

---

## Step 5 — Write a lesson (`node.md`)

Inside your path folder, make one folder per node (named by node id), each with a
`node.md`:

```text
html-basics/
  path.json
  intro/
    node.md
  tags/
    node.md
  ...
```

`node.md` is plain **Markdown**. Everything standard works — headings, lists,
**bold**, *italics*, links, tables, blockquotes, images, and fenced code blocks
with syntax highlighting:

````markdown
---
title: What is HTML?
type: lesson
---

# What is HTML?

**HTML** is the language that describes the structure of a web page.

## A first tag

```html
<h1>Hello, world!</h1>
```

- Tags usually come in pairs: an opening `<h1>` and a closing `</h1>`.
- The text between them is what shows up on the page.

> Tip: every page you've ever visited is built out of tags like these.
````

A few things to know:

- The block between the first pair of `---` lines is **front matter**. It's
  **ignored** by the renderer — use it for your own notes. The Lesson/Challenge
  badge and title actually come from `path.json`, not from here.
- Code fences get colored automatically. Add the language after the opening
  backticks (` ```html `, ` ```python `, ` ```bash `) for correct highlighting.
- **Images must use a full URL** (e.g. a link to an image hosted on GitHub or
  elsewhere). Relative image paths won't resolve, because the Markdown is
  rendered on the website, not in this repo.
- End lessons by telling the reader to hit **Mark as Complete** to unlock the
  next node.

Repeat for every lesson node.

---

## Step 6 — Add a challenge

A **challenge** is just a node with `"type": "challenge"` in `path.json`. It
renders as a rectangle instead of a diamond and gets a yellow "Challenge" badge.
The `node.md` is written exactly the same way — the convention is to give the
reader a concrete task and a way to check their work:

````markdown
---
title: Build a Profile
type: challenge
---

# Challenge: Build a Profile Page

Put it all together and build a tiny web page about yourself.

## Your task

1. Create a file called `me.html`.
2. Add a heading with your name.
3. Add a short paragraph about a hobby.
4. Add a link to your favourite website.

## Success looks like

A page that shows your name as a big heading, a sentence below it, and a
clickable link.

## Hints

- Forgot how links work? Revisit *Links & Images*.
- Open the file in your browser to see it render.
````

There's nothing special to "turn on" — `type: "challenge"` is the only
difference from a lesson.

---

## Step 7 — Preview it locally

The pages fetch your files over HTTP, so you can't just double-click the HTML —
you need to serve both this content repo and the website over `localhost`.

1. **Serve this content repo** — from this folder:
   ```bash
   python -m http.server 8001
   ```
2. **Point the site at your local content** — in the website repo, open
   `js/base/learn-config.js` and temporarily set:
   ```js
   var LEARN_CONTENT_BASE = 'http://localhost:8001';
   ```
3. **Serve the website** — from the website repo root:
   ```bash
   python -m http.server 8000
   ```
4. Open **`http://localhost:8000/pages/learn.html`** and click your new card.

Walk the whole flow: card → graph → a lesson → **Mark as Complete** → confirm the
next node unlocks and a ✓ appears. Open the browser's **DevTools → Console**; it
should be clean (no "Could not load…" errors).

> Remember to change `LEARN_CONTENT_BASE` back to the real Pages URL before
> committing the website repo.

---

## Step 8 — Commit and push

Once it looks right:

```bash
git add paths.json html-basics/
git commit -m "Add HTML Basics learning path"
git push
```

GitHub Pages redeploys automatically (usually within a minute). Reload the live
Learn page and your path is there — no website changes needed.

---

## Hosting a path in a different repo

Sometimes a course already has its own repo and you don't want to copy its files
here. Instead of creating a folder, give the `paths.json` entry a **`source`**:

```json
{
  "id": "discord-python",
  "title": "Discord with Python",
  "icon": "🐍",
  "description": "Build a Discord bot in Python.",
  "source": "CCA-Coding-Club/Discord-with-Python"
}
```

The referenced repo must:

- Have **GitHub Pages enabled** and a **`.nojekyll`** file at its publish root.
- Contain `path.json` and `<node-id>/node.md` **at its root** (the repo root acts
  as the path folder — there's no extra `<path-id>/` level).

`source` formats (note: no `@branch` — Pages publishes one configured branch):

| `source` value          | Content is loaded from                          |
| ----------------------- | ----------------------------------------------- |
| `owner/repo`            | `https://owner.github.io/repo`                  |
| `owner/repo:subfolder`  | `https://owner.github.io/repo/subfolder`        |
| `https://…` (full URL)  | used exactly as written                         |

This is the whole point of the redesign: a new path is always *just an entry in
`paths.json`* — its content can live here or anywhere else, and the website never
has to change.

---

## Customizing the look

Content lives in **this** repo. The **appearance** lives in the website repo
(`CCA-Coding-Club.github.io`). You only need to touch these if you want to
restyle the Learn pages — adding paths never requires it. Edit, save, reload.

### Brand colors (affects the whole site)

`css/base/variables.css` holds the design tokens:

```css
--accent: #3b82f6;     /* links, progress bars, available nodes, hovers */
--bg-card: #1a1d2e;    /* card and panel background */
--text: #e2e8f0;       /* main text */
--text-dim: #94a3b8;   /* secondary text */
--radius: 8px;         /* corner roundness */
```

Changing `--accent` recolors a lot at once (it's the site-wide highlight color).

### Path cards & node-page layout

`css/pages/learn.css` controls:

- `.path-card`, `.path-icon`, `.paths-grid` — the cards on the Learn page and how
  they wrap into a grid.
- `.progress-bar` / `.progress-fill` — the little progress meter on each card.
- `.node-type-badge` and `.node-type-badge.challenge` — the Lesson/Challenge
  badge colors.
- `.btn-complete` — the green "Mark as Complete" button.

### The node graph (diamonds, rectangles, edges, colors)

`css/components/graph.css` controls the SVG graph's *colors* per state:

```css
.graph-node.locked    .node-shape { fill: #2a2d3e; stroke: #3a3f55; }
.graph-node.available .node-shape { fill: #1d4ed8; stroke: #3b82f6; }
.graph-node.complete  .node-shape { fill: #15803d; stroke: #22c55e; }
.graph-edge           { stroke: #3a3f55; }   /* connector lines */
.graph-node .node-check { fill: #4ade80; }   /* the ✓ on finished nodes */
```

To change the node **sizes or the canvas dimensions**, edit the geometry
constants at the top of `js/pages/learn-path.js`:

```js
var DIAMOND_HW = 75;    // lesson half-width
var DIAMOND_HH = 55;    // lesson half-height
var CHALLENGE_HW = 110; // challenge half-width
var CHALLENGE_HH = 28;  // challenge half-height
var SVG_W = 760;        // canvas width
var SVG_H = 810;        // canvas height
```

If you change these, revisit your nodes' `x`/`y` values so nothing overlaps.

### Lesson typography (headings, code blocks, tables)

`css/components/markdown.css` styles the rendered lesson content — heading sizes,
inline `code`, code blocks (`pre`), tables, blockquotes, links, and images. The
code-block color theme itself comes from the highlight.js stylesheet linked in
`pages/learn-node.html` (swap the `atom-one-dark` URL for another highlight.js
theme to recolor syntax highlighting).

---

## Troubleshooting

| Symptom | Likely cause & fix |
| ------- | ------------------ |
| Card shows but clicking does nothing / "Could not load path data." | `path.json` is missing, in the wrong folder, or has a JSON syntax error. Folder name must equal the `id`. |
| "Could not load content." on a node | The `<node-id>/node.md` path doesn't match the node `id` in `path.json`, or the file isn't pushed yet. |
| Node content downloads as HTML / looks broken | The repo is missing its **`.nojekyll`** file. Add an empty `.nojekyll` at the root. |
| Every node is locked | No node has zero incoming edges. Make sure your first node isn't listed as a `to` in any edge. |
| Card icon shows as a box or `undefined` | Bad/again-stripped emoji; it's safe to omit `icon` (it falls back to 📘). |
| Changes don't appear live | Pages takes ~1 min to redeploy; also try a hard refresh (Ctrl/Cmd-Shift-R) to bypass the CDN cache. |
| Progress reset for users | An `id` was renamed. Restore the original id; progress is keyed by it. |
| Works locally but not deployed | `LEARN_CONTENT_BASE` was left pointing at `localhost`. Set it back to the Pages URL. |

---

## Final checklist

- [ ] Added an entry to `paths.json` (valid JSON, no trailing comma).
- [ ] Created a `<id>/` folder with `path.json` (nodes + edges).
- [ ] First node has no incoming edge (so it starts available).
- [ ] Every node has a `<id>/<node-id>/node.md`.
- [ ] Node ids in `path.json` match their folder names exactly.
- [ ] Previewed locally — card, graph, a lesson, and "Mark complete" all work.
- [ ] `nodeCount` matches the number of nodes.
- [ ] `.nojekyll` still present at the repo root.
- [ ] Committed and pushed.

Welcome aboard — happy authoring! 🎉
