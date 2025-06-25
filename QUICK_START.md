# Quick Start Guide

This guide provides the essential steps to quickly set up and start using the AI-HR-CV-Scan system. For more detailed instructions, refer to the [Setup Guide](SETUP.md).

## Prerequisites

- n8n instance (self-hosted or cloud)
- Google account with access to Drive and Sheets
- OCR.space API key (free tier available)
- Google Gemini AI API access

## 1. Set Up Google Drive

1. Create two folders in your Google Drive:
   - **CV Collection Folder**: Where new CVs will be uploaded
   - **Talent Pool Folder**: Where processed CVs will be moved

2. Note the folder IDs from the URL:
   ```
   https://drive.google.com/drive/folders/[FOLDER_ID]
   ```

## 2. Set Up Google Sheet

1. Create a new Google Sheet with two tabs:
   - **Datapool**: Main tab for storing candidate data
   - **Vị trí tuyển dụng**: Tab for job positions

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
   - col_1 (for dates)
   - col_2 (for job descriptions)

4. Note your Google Sheet ID from the URL:
   ```
   https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit
   ```

## 3. Create API Credentials

### Google API

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project
3. Enable the Google Drive API and Google Sheets API
4. Create OAuth 2.0 credentials (Web application type)
5. Add redirect URI: `https://[YOUR_N8N_DOMAIN]/oauth/callback`
6. Download the credentials JSON file

### OCR.space API

1. Sign up at [OCR.space](https://ocr.space/ocrapi)
2. Obtain your free API key

### Google Gemini AI API

1. Get API access from [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create an API key

## 4. Import and Configure the Workflow

1. Access your n8n instance
2. Go to Workflows > Import From File
3. Upload the `Agent_HR_CV_Scan.json` file
4. Configure credentials:
   - Add Google Drive OAuth2 credentials
   - Add Google Sheets OAuth2 credentials
   - Add OCR.space API key
   - Add Google Gemini API credentials

5. Update node configurations:
   - **Tìm file1** and **Tìm file**: Update folder ID to your CV Collection Folder
   - **Vị trí cần tuyển** and **Tổng hợp dữ liệu và DTB**: Update Sheet ID
   - **Chuyển sang Talent pool**: Update folder ID to your Talent Pool Folder

## 5. Add a Test Job Position

1. In your Google Sheet, go to the "Vị trí tuyển dụng" tab
2. Add a new row with:
   - col_1: Current date (e.g., "25/06/2025")
   - col_2: Job description following the format in [JOB_POSITION_TEMPLATE.md](JOB_POSITION_TEMPLATE.md)

Example:
```
Software Developer

Yêu cầu:
- Phát triển và bảo trì các ứng dụng web
- Tối ưu hóa hiệu suất ứng dụng
- Làm việc trong môi trường Agile/Scrum

Kỹ năng:
- JavaScript/TypeScript
- React hoặc Angular
- Node.js
- RESTful API

Kinh nghiệm:
- Tối thiểu 3 năm kinh nghiệm phát triển phần mềm

Bằng cấp:
- Tốt nghiệp Đại học chuyên ngành CNTT hoặc tương đương
```

## 6. Test the Workflow

1. Upload a test CV to your CV Collection Folder in Google Drive
2. In n8n, open the workflow
3. Click "Execute Workflow"
4. Monitor the execution for any errors
5. Check your Google Sheet to verify data was correctly extracted and stored
6. Verify the CV was moved to the Talent Pool folder and renamed

## 7. Activate Automated Processing

1. In the n8n workflow editor, click the "Active" toggle to activate the workflow
2. The workflow will now run automatically according to the schedule (every 5 minutes during business hours on weekdays)

## 8. Regular Usage

1. **Add Job Positions**: Add new job positions to the "Vị trí tuyển dụng" tab as needed
2. **Upload CVs**: Place new CVs in the CV Collection Folder
3. **Review Results**: Check the "Datapool" tab for processed candidates
4. **Access CVs**: Use the links in the "Link Hồ sơ" column to access the original CVs

## Troubleshooting

If you encounter issues:

1. Check the n8n execution logs for error messages
2. Verify all credentials are valid
3. Ensure folder and sheet IDs are correct
4. Refer to the [Troubleshooting Guide](TROUBLESHOOTING.md) for common issues and solutions

## Next Steps

After getting the basic system running:

1. Customize AI prompts for better extraction and evaluation
2. Adjust the schedule to match your recruitment volume
3. Set up regular backups of your Google Sheet data
4. Review the [Future Enhancements](FUTURE_ENHANCEMENTS.md) document for improvement ideas
