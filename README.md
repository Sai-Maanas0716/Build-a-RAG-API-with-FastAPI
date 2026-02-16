<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a RAG API with FastAPI

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-devops-api)

**Author:** S Maanas  
**Email:** smaanas03@gmail.com

---

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_g3h4i5j6)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create our own RAG API with the help of FAST API which is a web framework that is used for building the api's easily. This RAG will retrieve the closer information regarding the user query by doing the semantic search between the embeddings of both query and the docs that are stored in the chroma database and then gives the docs to the llm through the template of the prompt and the llm generates the response by doing the summarization on the docs information. I'm doing this project to learn more about RAG and how to work with RAG and APIs that will help me in understanding the process of building the application which are build on llms.

### Key services and concepts

Services I used were the cost free access of the models from ollama and uvicorn for running the api server for the vreation of the fastAPI instance or created from that which is RAG API integrated with the ollama tinyllama model and also swagger UI interface for testing the api endpoint directly in the browser, also the logging and os packages for the operations or the services to be logged so that the developers can know about when and is the api endpoint or the api is being called or not. Key concepts I learnt include how to play with fast api and how to create the different api endpoints for making this RAG API do more works than what we have done here and also how the model of ollama is being integrated into the api along with the accessing the data from the database (chromaDB) by doing the similarity search for the given query which is using the post method to submit the query to the api endpoint and the actual search of the data is being happen giving the nearest 1 document.

### Challenges and wins

This project took me approximately two days to do. The most challenging part was to understand the workflow and the packages that I have used here. It was most rewarding to know how the api can be played with integration of the llm and how the actual api calls can answer the questions like real llm or real llm application interface can answer the user query with the loaded data  or the knowledge base that we have in the chromeDB.

### Why I did this project

I did this project because, I love to do the projects that related to RAG and how the api can be played along with them giving the actual response from the llm which is being integrated into the api endpoint method of api.

---

## Setting Up Python and Ollama

In this step, I'm setting up Python and Ollama. Python is a programming language that allows the programmers to build the web applications giving the required tools and the frameworks. Ollama is a llm which can be run locally in the personal computers of laptops. I need these tools because, to create the RAG API I need the frameworks available in the python through the fast api tools and the features which makes the building of this api very easy and also Ollama which helps me in generating the response after retrieving the documents by RAG.

### Python and Ollama setup

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_i9j0k1l2)

### Verifying Python is working

### Ollama and tinyllama ready

Ollama is the local llm provider that allows the user to run llm's on their own laptop without using the cloud services of llm which will eventually run out of the free tier and some can be costly to use the api calls. I downloaded the tinyllama model because it is the open source and free and can be used any time and however we want. The model will help my RAG API by generating the response from whatever the retrieval of the docs it did through the semantic search for the query given by the user.

---

## Setting Up a Python Workspace

In this step, I'm setting up the project and the required virtual environment and activate it for the project to keep the python dependensies safe and prevent the clashing of the python versions. I need it because, it is for to keep the python dependensies safe and prevent the clashing of the python versions.

### Python workspace setup

### Virtual environment

A virtual environment is the separate environment that gives the  project runs it own codebase in the sepearate desktop kind of environment without clashing with the global packages. I created one for this project to do the same thing for the project where it the python dependiea of the ollama and fast api will be stored and executed in this virtual envirinment only. Once I activate it, it opens into the seperate environment from the global python depedencies like seperate executable desktop. To create a virtual environment, I use the python command - python -m venv .venv.

### Dependencies

The packages I installed are fast api, uvicorn, chromaDB, ollama. FastAPI is used for processing the requests by the user by giving the framework to access the particular endpoint that actually asks the RAG to retrive the docs using semantic search and generation of the reponse at the end. Chroma is used for storing the docs where the linkage of the doc chunks and the embeddings related to that resides for the semantic search between the user query and the docs that are there from the start in the database. Uvicorn is used for running the fast api which listens to the user http requests and converts them into the python calls and then forward those requests to the correct api endpoint and does the same thing when the rag genearates the response. Ollama is used for receiving the retrieved docs related to the query asked by the user and then summarizes the docs and gives the response back to the user using the human conversation template as data on which training has done.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_u1v2w3x4)

---

## Setting Up a Knowledge Base

