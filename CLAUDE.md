# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static site that hosts release notes for Tedee products including Android/iOS apps and firmware for various smart devices (Lock, Lock GO, Bridge, Keypad, etc.). The site is hosted on GitHub Pages and uses the "just-the-docs" theme.

## Development Commands

### Local Development
```bash
# Install dependencies (first time setup)
bundle install

# Start local development server
bundle exec jekyll serve

# The site will be available at http://localhost:4000/tedee-release-notes/
```

### Requirements
- Jekyll 3.9.0
- Ruby 2.7.5 (Windows) or default for macOS
- Bundler gem

## Architecture

### Site Structure
- `_config.yml` - Jekyll configuration with site settings, theme, and collections
- `_docs/` - Contains all release notes organized by product category
- `_layouts/` - Custom Jekyll layouts (home.html, page.html)
- `_includes/` - Reusable template components (footer, TOC)
- `_sass/` - Custom styling and color schemes
- `index.md` - Homepage with Liquid logic to display latest releases

### Product Categories
The site organizes release notes into these categories:
- **Android** - Mobile app releases
- **iOS** - Mobile app releases
- **Lock** - Smart lock firmware
- **Lock GO** - Lock GO firmware
- **Bridge** - Bridge device firmware
- **Keypad** / **Keypad PRO** - Keypad firmware
- **Portal** - Web portal/admin interface
- **Dry contact** - Dry contact sensor firmware
- **Door sensor** - Door sensor firmware

### Release Note Format
Each release note follows this frontmatter structure:
```yaml
---
layout: page
title: "1.228.0"           # Version number
permalink: /docs/android/1.228.0/
parent: Android             # Product category
nav_order: -228            # Negative for reverse chronological order
release_date: 08.09.2025   # DD.MM.YYYY format
---
```

### Navigation System
- Uses `nav_order` with negative values to display newest releases first
- Homepage automatically displays latest release from each category
- Categories are ordered: Android, iOS, Lock, Lock GO, Bridge, Keypad, Keypad PRO, Dry contact, Portal, Door sensor

### Theme Customization
- Uses "just-the-docs" remote theme
- Custom "tedee" color scheme defined in `_sass/color_schemes/`
- Google Analytics tracking enabled (G-1FQP7Q9QMC)
- Custom footer and TOC components

## Adding New Release Notes

1. Create new markdown file in appropriate `_docs/{category}/` directory
2. Use version number as filename (e.g., `1.229.0.md`)
3. Include proper frontmatter with correct nav_order (negative version number)
4. Follow existing content structure and formatting
5. Commit and push - GitHub Pages will automatically build and deploy

## Important Notes

- Site uses Jekyll collections (`collections.docs`) for organizing release notes
- Homepage uses complex Liquid logic to automatically show latest releases
- Navigation order is critical - use negative nav_order values for proper sorting
- Release dates use DD.MM.YYYY format consistently
- All pages use the custom "page" layout except homepage which uses "home"