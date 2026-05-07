# Contributing to The Madsen Lab Website

Thank you for contributing! This guide explains how to add or update content on the lab website. You do **not** need to be a developer — most updates involve editing simple text files.

---

## Quick Reference

| What you want to do | File to edit |
|---|---|
| Add a news post | Create a new file in `_posts/` |
| Add a publication | Edit `_data/publications.yml` |
| Add/update a team member | Edit `_data/team.yml` |
| Edit the Research page | Edit `pages/research.md` |
| Edit the Open Science page | Edit `pages/open-science.md` |
| Edit contact details | Edit `pages/contact.md` and `_config.yml` |
| Add a team photo | Save to `assets/images/team/` |

---

## 1. Adding a News Post

Create a new Markdown file in the `_posts/` directory. The filename **must** follow this format:

```
YYYY-MM-DD-title-with-hyphens.md
```

For example: `2025-09-01-welcome-new-postdoc.md`

Copy this template at the top of the file:

```yaml
---
layout: post
title: "Your Post Title Here"
date: 2025-09-01
author: Ralitsa Madsen
categories: [lab-news]
excerpt: >
  A one or two sentence summary that will appear in previews.
---

Your post content goes here, written in Markdown.

You can use **bold**, *italic*, [links](https://example.com), and more.

## Subheadings

Use ## for subheadings within the post.
```

**Available categories:** `lab-news`, `science`, `open-science`, `reflections`, `events`

---

## 2. Adding a Publication

Open `_data/publications.yml` and add a new entry following the template at the bottom of that file:

```yaml
- title: "Full title of the paper"
  authors: "Last FM, Last FM, Madsen R"
  journal: "Journal Name"
  year: 2025
  doi: "10.xxxx/xxxxxx"          # DOI without the https://doi.org/ prefix
  preprint_doi: "10.1101/xxxxx"  # bioRxiv/medRxiv DOI if applicable
  status: "published"            # published | preprint | in-review
  highlight: false               # set true to feature it on the Publications page
  description: >
    One sentence summary of the key finding.
```

---

## 3. Adding or Updating a Team Member

Open `_data/team.yml` and add or edit an entry:

```yaml
- name: "First Last"
  role: "Postdoctoral Researcher"   # or PhD Student, Research Associate, etc.
  photo: "first-last.jpg"           # save photo to assets/images/team/
  bio: >
    Short biography of 2–4 sentences.
  email: "email@glasgow.ac.uk"
  twitter: "handle"                 # without the @
  github: "githubusername"
  orcid: "0000-0000-0000-0000"
  google_scholar: "https://scholar.google.com/..."
  website: ""
  group: "postdoc"   # pi | postdoc | phd | msc | alumni
```

**Adding a photo:**
1. Save the photo as a `.jpg` or `.png` file (square crop, ideally 400×400px or larger)
2. Name it to match the `photo:` field (e.g., `first-last.jpg`)
3. Save it to `assets/images/team/`

---

## 4. Updating Site-Wide Information

Global settings (lab name, email, GitHub handle, etc.) are in `_config.yml`. Edit the `lab:` section:

```yaml
lab:
  pi: "Dr. Ralitsa Madsen"
  institution: "CRUK Scotland Institute & University of Glasgow"
  email: "ralitsa.madsen@glasgow.ac.uk"
  twitter: "your_handle"      # optional
  github: "RMlab2023"
  orcid: "your-orcid"         # optional
```

---

## 5. Editing Page Content

All pages are Markdown files in the `pages/` directory. Open the relevant file and edit the text. Markdown basics:

```markdown
## Heading 2
### Heading 3

Normal paragraph text.

**Bold text** and *italic text*.

- Bullet point
- Another bullet

[Link text](https://example.com)
```

---

## 6. Working with GitHub

### Authenticating with GitHub

Before you can push changes from your computer, you need to authenticate with GitHub. **GitHub no longer accepts your account password for Git operations over HTTPS** — you must use one of the following:

**Option A: Personal Access Token (PAT)** — recommended for most contributors

1. On GitHub, go to **Settings → Developer settings → Personal access tokens → Tokens (classic)** (or use [Fine-grained tokens](https://github.com/settings/tokens?type=beta))
2. Click **Generate new token**, give it a descriptive name (e.g. "RMlab website laptop"), set an expiration, and tick the **`repo`** scope
3. Click **Generate token** and **copy the token immediately** — you will not be able to see it again
4. The first time you `git push`, Git will prompt for your username and password. Enter your GitHub username, and **paste the token in place of the password**
5. To avoid being asked every time, enable a credential helper:
   - macOS: `git config --global credential.helper osxkeychain`
   - Windows: `git config --global credential.helper manager`
   - Linux: `git config --global credential.helper store` (stores in plain text) or `cache` (in-memory only)

**Option B: SSH key** — recommended if you push frequently

1. Generate a key on your computer: `ssh-keygen -t ed25519 -C "your.email@example.com"`
2. Copy the public key: `cat ~/.ssh/id_ed25519.pub`
3. On GitHub, go to **Settings → SSH and GPG keys → New SSH key**, paste it in, and save
4. Use the SSH clone URL when cloning: `git clone git@github.com:YOUR-USERNAME/RMlab2023.github.io.git`

**Option C: GitHub CLI** — easiest if you don't want to manage tokens manually

1. Install the [GitHub CLI](https://cli.github.com/)
2. Run `gh auth login` and follow the prompts — it will set up Git authentication for you

### Recommended workflow

If you are comfortable with Git:

1. **Fork** the repository (click Fork on GitHub)
2. **Clone** your fork locally: `git clone https://github.com/YOUR-USERNAME/RMlab2023.github.io.git` (or use the SSH URL if you set up an SSH key)
3. **Create a branch**: `git checkout -b add-new-publication`
4. Make your changes
5. **Commit**: `git add . && git commit -m "Add Smith et al. 2025 publication"`
6. **Push**: `git push origin add-new-publication` (you'll be prompted for credentials the first time — see above)
7. Open a **Pull Request** on GitHub

If you are not comfortable with Git, you can also **edit files directly on GitHub** (click the pencil icon on any file) and GitHub will create a pull request for you. This avoids the authentication step entirely, since you are already signed in to GitHub in your browser.

---

## 7. Running the Site Locally (optional)

If you want to preview changes before pushing:

**Prerequisites:** Ruby, Bundler

```bash
# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve

# Open http://localhost:4000 in your browser
```

---

## Questions?

Open a [GitHub Issue](https://github.com/RMlab2023/RMlab2023.github.io/issues) or contact the lab directly.
