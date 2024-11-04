# Project Overview
This repository contains resources and guidelines to quality assure Terms of Reference (ToR) for development aid evaluations. 

This README provides:

- **A prompt for assessing ToR for development aid evaluations** using large language models (LLMs) to generate quality feedback.
- **A Python script that performs a similar assessment of ToR for development aid evaluations with additional features** such as simulation of feedback from two different perspectives.

## Prompt for LLM Chatbots
Use the following prompt in a chatbot to evaluate a ToR for development aid evaluation according to a specified quality assessment protocol. It includes a structured scoring guide covering multiple ToR components. The scoring protocol was initially developed based on similar frameworks used in studies of decentralized evaluations conducted by the Department for Evaluation at Norad in 2017, 2020, and 2021 (https://www.norad.no/en/evaluations/evaluations/planned-evaluations/study-assessment-of-quality-of-decentralised-evaluations-in-norwegian-aid-management). These protocols were then revised based on my professional judgment and experience, and further refined through test trials in the OpenAI Playground, incorporating feedback from GPT-4o. The prompt has been tested with both ChatGPT (GPT-4o and GPT-4o-mini) and Claude (3.5 Sonnet). 
```
Please assess the following ToR document according to the scoring guide provided, and return feedback in markdown format:

### Terms of Reference Quality Assessment Protocol:

#### 1. Context and Background
Objective: Evaluate the extent to which the ToR provide relevant background and context of the program being evaluated.
- **Criteria**:
  - Inclusion of socio-economic, political, or cultural context pertinent to the evaluation.
  - Reference to previous evaluations or related evidence.
- **Scoring**:
  - 4: Comprehensive context with all relevant information.
  - 3: Adequate but with minor gaps.
  - 2: Limited context with major gaps.
  - 1: Context missing.

#### 2. Purpose, Rationale, and Evaluation Objectives
Objective: Assess whether the ToR clearly state the purpose, intended use, and specific objectives of the evaluation.
- **Criteria**:
  - Clear rationale on why the evaluation is conducted and for whom.
  - Articulation of the ToR's purpose in terms of accountability or learning functions.
  - Specific evaluation objectives that outline what the evaluation aims to accomplish, serving as a foundation for developing relevant questions and methodology.
- **Scoring**:
  - 4: Fully clear and detailed purpose, rationale, and objectives.
  - 3: Mostly clear with minor gaps.
  - 2: Described but with significant gaps.
  - 1: Not stated or unclear.

#### 3. Evaluation Scope
Objective: Ensure the ToR clearly outline the scope, including geographic, temporal, and thematic boundaries of the evaluation.
- **Criteria**:
  - Clear definition of geographic, temporal, and thematic scope, delineating the focus areas of the evaluation.
- **Scoring**:
  - 4: Fully defined scope with relevant details.
  - 3: Mostly clear scope, minor gaps in detail.
  - 2: Limited description of scope with significant gaps.
  - 1: Scope not provided or unclear.
- **Additional Commentary (non-scored)**: Please add any relevant commentary on whether the ToR reference specific evaluation criteria (e.g., OECD-DAC criteria), as this can enhance the evaluation’s alignment with standard frameworks.

#### 4. Evaluation Questions and Relevance
Objective: Determine if the ToR include tailored and relevant evaluation questions.
- **Criteria**:
  - Questions are specific, aligned with the evaluation objectives (outlined under Purpose), and relevant to the intended use.
- **Scoring**:
  - 4: Evaluation questions are specific, relevant, and customized.
  - 3: Mostly specific and relevant, minor gaps.
  - 2: Evaluation questions lack relevance or specificity.
  - 1: No clear questions.

#### 5. Methodology and Feasibility
Objective: Assess if the ToR provide a feasible methodological approach considering the evaluation questions, given the timeframe and resources.
- **Criteria**:
  - Proposed methodology is clear, suitable for addressing the evaluation questions, and feasible within the set timeline.
- **Scoring**:
  - 4: Clear, feasible methodology aligned with evaluation questions.
  - 3: Feasible with minor adjustments needed.
  - 2: Major feasibility issues.
  - 1: Unfeasible or not described.

#### 6. Roles and Responsibilities
Objective: Evaluate whether the ToR clearly outline roles, responsibilities, and references to quality assurance steps.
- **Criteria**:
  - Clear definition of roles for consultants, team members, and commissioners.
  - References to quality assurance steps in the evaluation.
- **Scoring**:
  - 4: All roles and quality assurance steps clearly defined.
  - 3: Mostly clear with minor ambiguities.
  - 2: Described but with major gaps.
  - 1: Not defined or unclear.
- **Additional Commentary (non-scored)**: Please include commentary on process elements in the ToR, such as evaluation phases (e.g., inception, data collection, reporting) and other process-related instructions, as these insights can highlight procedural guidance in the ToR.

#### 7. Ethics, Risk, and Mitigation Strategies
Objective: Evaluate whether the ToR address ethical considerations, potential risks, and mitigation strategies relevant to the evaluation.
- **Criteria**:
  - Mention of ethical standards or safeguards, with relevant considerations such as human rights, gender, or environmental impact.
  - Identification of key risks (e.g., data availability, stakeholder engagement, logistical challenges).
  - Mitigation strategies that are practical and aligned with the evaluation's scope and timeline.
- **Scoring**:
  - 4: Comprehensive ethical considerations and risk assessment with robust mitigation strategies.
  - 3: Adequate ethics and risk assessment with minor gaps in mitigation plans.
  - 2: Limited ethical considerations or risk assessment with insufficient mitigation strategies.
  - 1: Ethics or risk assessment not included or poorly addressed.

#### 8. Deliverables
Objective: Ensure the ToR clearly outline all required deliverables, including reports and datasets, to support transparency and replicability.
- **Criteria**:
  - Specifies all essential deliverables, including an inception report, a draft report, and a final report, with clear guidelines on content, format, quality standards, and submission timelines.
  - Includes a requirement for datasets generated or used during the evaluation, detailing standards for documentation and organization to facilitate replicability and future use.
  - Lists any additional deliverables (e.g., executive summaries, presentations) and provides expectations for these.
- **Scoring**:
  - 4: Comprehensive list of deliverables, including datasets with complete guidance on format, standards, and timelines for each deliverable.
  - 3: Deliverables and expectations are mostly clear, including datasets, but minor gaps in guidance or format expectations exist.
  - 2: Limited information on deliverables, including datasets, with significant gaps in format or expectations.
  - 1: Deliverables, including datasets, are not clearly defined or missing from the ToR.

---

Provide your evaluation in markdown, including scores, comments, and any additional commentary specified in each section.
```

## Python Script 

This Python script automates the assessment of ToR using the same structured scoring guide as in the prompt above, but with some additional features. It uses OpenAI's API to quality assure and score the document, and to generate feedback from two additional perspectives. The script also includes a readability function. 

#### Key Components

1. **ToR Assessment using the quality assessment score**\
   The script first assesses the ToR document using a set of structured criteria across various dimensions, as with the prompt above. Each dimension has a scoring system, and the model generates markdown-formatted feedback with scores and commentary.

2. **Feedback from two different perspectives**:

   - **Evaluation Team**: Simulates feedback from an evaluation team that could carry out the assignment, focusing on operational clarity (e.g., clear timelines, defined deliverables, and resource allocation) and feasibility.
   - **Norwegian Development Aid Bureaucrat**: Provides feedback as if it were reviewed by a bureaucrat within the Norwegian development aid system, focusing on ease of understanding, clarity, and policy alignment.

3. **Readability Analysis**:\
   The Flesch Reading Ease score measures how easy the ToR document is to read, ranging from 0 to 100, with higher values meaning easier readability. Typical score ranges are: 90-100 (very easy), 60-70 (standard), 30-50 (difficult), and below 30 (very complex). In my testing with real-life ToR evaluation examples, max. scores have generally been around 35. Establishing an acceptable readability score for ToRs depends on the purpose and nature of these documents and involves many factors. While the score alone is of very limited use, it offers context when interpreted alongside feedback from the two different perspectives.

4. **Summary Generation**:\
   Combines feedback from all perspectives and the readability score into a brief summary, outlining the document’s main strengths and areas for improvement.

5. **Report Generation in Word Document**:\
   Compiles the assessment, feedback, readability score, and summary into a structured Microsoft Word report.

#### Requirements
To run this script, you’ll need the following dependencies:
```
pip install openai
pip install python-docx
pip install textstat
```

#### How to Use

1. **Run the script**: Input your ToR document when prompted, marking the end of the document input with the word "END".
2. **Generate Report**: The script will process the text and produce a Word document titled `ToR_Quality_Assurance_Report.docx` containing detailed feedback on each assessment area.


