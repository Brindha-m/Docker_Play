
### 🐳 Docker Containers 🛳️📦

> #### Online Labs - [Docker Play Lab](https://labs.play-with-docker.com/)

> #### For Windows Download - [Docker Desktop](https://www.docker.com/products/docker-desktop/)

<img width="700" src="https://github.com/user-attachments/assets/92a6b722-5bb6-4d38-9790-a233f7c2641b">

<br>

- #### **Docker** helps you package everything your ` app needs (like code, libraries, and dependencies) ` into a neat, portable container. 
- #### This way, you can run your app on any machine, and it’ll work just like it did on your own.
  
<img width="700" alt="{F7F7D4DB-DC3E-43CE-8047-ADAE82AE5C94}" src="https://github.com/user-attachments/assets/e1a5cd62-ef10-4851-9dbb-09e4f5b33136">

 <br>

> ## Build, Ship and Run Anywhere

In Docker terms:
  
  - `Build`: Create Docker images with all the dependencies and configurations your application needs.
  
  - `Ship` : Distribute these images through a `Docker registry`, so they can be accessed from anywhere.
  
  - `Run`  : Deploy the images as containers on any environment or platform, ensuring consistent performance regardless of where they are executed.


### Check Docker version in terminal

<img width="700" alt="{6CA32684-3B8E-4BF0-BD4C-F8DA9DD8F060}" src="https://github.com/user-attachments/assets/fd0840be-8b79-4d44-b2c1-3fd2baae9391">

## Let's Get Started
### 1. Create a Dockerfile - Containerize an application

  **Docker** builds images by reading the instructions from a **Dockerfile**. 
  A Dockerfile is a **text document** that contains all the commands a user could call on the command line to assemble an image.

  #### Mnenomic covers some of common Dockerfile commands
  Sure! Here’s a mnemonic that covers all those commands:

  **"Funky Workers Cook Regularly, Examining Health Constantly"**
  
  - **F**unky – **FROM** (base image)
  - **W**orkers – **WORKDIR** (set working directory)
  - **C**ook – **COPY** (copy files)
  - **R**egularly – **RUN** (execute commands)
  - **E**xamining – **EXPOSE** (open ports)
  - **H**ealth – **HEALTHCHECK** (check container health)
  - **C**onstantly – **CMD** (default command)

  <img width="700" src="https://github.com/user-attachments/assets/07252c05-b476-44a4-8944-912c72b9e179">
  

```dockerfile

# Use a base image - This sets up the container with Python 3.10 installed.
FROM python:3.10-slim

# This sets the working directory inside the container
WORKDIR /app

# Copy the requirements file to the working directory
COPY requirements.txt .

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code to the working directory
COPY app.py .

# Expose the port that the app will run on
EXPOSE 8000

# Create a .streamlit directory if needed
RUN mkdir ~/.streamlit

# Set the default command for the container to run the app with Streamlit
ENTRYPOINT ["streamlit", "run", "app.py"]

# Health check to verify that the container is running correctly
HEALTHCHECK CMD curl --fail http://localhost:8000/ || exit 1

 ```

#### Navigate to the folder where the Dockerfile and main files.

<img width="700" alt="{23DAB79A-221C-4351-813F-BD7668594783}" src="https://github.com/user-attachments/assets/b59cd638-d3a1-47ca-a9d0-9b8dfcfb633c">
<br>

### 2. Build the app's image

<img width="200" src="https://github.com/user-attachments/assets/257787c1-24e2-4f8b-b909-945bf58a52f3">


```dockerfile
 # -t is the tag name
 docker build -t <image name> .

```

```dockerfile
 docker images
```
<img width="700" alt="{5D1FD38D-FF06-4035-BE67-C4DCCC77986B}" src="https://github.com/user-attachments/assets/2f26cb50-22fd-4393-9de1-79a9039dfa33">

<br>

#### New image and container will be created in the docker desktop

