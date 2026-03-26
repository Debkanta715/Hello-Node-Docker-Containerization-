# app1-hello (Node.js)

A simple Node.js Express application that returns a JSON greeting and environment info. Designed for containerization with Docker.

## Features

- Express server with a single `/` endpoint
- Returns a JSON object with a message, environment variable, and container hostname
- Ready for Docker deployment

## Project Structure

```
app.js           # Main application file
package.json     # Node.js dependencies
Dockerfile       # Docker build instructions
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (if running locally)
- [Docker](https://www.docker.com/) (for containerization)

### Install & Run Locally

1. Install dependencies:
   ```sh
   npm install
   ```
2. Start the server:
   ```sh
   node app.js
   ```
3. Visit [http://localhost:3000](http://localhost:3000) in your browser.

### Run with Docker

#### 1. Build the Docker image

You can build the Docker image with your own Docker Hub username and a custom image name. Replace `debkantadey29` with your Docker Hub username if you want to push to Docker Hub.

```sh
docker build -t debkantadey29/hello-node .
```

Or use a different image name:

```sh
docker build -t debkantadey29/hello-node1 .
```

#### 2. Run the Docker container

Run the container with a custom name and port mapping:

```sh
docker run -d --name hello-node -p 3000:3000 debkantadey29/hello-node
```

Or, if you used a different image name:

```sh
docker run -d --name hello-node1 -p 3000:3000 debkantadey29/hello-node1
```

#### 3. Check running containers

```sh
docker ps
```

#### 4. Push the image to Docker Hub (optional)

If you want to upload your image to Docker Hub:

```sh
docker push debkantadey29/hello-node
# or
docker push debkantadey29/hello-node1
```

#### 5. Access the app

Visit [http://localhost:3000](http://localhost:3000) in your browser to see the app running in Docker.

#### Environment Variables

- `PORT` (default: 3000)
- `ENV_VALUE` (optional, shown in response)

## Example Response

```
{
  "message": "Hello from Simple App (Node)",
  "env": "No env set",
  "container": "<container-hostname>"
}
```

---

This is a minimal Node.js app for demo or learning purposes. Feel free to modify and extend!
