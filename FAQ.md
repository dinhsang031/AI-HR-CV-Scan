# Frequently Asked Questions (FAQ)

This document answers common questions about the AI-HR-CV-Scan system. If you don't find your question answered here, refer to the other documentation files or contact the system administrator.

## General Questions

### What is the AI-HR-CV-Scan system?
The AI-HR-CV-Scan system is an automated workflow that processes CVs, extracts relevant information, evaluates candidates against job requirements, and organizes the data in a structured format. It helps HR departments and recruiters streamline the initial CV screening process.

### What technologies does the system use?
The system uses n8n for workflow automation, Google Drive for file storage, Google Sheets for data storage, OCR.space for text extraction from scanned documents, and Google Gemini AI for information extraction and candidate evaluation.

### Is the system suitable for my organization?
The system is designed for organizations of various sizes that regularly process CVs as part of their recruitment process. It's particularly valuable for HR departments that want to:
- Save time on initial CV screening
- Apply consistent evaluation criteria
- Build a searchable talent database
- Reduce unconscious bias in the screening process

### How much technical knowledge do I need to set up the system?
Setting up the system requires basic technical knowledge, including:
- Setting up an n8n instance
- Creating and configuring Google API credentials
- Basic understanding of Google Drive and Sheets
- Following technical setup instructions

If you have IT support, they can help with the initial setup, after which the system is relatively easy to use.

## Setup and Configuration

### How long does it take to set up the system?
Initial setup typically takes 2-4 hours, depending on your familiarity with the technologies involved. This includes:
- Setting up n8n (30-60 minutes)
- Creating Google API credentials (30-60 minutes)
- Configuring Google Drive and Sheets (30 minutes)
- Importing and configuring the workflow (30-60 minutes)
- Testing and troubleshooting (30-60 minutes)

### Can I customize the system for my specific needs?
Yes, the system is highly customizable. You can:
- Modify the AI prompts to extract different information
- Adjust the evaluation criteria for different positions
- Change the Google Sheet structure to include additional fields
- Modify the workflow to add additional steps or integrations

### Do I need to host n8n myself?
You have two options:
1. Self-host n8n on your own server or cloud infrastructure
2. Use n8n.cloud, the official hosted version of n8n (paid service)

The choice depends on your technical capabilities, budget, and security requirements.

### Can I use the system with other cloud storage providers?
The current implementation is designed specifically for Google Drive and Google Sheets. Adapting it to other providers (like Microsoft OneDrive/Excel or Dropbox) would require significant modifications to the workflow.

## Usage and Workflow

### How many CVs can the system process?
The system processes one CV at a time, with each processing cycle taking approximately 1-3 minutes depending on the CV's complexity and the OCR requirements. With the default schedule (every 5 minutes during business hours), it can theoretically process up to 12 CVs per hour.

Future enhancements could include batch processing for higher volume needs.

### What CV formats are supported?
The system currently supports:
- PDF files (both text-based and scanned with OCR)
- DOCX files

### What languages are supported for CV processing?
The system is primarily designed for Vietnamese and English CVs. The AI components can handle other languages to some extent, but extraction accuracy may vary. The system can be customized for better support of specific languages by adjusting the AI prompts.

### How accurate is the information extraction?
Accuracy depends on several factors:
- CV format and clarity
- Text quality (for scanned documents)
- Language used
- CV structure

Typically, the system achieves:
- 90%+ accuracy for well-structured, text-based CVs
- 70-90% accuracy for scanned or poorly structured CVs

Human verification of extracted information is recommended, especially for critical fields.

### How reliable is the candidate evaluation?
The AI evaluation provides a useful initial assessment but should not be the sole factor in hiring decisions. The evaluation is based on:
- Matching candidate skills and experience to job requirements
- Analyzing education and qualifications
- Assessing overall fit for the position

The system provides both a numerical score and a detailed explanation of the evaluation, which helps recruiters understand the reasoning behind the score.

## Data and Security

### Where is the candidate data stored?
All candidate data is stored in your own Google Drive and Google Sheets:
- Original CV files in Google Drive folders
- Extracted information in your Google Sheet

No data is stored on n8n servers or third-party systems (except temporarily during OCR processing).

### Is the system GDPR compliant?
The system can be implemented in a GDPR-compliant manner, but compliance ultimately depends on how you use and manage the data. Key considerations include:
- Obtaining appropriate consent from candidates
- Implementing proper data retention policies
- Providing candidates access to their data
- Securing access to the Google Sheet and Drive folders

