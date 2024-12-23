# altbound

Corporate website for altbound - where outbound meets inbound, differently.

## Project Structure

This is a Hugo static site with a custom theme. The main components are:

- `themes/altbound-theme/`: Custom theme with all layouts and styles
- `content/`: Markdown files for pages
- `static/`: Static assets
- `public/`: Generated site (tracked in main branch for Cloudflare Pages deployment)

## Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.140.0 or later)
- Git

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/00al/altbound.git
   cd altbound
   ```

2. Start the Hugo development server:
   ```bash
   hugo server -D
   ```

3. View the site at http://localhost:1313

### Git Workflow

The project uses two main branches:
- `development`: For active development
- `main`: For production deployment (includes the `public` directory)

Always work on the `development` branch:
```bash
git checkout development
```

### Making Changes

1. Make changes in the `development` branch
2. Test locally with `hugo server -D`
3. Commit changes:
   ```bash
   git add .
   git commit -m "Description of changes"
   ```
4. Push to development:
   ```bash
   git push origin development
   ```

## Deployment

The site is deployed via Cloudflare Pages from the `public` directory in the main branch. The deployment process is:

1. Stop the Hugo development server if it's running

2. Build the site:
   ```bash
   hugo
   ```

3. Merge to main:
   ```bash
   git checkout main
   git merge development
   ```

4. Add and commit the new build:
   ```bash
   git add public/
   git commit -m "Build site for deployment"
   ```

5. Push to GitHub:
   ```bash
   git push origin main
   ```

6. Cloudflare Pages will automatically deploy the contents of the `public` directory

### Cloudflare Pages Settings

- Build command: None (we push the pre-built site)
- Build output directory: `public`
- Environment variables: None needed (site is pre-built)

## Theme Customization

The custom theme is located in `themes/altbound-theme/` and includes:

- `layouts/`: HTML templates
- `assets/css/`: Stylesheets
- `static/`: Theme-specific static assets

Key files:
- `layouts/_default/baseof.html`: Base template
- `layouts/index.html`: Homepage template
- `assets/css/main.css`: Main stylesheet

## Contact Form

The contact form is implemented using Tally.so and is embedded in the contact page template. 