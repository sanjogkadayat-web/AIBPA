# Process Design Document (PDD) - Milestone 2: MVW Design

### Process Design Document (PDD) - Phase 1 Complete

**Team Name:** Albina, Jack and Sanjog (Team JAS)

**Project Title:** Intelligent Resume Editor Assistant

**Status:** Milestone 2 (Solution Design)

## Part 1: Process Analysis

### 1.1 The Scenario

The workflow analyzed represents how a job seeker/student currently tailors their resume for a specific job posting to have a strong fit.

**Who does it?**

Dolan undergraduate or graduate student

**Trigger**

- Student finds a job or internship posting
- On LinkedIn, company website, job board, or referral
- Often under time pressure to apply quickly

**When**

Throughout the semester, especially during recruiting periods

**Current manual behavior**

- Students manually prepare application materials for the job posting.
- The student is notified of a new job posting and decides to apply
- Does a research on the company background

Edits resume:

- Changes bullet points
- Adjusts keywords
- Removes/reshuffles content
- Tries to “guess” what the recruiter wants

Submits application through job portal


### 1.2 The "As-Is" Diagram (Mermaid)

```mermaid
flowchart LR

A[Find Job Posting] --> B[Read Job Description]
B --> C[Research Company]
C --> D[Manually Edit Resume]
D --> E{Feels Aligned?}
E -- No --> D
E -- Yes --> F[Submit Application]
```

### 1.3 Pain Point Diagnosis

**The Bottleneck:**

The primary bottleneck occurs during manual ATS (Applicant Tracking Systems) keyword alignment and resume bullet rewriting. This step dominates the workflow and directly influences whether an application is submitted with confidence.

**The Cost:**

Time: Approximately 5-8 hours per week spent on manual customization, keyword checking, and version handling.

Opportunity Cost: Missed recruiter callbacks or interview opportunities for strong-fit roles due to keyword misalignment.

Cognitive Load: High mental fatigue and anxiety caused by uncertainty around ATS rejection and resume effectiveness.
