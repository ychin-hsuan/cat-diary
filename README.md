# 🐱 Cat Diary · Postcard Studio

A cute, browser-based postcard generator. Upload a photo, pick a frame, drop your cats onto it, type the location — and download a high-resolution PNG.

Built as a single self-contained `index.html` (React + Babel inline, no build step).

![cat diary postcard studio](docs/preview.png)

---

## ✨ Features

- 📷 **Photo upload** — drop in any JPG/PNG; it fills the left pane edge-to-edge
- 🏷️ **Location + country** text overlay (top-left)
- 🎨 **6 postcard styles** — Cream Paper, Sunset Gold, Mossy Forest, Misty Blossom, Midnight Blue, Washi Collage
- 📮 **4 postage stamps** — lemon / flower / leaf / berry
- 🐈 **16 cat stickers** — sitting, hugging, sparkling, sleeping, peeking, side-by-side, rolling, waving, head-tilting, question-mark-ing, cuddling, in-a-box, belly-up, walking away, washing, meowing
- 🖱️ **Direct manipulation** — click a cat to select, drag to move, use the floating toolbar to resize / flip / delete
- ⌨️ **Keyboard shortcuts** — `Esc` to deselect, `Delete` / `Backspace` to remove a selected cat
- 📱 **Mobile-friendly** — works on phones too
- ⬇️ **One-click PNG export** at 1800×1200 (2× retina)

---

## 🚀 Run it

No build, no install. Just open the HTML.

```bash
# Clone
git clone <your-repo-url>
cd <your-repo>

# Option A — open the file directly
open index.html

# Option B — serve locally (recommended; some browsers block local image loading)
python3 -m http.server 8000
# then visit http://localhost:8000
```

Or drop the folder onto **GitHub Pages** / **Vercel** / **Netlify** — it's just static files.

---

## 📁 Project structure

```
.
├── index.html          # The whole app — markup, styles, React components, exporter
├── assets/
│   └── cats/           # 16 transparent-PNG cat stickers
│       ├── duo-sit.png
│       ├── hug.png
│       ├── sleep.png
│       └── … (13 more)
└── README.md
```

---

## 🛠️ How it works

- **UI**: React 18 + JSX, transpiled in-browser by `@babel/standalone` — no bundler.
- **Layout**: CSS Grid for the sidebar/stage split, flexbox inside.
- **Postcard rendering**: a regular DOM tree, scaled to fit any viewport with `aspect-ratio: 1.5/1`.
- **Drag & drop**: pointer events on the sprite layer, with percent-based positioning so sprites stay put when the postcard resizes.
- **PNG export**: a hand-rolled canvas renderer (`renderPostcardPNG`) that reads live DOM positions and re-paints everything to a `<canvas>` at 2× resolution. This avoids `html-to-image` / `foreignObject` quirks with user-uploaded photos and external SVGs.

---

## 🎨 Replacing the cat stickers

The 16 cats live in `assets/cats/<id>.png` as transparent PNGs. The list of variants is defined inline in `index.html`:

```js
const SPRITE_VARIANTS = [
  { id: "duo-sit",      name: "兩隻坐" },
  { id: "hug",          name: "抱抱" },
  // … etc.
];
```

To use your own stickers:
1. Drop transparent PNGs into `assets/cats/`
2. Update `SPRITE_VARIANTS` with your new ids and display names

---

## 📝 License

Code: MIT. Use it for anything.

Cat sticker artwork is the personal property of the project owner — feel free to fork the code, but please bring your own stickers.

---

Made with 🐾 for a tiny orange tabby and a fluffy white-orange friend.
