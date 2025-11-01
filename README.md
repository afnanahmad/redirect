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
- Bundler

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

Visit `http://localhost:4000` to view the site.

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
url: "https://redirect.afnanahmad.github.io"
remote_theme: b2a3e8/jekyll-theme-console
style: dark
```

## Custom CSS

The Hack font is loaded via [assets/css/custom.css](assets/css/custom.css), which imports the font from CDN and applies it globally.

## License

This project is open source and available under the MIT License.

## Author

**Afnan Ahmad**

- GitHub: [@afnanahmad](https://github.com/afnanahmad)
- Website: [afnanahmad.github.io](https://afnanahmad.github.io)

## Acknowledgments

- [Jekyll Theme Console](https://github.com/b2a3e8/jekyll-theme-console) by b2a3e8
- [Hack Font](https://sourcefoundry.org/hack/) by Source Foundry
