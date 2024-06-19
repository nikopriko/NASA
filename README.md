# NASA

## NASA

This document provides instructions on how to build and run a Docker container for the NASA static website.

## .dockerignore

Create a `.dockerignore` file in the root directory to prevent unnecessary files from being copied into the Docker image:

```
Dockerfile
.dockerignore
```

## Build and Run the Docker Container

Follow these steps to build and run the Docker container:

1. Open a terminal and navigate to your project directory.

2. Build the Docker image:

   ```sh
   docker build -t nasa .
   ```

3. Run the Docker container:

   ```sh
   docker run -d -p 8080:80 nasa
   ```

Your static website should now be accessible at `http://localhost:8080`.

## Explanation

- **FROM nginx:alpine**: Uses the official Nginx image based on Alpine Linux, which is lightweight.
- **COPY . /usr/share/nginx/html**: Copies all the files from your current directory (where `index.html` and `styles.css` are located) to the Nginx HTML directory.
- **EXPOSE 80**: Exposes port 80, which is the default port that Nginx listens to.
- **CMD ["nginx", "-g", "daemon off;"]**: Starts Nginx in the foreground (daemon off) to keep the container running.