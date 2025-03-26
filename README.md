## langchain-postgresql-pgvector
This repository provides guidance on using a PostgreSQL vector database with the pgvector extension.

## Objectives

-- Set up PostgreSQL with the pgvector extension in a Docker container, and create database
-- Use langchain to add embeddings to database, created with OpenAI's  text-embedding-ada-002 embedding model
-- Query the database from langchain to find the most similar embeddings to a given query
-- Query the database with SQL and explore pgvector features
-- Explore the concept of a vector database, and why it may be helpful in developing applications using LLMs

## Using pgvector for Storing Embeddings  

To store embeddings, we need to set up PostgreSQL and enable the **pgvector** extension. We'll do this using Docker by pulling the pgvector image and running a container.  

### **Step 1: Pull the pgvector Image**  
Run the following command to download the pgvector image:  

```sh
docker pull pgvector/pgvector:pg16
```

### **Step 2: Start the PostgreSQL Container**  
Use the command below to start a new PostgreSQL container with **pgvector** enabled:  

```sh
docker run --name pgvector-container \
  -e POSTGRES_USER=langchain \
  -e POSTGRES_PASSWORD=langchain \
  -e POSTGRES_DB=langchain \
  -p 6024:5432 -d pgvector/pgvector:pg16
```

### **Step 3: Connect to PostgreSQL via pgAdmin**  
When adding a new server in **pgAdmin**, use the following connection details based on the above Docker configuration:  

- **Host:** `localhost` (or `127.0.0.1` if `localhost` doesn’t work)  
- **Port:** `6024`  
- **Username:** `langchain`  
- **Password:** `langchain`  
- **Database Name:** `langchain` (or leave empty to list all databases)  

This setup allows you to use PostgreSQL with the **pgvector** extension for storing and managing vector embeddings. 🚀

