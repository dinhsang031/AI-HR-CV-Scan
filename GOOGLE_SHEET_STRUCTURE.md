# Google Sheet Structure

This document explains the structure of the Google Sheet used by the AI-HR-CV-Scan system. The sheet serves as the central database for storing job requirements, candidate information, and evaluation results.

## Overview

The Google Sheet consists of two main tabs:
1. **Datapool** - Stores all extracted candidate information and evaluation results
2. **Vị trí tuyển dụng** (Job Positions) - Contains job descriptions and requirements

## Sheet ID

When setting up the system, you'll need to provide the Google Sheet ID in the workflow configuration. You can find this ID in the URL of your Google Sheet:

```
https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit
```

The Sheet ID is the long alphanumeric string between `/d/` and `/edit` in the URL.

## Tab 1: Datapool

The Datapool tab stores all candidate information extracted from CVs, along with evaluation results. Each row represents one candidate, with columns for different data points.

### Column Structure

| Column Name | Description | Data Type | Example |
|-------------|-------------|-----------|---------|
| Điểm phù hợp | Suitability score (1-10) | Number | 8 |
| Thời gian | Processing timestamp | Date/Time | 25/06/2025 14:30:45 |
| Vị trí ứng tuyển | Position applied for | Text | Software Developer |
| Họ và Tên | Full name | Text | Nguyen Van A |
| Số điện thoại | Phone number | Text | 0912345678 |
| Email | Email address | Text | example@email.com |
| Nơi ở | Location/Address | Text | Ho Chi Minh City |
| Năm sinh | Year of birth | Number | 1990 |
| Giới tính | Gender | Text | Nam |
| Bằng cấp | Highest degree/qualification | Text | Đại học |
| Trường tốt nghiệp | University/Institution | Text | Đại học Bách Khoa TP.HCM |
| Ngành tốt nghiệp | Field of study | Text | Công nghệ thông tin |
| Năm tốt nghiệp | Graduation year | Number | 2015 |
| Loại tốt nghiệp | Graduation classification | Text | Giỏi |
| Lịch sử làm việc | Work history | Text | 2015-2018: ABC Company - Developer... |
| Task công việc | Job responsibilities | Text | Phát triển ứng dụng web, tối ưu hóa... |
| Kỹ năng | Skills | Text | JavaScript, React, Node.js, SQL... |
| Chứng chỉ | Certifications | Text | AWS Certified Developer, IELTS 7.0... |
| Tóm tắt | Evaluation summary | Text | Ứng viên có 5 năm kinh nghiệm... |
| Sự phù hợp | Detailed suitability assessment | Text | - Kinh nghiệm phù hợp với yêu cầu...\n- Kỹ năng JavaScript và React...\n- Thiếu kinh nghiệm về... |
| Link Hồ sơ | Link to CV file in Google Drive | URL | https://drive.google.com/file/d/... |

### Data Format Guidelines

- **Điểm phù hợp**: Numerical score from 1-10
- **Thời gian**: Automatically generated timestamp in DD/MM/YYYY HH:MM:SS format
- **Lịch sử làm việc**: Typically formatted as "Year-Year: Company - Position"
- **Kỹ năng**: Comma-separated list of skills
- **Sự phù hợp**: Bullet points (each starting with "-") listing specific matches to job requirements
- **Link Hồ sơ**: Direct link to the CV file in the Talent Pool folder

### Example Row

```
Điểm phù hợp: 8
Thời gian: 25/06/2025 14:30:45
Vị trí ứng tuyển: Software Developer
Họ và Tên: Nguyen Van A
Số điện thoại: 0912345678
Email: example@email.com
Nơi ở: Ho Chi Minh City
Năm sinh: 1990
Giới tính: Nam
Bằng cấp: Đại học
Trường tốt nghiệp: Đại học Bách Khoa TP.HCM
Ngành tốt nghiệp: Công nghệ thông tin
Năm tốt nghiệp: 2015
Loại tốt nghiệp: Giỏi
Lịch sử làm việc: 2015-2018: ABC Company - Developer; 2018-Present: XYZ Corp - Senior Developer
Task công việc: Phát triển ứng dụng web, tối ưu hóa hiệu suất, thiết kế database
Kỹ năng: JavaScript, React, Node.js, SQL, Git, Agile/Scrum
Chứng chỉ: AWS Certified Developer, IELTS 7.0
Tóm tắt: Ứng viên có 5 năm kinh nghiệm phát triển web, phù hợp với vị trí Software Developer. Có kinh nghiệm với React và Node.js, đáp ứng tốt các yêu cầu kỹ thuật.
Sự phù hợp: - Kinh nghiệm phát triển web (5 năm, yêu cầu: 3 năm)\n- Kỹ năng JavaScript và React phù hợp với yêu cầu\n- Có kinh nghiệm làm việc trong môi trường Agile\n- Thiếu kinh nghiệm về GraphQL
Link Hồ sơ: https://drive.google.com/file/d/1a2b3c4d5e6f7g8h9i0j/view
```

