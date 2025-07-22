# Next.js Blog Sample - Runner Plugin Ready

This portfolio is built with **Next.js** and a library called [Nextra](https://nextra.vercel.app/). It allows you to write Markdown and focus on the _content_ of your portfolio.

## ✨ Features

-   Automatically configured to handle Markdown/MDX
-   Generates an RSS feed based on your posts
-   A beautiful theme included out of the box
-   Easily categorize posts with tags
-   Fast, optimized web font loading
-   **🐳 Docker deployment ready**
-   **🚀 Backstage Runner Plugin compatible**
-   **💚 Health check endpoint included**

## 🐳 Docker & Runner Plugin Support

This template is fully configured for deployment with the **Backstage Runner Plugin**:

-   **Docker Configuration**: Multi-stage Dockerfile optimized for production
-   **Health Monitoring**: Built-in health check endpoint at `/api/health`
-   **Runner Annotations**: Pre-configured catalog-info.yaml with runner annotations
-   **Port Configuration**: Standardized on port 3000 for consistency

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

1.  Update your name in `theme.config.js` or change the footer.
2.  Update your name and site URL for the RSS feed in `scripts/gen-rss.js`.
3.  Update the meta tags in `pages/_document.tsx`.
4.  Update the posts inside `pages/posts/*.md` with your own content.

## 🔧 How to Change the Port (e.g., 3000 → 3001)

If you need to change the default port, here are all the steps and modifications required. The following example changes the port from 3000 to 3001.

### **Files to Modify**

1.  **`.runner/config.yml`**
2.  **`package.json`** - Update scripts
3.  **`Dockerfile`** - Update PORT and EXPOSE
4.  **`healthcheck.js`** - Update port reference
5.  **`pages/api/health.ts`** - Update default port in response
6.  **`README.md`** - Update documentation (as we're doing now!)

### **Summary of Changes**

Here is a summary of all the code changes required to switch from port 3000 to 3001.

#### 1. **`.runner/config.yml`**

```yaml
runner:
  type: docker
  dockerfile: ./Dockerfile
  ports: [3001]  # Changed from [3000]
  environment:
    NODE_ENV: production
    PORT: "3001"  # Changed from "3000"
    HOSTNAME: "0.0.0.0"
```

#### 2. **`package.json`**

```json
"scripts": {
  "dev": "next --port 3001",
  "start": "next start --port 3001",
  "docker:run": "docker run -p 3001:3001 nextjs-blog-sample"
}
```

#### 3. **`Dockerfile`**

```dockerfile
ENV NODE_ENV=production
ENV PORT=3001  # Changed from 3000
ENV HOSTNAME=0.0.0.0

# Expose port
EXPOSE 3001  # Changed from 3000
```

#### 4. **`healthcheck.js`**

```javascript
const options = {
  host: 'localhost',
  port: process.env.PORT || 3001,  // Changed from 3000
  path: '/api/health',
  timeout: 2000,
};
```

#### 5. **`pages/api/health.ts`**

```typescript
port: process.env.PORT || '3001'  // Changed from '3000'
```

### **🚀 Testing Steps**

1.  **Rebuild the Docker image:**
    ```bash
    npm run docker:build
    ```

2.  **Run the container:**
    ```bash
    npm run docker:run
    ```

3.  **Verify the application is accessible at:**
    -   ✅ `http://localhost:3001`
    -   ✅ Health check: `http://localhost:3001/api/health`

The template will now be fully configured to run on port 3001 instead of 3000! 🎉

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

1.  **Create the component** using this template in Backstage
2.  **Navigate to the component** in your Backstage catalog
3.  **Use the Runner Plugin** to deploy with one-click
4.  **Monitor the deployment** through the Runner Plugin interface

### Runner Plugin Configuration

The template includes:

-   **`.runner/config.yml`**: Docker configuration for the Runner Plugin
-   **`Dockerfile`**: Multi-stage build optimized for Next.js
-   **Health Check**: Endpoint at `/api/health` for container monitoring
-   **Catalog Annotations**: Pre-configured runner annotations

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