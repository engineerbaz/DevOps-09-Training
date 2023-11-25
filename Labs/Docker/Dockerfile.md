# Dockerfile
Dockerfile is like writing a set of instructions for Docker to build an image of our application. 
It's a text document that contains all the commands a user could call on the command line to assemble an image.

### Open a text editor and create a file named Dockerfile (no file extension) for our project directory.
```sh
nano Dockerfile
```
### add content in Dockerfile and save 

```sh

#Node.js official  image
FROM node:14

# Working directory in container
WORKDIR /app

# Copy package.json to the working directory
COPY package*.json ./

# Install application dependencies
RUN npm install

# All files Copy the application code and paste inside the container
COPY . .

# Expose port that the application will run on
EXPOSE 3000

#  CMD to run our application
CMD ["node", "app.js"]

```

### Build Dockerfile image we use -t flag -t = terminal

- docker build -t image-name . 

```sh
docker build -t myimage .
```

### Run Docker container:- Now we can run a container build Dockerfile image 
### and attach port 3000 -p = port and use -d flag -d mean deattach 

- docker run -d -p 3000:3000 image-name 

```sh
docker run -d -p 3000:3000 myimage       #myimage is image name
```            
##### OR we can attach container name 

- docker run -d -p 3000:3000 --name container-name image-name 

```sh
docker run -d -p 3000:3000 --name mycontainer myimage               # mycontainer is container name, myimage is image name 
```


## More Dockerfiles 

```sh
---- LAB 1 ---

FROM httpd:2.4
COPY ./public-html /usr/local/apache2/htdocs/

docker build -t 4lab .

docker run -d --name myapp1 -p 8089:80 myimage:1
```

----LAB 2 ----

```sh
FROM nginx:latest
MAINTAINER BAZTechKnow 
COPY . /usr/share/nginx/html
# comment
ENV abc=hello

---
docker build -t lab1 .
docker run -dit -p 8081:80 lab1
```