## Tab 2: Vị trí tuyển dụng (Job Positions)

The "Vị trí tuyển dụng" tab contains job descriptions and requirements used for candidate evaluation. The system uses the most recent job position (based on date) for evaluating new candidates.

### Column Structure

| Column Name | Description | Data Type | Example |
|-------------|-------------|-----------|---------|
| col_1 | Date of job posting | Date | 25/06/2025 |
| col_2 | Job description and requirements | Text | [See format below] |

### Job Description Format

The job description in col_2 should follow this structure for optimal AI evaluation:

```
[Job Title]

Yêu cầu:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]
...

Kỹ năng:
- [Skill 1]
- [Skill 2]
- [Skill 3]
...

Kinh nghiệm:
- [Experience requirement]

Bằng cấp:
- [Education requirement]
```

### Example Job Description

```
Software Developer

Yêu cầu:
- Phát triển và bảo trì các ứng dụng web
- Tối ưu hóa hiệu suất ứng dụng
- Làm việc trong môi trường Agile/Scrum
- Tham gia vào quá trình thiết kế và review code

Kỹ năng:
- JavaScript/TypeScript
- React hoặc Angular
- Node.js
- RESTful API
- Git
- SQL/NoSQL databases

Kinh nghiệm:
- Tối thiểu 3 năm kinh nghiệm phát triển phần mềm

Bằng cấp:
- Tốt nghiệp Đại học chuyên ngành CNTT hoặc tương đương
```

For more detailed guidelines and examples, see the [Job Position Template](JOB_POSITION_TEMPLATE.md).

## Sheet Setup Instructions

### Creating the Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new sheet
2. Rename the default tab to "Datapool"
3. Create a second tab named "Vị trí tuyển dụng"

### Setting Up the Datapool Tab

1. Add the column headers as listed in the Column Structure section above
2. Format the sheet as needed (optional):
   - Set "Điểm phù hợp" column to Number format
   - Set "Thời gian" column to Date Time format
   - Set "Link Hồ sơ" column to Hyperlink format

### Setting Up the Vị trí tuyển dụng Tab

1. Add two column headers: "col_1" and "col_2"
2. Add at least one job position following the format described above
3. Set the date in col_1 to the current date

## Workflow Integration

The AI-HR-CV-Scan workflow interacts with the Google Sheet in several ways:

1. **Reading Job Requirements**: The workflow reads the most recent job position from the "Vị trí tuyển dụng" tab to use for candidate evaluation.

2. **Writing Candidate Data**: After processing a CV, the workflow writes all extracted information and evaluation results to a new row in the "Datapool" tab.

3. **Updating Links**: Once a CV is moved to the Talent Pool folder, the workflow updates the "Link Hồ sơ" column with the new file location.

## Data Management Best Practices

### Regular Maintenance

- Periodically archive old data to prevent the sheet from becoming too large
- Consider creating separate sheets for different job categories if processing large volumes of CVs
- Regularly back up the sheet data (File > Download > Microsoft Excel)

### Data Organization

- Use filters to sort and analyze candidates
- Create views for different hiring managers
- Use conditional formatting to highlight high-scoring candidates

### Security Considerations

- Share the sheet only with necessary personnel
- Consider using Google Sheets' protected ranges feature to prevent accidental edits
- Regularly review access permissions

## Customization Options

The sheet structure can be customized to fit your specific needs:

- Add additional columns for tracking interview status, hiring decisions, etc.
- Create additional tabs for different departments or positions
- Add formulas for additional analysis or scoring

If you modify the column structure, you'll need to update the corresponding nodes in the n8n workflow to match your changes.

## Troubleshooting

### Common Issues

- **Missing Data**: If certain columns are consistently empty, check the AI prompts in the workflow
- **Formatting Problems**: If data appears in unexpected formats, check the data transformation nodes in the workflow
- **Access Errors**: Ensure the Google account used by n8n has edit access to the sheet

### Data Validation

Consider adding data validation rules to your sheet to ensure consistency:

- List validation for fields like "Giới tính" or "Bằng cấp"
- Number range validation for "Điểm phù hợp" (1-10)
- Date validation for "Thời gian"

This can help maintain data quality and make filtering more effective.
