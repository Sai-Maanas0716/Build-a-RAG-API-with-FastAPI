<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Containerize a RAG API with Docker

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-devops-docker)

**Author:** S Maanas  
**Email:** smaanas03@gmail.com

---

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_x7y8z9a0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to containerize a RAG API with docker. I'm doing this project to learn how to make sure that the api that we have created called "RAG API" can be able to execute or to run on every device, not only on a single pc in which I have created through the docker container instance for delivery of api every where in every device.

### Key services and concepts

Services I used were docker desktop for the local machine  to create the images for the application with the help of the docker file instructions and used the ollama client, created speacially for the docker to use the service from the docker container itself and also the uvicorn to run the fast api server behind the execution of the api that we have created and also the fast api python functionalities for the easy creation of the api functions or the endpoints. Key concepts I learnt include why docker is required and how the tag and pushing of the image of the app is done after creating the image, what makes pusing the image to the docker hub can make the deployment of the app through the cloud services easy or take it to reach this point, I have seen what makes the things go wrong when we run the commands. I have learned about how the tag to the images can actually help the docker hub and also the flow of instructions that can be executed using the docker file.

### Challenges and wins

This project took me approximately 5 days to complete the entire thing. The most challenging part was debugging the internel server error which occurs when the ollama client don't run locally or haven't started ollama or it can when the docker container requests the ollama service but, the mapping of the special host created for ollama client to the original host ip configuration is not done or happens when the special redirect link to the original ollama client in the local host is not created. It was most rewarding when the app finally runs after debugging the error that I have faced and finally the request is being send and the response from the api is finally appearing in the terminal.

### Why I did this project

I did this project because, I wanted to do deploy the app or the any kind of product that I have created so that I can be able to face the real problems like more users, more data and also the complex data that may cause the current implementation or the code that I have written for this app break and needs the better logic and the implementation that I'm currently using.

want to see how the real data from the world causes the break in the current implementation.

---

## Setting Up the RAG API

In this step, I'm setting up the workspace of RAG API and activate our venv, which was created for RAG API. The RAG API is one kind of api integrating the api functionaliies with ai response and searching through the documents in the knowledge base and retrieving the docs that are relevant to the query that user has asked through the api endpoint called /query in the browser url placeholder, where it does the semantic search using the embeddings that are directly created and stored in the chromaDB where the large docs will be broken down to chunks for to occupy the less space of the context window of the model that we are using through ollama.

### API setup and workspace

In this step, I'm creating the container for my RAG API so it to run in everyones devices. A virtual environment is the isolated environment in your computer, that allows the one who wants to run it separately without clashing of the current versions of the certain software with the global versions that were already  installed in the computer. I need it because, it will prevent from the python dependencies and it's versions clashing out with the global python dependencies and it's versions.

### Dependencies installed

The packages I installed are ollama, FastAPI, chromaDB and uvicorn. FastAPI is used for to build the api which means creating the api endpoints and the functionalities for that using the built-in functions which makes it easy to create using its frameworks available in the python language. Chroma is used for to store the knowledge base that llm uses to generate the response from the quesry asked by the users using the sematic search between the query embeddings and the embeddings that are indexed with the chunked data to save the context window space. Uvicorn is used for the api to run like a server that executes the api endpoints waiting for the query to be asked. Ollama is used for the llm to run in the local machine which it provides the interface or the ability to run those models locally without using the cloud models.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_c9d0e1f2)

### Local API working

I tested that my API works by invoking the api requesting the query endpoint with the message that I want to ask. The local API responded with the set of keys and values with the answer in the content section along with the meta data of the response. This confirms that the api endpoint or the RAG API is completely working fine with no errors when asking the query to the api and no problem with the endpoint query or the model that we are working with to generate the response from the retrieved documents.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_v5w6x7y8)

---

## Installing Docker Desktop

### Docker Desktop setup

Docker Desktop is the interface where it gives the containerize feature for the our app. I installed it because, I need it for my app or RAG API to be deployed in the real world. Containerization will help my project by creating the container for the project or app or our RAG API and does the packaginf of all our dependencies required for the app to run in everyones devices, making the app available to everyone.

### Docker verification

I verified Docker is working by running the bash command . The hello-world container proves that it is perfectly installed and working correctly.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_i9j0k1l2)

