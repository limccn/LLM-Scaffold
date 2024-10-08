# Running Text2SQL with LLMs on Docker Containers
## Overview
This demo showcases querying databases through Text2SQL technology, leveraging the advanced features of Large Language Models (LLMs) with the LangChain and Ollama frameworks. Additionally, it explores the deployment of LLM applications using Docker, outlining crucial steps for encapsulating your LLM application in a Docker container. This ensures a consistent and isolated operational environment across different host systems.

## Prerequisites
Before diving into this demo, please ensure that your system meets the following prerequisites:
1. **Operating System**: The demo is compatible with Linux operating systems and tested on Ubuntu 22.04.

2. **Docker, unzip and wget**: It's required to have `docker` and `docker-compose` installed on your system. Specifically, we have tested this demo with Docker Engine Community version 25.0.1 on Linux. 

3. **OpenAI API Key for ChatGPT**: If you wish to use the ChatGPT functionality within this demo, an OpenAI API key is required. Please note that usage of this API is subject to OpenAI's pricing and usage policies.

## Quick Start
### Setup environment on AWS
Please follow this [README file](../env-setup/aws/ubuntu-22.04/README.md) to setup the demo environment on AWS EC2.

### Running the demo on CPU
1. Start by cloning this repo to your EC2 CPU instance:
```
git clone https://github.com/limccn/LLM-Scaffold.git
cd LLM/text2sql
```
2. Insert your OpenAI API Key into conf/config.json for "OPENAI_API_KEY". This step can be skipped if you don't want to evaluate against the OpenAI backend.
3. Launch the demo. If everything runs smoothly, the last command in run.sh should show three containers actively running.
```
bash run.sh
```
4. Load the sample data into MySQL:
```
bash load_data.sh
```
5. Visit the UI at http://{IP of EC2 CPU instance}:8501. On the UI, you can choose either "ChatGPT" or "Local_LLM" (the default local model "sqlcoder:15b-q6_K" is configured to run on CPU) to query the MySQL database.
6. Shutdown the demo.
```
bash shutdown.sh
```

### Running the demo on GPU
1. Start by cloning this repo to your EC2 GPU instance:
```
git clone https://github.com/limccn/LLM-Scaffold.git
cd LLM/text2sql
```
2. Insert your OpenAI API Key into conf/config.json for "OPENAI_API_KEY". 
3. Launch the demo:
```
bash run.sh -gpu
```
4. Load the sample data into MySQL:
```
bash load_data.sh
```
5. Visit the UI at http://{IP of EC2 GPU instance}:8501. On the UI, you can choose either "ChatGPT" or "Local_LLM" (the default local model "sqlcoder:15b-q8_0" is configured to run on GPU) to query the tabular data.
6. Shutdown the demo.
```
bash shutdown.sh -gpu
```