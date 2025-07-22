# Next.js Blog Sample - Runner Plugin Ready

This portfolio is built with **Next.js** and a library called [Nextra](https://nextra.vercel.app/). It allows you to write Markdown and focus on the _content_ of your portfolio.

## ✨ Features

- Automatically configured to handle Markdown/MDX
- Generates an RSS feed based on your posts
- A beautiful theme included out of the box
- Easily categorize posts with tags
- Fast, optimized web font loading
- **🐳 Docker deployment ready**
- **🚀 Backstage Runner Plugin compatible**
- **💚 Health check endpoint included**

## 🐳 Docker & Runner Plugin Support

This template is fully configured for deployment with the **Backstage Runner Plugin**:

- **Docker Configuration**: Multi-stage Dockerfile optimized for production
- **Health Monitoring**: Built-in health check endpoint at `/api/health`
- **Runner Annotations**: Pre-configured catalog-info.yaml with runner annotations
- **Port Configuration**: Standardized on port 3000 for consistency

### Quick Docker Deployment

```bash
# Build the Docker image
npm run docker:build

# Run the container
npm run docker:run
```

The application will be available at `http://localhost:3000`

https://demo.vercel.blog

## Configuration

1. Update your name in `theme.config.js` or change the footer.
1. Update your name and site URL for the RSS feed in `scripts/gen-rss.js`.
1. Update the meta tags in `pages/_document.tsx`.
1. Update the posts inside `pages/posts/*.md` with your own content.

## Deploy your own

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/vercel/next.js/tree/canary/examples/blog&project-name=portfolio&repository-name=portfolio)

## How to use

Execute [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init), [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/), or [pnpm](https://pnpm.io) to bootstrap the example:

```bash
npx create-next-app --example blog my-blog
```

```bash
yarn create next-app --example blog my-blog
```

```bash
pnpm create next-app --example blog my-blog
```

Deploy it to the cloud with [Vercel](https://vercel.com/new?utm_source=github&utm_medium=readme&utm_campaign=next-example) ([Documentation](https://nextjs.org/docs/deployment)).

## 🚀 Backstage Runner Plugin Deployment

This template is designed to work seamlessly with the Backstage Runner Plugin:

1. **Create the component** using this template in Backstage
2. **Navigate to the component** in your Backstage catalog
3. **Use the Runner Plugin** to deploy with one-click
4. **Monitor the deployment** through the Runner Plugin interface

### Runner Plugin Configuration

The template includes:

- **`.runner/config.yml`**: Docker configuration for the Runner Plugin
- **`Dockerfile`**: Multi-stage build optimized for Next.js
- **Health Check**: Endpoint at `/api/health` for container monitoring
- **Catalog Annotations**: Pre-configured runner annotations

### Health Check Endpoint

The application includes a health check endpoint at `/api/health` that returns:

```json
{
  "status": "healthy",
  "timestamp": "2024-01-01T00:00:00.000Z",
  "uptime": 123.456,
  "environment": "production",
  "version": "1.0.0",
  "port": "3000"
}
```
