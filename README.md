# X-Mind project page

Static site for the X-Mind technical report. No build step, no dependencies — just HTML, CSS, and a tiny bit of JS.

## Preview locally

From the project root:

```sh
python -m http.server 8000 --directory web
```

Then open <http://localhost:8000/> in a browser. The root URL redirects to `/en/`.

## Layout

```
web/
  index.html          # redirects to ./en/
  en/index.html       # English page
  config.js           # arXiv / PDF / GitHub link constants
  assets/
    css/styles.css
    js/main.js
    img/              # figures exported from X_Mind_Report.pdf
    videos/           # with_wm.mp4, without_wm.mp4
  .nojekyll
video/                # source videos (copied into web/assets/videos/)
X_Mind_Report.pdf
```

## Updating external links

Edit `web/config.js`:

```js
window.X_MIND_CONFIG = {
  ARXIV_URL:  "https://arxiv.org/abs/XXXX.XXXXX",
  PDF_URL:    "../X_Mind_Report.pdf",
  GITHUB_URL: "https://github.com/<user>/X_Mind",
  YEAR: "2026"
};
```

## Regenerating figures from PDF

```sh
python extract_figures.py
```

## Deploy to GitHub Pages

Copy the contents of `web/` to your Pages repo root (include `.nojekyll`), or set Pages source to the `/web` folder of this repo.
