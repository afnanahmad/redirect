# Redirect Service

A minimal, developer-focused short link redirect service built with Jekyll and GitHub Pages.

## Overview

This site provides clean, memorable short URLs that redirect to various profiles and resources. Built with a terminal-inspired theme and the Hack monospace font for a true developer aesthetic.

## Features

- **Terminal/Console Theme**: Clean, minimalist design inspired by Linux consoles
- **Hack Font**: Professional monospace font optimized for developers
- **Dark Mode**: Easy on the eyes with a dark color scheme
- **Fast Redirects**: Lightweight Jekyll-based redirects using `jekyll-redirect-from`
- **GitHub Pages**: Free hosting with automatic builds

## Available Short Links

- `/scholar` - Google Scholar Profile
- `/linkedin` - LinkedIn Profile
- `/github` - GitHub Profile
- `/x` - X (Twitter) Profile
- `/stackoverflow` - Stack Overflow Profile

## Tech Stack

- **Jekyll**: Static site generator
- **Theme**: [Jekyll Theme Console](https://github.com/b2a3e8/jekyll-theme-console)
- **Font**: [Hack](https://sourcefoundry.org/hack/)
- **Hosting**: GitHub Pages
- **Plugins**:
  - `jekyll-redirect-from` - URL redirection
  - `jekyll-remote-theme` - Remote theme support

## Local Development

### Prerequisites

- Ruby 3.x
- Bundler (`gem install bundler`)

### Setup

1. Clone the repository:
```bash
git clone https://github.com/afnanahmad/redirect.git
cd redirect
```

2. Install dependencies:
```bash
bundle install
```

3. Build the site:
```bash
bundle exec jekyll build
```

4. Serve locally:
```bash
bundle exec jekyll serve
```

Visit `http://localhost:4000/redirect/` to view the site (note the `/redirect/` path to match GitHub Pages deployment).

## Adding New Redirects

1. Create a new `.md` file in the root directory (e.g., `newlink.md`)

2. Add front matter with redirect URL:
```yaml
---
redirect_to: "https://example.com/your-profile"
---
```

3. Update `index.md` to include the new link in the list

4. Commit and push - GitHub Pages will automatically rebuild

## Theme Customization

The theme supports multiple styles. Edit `_config.yml` to change:

```yaml
style: dark  # Options: dark, light, hacker, nord
```

### Style Options

- **dark** (default): Classic dark terminal look
- **light**: Light background variant
- **hacker**: Green-on-black matrix-style
- **nord**: Popular Nord color palette

## Configuration

Key settings in `_config.yml`:

```yaml
title: Afnan Ahmad
description: Short link redirect service
baseurl: "/link"  # Important: Must match your GitHub Pages path
url: "https://afnanahmad.github.io"
remote_theme: b2a3e8/jekyll-theme-console
style: dark
disable_google_fonts: true  # We use Hack font instead
```

### Important: GitHub Pages Deployment

When deploying to GitHub Pages at a project site (not user site), you **must** configure the `baseurl`:

- ✅ **Project Site** (e.g., `username.github.io/project/`):
  ```yaml
  baseurl: "/project"
  url: "https://username.github.io"
  ```

- ✅ **User Site** (e.g., `username.github.io/`):
  ```yaml
  baseurl: ""
  url: "https://username.github.io"
  ```

This ensures all CSS and asset paths work correctly on GitHub Pages.

## Custom Font Implementation

The Hack font is implemented through:

1. **Custom Layout** ([_layouts/default.html](_layouts/default.html)): Updates Content Security Policy to allow the Hack font CDN and inline styles
2. **Custom Head Include** ([_includes/head.html](_includes/head.html)): Loads Hack font from CDN and applies it globally via inline CSS

**Content Security Policy Configuration:**
```
style-src 'self' 'unsafe-inline' https://fonts.googleapis.com https://cdn.jsdelivr.net;
font-src 'self' https://fonts.gstatic.com https://cdn.jsdelivr.net data:;
```

This approach:
- Disables Google Fonts to reduce external dependencies
- Uses the professional Hack font optimized for code readability
- Allows inline styles (`'unsafe-inline'`) for font application
- Properly configures CSP headers for security while allowing the CDN

## Project Structure

```
redirect/
├── _config.yml              # Jekyll configuration
├── _includes/
│   └── head.html           # Custom head with Hack font
├── _layouts/
│   └── default.html        # Custom layout with updated CSP
├── _site/                  # Generated site (ignored in git)
├── .gitignore              # Git ignore rules
├── Gemfile                 # Ruby dependencies
├── README.md               # This file
├── index.md                # Homepage with link list
└── *.md                    # Individual redirect pages
```

## Troubleshooting

### CSS 404 Errors on GitHub Pages

If you see 404 errors for CSS files (like `main-dark.css`) after deploying:

1. **Check your `baseurl` in `_config.yml`**:
   - Must match your GitHub Pages URL path
   - For `username.github.io/redirect/`, use `baseurl: "/redirect"`
   - For `username.github.io/`, use `baseurl: ""`

2. **Verify the GitHub Pages source**:
   - Go to repository Settings → Pages
   - Ensure "Source" is set to the correct branch (usually `main`)
   - Check that the site is building successfully

3. **Wait for deployment**:
   - GitHub Pages can take 1-2 minutes to rebuild after pushing
   - Check the Actions tab for build status

### Font Not Loading

If the Hack font isn't appearing:

1. **Check browser console** for CSP violations
2. **Verify `_includes/head.html`** includes the Hack font CDN link
3. **Ensure `_layouts/default.html`** allows `cdn.jsdelivr.net` in CSP

### Local Development Issues

If `bundle exec jekyll serve` fails:

```bash
# Update dependencies
bundle update

# Clean and rebuild
bundle exec jekyll clean
bundle exec jekyll build
```

## License

This project is open source and available under the MIT License.

## Author

**Afnan Ahmad**

- GitHub: [@afnanahmad](https://github.com/afnanahmad)
- Website: [afnanahmad.github.io](https://afnanahmad.github.io)

## Acknowledgments

- [Jekyll Theme Console](https://github.com/b2a3e8/jekyll-theme-console) by b2a3e8
- [Hack Font](https://sourcefoundry.org/hack/) by Source Foundry
