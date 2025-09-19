# AgenticAI_Langflow
This repository contains specific use case examples corresponding to usage of Langflow framework

# Quiz Generator
This project demonstrates how to build an AI workflow using the Langflow framework. It leverages contextual information from documents stored in a vector database (Astra DB) and an LLM provider (Groq) to dynamically generate multiple-choice quizzes.

## Goal
The primary goal of this project is to:

Ingest domain-specific documents.

Use them as contextual knowledge for an LLM prompt.

Automatically generate a set of MCQs (Multiple Choice Questions) as a quiz.

Demonstrate an AI workflow where external knowledge retrieval, reasoning, and LLM inference are combined seamlessly.

## Solution Overview
Document Ingestion: User-provided documents are uploaded and embedded into Astra Vector DB for efficient similarity search.

Query & Context Retrieval: At runtime, the system retrieves relevant document chunks based on the input query.

Prompt Assembly: The retrieved context is combined with the user query to form the final prompt.

LLM Inference: The prompt is sent to an LLM hosted via Groq, which generates a structured set of MCQs.

Output Delivery: The generated quiz is returned in a human-readable format.

## Architecture Flow
          ┌──────────────┐
          │   Documents  │
          └──────┬───────┘
                 │ Upload & Embed
                 ▼
          ┌──────────────┐
          │ Astra Vector │
          │   Database   │
          └──────┬───────┘
                 │ Retrieve Relevant Context
                 ▼
          ┌──────────────┐
          │   Langflow   │
          │   Workflow   │
          └──────┬───────┘
                 │ Assemble Prompt
                 ▼
          ┌──────────────┐
          │   Groq LLM   │
          └──────┬───────┘
                 │ Generate MCQs
                 ▼
          ┌──────────────┐
          │    Output    │
          │   (MCQs)  │
          └──────────────┘

## Actual Workflow Reference

![image alt](https://github.com/slowlekar-iith/AgenticAI_Langflow/blob/e2b62770c7705540608b0f4fb4d1a451d0990213/Images/Langflow_MCQFlow.png)

## Technology Stack

Langflow: Low-code/no-code orchestration framework for LLM pipelines.

Astra DB (Vector Database): Stores document embeddings for semantic search.

Groq LLM Provider: Executes inference with fast, efficient large language models.

Python.

## Example "Input"/"User Query" :- 
(Lot's of prompts and models were tried. Below output corresponds to using Model 'openai/gpt-oss-120b' and keeping 'temperature' close to 0)

Generate a quiz consisting of around 12 technical multiple choice questions (MCQs). Assist in creating such a quiz , and after listing all questions then towards the end list answers for them with brief statements. Try your best to generate quiz questions based on the available data that you're receiving as part of contextual understanding in your prompt.


## Example "Output" :-

![image alt](https://github.com/slowlekar-iith/AgenticAI_Langflow/blob/e2b62770c7705540608b0f4fb4d1a451d0990213/Images/Langflow_MCQ_OutSample1.png)

![image alt](https://github.com/slowlekar-iith/AgenticAI_Langflow/blob/e2b62770c7705540608b0f4fb4d1a451d0990213/Images/Langflow_MCQ_OutSample2.png)

... up to Q12


## Future Enhancements

Add support for different quiz formats (True/False, Fill-in-the-blank).

Enhance prompt engineering for improved MCQ quality.


