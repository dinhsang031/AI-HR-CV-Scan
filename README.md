# AI HR CV Scan Automation System

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

An automated CV scanning and evaluation system powered by AI to streamline the recruitment process.

## Overview

AI-HR-CV-Scan is an intelligent workflow system that automates the initial screening of candidate CVs, extracting relevant information and evaluating candidates against job requirements. Built on the n8n workflow automation platform, it integrates Google Drive, Google Sheets, OCR technology, and Google Gemini AI to create a comprehensive recruitment assistant.

### Key Features

- **Automated CV Processing**: Automatically detects and processes new CVs uploaded to a designated Google Drive folder
- **Multi-format Support**: Handles both PDF and DOCX formats, including scanned documents via OCR
- **Intelligent Information Extraction**: Uses AI to extract candidate details, education, work experience, and skills
- **Automated Candidate Evaluation**: Compares candidate profiles against job requirements and provides a suitability score
- **Structured Data Storage**: Organizes all extracted information in a Google Sheet for easy filtering and analysis
- **Talent Pool Management**: Automatically organizes processed CVs into a talent database
- **Customizable Job Requirements**: Easily update job requirements to evaluate candidates for different positions

## How It Works

1. **CV Collection**: Upload CVs to a designated Google Drive folder
2. **Automated Processing**: The system automatically detects new files and processes them
3. **Text Extraction**: Text is extracted from PDF/DOCX files (with OCR for scanned documents)
4. **Information Extraction**: AI extracts structured information from the CV text
5. **Candidate Evaluation**: AI evaluates the candidate against current job requirements
6. **Data Storage**: All information is stored in a structured Google Sheet
7. **File Organization**: Processed CVs are renamed and moved to a talent pool folder

## Getting Started

### Prerequisites

- n8n instance (self-hosted or cloud)
- Google account with access to Drive and Sheets
- OCR.space API key (free tier available)
- Google Gemini AI API access

### Quick Setup

1. Import the workflow file into n8n
2. Configure Google Drive and Sheets connections
3. Set up the required folders and Google Sheet
4. Add job requirements to the sheet
5. Start uploading CVs

For detailed setup instructions, see the [Quick Start Guide](QUICK_START.md) or the comprehensive [Setup Guide](SETUP.md).

## Documentation

### Setup and Configuration
- [Setup Guide](SETUP.md) - Detailed installation and configuration instructions
- [Quick Start Guide](QUICK_START.md) - Essential steps to get up and running quickly
- [Google Sheet Structure](GOOGLE_SHEET_STRUCTURE.md) - Documentation of the data structure

### Usage Guides
- [Workflow Documentation](WORKFLOW.md) - Detailed explanation of the n8n workflow
- [Job Position Template](JOB_POSITION_TEMPLATE.md) - Guidelines for creating effective job descriptions
- [AI Evaluation Guide](AI_EVALUATION_GUIDE.md) - How to interpret candidate evaluations

### Technical Documentation
- [Architecture Overview](ARCHITECTURE.md) - System architecture and component interactions
- [Glossary](GLOSSARY.md) - Definitions of key terms and concepts
- [Troubleshooting Guide](TROUBLESHOOTING.md) - Solutions for common issues

### Additional Resources
- [Privacy and Security Guide](PRIVACY_SECURITY.md) - Guidelines for data handling and compliance
- [FAQ](FAQ.md) - Answers to frequently asked questions
- [Future Enhancements](FUTURE_ENHANCEMENTS.md) - Roadmap for future development
- [File Index](FILE_INDEX.md) - Comprehensive list of all project files

## Use Cases

### HR Departments
- Streamline initial CV screening process
- Create a searchable database of candidates
- Ensure consistent evaluation criteria
- Reduce time spent on administrative tasks

### Recruitment Agencies
- Process large volumes of CVs efficiently
- Quickly match candidates to job requirements
- Build and maintain a structured talent pool
- Provide data-driven candidate recommendations

### Small Businesses
- Implement professional recruitment processes with limited resources
- Ensure thorough evaluation of all applicants
- Maintain organized records of all applications
- Scale recruitment efforts without proportional time investment

## Benefits

- **Time Savings**: Reduce manual CV screening time by up to 80%
- **Consistency**: Apply the same evaluation criteria to all candidates
- **Organization**: Keep all candidate information structured and searchable
- **Scalability**: Process more CVs without proportional time increase
- **Data-Driven**: Make recruitment decisions based on comprehensive evaluations
- **Reduced Bias**: Focus on qualifications and experience with standardized evaluation

## Contributing

We welcome contributions to improve the AI-HR-CV-Scan system! See [Contributors](CONTRIBUTORS.md) for more information on how to contribute.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details.

## Acknowledgments

- n8n.io for the workflow automation platform
- Google for Drive, Sheets, and Gemini AI services
- OCR.space for text extraction capabilities

---

*Note: This system is designed to assist in the recruitment process, not replace human judgment. Always review AI evaluations and extracted information for accuracy.*
