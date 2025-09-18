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


## Technology Stack

Langflow: Low-code/no-code orchestration framework for LLM pipelines.

Astra DB (Vector Database): Stores document embeddings for semantic search.

Groq LLM Provider: Executes inference with fast, efficient large language models.

Python.

## Example "User Query" :- (Lot's of prompts and models were tried. Below output corresponds to using Model 'openai/gpt-oss-120b' and keeping 'temperature' close to 0)

Generate a quiz consisting of around 12 technical multiple choice questions (MCQs). Assist in creating such a quiz , and after listing all questions then towards the end list answers for them with brief statements. Try your best to generate quiz questions based on the available data that you're receiving as part of contextual understanding in your prompt.


## Example "Output" :-

Technical Quiz – Retrieval‑Augmented Generation, Prompt Engineering & Markdown Formatting
(All questions are based on the discussion excerpt you provided.)

Questions

1 Why can’t you simply “remember” a 500‑page PDF inside a language model’s prompt?	
A. The model’s context window is limited in size.
B. PDFs are encrypted by default.
C. The model cannot read any text at all.
D. PDFs contain hidden watermarks that block the model.

2 Which technique is suggested for answering user queries that refer to large documents?	
A. Fine‑tuning the model on the whole PDF.
B. Retrieval‑augmented generation (RAG).
C. Converting the PDF to an image and feeding it to the model.
D. Ignoring the document and answering from memory.

3 In a RAG pipeline, what is the typical order of operations?	
A. Generate → Retrieve → Post‑process.
B. Retrieve → Augment prompt → Generate.
C. Fine‑tune → Retrieve → Generate.
D. Tokenize → Summarize → Store.

Answers & Brief Explanations
#	Correct Answer	Explanation
1	A	Language models have a finite context window (e.g., 4 k‑8 k tokens). A 500‑page PDF far exceeds this limit.
2	B	Retrieval‑augmented generation fetches relevant passages from external sources and feeds them to the model.
3	B	First retrieve relevant chunks, then augment the prompt with those chunks, finally let the model generate the answer.


... up to Q12


## Future Enhancements

Add support for different quiz formats (True/False, Fill-in-the-blank).

Enhance prompt engineering for improved MCQ quality.


