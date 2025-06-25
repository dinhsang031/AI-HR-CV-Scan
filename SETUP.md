# Setup Guide

This guide provides step-by-step instructions for setting up the AI-HR-CV-Scan system. Follow these instructions to configure the workflow and start automating your CV screening process.

## Prerequisites

Before setting up the system, ensure you have:

1. **n8n Instance**: 
   - A running n8n instance (self-hosted or cloud)
   - n8n version 0.214.0 or higher recommended

2. **Google Account**:
   - Google account with access to Google Drive and Google Sheets
   - Permission to create API credentials

3. **API Keys**:
   - OCR.space API key (free tier available)
   - Google API credentials

## Step 1: Set Up Google Services

### Google Drive Setup

1. Create two folders in your Google Drive:
   - CV Collection Folder: Where new CVs will be uploaded
   - Talent Pool Folder: Where processed CVs will be moved

2. Note the folder IDs for both folders:
   - Open each folder in your browser
   - The folder ID is in the URL: `https://drive.google.com/drive/folders/[FOLDER_ID]`

### Google Sheet Setup

1. Create a new Google Sheet with two tabs:
   - "Datapool" (main tab)
   - "Vị trí tuyển dụng" (job positions)

2. In the "Datapool" tab, create the following columns:
   - Điểm phù hợp
   - Thời gian
   - Vị trí ứng tuyển
   - Họ và Tên
   - Số điện thoại
   - Email
   - Nơi ở
   - Năm sinh
   - Giới tính
   - Bằng cấp
   - Trường tốt nghiệp
   - Ngành tốt nghiệp
   - Năm tốt nghiệp
   - Loại tốt nghiệp
   - Lịch sử làm việc
   - Task công việc
   - Kỹ năng
   - Chứng chỉ
   - Tóm tắt
   - Sự phù hợp
   - Link Hồ sơ

3. In the "Vị trí tuyển dụng" tab, create two columns:
   - col_1 (for timestamps)
   - col_2 (for job position descriptions)

4. Note your Google Sheet ID:
   - The Sheet ID is in the URL: `https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit`

## Step 2: Create API Credentials

### Google API Credentials

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project
3. Enable the following APIs:
   - Google Drive API
   - Google Sheets API
4. Create OAuth 2.0 credentials:
   - Application type: Web application
   - Add authorized redirect URIs:
     - `https://[YOUR_N8N_DOMAIN]/oauth/callback`
5. Download the credentials JSON file

### OCR.space API Key

1. Sign up for an account at [OCR.space](https://ocr.space/ocrapi)
2. Obtain your free API key

## Step 3: Import and Configure the Workflow

1. Access your n8n instance
2. Go to Workflows > Import From File
3. Upload the `Agent_HR_CV_Scan.json` file
4. Configure the credentials:
   - Add Google Drive OAuth2 credentials
   - Add Google Sheets OAuth2 credentials
   - Add OCR.space API key
   - Add Google Gemini API credentials

5. Update the following nodes with your specific information:
   - **Tìm file1** and **Tìm file**: Update the folder ID to your CV Collection Folder
   - **Vị trí cần tuyển** and **Tổng hợp dữ liệu và DTB**: Update the Sheet ID to your Google Sheet
   - **Chuyển sang Talent pool**: Update the folder ID to your Talent Pool Folder

## Step 4: Test the Workflow

1. Add a test job position to your "Vị trí tuyển dụng" tab:
   - col_1: Current date (e.g., "25/06/2025")
   - col_2: Job position (e.g., "Software Developer with 3+ years experience in JavaScript")

2. Upload a test CV to your CV Collection Folder

3. Run the workflow manually:
   - In n8n, open the workflow
   - Click "Execute Workflow"
   - Monitor the execution for any errors

4. Check your Google Sheet to verify that the data was correctly extracted and stored

## Step 5: Activate the Automated Schedule

1. In the n8n workflow editor, click on the "Active" toggle to activate the workflow
2. The Schedule Trigger will now run the workflow automatically according to the defined schedule

## Customization Options

### Adjusting the Schedule

1. Click on the "Schedule Trigger" node
2. Modify the cron expression to change the schedule:
   - Default: `*/5 8-17 * * 1-6` (Every 5 minutes from 8 AM to 5 PM, Monday to Saturday)
   - For hourly: `0 * * * *`
   - For daily: `0 9 * * *` (Every day at 9 AM)

### Customizing AI Prompts

1. To adjust how information is extracted:
   - Modify the "Dữ liệu cá nhân" and "Thông tin công việc" nodes
   - Update the system prompt templates to change extraction behavior

2. To adjust candidate evaluation:
   - Modify the "Chuyên gia HR" node
   - Update the prompt to change evaluation criteria

## Troubleshooting

### Common Issues

1. **Authentication Errors**:
   - Ensure your Google OAuth credentials are correctly configured
   - Check that redirect URIs match your n8n instance

2. **File Processing Errors**:
   - Verify that file formats are supported (PDF, DOCX)
   - Check OCR API key if text extraction fails

3. **Data Not Appearing in Google Sheet**:
   - Verify Sheet ID and tab names
   - Check Google Sheets API permissions

### Getting Help

If you encounter issues:

1. Check the n8n logs for error messages
2. Verify all credentials are valid and have the necessary permissions
3. Test individual nodes to isolate the problem

## Maintenance

### Regular Tasks

1. **Monitor Google Sheet**: Periodically check for duplicate or incomplete entries
2. **Update Job Positions**: Keep the "Vị trí tuyển dụng" tab updated with current openings
3. **Credential Renewal**: Refresh OAuth tokens if they expire

### Backup Recommendations

1. Export your n8n workflow regularly
2. Create backups of your Google Sheet data
3. Document any customizations made to the workflow
