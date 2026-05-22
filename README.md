<div align="center">

![Cat Diary Postcard Studio](docs/banner.png)

</div>

```
╭─────────────────────────────────────────────────────────────╮
│                                                             │
│   一個會把照片變成可愛明信片的小網站。                       │
│   上傳照片 → 選明信片款式 → 撒幾隻貓貓 → 下載 PNG。          │
│                                                             │
│   A browser postcard studio for your cat photos.            │
│                                                             │
╰─────────────────────────────────────────────────────────────╯
```

<div align="center">

`React 18`　·　`Vanilla CSS`　·　`Canvas 2D`　·　`No build step`

</div>

---

## ░░ Features ░░

```
  ┌──────────────────────┬───────────────────────────────────┐
  │  📷  upload          │  Drop any JPG/PNG into the page.  │
  │  🏷️  title           │  Location + country, top-left.    │
  │  🎨  frame           │  6 styles to pick from.           │
  │  📮  stamp           │  4 fruit / flower postage stamps. │
  │  🐈  cats            │  16 sticker poses to drop in.     │
  │  ✋  drag / resize   │  Click → drag → slider → flip.    │
  │  📱  responsive      │  Phone, tablet, desktop — same.   │
  │  ⬇️  export          │  1800×1200 PNG, one click.        │
  └──────────────────────┴───────────────────────────────────┘
```

---

## ▓▓ The 16 cats ▓▓

```
   ╭─────╮  ╭─────╮  ╭─────╮  ╭─────╮
   │ ◕‿◕ │  │ ⊂(˘    │ ✦◕‿◕ │  │ ︶︶ │     兩隻坐  ·  抱抱
   │/ ▽ \│  │ ◕)っ │  │/ ▽ \│  │ zzz │     閃亮     ·  睡覺
   ╰─────╯  ╰─────╯  ╰─────╯  ╰─────╯

   ╭─────╮  ╭─────╮  ╭─────╮  ╭─────╮
   │ 👀  │  │ ◕◕  │  │  ⤳  │  │ ✋  │     偷看     ·  並排
   │  ノ  │  │ /\/\│  │ ʕ•ᴥ•ʔ│  │ ◕‿◕ │     翻滾     ·  招手
   ╰─────╯  ╰─────╯  ╰─────╯  ╰─────╯

   ╭─────╮  ╭─────╮  ╭─────╮  ╭─────╮
   │ ◕_◕?│  │ ◑_◑?│  │ ◕◡◕ │  │ ▱_▱ │     歪頭     ·  問號
   │  ?  │  │  ?  │  │ ♡♡♡ │  │ 📦  │     貼貼     ·  紙箱
   ╰─────╯  ╰─────╯  ╰─────╯  ╰─────╯

   ╭─────╮  ╭─────╮  ╭─────╮  ╭─────╮
   │ ʘ‿ʘ │  │ ⊂)⊃ │  │ ฅʕ•ᴥ│  │ =^ω^│     翻肚     ·  背影
   │ \^^/│  │ /\/\│  │ /\/\│  │  ♪♪ │     洗澡     ·  喵叫
   ╰─────╯  ╰─────╯  ╰─────╯  ╰─────╯
```

*（實際長相當然比 ASCII 可愛太多了 — 看 `assets/cats/` 裡的 PNG）*

---

## ▒▒ Quick start ▒▒

```bash
$ git clone https://github.com/<you>/cat-diary.git
$ cd cat-diary
$ python3 -m http.server 8000
$ open http://localhost:8000
```

…or just drag `index.html` into a browser. No build, no install, no node_modules.

For deployment: drop the folder on **GitHub Pages**, **Vercel**, **Netlify**, or any static host. Done.

---

## ▒▒ How it's built ▒▒

```
┌───────────────────────────────────────────────────────────┐
│                                                           │
│   index.html  ←  EVERYTHING lives in here                 │
│        │                                                  │
│        ├─ <style>     · ~700 lines of CSS                 │
│        ├─ React 18    · via CDN, no bundler               │
│        ├─ Babel       · transpiles JSX in-browser         │
│        └─ <App />     · sidebar + stage + canvas exporter │
│                                                           │
│   assets/cats/<id>.png  ←  16 transparent stickers        │
│                                                           │
└───────────────────────────────────────────────────────────┘
```

A few interesting bits:

- The postcard is **always rendered at 900 × 600 internally**, then visually scaled with `transform: scale()` to fit any container. So a phone and a desktop see the same layout — the only difference is how big it looks.
- **Direct manipulation**: click a cat, drag to move, use the floating toolbar to resize / flip / delete. Positions are stored as percentages so they survive resize.
- **PNG export**: handwritten canvas renderer reads positions from the live DOM and re-paints everything at 2×. No `html2canvas`, no SVG `foreignObject` quirks.

---

## ▒▒ File map ▒▒

```
cat-diary/
├── index.html            ← the whole app (~1900 lines)
├── README.md             ← you are here
├── assets/
│   └── cats/             ← 16 transparent-PNG sticker poses
│       ├── duo-sit.png         兩隻坐
│       ├── hug.png             抱抱
│       ├── sparkle.png         閃亮
│       ├── sleep.png           睡覺
│       ├── peek.png            偷看
│       ├── side-by-side.png    並排
│       ├── roll.png            翻滾
│       ├── wave.png            招手
│       ├── huh.png             歪頭
│       ├── huh-white.png       問號
│       ├── heart-cuddle.png    貼貼
│       ├── box.png             紙箱
│       ├── belly.png           翻肚
│       ├── backs.png           背影
│       ├── wash.png            洗澡
│       └── meow.png            喵叫
└── docs/
    └── banner.png
```

---

## ▒▒ Bring your own cats ▒▒

```
   ┌─── 1 ────────────────────────┐
   │ Drop transparent PNGs into   │
   │ assets/cats/<your-id>.png    │
   └──────────────────────────────┘
                │
                ▼
   ┌─── 2 ────────────────────────┐
   │ Edit SPRITE_VARIANTS         │
   │ inside index.html:           │
   │                              │
   │   { id: "your-id",           │
   │     name: "顯示名稱" }       │
   └──────────────────────────────┘
                │
                ▼
   ┌─── 3 ────────────────────────┐
   │ Reload. Your cats appear     │
   │ in the sticker picker.       │
   └──────────────────────────────┘
```

---

## ░░ Keyboard ░░

```
  ┌──────────────┬───────────────────────┐
  │  Click cat   │  select               │
  │  Drag        │  move (anywhere)      │
  │  Slider      │  resize (60—300 px)   │
  │  Flip btn    │  mirror               │
  │  Delete      │  remove selected      │
  │  Esc         │  deselect             │
  └──────────────┴───────────────────────┘
```

---

## ▒▒ License ▒▒

Code: **MIT** — fork it, hack it, postcard-ify it.

Cat sticker artwork in `assets/cats/` belongs to the project owner — please bring your own stickers when you fork.

---

<div align="center">

```
        ╱|、
      (˚ˎ 。7      made with 🐾 for two very specific cats
       |、˜〵      and anyone else who likes mail.
       じしˍ,)ノ
```

</div>
