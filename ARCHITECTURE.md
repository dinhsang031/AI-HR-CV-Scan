# System Architecture

This document provides a high-level overview of the AI-HR-CV-Scan system architecture, explaining how the different components interact to create a complete CV scanning and evaluation solution.

## Architecture Overview

The AI-HR-CV-Scan system follows a modular architecture with several interconnected components that work together to process, analyze, and evaluate CVs. The system is built on the n8n workflow automation platform and integrates with various external services.

## System Components

### 1. Data Storage Layer

**Google Drive**
- Serves as the primary file storage system
- Stores original CV files (PDF, DOCX)
- Organizes processed CVs in a talent pool folder
- Provides secure access control and file management

**Google Sheets**
- Functions as the structured database for candidate information
- Stores job position requirements
- Maintains a comprehensive record of all processed candidates
- Enables easy filtering, sorting, and analysis of candidate data

### 2. Processing Layer

**n8n Workflow Engine**
- Orchestrates the entire CV processing pipeline
- Manages the flow of data between components
- Handles scheduling and automation
- Provides error handling and recovery mechanisms

**File Processing Components**
- PDF text extraction
- OCR processing for scanned documents
- DOCX parsing
- File format handling and conversion

### 3. AI Analysis Layer

**Information Extraction**
- Personal information extraction (name, contact details, etc.)
- Education information extraction
- Work experience analysis
- Skills identification

**Candidate Evaluation**
- Comparison of candidate profiles against job requirements
- Scoring and ranking of candidates
- Generation of detailed assessment reports
- Identification of candidate strengths and weaknesses

### 4. Integration Layer

**API Connections**
- Google Drive API integration
- Google Sheets API integration
- OCR.space API integration
- Google Gemini AI API integration

**Authentication**
- OAuth 2.0 authentication for Google services
- API key authentication for OCR services
- Secure credential management

## Data Flow

The system follows a sequential data flow process:

1. **Input**: CV files are uploaded to a designated Google Drive folder
2. **Trigger**: The workflow is triggered on a schedule to check for new files
3. **Job Requirements**: The latest job position is retrieved from Google Sheets
4. **File Processing**: CV files are downloaded and text is extracted
5. **Information Extraction**: AI extracts structured information from CV text
6. **Evaluation**: AI evaluates the candidate against job requirements
7. **Data Storage**: Processed information is stored in Google Sheets
8. **File Management**: Processed CV files are renamed and moved to the talent pool

## Architecture Diagram

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│  Google Drive   │◄────┤    n8n Workflow │◄────┤  Google Sheets  │
│  (File Storage) │     │  (Orchestration)│     │  (Data Storage) │
│                 │     │                 │     │                 │
└────────┬────────┘     └────────┬────────┘     └────────▲────────┘
         │                       │                       │
         │                       ▼                       │
         │              ┌─────────────────┐              │
         │              │                 │              │
         └─────────────►│ Text Extraction │──────────────┘
                        │    (PDF/OCR)    │
                        │                 │
                        └────────┬────────┘
                                 │
                                 ▼
                        ┌─────────────────┐
                        │                 │
                        │  AI Processing  │
                        │   (Gemini AI)   │
                        │                 │
                        └────────┬────────┘
                                 │
                                 ▼
                        ┌─────────────────┐
                        │                 │
                        │ Data Formatting │
                        │  & Validation   │
                        │                 │
                        └─────────────────┘
```

## Component Details

### n8n Workflow

The n8n workflow is the central orchestration component that:
- Manages the execution sequence
- Handles data transformation between steps
- Provides error handling and retry logic
- Enables monitoring and debugging

### Google Services Integration

The system leverages Google services for:
- File storage and management (Google Drive)
- Structured data storage (Google Sheets)
- Authentication and access control (Google OAuth)

### AI Processing

The AI processing components use:
- Google Gemini AI for natural language understanding
- LangChain framework for structured information extraction
- Custom prompts for specialized CV analysis
- Evaluation algorithms for candidate scoring

### OCR Integration

For documents requiring OCR:
- OCR.space API provides text extraction from images
- Results are processed and normalized
- Extracted text is fed into the AI analysis pipeline

## Scalability Considerations

The architecture is designed with scalability in mind:

1. **Horizontal Scaling**
   - Multiple n8n instances can process different batches of CVs
   - Google services automatically scale to handle increased load

2. **Workflow Optimization**
   - Batch processing capabilities for handling multiple CVs
   - Efficient resource utilization through targeted processing

3. **Storage Scaling**
   - Google Drive and Sheets automatically scale with data volume
   - No practical limits for typical HR usage scenarios

## Security Architecture

Security is integrated throughout the architecture:

1. **Authentication**
   - OAuth 2.0 for secure Google service access
   - API key management for third-party services
   - Credential isolation in n8n's secure storage

2. **Data Protection**
   - Data remains within the Google ecosystem
   - Minimal data transfer to external services
   - Access controls at file and sheet levels

3. **Process Isolation**
   - Each workflow execution is isolated
   - Failed executions don't impact other processes

## Extensibility

The modular architecture allows for easy extension:

1. **Additional AI Services**
   - New AI models can be integrated for specialized analysis
   - Multiple AI services can be used in parallel for different tasks

2. **Additional Data Sources**
   - Support for more CV formats can be added
   - Integration with job boards or applicant tracking systems

3. **Output Integrations**
   - Results can be exported to other HR systems
   - Notifications can be sent via email, Slack, or other channels

## Technical Requirements

To implement this architecture, you need:

1. **n8n Environment**
   - n8n instance (self-hosted or cloud)
   - Node.js runtime environment
   - Network access to Google APIs and OCR.space

2. **Google Workspace**
   - Google account with Drive and Sheets access
   - API project with necessary permissions
   - OAuth credentials for authentication

3. **External Services**
   - OCR.space API account
   - Google Gemini AI API access

## Architecture Limitations

Be aware of these architectural limitations:

1. **Processing Speed**
   - AI analysis can take time for complex CVs
   - OCR processing adds additional time for scanned documents

2. **Dependency on External Services**
   - Requires reliable internet connectivity
   - Subject to API rate limits and service availability

3. **AI Accuracy**
   - Information extraction accuracy depends on CV format and clarity
   - Evaluation quality depends on job description specificity

## Future Architecture Considerations

The architecture can evolve in several directions:

1. **Machine Learning Enhancements**
   - Custom ML models for specific industries or roles
   - Feedback loops to improve evaluation accuracy over time

2. **Integration Expansion**
   - Direct integration with job posting platforms
   - Connection to interview scheduling systems
   - Integration with HRIS and onboarding systems

3. **Advanced Analytics**
   - Talent pool analysis and reporting
   - Hiring funnel analytics
   - Recruitment performance metrics
