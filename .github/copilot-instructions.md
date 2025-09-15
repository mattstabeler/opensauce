# Matt's Open Sauce Recipes - Jekyll Static Site

Matt's Open Sauce is a Jekyll-based static website containing cooking and brewing recipes. The site is hosted on GitHub Pages and uses the Merlot theme to showcase recipe collections, brewing guides, and blog posts.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Bootstrap, Build, and Test the Repository

Follow these steps in order to set up the development environment:

1. **Install Ruby dependencies:**
   ```bash
   gem install --user-install jekyll bundler
   export PATH="$PATH:/home/runner/.local/share/gem/ruby/3.2.0/bin"
   ```

2. **Install project dependencies:**
   ```bash
   bundle config set --local path 'vendor/bundle'
   bundle install
   ```
   - Takes 2-3 minutes on first run
   - Installs Jekyll 3.10.0 and theme dependencies
   - May show warnings about Ruby Sass deprecation - this is normal

3. **Build the site:**
   ```bash
   bundle exec jekyll build
   ```
   - Build time: ~0.3 seconds (very fast)
   - Generates static site in `_site/` directory
   - No timeout concerns - build completes quickly

4. **Run the development server:**
   ```bash
   bundle exec jekyll serve --host=0.0.0.0 --port=4000
   ```
   - Starts local development server at http://localhost:4000
   - Supports live reload during development
   - Use Ctrl+C to stop the server

### Validation

**ALWAYS manually test any changes by running through these validation scenarios:**

1. **Build validation:**
   ```bash
   bundle exec jekyll build
   ```
   - Must complete without errors
   - Check that `_site/index.html` exists and is generated properly

2. **Local server validation:**
   ```bash
   bundle exec jekyll serve --host=0.0.0.0 --port=4000
   ```
   - Server should start successfully on http://localhost:4000
   - Test homepage loads with recipe links
   - Navigate to at least one recipe page (e.g., brewing/Simple_English_Ale.md)
   - Verify blog post links work from homepage

3. **Content validation scenarios:**
   - **Homepage navigation:** Verify all recipe links in main sections work
   - **Recipe accessibility:** Test that brewing recipes load properly (e.g., /brewing/Simple_English_Ale)
   - **Blog functionality:** Check that blog posts are listed and accessible
   - **Theme rendering:** Confirm Merlot theme styles load correctly

## Repository Structure

### Key directories and files:
```
.
├── README.md              # Repository description
├── _config.yml           # Jekyll configuration
├── _layouts/default.html # Custom theme layout
├── _includes/            # Theme partials
├── _posts/              # Blog posts (date-prefixed)
├── assets/              # CSS and static assets
├── brewing/             # Brewing recipe markdown files
├── recipes/             # Cooking recipe markdown files
├── index.md             # Homepage content
├── Gemfile              # Ruby dependencies
└── .gitignore           # Excludes build artifacts
```

### Recipe organization:
- **Brewing recipes:** `/brewing/` directory (12 recipe files)
- **Cooking recipes:** `/recipes/` directory (2 recipe files) 
- **Blog posts:** `/_posts/` directory (2 posts)

## Common Tasks

### Adding new recipes:
1. Create new `.md` file in appropriate directory (`recipes/` or `brewing/`)
2. Use existing recipe files as templates for front matter format
3. Add recipe link to `index.md` homepage
4. Test locally with `bundle exec jekyll serve`

### Modifying site appearance:
- Edit `_layouts/default.html` for structural changes
- Theme assets are in `/assets/` directory
- Configuration in `_config.yml`

### Troubleshooting common issues:

**"GitHub API access errors during build":**
- Already resolved in current layout - hardcoded GitHub links instead of dynamic API calls
- If errors persist, verify `_layouts/default.html` has static links

**"Missing kramdown-parser-gfm dependency":**
- Dependency is included in `Gemfile`
- Run `bundle install` to resolve

**"Bundle permission errors":**
- Use `bundle config set --local path 'vendor/bundle'` for local installation
- Avoid system-wide gem installation

## File Reference

### Repository root contents:
```
total 48
drwxr-xr-x 9 runner runner 4096 .
drwxr-xr-x 3 runner runner 4096 ..
drwxrwxr-x 7 runner runner 4096 .git
drwxrwxr-x 2 runner runner 4096 .github
-rw-rw-r-- 1 runner runner  167 .gitignore
-rw-rw-r-- 1 runner runner 1283 GHPAGES.md
-rw-rw-r-- 1 runner runner  922 README.md
-rw-rw-r-- 1 runner runner   89 _config.yml
drwxrwxr-x 2 runner runner 4096 _includes
drwxrwxr-x 2 runner runner 4096 _layouts
drwxrwxr-x 2 runner runner 4096 _posts
drwxrwxr-x 3 runner runner 4096 assets
drwxrwxr-x 2 runner runner 4096 brewing
-rw-rw-r-- 1 runner runner  141 Gemfile
-rw-rw-r-- 1 runner runner  979 index.md
drwxrwxr-x 2 runner runner 4096 recipes
```

### Current Gemfile:
```ruby
source "https://rubygems.org"

gem "jekyll", "~> 3.10.0"
gem "jekyll-theme-merlot"
gem "jekyll-seo-tag"
gem "kramdown-parser-gfm"
```

### Current _config.yml:
```yaml
theme: jekyll-theme-merlot
google_analytics: UA-60465304-1
repository: mattstabeler/opensauce
github: [metadata]
```

## Technology Stack
- **Static site generator:** Jekyll 3.10.0
- **Theme:** jekyll-theme-merlot 
- **Content format:** Markdown with YAML front matter
- **Hosting:** GitHub Pages
- **Ruby version:** 3.2.3
- **Build environment:** Ubuntu Linux

## Development Workflow
1. Make changes to content files (`.md` files in `/recipes/`, `/brewing/`, or `/_posts/`)
2. Test locally: `bundle exec jekyll serve`
3. Verify changes in browser at http://localhost:4000
4. Build for production: `bundle exec jekyll build`
5. Commit changes (build artifacts in `_site/`, `vendor/`, etc. are excluded by `.gitignore`)