---

## Creating the Dockerfile

In this step, I'm building a RAG API. RAG stands for Retrieval augmented Generation. I'm creating files like embed.py for adding the embeddings of the documents to the knowledge so that the docs gets chunked and indexed with the emneddings so that RAG will do the sematic search between the query and the docs through the embeddings and gets the docs that are relevant to the query asked and then it uses llm to summarize the docs retrieved from the search. It reduces the hallucinations of the model.

### How the Dockerfile works

A Dockerfile is a text file with the instructions to create the docker image. It specifies the bsae image, install the packages and the dependencies, copies the code and defines how to run your app. The key instructions in my Dockerfile are : it starts with the python 3.11 and then it sets the working directory to /app and then it installs the system dependencies (curl) and copies the code of your codebase and then it installs the packages required for the app to run and then it pre-computes the embeddings required to do the sematic search, then it exposes the port and then it will start the api server. FROM tells Docker to start with the python 3.11. COPY is used for to copy the code files. RUN executes the embeddings python file CMD defines the instructions and the commands to start the api server at the particular port like the sequence of commads to be followed to start the API server.

### Containerized API test results

Testing the API after containerization proved that the RAG API is working correctly by running the container at port 8000 The difference between running locally and in Docker is that it executes in the separate environment, not in the host's system environment and the dependencies and the docker containers are isolated from the local host network. The difference is that the host runs the ollama and requests the ollama or the tinyllama services locally by the host itself and in the docker, the container itself acts as the host and asks the ollama services from the container itself, using the host IP address directly from the container  Containerization helps because, we don't need to share the tools and the other things that are required to run or use this RAG API to everyone. They can use this service with the help of the containers that executes the API and makes available to everyone without running the server and the models in their own devices.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_o1p2q3r4)

---

## Building and Running the Container

### Docker image build complete

Building a Docker image involves writing the instructions for how the docker image should be created, in the docker file. I verified my Docker image was built successfully by running the command - "docker image | Select-String rag-app" and it gave the output where it shown the lastest created image with the tag latest. This confirms that my API is now containerized because, the docker image which is used for to take the screen shot of the current application or for the packaging of my application, takes the current condition of my app and place it in the container by docker image using the docker file helping with the creation of the docker image.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_p9q0r1s2)

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_x7y8z9a0)

---

## Pushing to Docker Hub

In this project extension, I'm pushing to Docker Hub. Docker Hub is the interface where the people can tag and push their image of the application or it is a registery service for storing and sharing Docker images. Your user name becomes the part of the docker images, that they made and can be seen by the other peers or the users who wants to use this service. I'm doing this because, this is essential for sharing the work, deploying to the production, CI/CD pipelines, and learning how container registeries work which depicts the same concept as AWS ECR, Google Container Registry, etc.

### Docker Hub push complete

I pushed to Docker Hub by first creating the account for the docker hub to maintain the repositories that we have created or the containers and I have used the command - "docker push your-username/rag-app". This name that we have tagged to the container tells the docker to use this account and store this repository into that particular account. Docker Hub is useful because, it helps in storing the images of the app where it stores the current screen shot of the app and makes it available to the users those are in the docker hub. The advantage of pushing to a registry is that we can share our work with the people on docker hub and it gives the sevices like version control for the docker images where only the updated parts of the images gets pushed if there any changes or any creations. It enables the CI/CD where it integrates the image building and pushing those into the automated deployment pipelines (to make it ready for the deployment) so we can easily deploy to clould platforms.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_m5n6o7p8)

### Pulling from Docker Hub

Pulling an image from Docker Hub means downloading the pre-built-in image into the users local machine and using the app features directly from their own devices without dowloading the requied dependencies and the packages for the app to run in their local machines. They can use the services of the app from just the download or pulling of the image of the particular owner or the person who is giving the app as a service. When I ran docker pull, Docker downloaded the image from the account that we have mentioned in the command. The difference between building locally and pulling from Docker Hub is that it reduces the time and the work and also it is useful for the people who finds difficulty in doing it from the scratch and debug is any version gets wrong or any environment which the people who are beginners in this particular field and also it is useful when the running of the app in their local machine puts a huge load on their local machine and it is useful when the app is very huge.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-docker_f5g6h7i8)

---

---
