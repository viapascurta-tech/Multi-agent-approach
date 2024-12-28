![PyPI - Version](https://img.shields.io/badge/Pyhton-v3.11.10-blue)
![PyPI - Version](https://img.shields.io/badge/crewai-v0.86.0-red)
![PyPI - Version](https://img.shields.io/badge/chromadb-v0.5.23-brown)
![PyPI - Version](https://img.shields.io/badge/llama%20index-v0.12.5-blue)
![PyPI - Version](https://img.shields.io/badge/Writer_Palmyra_med_llm-70b-blue)
![PyPI - Version](https://img.shields.io/badge/NVIDIA_platform-green)

# Multi-agent-approach
Describes how to create multi-agents for a sepsis management crew to be used in the decision-making process 
## Overview
Given a complex task, a multi-agent approach would break down the task into subtasks to be executed by different roles 
and have different agents accomplish different subtasks. The tables below present a structured overview of these aspects concerning
an LLM-based sepsis management crew to be used at the early stage of sepsis (i.e. before culture results are available).

**Agents**

Aspects|Sepsis management agent|Antibiotic recommendation agent|Gudelines compliance agent
----- |-----|-----|-----
Role|Sepsis Management Advisor|Antibiotic Specialist|Guidelines Compliance Officer
Goal|Provide literature-based recommendations for sepsis management tailored to a patient case|Provide antibiotic recommendations based on the 'special comments' field of the patient vignette|Check if the recommendations comply with current sepsis management guidelines and provide additional guideline-based case management recommendations
Backstory|You are a medical expert specializing in sepsis management, equipped with the latest literature and research findings|You are an expert in antibiotic therapy, capable of tailoring recommendations to specific patient needs|You are tasked with ensuring that sepsis management adheres to the latest guidelines
Tools|RAG|RAG|RAG

RAG stands for retrieval augmented generation

**Tasks**

Aspects|Sepsis management task|Antibiotic task|Compliance task
-----|-----|-----|-----
Task description|Provide literature-based recommendations for sepsis management for the given patient case|Provide antibiotic recommendations for the given patient case, focusing on the 'special comments' field|Check the recommendations for compliance with current sepsis management guidelines and provide additional recommendations based on the guidelines
Expected output|Recommendations for sepsis management|Antibiotic recommendations for a particular sepsis case|Compliance statement and guideline-based recommendations
Agent|Sepsis management agent|Antibiotic recommendation agent|Guideline compliance agent
Inputs|Vignette input|Vignette input: 'special comments'|Sepsis task result; Antibiotic task result; Vignette input

A clinical vignette represents here a structured way to present the sepsis case and contains several fields (e.g., diagnosis, demographics, vital signs, laboratory findings, medical history, and special comments)

The *Crewai_sepsis.ipynb* file provides the code for building the sepsis management crew, which is based on the [crewai platform](https://www.crewai.com/).

Persistent databases used for RAG are based on the [Chromadb platform](https://www.trychroma.com/). The [llamaIndex platform](https://docs.llamaindex.ai/en/stable/) is used for orchestration/indexing. 
The code for this part of the work is available [here](https://github.com/viapascurta-tech/Creating_ChromaDBs_sepsis_related/blob/main/Creating_Chroma_DBs_sepsis.ipynb).

The inference engine is [Writer Palmyra-med 70B LLM](https://writer.com/blog/palmyra-med-fin-models/) on [NVIDIA platform](https://build.nvidia.com/explore/discover). 
The LLM can be replaced with other LLM (e.g., GPT-3.5-turbo, GPT-4o, etc.), making respective changes in the code (i.e., API key, model name). 

