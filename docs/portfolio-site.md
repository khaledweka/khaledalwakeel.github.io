# Portfolio Site Documentation

GitHub Pages portfolio and blog for Khaled Alwakeel. Plain HTML, CSS, and JavaScript—no build step.

## Site Structure

```
khaledalwakeel.github.io/
├── index.html          # Home: CV sections (About, Experience, Skills, Certifications)
├── blog/
│   ├── index.html      # Blog listing
│   ├── welcome-post.html
│   └── restful-api-design.html
├── css/
│   └── styles.css
├── js/
│   └── main.js
└── docs/
    └── portfolio-site.md
```

## How to Add Blog Posts

1. Create a new HTML file in `blog/`, e.g. `blog/my-new-post.html`.
2. Copy the structure from `blog/welcome-post.html` (header, footer, theme toggle).
3. Update the `<title>`, `<meta name="description">`, post header, and content.
4. Add an entry to `blog/index.html` in the `<ul class="post-list">`:

```html
<li class="post-item">
  <a href="my-new-post.html" class="post-link">
    <h2 class="post-title">Your Post Title</h2>
    <p class="post-meta">Month Day, Year</p>
    <p class="post-excerpt">Short excerpt...</p>
  </a>
</li>
```

## Profile Photo

Place your profile image at `assets/profile.png`. Recommended size: 400x400px or larger (square). If the image is missing, a fallback with initials "KA" is shown.

## How to Update CV Content

- **About**: Edit the `.about-text` paragraph and `.contact-list` in `index.html`.
- **Experience**: Edit the `.timeline` section; each `.timeline-item` is one role.
- **Skills**: Edit the `.skills-grid`; each `.skill-category` has a title and `.skill-tags`.
- **Certifications**: Edit the `.cert-list` in `index.html`.

## Theme System

- Dark/light mode toggle in the header.
- Preference stored in `localStorage` under key `theme`.
- First visit uses `prefers-color-scheme` if no stored preference.
- CSS variables in `css/styles.css` under `[data-theme="dark"]` and `[data-theme="light"]`.

## Deployment

1. Push to the `main` branch.
2. In GitHub repo **Settings** → **Pages**:
   - Source: Deploy from a branch
   - Branch: `main` / `(root)`
3. Site URL: `https://khaledalwakeel.github.io` (or custom domain via CNAME).

## Custom Domain

Create a `CNAME` file in the repo root with your domain, e.g.:

```
khaled-elwakeel.com
```

Then configure DNS for your domain to point to GitHub Pages.