In this step, I'm creating the script that prepares the content for AI search. A knowledge base is a data hub that having the up to date information for the rag to work on this by converting the data into embeddings and does the semantic search given query and converting the query into embeddings. I need it because, giving this knowledge base for the rag to work on this by converting the data into embeddings and does the semantic search given query and converting the query into embeddings.

### Knowledge base setup

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_t1u2v3w4)

### Embeddings created

Embeddings are the ones that have the semantic meaning of the actual words listed in vectors and these are the ones that will allow the similarity search done by rag between the query embeddings and the embeddings that are stored in the database. I created them by using the bult-in function - add function given to the collections created by the client instantiated from the persistentClient, which can load the data as soon as it is available in the local machine. The db/ folder contains the documents and the embeddings of the chunks, broken down for the favour to the context window of the llm that we are going to get the response from the retrieved docs by RAG. This is important for RAG because, it is the only one that does the search for the answer or the related documents related to the query asked by the user and which is not there in the data which was used to train the model. So, this is required to get the up-to date data, where nowadays training data frequently can be expensive.

---

## Building the RAG API

In this step, I'm building a RAG API. An API is the interface where it lets the software retrieve and share data with other apps FastAPI is the web framework which will let me create the APIs very easily with the automated documentation for the api that I'm creating. I'm creating this because, I want the ai response from whatever the query might be related to the application that the user is using, so I want one api to retrieve the realated doucuments related to the query and then giving the response back to the user rather than just giving them the whole information and then making them to read it by themself .

### FastAPI setup

### How the RAG API works

My RAG API works by first searching the data relevant to the query through the similarity search on the embeddings from whatever knowledge we have in chromaDB, then it retrieves the data or the docs from the search and lists the data and now it gives the context which is data from the retrieval and inserts into the prompt that we have created to generate the response through ollama tinyllama. So, at the end the ouput will be the ai response from RAG API about query asked by the user.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_f3g4h5i6)

---

## Testing the RAG API

In this step, I'm testing my RAG API. I'll test it using swagger UI. Swagger UI is automatically generated,interactive documentation page for our FastAPI server. I'll use it to visually see my API's endpoints, what paprameters it is accepting and even to try them right from the browser.

### Testing the API

### API query breakdown

I queried my API by running the command - "curl http://localhost:11434" first to test whether the ollama is running or not NS then I run this command - "uvicorn app:app --reload" to run the api server and then I run this command - "Invoke-RestMethod -Uri "http://127.0.0.1:8000/query?q=What is Kubernetes?" -Method Post" to get the response by sending the query through the post method. The command uses the POST method, which means the query is being sent to the server(here api server) and then the response from the ollama model will be recieved at the end. The API responded with giving the ai generated response from the model ollama.

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_g3h4i5j6)

### Swagger UI exploration

Swagger UI is the application interface for the api that we have created for this project. I used it to test the api endpoint method whehter it is working or not directly in the browser preventing from the manual commands to check the answer by opening the local hosting link that leads to the interface where we can see the methods if the api endpoints like in this case - POST/query and clicking the "Try it out" and entering the query and we will get the response. The best part about using Swagger UI was we are able to see how the api endpoint can truly be accessed in real time and also we can be able to see the attributes of the endpoint without using the manual curl commands and thinking how does it happened.

---

## Adding Dynamic Content

In this project extension, I'm going to create one api endpoint called /add to add the data to the chromDb or update the data or removing the data dynamically using the api call while running the web app without editing or adding the data to the text file in which we have stored the data and again running the embeddings creation python script every time. So, we can do this with the call of api endpoint in the url and also I'm going to run the application and check whether it is really working through the swagger UI (testing of the api endpoint).

### Adding the /add endpoint

![Image](http://learn.nextwork.org/daring_turquoise_proud_goblin/uploads/ai-devops-api_w9x0y1z2)

### Dynamic content endpoint working

The /add endpoint allows me to add the text dynamically through the direct entry of the text in the parameters given for the /add endpoint method to enter so that it will directly add the text that we have written in the parameter cell into the chromaDB directly and automatically generating the embeddings and doing the indexing for the chunks of the data that is being stored in the database from which we have entered under the parameters textbox. This is useful because, it helps inadding the text into the database without adding the text into the separate text file and again updating the embed.py manually and executing the app again from the start using the curl commands.

---

---
