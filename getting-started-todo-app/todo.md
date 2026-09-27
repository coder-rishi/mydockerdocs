# Getting started with Docker

With a prepared todo-app, go through some basic steps:
1. Get some ready-to-run code from github: git clone https://github.com/docker/getting-started-todo-app
 - This repo already contains a compose.yaml file that docker compose uses to build individual containers for each service.\

2. Start the dev stack: $ docker compose up --build --detach 
 - --detach leaves the containers running in the background, and --build builds the images
 - This step also connects these to localhost.
 - $ docker ps lets you see the running containers.

3. Build the image to package everything together using the Dockerfile: docker build --tag <USERNAME>/getting-started-todo-app .
 - the . at the end tells docker to find the Dockerfile in the repo.

4. Create a container from the image you built: docker run --detach --name todo --publish 8080:80 <USERNAME>/getting-started-todo-app
 - this makes a container and runs it on localhost:8080.
 - Now the frontend APIs and the backend sql interfaces are running together in one single package, instead of different containers. The Dockerfile provides a procedure for docker to create such a container.

5. Share your image on Docker Hub: $ docker login && docker push <USERNAME>/getting-started-todo-app
 - basically publishes an image of your container (not your container itself) so that others can pull it onto their local machines and repeat the same process.

6. Optional clean-up: $ docker rm --force todo && docker compose down --volumes
 - removes the todo container and all the service containers (volumes?)
 - $ docker ps and $ docker compose ps should give empty tables now, unlike before (hopefully).

## Questions to self:
* What is the difference between a container and an image?
* What are volumes?
* How are steps 2 and 4 fundamentally different?
* How did the app run coherently when the existing containers were actually separate after step 2?
