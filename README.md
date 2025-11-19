# Kane Le Blog

A personal blog and portfolio website built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Sections

- **Home** - Landing page
- **Blogs** - Technical articles and tutorials
- **Projects** - Portfolio of personal projects

## Tech Stack

- [Hugo](https://gohugo.io/) - Static site generator
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) - Hugo theme
- GitHub Pages - Hosting

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended version recommended)
- Git

## Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/kanelv/kanelv.github.io.git
   cd kanelv.github.io
   ```

2. Initialize the theme submodule:
   ```bash
   git submodule update --init --recursive
   ```

3. Start the development server:
   ```bash
   hugo server -D
   ```

4. Open your browser and visit `http://localhost:1313`

## Creating New Content

### New Blog Post
```bash
hugo new blogs/your-post-title.md
```

### New Project
```bash
hugo new projects/your-project-name.md
```

## Building for Production

```bash
hugo --minify
```

The generated static files will be in the `public/` directory.

## Deployment

This site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch.

## License

This project is open source and available under the [MIT License](LICENSE).
