# hugo-mock-landing-page-domain-name

# Stitched Social

## About Stitched Social
Stitched Social is a modern, AI-driven matchmaking service that revolutionizes how people find meaningful relationships. By combining AI technology with social matchmaking elements, we deliver a more effective, community-driven, and personalized approach to dating – all at less than 1/10th the cost of traditional matchmaking.

Our platform offers:
- AI-driven personalized matching
- Group dates and curated social experiences
- Community feedback integration
- Continuous match improvement through real-time feedback

## Project Structure
- `USER-STORIES.md`: Contains detailed user stories and feature requirements
- `layouts/`: Contains the HTML templates
- `assets/`: Contains SCSS and images
- `content/`: Contains the site content
- `themes/`: Contains the Hugo theme

## Success Metrics
- 48% of matches lead to second dates (triple Hinge's success rate)
- 79% exchange contact information
- 100% trust rate for future matches

## Development
This site is built using:
- Hugo static site generator
- Bootstrap for styling
- SCSS for custom styling

### Local Development
1. Install Hugo (extended version)
bash
brew install hugo
2. Clone the repository
git clone [[repository-url](https://github.com/Natalielim/hugo-mock-landing-page.git)]
cd [repository-name]hugo-mock-landing-page
3. Start the Hugo server
hugo server

## Continuous Deployment with GitHub Actions

### Workflow Overview
This project uses a GitHub Actions workflow to automatically build and deploy the Hugo website to GitHub Pages. Key features include:

- **Automatic Deployment**: Triggered on pushes to the `main` branch
- **Hugo Build**: Uses Hugo version 0.144.1 with extended features
- **Optimization**: 
  - Includes draft content
  - Performs garbage collection
  - Minifies static files
- **Deployment**: Publishes to GitHub Pages `gh-pages` branch

### Workflow Details
The workflow (`build-and-deploy.yml`) performs these key steps:
1. Checkout the repository
2. Set up Hugo environment
3. Build static site
4. Deploy to GitHub Pages

### Workflow Configuration
```yaml
name: 🏗️ Build and Deploy GitHub Pages
on:
  push:
    branches:
      - main
jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - name: Check Out Source Repository
        uses: actions/checkout@v3.5.1
        with:
          submodules: true
          fetch-depth: 0
      - name: Initialize Hugo Environment
        uses: peaceiris/actions-hugo@v2.6.0
        with:
          hugo-version: "0.144.1"
          extended: true
      - name: Compile Hugo Static Files
        run: hugo -D --gc --minify
      - name: Publish to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3.9.3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
