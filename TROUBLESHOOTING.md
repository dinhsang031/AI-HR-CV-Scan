# Troubleshooting Guide

This document provides solutions for common issues you might encounter when using the AI-HR-CV-Scan system. If you experience problems with the workflow, use this guide to diagnose and resolve them.

## Workflow Execution Issues

### Workflow Not Starting

**Symptoms:**
- The workflow doesn't run on schedule
- Manual execution doesn't start

**Possible Causes and Solutions:**

1. **n8n Service Issues**
   - Check if the n8n service is running
   - Restart the n8n service: `sudo systemctl restart n8n` (Linux) or restart the Docker container
   - Check n8n logs for errors: `sudo journalctl -u n8n` (Linux) or `docker logs n8n` (Docker)

2. **Schedule Trigger Configuration**
   - Verify the cron expression in the Schedule Trigger node
   - Ensure the timezone settings in n8n match your local timezone
   - Try changing the schedule to run more frequently for testing

3. **Workflow Activation**
   - Ensure the workflow is activated (toggle in the top-right of the n8n editor)
   - Check if the workflow was deactivated due to too many errors

### Workflow Starts But Fails Early

**Symptoms:**
- Workflow execution begins but stops after a few nodes
- Error messages in the execution log

**Possible Causes and Solutions:**

1. **Credential Issues**
   - Check if OAuth tokens have expired
   - Verify that all credentials are correctly configured
   - Re-authenticate Google services if necessary

2. **Missing Folders or Files**
   - Verify that the Google Drive folders exist and have the correct IDs
   - Check permissions on the folders

3. **Google Sheet Issues**
   - Confirm the Google Sheet exists and has the correct ID
   - Verify the sheet names match what's configured in the workflow

## File Processing Issues

### PDF Text Extraction Fails

**Symptoms:**
- Workflow fails at the "Tách PDF" node
- Empty or incomplete text extraction

**Possible Causes and Solutions:**

1. **Unsupported PDF Format**
   - Check if the PDF is encrypted or password-protected
   - Verify the PDF is not a scanned image without OCR
   - Try converting the PDF to a different format and re-uploading

2. **OCR Issues**
   - Verify the OCR.space API key is valid
   - Check OCR.space service status
   - Try using a different OCR engine setting

3. **Large File Size**
   - Check if the PDF exceeds size limits
   - Split large PDFs into smaller files

### DOCX Processing Issues

**Symptoms:**
- Workflow fails when processing DOCX files
- Incomplete text extraction

**Possible Causes and Solutions:**

1. **File Format Compatibility**
   - Ensure the file is a standard DOCX format
   - Check for complex formatting or embedded objects
   - Try saving the file as a simpler format

2. **File Access Issues**
   - Verify permissions on the file
   - Check if the file is locked by another process

## AI Processing Issues

### Information Extraction Problems

**Symptoms:**
- Missing or incorrect data in the extracted fields
- AI nodes complete but with poor results

**Possible Causes and Solutions:**

1. **CV Format Issues**
   - Check if the CV has a standard format
   - Verify text extraction was successful
   - Try with a cleaner, more structured CV format

2. **AI Prompt Configuration**
   - Review and adjust the system prompts in the AI nodes
   - Make prompts more specific for problematic fields

3. **Language Issues**
   - Ensure the CV language matches what the AI is configured for
   - Add language detection and handling for multilingual support

### Evaluation Accuracy Issues

**Symptoms:**
- Evaluation scores seem inconsistent or inaccurate
- Missing or generic evaluation text

**Possible Causes and Solutions:**

1. **Job Description Format**
   - Ensure job descriptions follow the recommended format
   - Add more specific requirements and skills to the job description
   - Use the format from the Job Position Template

2. **AI Model Limitations**
   - Adjust expectations for AI evaluation accuracy
   - Always have human review of AI evaluations
   - Consider updating the AI prompts for better evaluation

3. **Insufficient Context**
   - Ensure all relevant CV information is being passed to the evaluation node
   - Check for data truncation in the workflow

## Google Services Issues

