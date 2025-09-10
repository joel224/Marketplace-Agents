# Marketplace-Agents

Local RAG with In-Memory Caching and Unified Chat Agent

This project implements a local Retrieval-Augmented Generation (RAG) system with in-memory caching using Ollama and a simple Flask web interface. It includes two agents: a Price Suggestor and a Chat Moderation agent, operating on a local dataset.

Project Components
Data Ingestion and Local Knowledge Base: Reads product data from a text file into a pandas DataFrame for an in-memory knowledge base.

Adaptive Replacement Cache (ARC): Implements an ARC caching mechanism to optimize retrieval for frequent queries.

Retrieval-Augmented Generation (RAG): Combines user queries with relevant data from the in-memory knowledge base to augment prompts for a local Large Language Model (LLM).

Unified Chat Router Agent: Directs incoming user messages to either the Price Suggestor or Chat Moderation agent based on intent.

Price Suggestor Agent: Uses the RAG process to provide price suggestions based on product details.

Chat Moderation Agent: Classifies chat messages based on predefined rules using the LLM.

Flask App and ngrok Interface: Provides a web interface to interact with the unified chat agent, exposed via ngrok for external access.


Setup and Run Instructions
Open the Notebook: Open this Google Colab notebook.

Mount Google Drive: Ensure your Google Drive is mounted to access the db.txt file. 

If not already mounted, you can do so using the file explorer in the left sidebar or by adding a code cell with from google.colab import drive and drive.mount('/content/drive').

Create db.txt: Make sure you have a text file named db.txt in your Google Drive at the path /content/drive/MyDrive/db.txt. The file should be in a comma-separated value (CSV) format with a header row, as described in the project plan.


Set up ngrok Secret:
You need an ngrok account and an authentication token. Sign up at ngrok.com.
Get your Authtoken from the ngrok dashboard.
In Google Colab, go to the "Secrets" tab in the left sidebar (🔑 icon).
Click "New secret".
For the "Name", enter ngrok.
For the "Value", paste your ngrok Authtoken.
Ensure "Notebook access" is enabled for this secret.


Install Libraries and Start Ollama: Run the first code cell in the notebook. This will:
Install necessary Python libraries (Flask, pyngrok).
Download and start the Ollama server within the Colab environment.
Pull the mistral LLM model (you can change this model name in the start_ollama_server function if desired).
Load your db.txt dataset.
Run the Flask App: Running the first code cell will also start the Flask development server and expose it via ngrok. Look for output similar to:
<img width="1366" height="717" alt="screencapture-f0da114547d8-ngrok-free-app-2025-09-10-11_36_51" src="https://github.com/user-attachments/assets/de7b4316-757a-4201-83ae-e39ec8578d53" />

<img width="1366" height="717" alt="screencapture-f0da114547d8-ngrok-free-app-2025-09-10-11_37_19" src="https://github.com/user-attachments/assets/263a2c14-8a10-48b0-ae42-b353b2d4dcae" />
