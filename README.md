
### 🐳 Docker Containers 🛳️📦

> ## https://labs.play-with-docker.com/

 - **Docker** helps you package everything your ` app needs (like code, libraries, and dependencies) ` into a neat, portable container. 
 - This way, you can run your app on any machine, and it’ll work just like it did on your own. I

> ## Build, Ship and Run Anywhere

In Docker terms:
  
  - `Build`: Create Docker images with all the dependencies and configurations your application needs.
  
  - `Ship` : Distribute these images through a `Docker registry`, so they can be accessed from anywhere.
  
  - `Run`  : Deploy the images as containers on any environment or platform, ensuring consistent performance regardless of where they are executed.


## Let's Get Started
### 1. Create a Dockerfile

  **Docker** builds images by reading the instructions from a **Dockerfile**. 
  A Dockerfile is a **text document** that contains all the commands a user could call on the command line to assemble an image.

#### Mnemonic to remember some most used commands in a Dockerfile 
##  > **"Funky Workers Cook Regularly, Examining Health Constantly"**
  
   - **F**unky – **FROM** (base image)
   - **W**orkers – **WORKDIR** (set working directory)
   - **C**ook – **COPY** (copy files)
   - **R**egularly – **RUN** (execute commands)
   - **E**xamining – **EXPOSE** (open ports)
   - **H**ealth – **HEALTHCHECK** (check container health)
   - **C**onstantly – **CMD** (default command)
 
