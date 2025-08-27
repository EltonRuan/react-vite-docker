<div align='center'>
 <img style="width:100%" src="https://capsule-render.vercel.app/api?type=soft&height=200&color=FFFFFF&text=React%20Vite%20Nginx%20Docker&fontSize=50&fontAlign=50&strokeWidth=0&descAlignY=80&stroke=000000">
</div>

<nav align="center">
  <h2>🔗 NAVIGATION </h2>
  <p>
   <a href="#about-this-project">ABOUT THIS PROJECT</a> |
   <a href="#setup">SETUP</a> |
   <a href="#running-the-application">RUNNING THE APPLICATION</a> |
   <a href="#final-considerations">FINAL CONSIDERATIONS</a>
  </p>
</nav>

## ABOUT THIS PROJECT

This project is a **React Single Page Application (SPA) built with Vite and served via Nginx** using **Docker**.

It already contains the complete React project structure and Nginx configuration, ready to run inside containers without any local installation except Docker.

## SETUP

### PREREQUISITES

* Docker Desktop installed (Linux containers mode)
* Docker Compose
* Project cloned locally

### STARTING THE CONTAINERS

From the project directory, run:

```bash
docker-compose up -d --build
```

This will:

* Build the Docker images (Node/Vite for building, Nginx for serving) if not already present
* Create and start the containers

## RUNNING THE APPLICATION

After the containers are up and the build completes, your application will be served by Nginx automatically.

It will be accessible at:

```
http://localhost:3000
```

### IF THE BUILD FAILS

If the build fails (common issues with ESM modules in Vite + React), follow these steps:

1. Make sure Node version in Dockerfile is compatible (Node 18 recommended):

```dockerfile
FROM node:18-alpine AS build
```

2. Ensure `package.json` includes:

```json
{
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^5.0.0",
    "vite": "^5.4.19"
  }
}
```

3. Rebuild the containers:

```bash
docker-compose down -v
docker-compose up --build -d
```

After this, the app should be built and served without errors.

## FINAL CONSIDERATIONS

This Docker setup allows you to:

* Run a modern React + Vite SPA without installing Node or Nginx locally
* Ensure consistent behavior across any machine
* Simplify development, testing, and deployment

<p><strong>© 2025 EltonRuan. All rights reserved.</strong></p>

<footer align="center">
 <img style="width:100%" src="https://capsule-render.vercel.app/api?type=soft&height=20&color=FFFFFF&fontSize=50&fontAlign=50&strokeWidth=0&descAlignY=80&stroke=000000&reversal=false&section=footer">
</footer>
