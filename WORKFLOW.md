# Workflow Documentation

This document provides a detailed explanation of the n8n workflow that powers the AI-HR-CV-Scan system. The workflow automates the process of scanning, analyzing, and evaluating CVs for HR departments.

## Workflow Overview

The workflow consists of multiple interconnected nodes that perform specific functions in the CV processing pipeline. The workflow is triggered on a schedule and processes any new CVs found in a designated Google Drive folder.

## Trigger

- **Schedule Trigger**: The workflow is triggered automatically on a schedule (every 5 minutes during business hours on weekdays).
  - Schedule: `*/5 8-17 * * 1-6` (Every 5 minutes from 8 AM to 5 PM, Monday to Saturday)

## CV Collection and Processing

1. **Tìm file1**: Searches for files in the designated Google Drive folder (`1E-aesbw4l7K8yHaO1jXZBmQjDKrF7Ehp`).

2. **Vị trí cần tuyển**: Retrieves the latest job position information from the Google Sheet.

3. **Code**: Extracts the most recent job position data.

4. **Profile Wanted**: Formats and stores the job position information for later use.

5. **Tìm file**: Searches for new CV files in the Google Drive folder.

6. **Tải CV**: Downloads the CV file for processing.

7. **Switch1**: Determines the file type (PDF or DOCX) and routes it accordingly.

8. **Tách PDF**: Extracts text from PDF files.

9. **Switch**: Determines if the text extraction was successful or if OCR is needed.

10. **OCR API**: Uses OCR.space API to extract text from scanned documents or images.

11. **Edit Fields**: Combines and formats the extracted text.

## Information Extraction

1. **Dữ liệu cá nhân**: Uses AI to extract personal information from the CV text:
   - Full name
   - Phone number
   - Email
   - Location
   - Year of birth
   - Gender
   - Position applied for
   - Application timestamp

2. **Thông tin công việc**: Uses AI to extract professional information:
   - Education (institution, field, graduation year, classification)
   - Work history
   - Skills
   - Certifications
   - Job tasks

3. **Merge**: Combines personal and professional information.

4. **Tóm tắt thông tin**: Generates a concise summary of the candidate's profile.

## Evaluation and Processing

1. **Chuyên gia HR**: Uses AI to evaluate the candidate's suitability for the position:
   - Assigns a score from 1 to 10
   - Provides a detailed assessment of the candidate's fit
   - Lists strengths and relevant qualifications

2. **Structured Output Parser**: Parses the AI evaluation into a structured format.

3. **Đổi tên file**: Renames the CV file with a standardized format: `[Date] - [Position] - [Name]`.

4. **Chuyển sang Talent pool**: Moves the processed CV to a talent pool folder in Google Drive.

5. **Code2**: Generates a direct link to the CV file in Google Drive.

## Data Aggregation and Storage

1. **Merge1**: Combines all extracted and generated information.

2. **Code1**: Formats and structures all data for storage:
   - Converts text to proper case
   - Parses numerical values
   - Creates a consistent data structure

3. **Tổng hợp dữ liệu và DTB**: Appends the processed data to the Google Sheet.

## Node Details

### AI Processing Nodes

1. **Google Gemini Chat Model**: Provides the AI capabilities for:
   - Information extraction
   - Candidate evaluation
   - Text summarization

2. **Information Extractor Nodes**:
   - Use LangChain framework
   - Custom prompts for specific information extraction
   - Structured output schemas

### Data Transformation Nodes

1. **Code Nodes**: JavaScript functions for data manipulation:
   - Text formatting
   - Data cleaning
   - Link generation
   - Array manipulation

2. **Set Nodes**: Assign and format specific fields.

### Google Integration Nodes

1. **Google Drive Nodes**:
   - File search
   - Download
   - Rename
   - Move

2. **Google Sheets Nodes**:
   - Read job positions
   - Append candidate data

## Error Handling

The workflow includes several error handling mechanisms:

1. **Switch Nodes**: Route processing based on file types and extraction success.
2. **OCR Fallback**: If direct text extraction fails, OCR is used as a backup.
3. **Data Validation**: Checks for empty or invalid data before processing.

## Workflow Diagram

The workflow follows this general sequence:

```
Schedule Trigger → Find Files → Get Job Position → Download CV → Extract Text → 
Extract Information → Evaluate Candidate → Process File → Store Data
```

Each step in the process is dependent on the successful completion of the previous steps, creating a robust pipeline for CV processing.

## Performance Considerations

- The workflow is designed to process one CV at a time
- Processing time varies based on file size and complexity
- OCR processing may take longer for scanned documents
- AI evaluation requires more processing time than simple text extraction

## Security and Privacy

- All data is processed within the n8n environment
- Files remain within the Google Drive ecosystem
- API keys and credentials are securely stored in n8n
- No data is sent to external services except for OCR processing
