# altbound

Corporate website for altbound - where outbound meets inbound, differently.

## Project Structure

This is a Hugo static site with a custom theme. The main components are:

- `themes/altbound-theme/`: Custom theme with all layouts and styles
- `content/`: Markdown files for pages
- `static/`: Static assets
- `public/`: Generated site (tracked in main branch for Cloudflare Pages deployment)

### Key Features

- Responsive design with mobile-friendly navigation
- Pricing plans with integrated Calendly booking
- Newsletter integration via Beehiiv
- SEO optimizations including canonical URLs and HTTPS enforcement
- Hidden pages support (e.g., contact page preserved but not linked)
- Automatic image optimization with WebP conversion and fallbacks
- High-quality image processing with lazy loading

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

4. Push to GitHub:
   ```bash
   git push origin main
   ```

5. Switch back to development:
   ```bash
   git checkout development
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
- `layouts/_default/baseof.html`: Base template with meta tags and navigation
- `layouts/index.html`: Homepage template with services, pricing, and newsletter
- `assets/css/main.css`: Main stylesheet

## Hidden Pages

Some pages are maintained in the codebase but not linked in the navigation. To restore a hidden page:

1. Add its menu entry to `hugo.toml`. Example for the contact page:
   ```toml
   [[menu.main]]
     name = "Contact"
     url = "/contact/"
     weight = 4
   ```

2. Rebuild and deploy as usual

## Image Handling

The site uses Hugo's built-in image processing for optimal performance:

- Images should be placed in the `assets/images/` directory
- Automatic WebP conversion with PNG/JPG fallbacks
- Lazy loading for better performance
- Original quality preserved while providing optimized formats
- Responsive images with proper width/height attributes

Example image structure:
```
assets/
  images/
    testimonials/    # Testimonial screenshots
    founder.jpg      # Team/profile photos
    og-image.jpg     # Social media images
``` 