# Learn

Content for the CCA Coding Club **Learn** pages. This is the single source of
truth for every learning path on the website — to add or edit a path, push to
this repo. No website code changes are needed.

The website reads this repo over **GitHub Pages**
(`https://cca-coding-club.github.io/Learn/`), so this repo must keep Pages
enabled, and the **`.nojekyll`** file at the root must stay (without it GitHub
would convert `node.md` files into HTML and the site couldn't load them).

## Repository layout

```text
paths.json                  ← master list of every learning path
.nojekyll                   ← required; serve files verbatim (do not delete)
<path-id>/
  path.json                 ← the path's node graph
  <node-id>/
    node.md                 ← the lesson / challenge content (Markdown)
```

See `git-basics/` for a complete working example.

## `paths.json`

An array of path entries shown as cards on the Learn page:

```json
[
  {
    "id": "git-basics",
    "title": "Git Basics",
    "description": "Learn version control...",
    "nodeCount": 3
  }
]
```

| Field | Required | Notes |
| ----- | -------- | ----- |
| `id` | yes | URL-safe slug; **never change it** — it keys users' saved progress. |
| `title` | yes | Shown on the card and path page. |
| `icon` | no | An emoji; defaults to 📘 if omitted. |
| `description` | yes | One-line summary on the card. |
| `nodeCount` | no | Total nodes, for the progress label. |
| `source` | no | Pull this path's content from a **different** repo (see below). |

## Adding a path that lives in *this* repo

1. Add an entry to `paths.json`.
2. Create a `<id>/path.json` describing the node graph.
3. Add a `<id>/<node-id>/node.md` for each node.

### `path.json`

```json
{
  "id": "git-basics",
  "title": "Git Basics",
  "nodes": [
    { "id": "intro",  "type": "lesson",    "title": "What is Git?",  "x": 380, "y": 130 },
    { "id": "commit", "type": "challenge", "title": "First Commit",  "x": 380, "y": 400 }
  ],
  "edges": [
    { "from": "intro", "to": "commit" }
  ]
}
```

- `type` is `"lesson"` (diamond) or `"challenge"` (rounded rectangle).
- `x`/`y` position the node on an `760 × 810` canvas.
- `edges` define prerequisites: a node unlocks once all nodes pointing **to** it
  are complete.

### `node.md`

Plain Markdown. An optional `--- ... ---` front-matter block at the top is
ignored by the renderer (use it for your own notes). Code blocks get syntax
highlighting.

## Adding a path sourced from *another* repo

Give the entry a `source` instead of putting content in this repo. The other
repo must also have **Pages enabled** and a **`.nojekyll`** file, and its root
must contain `path.json` + `<node-id>/node.md`.

```json
{ "id": "discord-python", "title": "Discord with Python",
  "description": "Build a Discord bot.", "source": "CCA-Coding-Club/Discord-with-Python" }
```

`source` formats (no branch component — Pages serves one configured branch):

| `source` | Resolves to |
| -------- | ----------- |
| `owner/repo` | `https://owner.github.io/repo` |
| `owner/repo:subpath` | `https://owner.github.io/repo/subpath` |
| `https://…` | used as-is |