### Google Drive Problems

**Symptoms:**
- Cannot find or access files in Google Drive
- File operations (move, rename) fail

**Possible Causes and Solutions:**

1. **Permission Issues**
   - Verify the OAuth scope includes necessary Drive permissions
   - Check folder sharing settings
   - Ensure the authenticated user has access to all folders

2. **Folder ID Errors**
   - Double-check all folder IDs in the workflow
   - Verify folders haven't been deleted or moved
   - Update folder IDs if they've changed

3. **API Quota Limits**
   - Check if you've hit Google API quota limits
   - Implement rate limiting in the workflow
   - Consider upgrading to higher API quotas if needed

### Google Sheets Problems

**Symptoms:**
- Data not appearing in the Google Sheet
- Sheet operations fail with errors

**Possible Causes and Solutions:**

1. **Sheet Configuration**
   - Verify the Sheet ID and tab names
   - Check column names match what the workflow expects
   - Ensure the sheet isn't protected from editing

2. **Data Format Issues**
   - Check for data type mismatches
   - Look for special characters that might cause issues
   - Verify data isn't being truncated

3. **API Limitations**
   - Be aware of Google Sheets API limits
   - Implement batching for large data operations
   - Add error handling for API failures

## Data Quality Issues

### Missing or Incorrect Data

**Symptoms:**
- Some fields are consistently empty or incorrect
- Data appears in wrong columns

**Possible Causes and Solutions:**

1. **Extraction Pattern Issues**
   - Adjust AI prompts to better extract problematic fields
   - Add validation for commonly problematic fields
   - Implement fallback extraction methods

2. **CV Format Variations**
   - Test with different CV formats to identify patterns
   - Add preprocessing steps for non-standard formats
   - Create format-specific extraction paths

3. **Data Transformation Errors**
   - Review the Code nodes that transform data
   - Check for errors in data mapping
   - Add more robust error handling

### Duplicate Entries

**Symptoms:**
- Same CV appears multiple times in the Google Sheet
- Duplicate processing of the same file

**Possible Causes and Solutions:**

1. **Workflow Trigger Issues**
   - Implement deduplication based on file name or content
   - Add a tracking mechanism for processed files
   - Use a database to track processed files

2. **Manual Intervention**
   - Establish clear procedures for manual file handling
   - Document when files should be moved or deleted
   - Implement a logging system for manual operations

## Performance Issues

### Slow Processing

**Symptoms:**
- Workflow takes a long time to complete
- Timeouts during execution

**Possible Causes and Solutions:**

1. **Resource Limitations**
   - Check n8n server resources (CPU, memory)
   - Consider upgrading server resources
   - Optimize workflow for performance

2. **External Service Delays**
   - Monitor response times from external services
   - Implement timeouts and retry logic
   - Consider caching where appropriate

3. **Large File Processing**
   - Implement file size checks and limitations
   - Add preprocessing for large files
   - Consider parallel processing for multiple files

## Advanced Troubleshooting

### Debugging Techniques

1. **Node-by-Node Testing**
   - Execute individual nodes to isolate issues
   - Use the n8n debugger to inspect data at each step
   - Add "Debug" nodes to log intermediate results

2. **Logging and Monitoring**
   - Implement comprehensive logging
   - Monitor workflow executions
   - Set up alerts for failures

3. **Version Control**
   - Keep backups of working workflow versions
   - Document changes and their effects
   - Test changes in a staging environment first

### Getting Help

If you've tried the solutions in this guide and still have issues:

1. **n8n Community**
   - Search the [n8n forum](https://community.n8n.io/) for similar issues
   - Post detailed descriptions of your problem

2. **API Documentation**
   - Review documentation for the services you're using:
     - [Google Drive API](https://developers.google.com/drive/api/v3/reference)
     - [Google Sheets API](https://developers.google.com/sheets/api/reference/rest)
     - [OCR.space API](https://ocr.space/ocrapi)

3. **Professional Support**
   - Consider engaging with n8n experts for complex issues
   - Consult with API specialists for specific service problems
