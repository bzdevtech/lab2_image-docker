# Static Website — Docker Image

## 1. Project Overview

This project demonstrates how to containerize a static website using Docker and Nginx.

The website is based on the `static-website-example` project from Cloud Academy and uses the Dimension template by HTML5 UP.

**Objective:** Build a Docker image, run a container, and verify that the website is accessible through a web browser.

## 2. Technologies Used

- **Docker** — builds the image and runs the container.
- **Nginx** — serves the static website.
- **HTML, CSS and JavaScript** — provide the website content and presentation.
- **GitHub Codespaces** — provides the cloud development environment.

## 3. Project Structure

lab2_image-docker/
├── assets/          # Website styles, scripts and other assets
├── error/           # Error-page resources
├── images/          # Website images
├── Dockerfile       # Instructions to build the Docker image
├── index.html       # Main website page
├── LICENSE.MD       # Original license information
└── README.MD        # Project documentation


## 4. Dockerfile

The Dockerfile defines how the website image is built.

FROM nginx:alpine

COPY . /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


### Instruction Explanation

FROM nginx:alpine : Uses a lightweight Nginx image as the base.
COPY . /usr/share/nginx/html : Copies the project files into Nginx's web root.
EXPOSE 80 : Documents the port used by Nginx inside the container.
CMD [...] : Starts Nginx in the foreground.

## 5. Build the Docker Image

Run this command from the directory containing the Dockerfile:
`docker build -t static-site-dimension` .

**Purpose:** Builds a Docker image named `static-site-dimension`.

Verify that the image exists: `docker images` 


## 6. Run the Container

Start a container from the image:

`docker run --name dimension -d -p 8080:80 static-site-dimension` 

### Command Explanation

- `--name dimension`: assigns the name `dimension` to the container.
- `-d`: runs the container in the background.
- `-p 8080:80`: maps host port `8080` to container port `80`.
- `static-site-dimension`: specifies the image to use.

## 7. Access the Website

In GitHub Codespaces:

1. Open the **Ports** tab in VS Code.
2. Locate port `8080`.
3. Click the forwarded address to open the website in your browser.

The Nginx welcome page should be replaced by the static website when the project files have been copied correctly into the web root.

## 8. Verify the Container

Check the running containers: `docker ps` 

View the container logs: `docker logs dimension` 

Inspect the container configuration: `docker inspect dimension`

## 9. Stop and Remove the Container

Stop the container: `docker stop dimension`

Remove the stopped container: `docker rm dimension`

The Docker image remains available after the container is removed.


## 10. License and Attribution

This repository is based on the public `static-website-example` project from Cloud Academy.

The original website uses the Dimension template by HTML5 UP. Keep the original license and attribution files when redistributing the project.