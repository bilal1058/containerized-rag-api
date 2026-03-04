# Build a RAG API with FastAPI

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_g3h4i5j6)

---

## Introducing Today's Project!

In this project i will create a RAG using fastapi ,ollama and chromadb which we can run locally and ask questions with it without accessing the need of internet


### Key services and concepts

Services I used were FastAPI, Ollama (for the LLM tinyllama), ChromaDB (for embeddings), and Uvicorn. Key concepts I learned include building APIs, using Retrieval-Augmented Generation (RAG), creating embeddings, and connecting an LLM to a knowledge base for dynamic question-answering.

### Challenges and wins

This project took me approximately 2-3 hours.The most challenging part was nothing(You made it easy). It was most rewarding to seeing the working.

### Why I did this project

I did this project because i wanna learn new skills

---

## Setting Up Python and Ollama

In this step, I'm setting up Python and Ollama. Python will be used for fastapi .Ollama is used for running llm on local machine. I need these tools because to make RAG and then use it for answering without internet.

### Python and Ollama setup

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_i9j0k1l2)

### Verifying Python is working

### Ollama and tinyllama ready

Ollama is used to run llm on local models. I downloaded the tinyllama model because it's a llm which will generate answers The model will help my RAG API by generating answers.

---

## Setting Up a Python Workspace

In this step, I'm setting up python virtual environment along with dependencies needed like fastapi,uvicorn,chormadb,ollama. I need it because to run RAG and use it locally on my system privately without affecting other versions needed for other projects. 

### Python workspace setup

### Virtual environment

A virtual environment is like a separate/private environment to run a project privately without interfering with others. I created one for this project to use python for fastapi to use this specific version and don't disturb others.Once I activate it will make sure to use libraries and packages from this folder. To create a virtual environment, I typed
python -m venv venv

### Dependencies

The packages I installed are fastapi,uvicorn,chormadb,Ollama.
FastAPI is used for data validation using pydantic model.It is used for creating APIs with builtin functioning like handling requests,headers,json conversions,responses.
Chroma is used for text->embeddings vectors.
Uvicorn is used for listening and then send the incoming request to fastApi for further processing.
Ollama is used for running models on local machine like tinyllama which will generate answers using our documents(uses chromadb) and our question then generate a response using both things.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_u1v2w3x4)

---

## Setting Up a Knowledge Base

In this step, I'm creating a knowlede base. A knowledge base is like a extra information for my questions related. I need it because sometimes the small models generates hallucinations (confident but wrong) answers so to avoid this the model(chromadb) will use our knowledge base then generate answers using llm

### Knowledge base setup

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_t1u2v3w4)

### Embeddings created

Embeddings are numerical representation of text. I created them by using chromadb. The db/ folder contains subfolders of embeddings in which they also have metadata . This is important for RAG because chromadb searches for most closest vector and return it(Bcz the knowledge base is stored in numerical vectors formS)

---

## Building the RAG API

In this step, I'm building a RAG API. An API is used for retreiving information can be access by others and send it to other apps. FastAPI is used to build api by python. I'm creating this because to use ollama and our knowledge base. 

### FastAPI setup

### How the RAG API works

My RAG API works by receiving question then searches in chromadb knowledge base then combining question and context(text by chromadb) to send it to ollama(llm like tinyllama) which will then generated a answers and send it to users.FastApi works on specific endpoints like in web url we have links just like that fastapi works on endpoints like in this /query on which it expects string(question).

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_f3g4h5i6)

---

## Testing the RAG API

In this step, I'm testing my RAG API. I'll test it using command line.Swagger UI is fastApi feature where we can see our endpoints and try them without coding. I'll use it to test that my FastApi is working correctly.

### Testing the API

### API query breakdown

I queried my API by running the command
Invoke-RestMethod -Uri "http://127.0.0.1:8000/query?q=What is kubernetes?" -Method POST
The command uses the POST method, which means we want to send data. The API responded with answer and server says 200 ok.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_g3h4i5j6)

### Swagger UI exploration

Swagger UI is python FastApi feature used for testing endpoints like in our case /query. I used it to test our /query endpoint by asking a question using post method.The best part about using Swagger UI was builtin feature we don't need to manually type the code or by sending different requests.

---

## Adding Dynamic Content

In this project extension, I'm adding an endpoint through where others(users/apps) can update my knowledge base.

### Adding the /add endpoint

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-api_w9x0y1z2)

### Dynamic content endpoint working

The /add endpoint allows me to add any information to my knowledge base. This is useful because  now i don't have to maually add info to my knowledge base also others can also add info to my knowledge base.

# Containerize a RAG API with Docker

## Installing Docker Desktop

### Docker Desktop setup

Docker Desktop is a tool which containerize my application.I installed it because to containerize my app. Containerization will help my project by using it on any other device without installing the exact dependencies.

### Docker verification

I verified Docker is working by docker run hello-world .The hello-world container proves that docker can download images from internet and create containers also.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_i9j0k1l2)

---

## Creating the Dockerfile

In this step, I'm building a RAG API. RAG stands for Retreival ,Augmented and Generation. I'm creating files like embed.py,app.py,/db folder,k8s.txt and venv script.

### How the Dockerfile works

A Dockerfile is a set of instructions that tells Docker how to make/build a container image. The key instructions in my Dockerfile are FROM,RUN,COPY,CMD,WORKDIR. FROM tells Docker the Base image.COPY is used for copying file from system to conatiner. RUN executes commands like downloading dependencies etc. CMD defines which command to run when the container starts.

### Containerized API test results

Testing the API after containerization proved that i can now use simply run docker image and use it. The difference between running locally and in Docker is u have all dependencies and exact version of library/technologies to run app/api whereas in docker u only need docker and run that image and use it. Containerization helps because it bundles exact version to run application and make it portable and scaling.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_o1p2q3r4)

---

## Building and Running the Container

### Docker image build complete

Building a Docker image involves FROM(selecting base like python 3.11 in my case),WORKDIR(the working directory for docker image like /app),RUN(downloads dependencies like fastapi etc),COPY(copy the code file like embed.py and others to docker image),CMD(which command to run when docker image started). I verified my Docker image was built successfully by this command to list all docker images "docker images | Select-String rag-app
".This confirms that my API is now containerized because i saw an entry of rag-app in docker images.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_p9q0r1s2)

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_x7y8z9a0)

---

## Pushing to Docker Hub

In this project extension, I'm pushing to Docker Hub. Docker Hub is like a github for container where i can push my image and other/me(on other machine) can pull and use it. I'm doing this because to be accessible by my team and me(on other machine) to pull and test it on other systems.

### Docker Hub push complete

I pushed to Docker Hub by docker push bilal888/rag-app. Docker Hub is useful because it's a place where i and other can share and use docker images. The advantage of pushing to a registry is to make app prtable and accessible.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_m5n6o7p8)

### Pulling from Docker Hub

Pulling an image from Docker Hub means we can download and use it. When I ran docker pull, Docker pulled the image in my system. The difference between building locally and pulling from Docker Hub is building locally requires all exact version of dependencies whereas docker image doesn't requires any pre-dependencies all are already packed and ready-to-use.

![Image](http://learn.nextwork.org/radiant_purple_playful_oriental_melon/uploads/ai-devops-docker_f5g6h7i8)