<img width="700" alt="{C136CD6C-D81F-4052-99CD-585631E7148B}" src="https://github.com/user-attachments/assets/d11b7e7f-f8fd-42d2-8b66-0d81a7b21daa">

<br>

<img width="700" alt="{D93F7C23-A96A-44E7-B299-AC84813F6073}" src="https://github.com/user-attachments/assets/79e073b3-75dc-43cd-b2f6-358beb2dc385">

<br>

<img width="700" alt="{550061DC-E64A-44B3-9D48-1A07E9435061}" src="https://github.com/user-attachments/assets/462ec4a4-d267-486f-8c7c-476ad8599f3d">

<br>

### 3. Run the docker container
```dockerfile
 docker run -p 80:80 <imagename>
             # OR
 docker run -dp 80:80 <imagename>
```

#### Note

 - **`-d`**: This runs the container in **detached** mode.
 - **`-p`**: The additional `p` flag (`-dp`) stands for **publish port mapping** between the host and the container.
 - **`80:80`**: As with the first command, this maps port `80` of the host machine to port `80` of the container.

 
<img width="700" alt="{41D1B46A-A572-46BF-821A-2C2312ABDA1E}" src="https://github.com/user-attachments/assets/3d37d997-08c2-47fa-9cd5-894264c5414a">

<br>

#### To view your app

<img width="700" alt="{ABBE22E8-71B5-452C-BCFB-8C5563191C29}" src="https://github.com/user-attachments/assets/50b71467-b263-452d-aa21-a121307ee41a">

<br>

### 4. Share the Project using Docker HuB Registry 
- To Create a repository in dockerhub. Either Use CMD OR Direct website [steps](https://docs.docker.com/get-started/workshop/04_sharing_app/)

  <img width="700" alt="{ACF518FD-6814-4848-AB73-F62FF5781E2C}" src="https://github.com/user-attachments/assets/848640d3-9bbe-4f3e-a949-a36613a7f456">

  - ## docker tag and push
    
    ```
    >docker login -u YOUR-USER-NAME
    
    docker tag imagetagname YOUR-USER-NAME/imagetagname

    dokcer push YOUR-USER-NAME/imagetagname
    
    ```
  <img width="700" alt="{62571B08-9F83-4209-BB35-4F147FFC121C}" src="https://github.com/user-attachments/assets/df4dba26-6d04-4874-b02b-bd2e7ede8096">

  <img width="769" alt="{F273A5DC-EC0E-4D73-BAD8-9677EC5C42C9}" src="https://github.com/user-attachments/assets/0c94355f-1c1f-4bdd-9a97-f3ad9dd254f0">


<img width="700" alt="{10232255-A681-42FA-AAF0-D07DE48D934B}" src="https://github.com/user-attachments/assets/9cab75eb-6bf1-46ba-ab75-32d7261b3e30">
<img width="700" src="https://github.com/user-attachments/assets/f4ac754e-511f-4999-98cc-567a4ec20358">

<br>

```dockerfile
docker build --platform linux/amd64 -t YOUR-USER-NAME/getting-started .

docker run -p 80:80 USER_NAME/imagename(i.reponame)
```
<img width="700" alt="{8D86E244-CDA0-4478-83D7-ADC80022CF1C}" src="https://github.com/user-attachments/assets/ec093af5-db55-4c30-93b5-5bac3713b015">
<img width="700" alt="{E9294307-B828-48DE-9C06-0CE786BF5694}" src="https://github.com/user-attachments/assets/67a8b3a7-260d-4294-b7e9-130f94bc817d">



### Logout from docker account and just pull the public repo and you will be able to run the docker container.
<img width="700" alt="{DD07D8AB-5DE3-4392-8923-1D9E8329BE59}" src="https://github.com/user-attachments/assets/be86407d-46ad-4b7d-b639-7da8ba846082">


# TODOS: docker compose 
