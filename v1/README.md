# Angular-D
The pleasure of Angular linked to the utility of a Docker container

## Version 1

### Usage with new Angular app

Don't use this version for production, only for demo purpose

Create your app with Angular CLI
> ng new [app-name]

Copy the `Dockerfile` and `.dockerignore` inside your Angular folder project


Start your app for the first time with 
> ng serve

You can see for the first time how your application looks like, but in reality this is the default application provided by Angular, don't worry later you can provide your own application, let's continue 😉.

Exit the serve process
`cd` inside your folder app, open `package.json` and replace: 
> "start": "ng serve",

to 

> "start": "ng serve --host 0.0.0.0 --poll",

This will allow access to the `ng serve` from outside the container \

Build the image from the `Dockerfile`
> docker build -t [image-name] .

After finishing the construction of the image, we will launch the container by binding the port of the host.

>  docker run -d -p 4200:4200 --name [container-name] [image-name]


You can replace with any port you want, you just have to keep the link to the `4200` port used by `ng serve`.


You can access the [localhost:4200](http://localhost:4200) to see the same application, the difference in this case we do not have an angular process running on our host machine but in a Docker container.

 In fact this type of container is not useful because if we want to change any component of our application we have to reload all the Docker images/containers, in the next version we will create a real development container with NFS volumes to take advantage of the hot reloading. 

You can find my Docker image with the steps that we just follow on [Docker Hub](https://hub.docker.com/r/mravily/angular)