# Glossary of Terms

This document provides definitions for key terms and concepts used in the AI-HR-CV-Scan system documentation. Understanding these terms will help you better navigate and use the system.

## A

### AI (Artificial Intelligence)
Technology that enables computers to perform tasks that typically require human intelligence, such as understanding natural language, recognizing patterns, and making decisions. In the AI-HR-CV-Scan system, AI is used for information extraction and candidate evaluation.

### API (Application Programming Interface)
A set of rules and protocols that allows different software applications to communicate with each other. The AI-HR-CV-Scan system uses APIs to interact with Google Drive, Google Sheets, OCR services, and AI services.

### ATS (Applicant Tracking System)
Software used by recruiters and HR professionals to manage the recruitment process, including job postings, application collection, candidate screening, and interview scheduling.

## C

### Candidate Evaluation
The process of assessing a candidate's qualifications, skills, and experience against job requirements. In the AI-HR-CV-Scan system, this is performed automatically by AI.

### Credentials
Authentication information (such as API keys, usernames, passwords, or OAuth tokens) used to access protected resources and services. The AI-HR-CV-Scan system uses credentials to access Google services and OCR.space.

### CV (Curriculum Vitae)
A document that outlines a person's education, work experience, skills, and qualifications. Also known as a resume in some regions. The AI-HR-CV-Scan system processes CVs to extract and evaluate candidate information.

## D

### Data Extraction
The process of retrieving specific information from unstructured or semi-structured documents. The AI-HR-CV-Scan system extracts personal details, education, work experience, and skills from CVs.

### DOCX
A file format used by Microsoft Word for document storage. The AI-HR-CV-Scan system can process CVs in DOCX format.

## G

### GDPR (General Data Protection Regulation)
A regulation in EU law on data protection and privacy that applies to the processing of personal data. Organizations using the AI-HR-CV-Scan system should ensure compliance with GDPR when processing candidate data.

### Google Drive
A file storage and synchronization service developed by Google. The AI-HR-CV-Scan system uses Google Drive to store CV files and organize them into folders.

### Google Sheets
A spreadsheet program included as part of the Google Docs Editors web-based software office suite. The AI-HR-CV-Scan system uses Google Sheets to store structured candidate data and job requirements.

### Google Gemini AI
An AI model developed by Google that can process and generate text, images, and other content. The AI-HR-CV-Scan system uses Google Gemini AI for information extraction and candidate evaluation.

## I

### Information Extraction
The process of automatically extracting structured information from unstructured or semi-structured documents. The AI-HR-CV-Scan system extracts information such as contact details, education, and work experience from CVs.

## J

### Job Description
A document that outlines the responsibilities, qualifications, skills, and experience required for a specific job position. The AI-HR-CV-Scan system uses job descriptions to evaluate candidate suitability.

## L

### LangChain
A framework for developing applications powered by language models. The AI-HR-CV-Scan system uses LangChain for structured information extraction from CV text.

## N

### n8n
An open-source workflow automation tool that allows you to connect different services and automate tasks. The AI-HR-CV-Scan system is built on n8n to orchestrate the CV processing workflow.

### Node
In the context of n8n, a node is a building block that performs a specific function within a workflow. The AI-HR-CV-Scan system uses various nodes for file operations, text extraction, AI processing, and data storage.

## O

### OAuth 2.0
An authorization framework that enables third-party applications to obtain limited access to a user's account on an HTTP service. The AI-HR-CV-Scan system uses OAuth 2.0 to securely access Google services.

### OCR (Optical Character Recognition)
Technology that converts different types of documents, such as scanned paper documents, PDF files, or images, into editable and searchable data. The AI-HR-CV-Scan system uses OCR.space for text extraction from scanned CVs.

## P

### PDF (Portable Document Format)
A file format used to present documents in a manner independent of application software, hardware, and operating systems. The AI-HR-CV-Scan system can process CVs in PDF format.

### Prompt
In the context of AI, a prompt is the input text that guides the AI model to generate a specific type of output. The AI-HR-CV-Scan system uses carefully crafted prompts to extract information and evaluate candidates.

## S

### Schedule Trigger
In n8n, a trigger that starts a workflow at specified times according to a schedule. The AI-HR-CV-Scan system uses a schedule trigger to periodically check for new CV files.

### Structured Data
Information organized in a formatted repository that is typically searchable and easily accessible. The AI-HR-CV-Scan system converts unstructured CV text into structured data stored in Google Sheets.

### Suitability Score
A numerical rating (1-10) assigned to candidates based on how well their qualifications match the job requirements. The AI-HR-CV-Scan system generates suitability scores as part of the evaluation process.

## T

### Talent Pool
A database of candidates who have previously applied for positions or been identified as potential future hires. The AI-HR-CV-Scan system organizes processed CVs into a talent pool folder in Google Drive.

### Text Extraction
The process of obtaining text content from files such as PDFs or images. The AI-HR-CV-Scan system uses both direct extraction for text-based PDFs and OCR for scanned documents.

## W

### Workflow
In n8n, a workflow is a sequence of connected nodes that process data and perform actions. The AI-HR-CV-Scan system is implemented as an n8n workflow that processes CVs from upload to evaluation.

## Technical Terms

### API Key
A unique identifier used to authenticate a user, developer, or calling program to an API. The AI-HR-CV-Scan system uses API keys for services like OCR.space.

### Batch Processing
The processing of multiple items at once rather than individually. Future enhancements to the AI-HR-CV-Scan system may include batch processing of multiple CVs.

### Cron Expression
A string representing a schedule in a format used by cron job schedulers. The AI-HR-CV-Scan system uses a cron expression (`*/5 8-17 * * 1-6`) to define when the workflow should run.

### JSON (JavaScript Object Notation)
A lightweight data-interchange format that is easy for humans to read and write and easy for machines to parse and generate. The AI-HR-CV-Scan workflow is stored as a JSON file.

### OAuth Token
A credential used in OAuth authentication flows to grant access to protected resources. The AI-HR-CV-Scan system uses OAuth tokens to access Google services.

### REST API
An architectural style for an application program interface (API) that uses HTTP requests to access and manipulate data. The AI-HR-CV-Scan system interacts with Google and OCR services through REST APIs.

## System-Specific Terms

### Chuyên gia HR
The name of the node in the workflow that performs AI-based candidate evaluation, acting as an "HR Expert" to assess candidate suitability.

### Datapool
The main tab in the Google Sheet where all extracted candidate information is stored.

### Điểm phù hợp
Vietnamese term for "Suitability Score," the numerical rating assigned to candidates based on how well they match job requirements.

### Sự phù hợp
Vietnamese term for "Suitability Assessment," the detailed evaluation of a candidate's strengths relative to the job position.

### Tách PDF
The name of the node in the workflow that extracts text from PDF files.

### Tìm file
The name of the node in the workflow that searches for CV files in Google Drive.

### Vị trí tuyển dụng
Vietnamese term for "Job Positions," the name of the tab in the Google Sheet where job requirements are stored.