Refer to the [Privacy and Security Guide](PRIVACY_SECURITY.md) for detailed information.

### Who can access the candidate data?
Access is controlled through Google's sharing settings:
- Only users with access to the specific Google Drive folders can view the CV files
- Only users with access to the Google Sheet can view the extracted data
- n8n credentials should be secured to prevent unauthorized workflow access

### How long is candidate data kept?
The system does not automatically delete data. You should implement your own data retention policy based on your organizational needs and applicable regulations. This can include:
- Regularly archiving or deleting old entries from the Google Sheet
- Removing CV files from Google Drive after a certain period
- Anonymizing candidate data for long-term storage

## Troubleshooting and Maintenance

### What should I do if the workflow stops working?
If the workflow stops working:
1. Check if n8n is running properly
2. Verify that all credentials are valid and not expired
3. Check the execution logs for error messages
4. Ensure Google Drive and Sheets are accessible
5. Verify that the OCR.space API key is valid
6. Restart the workflow

Refer to the [Troubleshooting Guide](TROUBLESHOOTING.md) for detailed steps.

### How do I update the system?
To update the system:
1. Export your current workflow from n8n
2. Import the new workflow version
3. Reconfigure credentials and settings
4. Test the updated workflow before activating it

It's recommended to keep a backup of your previous workflow version.

### Can I migrate my existing candidate data into the system?
Yes, you can manually add existing candidate data to the Google Sheet. However, the system is primarily designed for processing new CVs rather than importing existing data.

If you have a large volume of existing CVs to process, you could:
1. Place them in the CV Collection folder
2. Run the workflow manually to process them
3. Monitor the process to ensure proper extraction

### How do I back up the system?
To back up the system:
1. Export the n8n workflow regularly
2. Back up your Google Sheet data (export as CSV/Excel)
3. Back up your Google Drive folders containing CVs
4. Document any customizations you've made to the workflow

## Advanced Questions

### Can the system integrate with our ATS (Applicant Tracking System)?
The current version doesn't have direct ATS integration. However, since the data is stored in Google Sheets, you can:
- Export the data to your ATS manually
- Use Google Sheets integrations if your ATS supports them
- Develop custom integrations using the Google Sheets API

Future enhancements could include direct ATS integrations.

### Can the system handle video CVs or other non-text formats?
The current version is designed for text-based documents only. Processing video CVs would require significant enhancements to the workflow, including:
- Video processing capabilities
- Speech-to-text conversion
- Potentially different AI models for analysis

### How can I improve the AI evaluation accuracy?
To improve evaluation accuracy:
1. Use well-structured job descriptions following the template
2. Be specific about required skills and experience
3. Adjust the AI prompts in the "Chuyên gia HR" node
4. Provide feedback by comparing AI evaluations with your own assessments
5. Regularly update the system with improved prompts

### Can the system be used for other document processing tasks?
While designed specifically for CV processing, the core architecture could be adapted for other document processing tasks, such as:
- Contract analysis
- Financial document processing
- Research paper analysis
- Customer feedback processing

This would require significant modifications to the workflow and AI prompts.

### How can I contribute to the system's development?
If you'd like to contribute to the system's development:
1. Document any improvements or customizations you make
2. Share feedback on what works well and what could be improved
3. Suggest new features or enhancements
4. If you develop significant improvements, consider sharing them with the community

## Cost and Licensing

### What are the costs associated with running the system?
The costs include:
1. n8n hosting (self-hosted or n8n.cloud subscription)
2. Google Workspace (for Google Drive and Sheets)
3. OCR.space API (free tier available, paid tiers for higher volume)
4. Google Gemini AI API (pricing based on usage)

For a small to medium organization processing a moderate volume of CVs, the monthly cost typically ranges from $20-100 depending on your choices and volume.

### Are there any licensing restrictions?
The system is provided for demonstration and educational purposes. There are no specific licensing restrictions on the workflow itself, but you should comply with the terms of service for all integrated services:
- n8n licensing terms
- Google API terms of service
- OCR.space terms of service
- Google Gemini AI terms of service

### Can I use the system commercially?
Yes, you can use the system for commercial purposes within your organization. However, you cannot resell the system as a service without proper attribution and compliance with the licensing terms of all components.
