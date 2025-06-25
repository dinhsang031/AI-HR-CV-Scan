# AI Evaluation Guide

This document explains how the AI-HR-CV-Scan system evaluates candidates and how to interpret the evaluation results. Understanding this process will help you make the most of the automated CV screening system.

## Evaluation Process Overview

The AI-HR-CV-Scan system uses a sophisticated AI evaluation process to assess candidate suitability for specific job positions. The evaluation is performed by the "Chuyên gia HR" node in the workflow, which uses Google Gemini AI to analyze candidate profiles against job requirements.

## Evaluation Components

The AI evaluation produces three key outputs:

### 1. Suitability Score (Điểm phù hợp)

- A numerical score from 1 to 10
- Higher scores indicate better matches for the position
- Score interpretation:
  - 1-3: Not suitable for the position
  - 4-6: Partially meets requirements
  - 7-8: Good match for the position
  - 9-10: Excellent match, highly recommended

### 2. Consideration Summary (Tóm tắt)

- A concise explanation of why the candidate received their score
- Highlights key factors that influenced the evaluation
- Provides context for the numerical score

### 3. Suitability Assessment (Sự phù hợp)

- A detailed list of the candidate's strengths relative to the position
- Specific skills, experiences, and qualifications that match the job requirements
- Areas where the candidate exceeds expectations

## Evaluation Criteria

The AI evaluates candidates based on several factors:

### 1. Skills Match

- Technical skills required for the position
- Soft skills relevant to the role
- Tools and technologies mentioned in the job description

### 2. Experience Relevance

- Years of experience in relevant roles
- Specific industry experience
- Project experience related to job requirements

### 3. Educational Background

- Degree level (Bachelor's, Master's, etc.)
- Field of study relevance
- Academic achievements

### 4. Career Trajectory

- Progression and growth in previous roles
- Consistency with the target position
- Leadership or specialized experience

## Sample Evaluation Output

Here's an example of what the AI evaluation output looks like in the Google Sheet:

| Field | Example Value |
|-------|---------------|
| Điểm phù hợp | 8 |
| Tóm tắt | Ứng viên có 4 năm kinh nghiệm phát triển web với React và Node.js, phù hợp với yêu cầu vị trí. Có bằng đại học CNTT và kinh nghiệm làm việc trong môi trường Agile. Thiếu kinh nghiệm với một số công nghệ yêu cầu như GraphQL, nhưng có nền tảng kỹ thuật vững để học nhanh. |
| Sự phù hợp | - 4 năm kinh nghiệm phát triển web (yêu cầu: 3 năm)<br>- Thành thạo React và Node.js<br>- Kinh nghiệm với RESTful API<br>- Tốt nghiệp đại học ngành CNTT<br>- Kinh nghiệm làm việc trong môi trường Agile/Scrum<br>- Kỹ năng Git tốt |

## Interpreting the Results

### How to Use the Suitability Score

The suitability score provides a quick way to filter and prioritize candidates:

- **High Priority (8-10)**: Schedule interviews promptly
- **Medium Priority (6-7)**: Consider for interviews if high-priority candidates are unavailable
- **Low Priority (4-5)**: Keep in talent pool for future positions
- **Not Suitable (1-3)**: Not recommended for the current position

### Beyond the Score

While the numerical score is useful for quick filtering, always review the detailed assessment:

1. **Look for Specific Strengths**: The "Sự phù hợp" field highlights specific qualifications that match your requirements.

2. **Consider Context**: The "Tóm tắt" field explains why the candidate received their score and provides important context.

3. **Identify Potential**: Some candidates may score lower but show potential for growth or have unique skills not captured by the score alone.

## Customizing the Evaluation

You can customize how the AI evaluates candidates by modifying the "Chuyên gia HR" node in the workflow:

1. **Adjust Evaluation Criteria**: Modify the prompt to emphasize different aspects of candidate profiles.

2. **Change Scoring Parameters**: Adjust how different factors are weighted in the final score.

3. **Add Custom Evaluation Fields**: Create additional evaluation categories specific to your organization's needs.

## Best Practices for Using AI Evaluations

### Do's

- **Use as a First Filter**: Let the AI handle initial screening to save time.
- **Review Details**: Always read the detailed assessment, not just the score.
- **Compare Multiple Candidates**: Use the standardized format to easily compare candidates.
- **Combine with Human Judgment**: Use AI evaluations alongside human expertise.

### Don'ts

- **Don't Rely Solely on Scores**: Avoid making decisions based only on numerical scores.
- **Don't Ignore Potential**: Some candidates may have transferable skills not directly matched to requirements.
- **Don't Skip Verification**: Verify key qualifications during interviews.

## Continuous Improvement

The AI evaluation system can be improved over time:

1. **Feedback Loop**: Compare AI evaluations with actual interview and job performance.
2. **Prompt Refinement**: Adjust AI prompts based on hiring outcomes.
3. **Custom Scoring**: Develop custom scoring models for different departments or roles.

## Ethical Considerations

When using AI for candidate evaluation:

1. **Avoid Bias**: Regularly review evaluations for potential biases.
2. **Maintain Transparency**: Be clear with candidates about the use of AI in the screening process.
3. **Human Oversight**: Always have human oversight in the final hiring decisions.
4. **Data Privacy**: Ensure all candidate data is handled according to privacy regulations.

## Conclusion

The AI evaluation system provides a powerful tool for initial candidate screening, but it works best when combined with human expertise. Use the scores and detailed assessments as a starting point for your hiring process, not as the final decision.
