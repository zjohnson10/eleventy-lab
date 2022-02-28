### [Return to posts page](posts)

# Getting Started with Docker

Before getting started with Docker, it is important to talk about why this technology is so important in the realm of web development. Docker acts as a way to bypass using VMs and having to run many OSs on a system at one time. It allows a user to run applications in containers, which are 
> standardized executable components combining application source code with the operating system (OS) libraries and dependencies required to run that code in any environment.

All that to say that containers make it easy to develop, build, and deploy applications at a very high level. 

### Getting Started
The best way to start using docker is to follow this tutorial [here](https://www.docker.com/101-tutorial). The tutorial gives a simple approach to docker and helps to create a simple Todo list web app. The final product after adding a few list items looks something like this:

![Finished Product of ToDo App](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/r5zwqulwxm1uwxiwfxvm.png)

### Play with Docker
Play with Docker is a web-based lab environment for exploring and developing your apps that can be found [here](https://www.docker.com/play-with-docker). The 101 tutorial eventually starts using Play with Docker as well, so if you follow that, you will become familiar with Play with Docker.

### Create a Dockerfile for NASA Image Search Repo
In our lab, we created a news api microservice that basically fetches articles from a news api and then deployed it onto Play with Docker. The github can be found [here](https://github.com/heyMP/news-api-workshop). We can do something very similar with the NASA Image Search microservice we created [here](https://github.com/IST402-Group-E/ip-project). We can write a Dockerfile to be able to deploy our microservice on Play with Docker.

We will have a Dockerfile on both the frontend and backend sides of our microservice. The frontend (part where the user interacts) will look something like this:

![Frontend Dockerfile code](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/q4dgf1o070arebejwj3n.png)

And the backend Dockerfile will look something like this:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9no9dplejr4cz79waqy4.png)

These files are being read by Play with Docker to help deploy our microservice on their platform. Some things will need to be changed in each file and shifted around, but for the most part, the shell of the microservice and deploying it are the same.