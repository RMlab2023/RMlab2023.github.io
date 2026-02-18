# The Madsen Lab Website

[![Deploy Jekyll site to GitHub Pages](https://github.com/RMlab2023/RMlab2023.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/RMlab2023/RMlab2023.github.io/actions)

Source for **[RMlab2023.github.io](https://RMlab2023.github.io)** — the website of The Madsen Lab, a quantitative systems biology group at UCL Cancer Institute studying PI3K signalling in health and disease.

Built with [Jekyll](https://jekyllrb.com) and hosted via [GitHub Pages](https://pages.github.com).

---

## For Lab Members: Adding Content

See [CONTRIBUTING.md](CONTRIBUTING.md) for step-by-step instructions on:
- Adding news posts
- Adding publications
- Adding team members
- Updating page content

You do **not** need to be a developer to contribute.

---

## Site Structure

```
madsen-lab-website/
├── _config.yml            # Site-wide settings (name, email, GitHub handle, etc.)
├── Gemfile                # Ruby dependencies
├── index.md               # Homepage
│
├── pages/                 # Static pages
│   ├── research.md
│   ├── people.md
│   ├── publications.md
│   ├── open-science.md
│   ├── students.md
│   ├── news.md
│   └── contact.md
│
├── _posts/                # Blog/news posts (YYYY-MM-DD-title.md)
│
├── _data/                 # Structured data (edit to add team/publications)
│   ├── team.yml           ← Add team members here
│   └── publications.yml   ← Add publications here
│
├── _layouts/              # Page templates (default, page, post)
├── _includes/             # Reusable components (header, footer, head)
│
└── assets/
    ├── css/main.css       # All styles
    ├── js/main.js         # JavaScript
    └── images/
        └── team/          ← Save team photos here
```

---

## Setting Up GitHub Pages

1. **Create a repository** on GitHub named `RMlab2023.github.io` (replace with your org name)
2. Push this folder as the repository contents:
   ```bash
   cd madsen-lab-website
   git init
   git add .
   git commit -m "Initial commit: Madsen Lab website"
   git remote add origin https://github.com/RMlab2023/RMlab2023.github.io.git
   git push -u origin main
   ```
3. In the repository Settings → Pages → Source, select **main branch / root**
4. The site will be live at `https://RMlab2023.github.io` within a few minutes

---

## Running Locally

**Requirements:** Ruby ≥ 3.0, Bundler

```bash
bundle install
bundle exec jekyll serve
```

Then open [http://localhost:4000](http://localhost:4000).

---

## Customisation

- **Colours / fonts:** Edit `assets/css/main.css` (CSS variables at the top of the file)
- **Navigation:** Edit the `navigation:` section in `_config.yml`
- **Lab info:** Edit the `lab:` section in `_config.yml`

---

## Licence

Site code: [MIT Licence](LICENSE)
Content: © The Madsen Lab. All rights reserved unless otherwise stated.
