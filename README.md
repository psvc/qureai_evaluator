# Response Evaluation: Quantifying Trust and Accuracy

## Overview

This project provides a robust framework for evaluating the response quality of medical chatbots, particularly those leveraging Retrieval-Augmented Generation (RAG) and local Large Language Models (LLMs). Recognizing the critical need for trustworthy, accurate, and safe information in healthcare, this methodology employs a hybrid approach—combining automated AI evaluation with human-centric Likert scale assessments—to rigorously test conversational AI products.

The primary goal is to identify and mitigate issues such as factual inaccuracies (hallucinations), lack of clarity, and potential safety concerns, ensuring the AI delivers reliable and user-centric medical guidance.

## Features

- **Hybrid Evaluation Methodology**: Integrates automated evaluation by powerful LLMs (e.g., Gemini) with a structured Likert scale for objective scoring.
- **Adversarial Prompting**: Utilizes a curated dataset of diverse and challenging medical questions to stress-test chatbot responses.
- **Automated Scoring**: A custom Python script automates the evaluation process, generating Likert scale scores (1–5) and explanations for each response against predefined criteria.
- **Data-Driven Insights**: Generates detailed CSV outputs for granular analysis of response quality across various criteria and over time.
- **Continuous Improvement Loop**: Designed to inform iterative product development, helping quickly identify and address areas for enhancement.
- **Scalable & Efficient**: Leverages cost-effective and fast LLM APIs for efficient, large-scale evaluation.

## Methodology

Process is built around a rigorous three-step cycle:

### 1. Adversarial Prompting

The medical chatbot (e.g., `QureAI_assessment_test - 2107_offlineLLM.csv`) is fed a series of carefully crafted, diverse, and often adversarial medical questions. These questions are designed to push the boundaries of the bot's knowledge and understanding, testing its robustness and reliability under pressure.

### 2. Automated Quality Assessment

An external, high-performing LLM (Google Gemini Flash in this case) acts as an expert medical evaluator. It assesses each bot response against specific, predefined criteria (loaded from `evaluation_prompts.csv`).

The LLM generates a score on a Likert scale from 1 (Strongly Agree – fully meets criterion) to 5 (Strongly Disagree – completely fails criterion), accompanied by a brief explanation. This process is fully automated using a Python script, ensuring consistency and efficiency.

### 3. Continuous Product Iteration

The quantitative scores and qualitative explanations derived from the evaluation are then fed back into the product development cycle. This data-driven feedback loop enables the team to identify areas of weakness, experiment with improvements, and continually refine the chatbot's features and performance.

## Getting Started

To set up and run this evaluation framework, follow these steps:

### Prerequisites

- Python 3.8+
- `pip`
- Access to the Google Gemini API
- A `.env` file containing your `GOOGLE_API_KEY` (or `GEMINI_API_KEY`)

### Installation

Clone the repository:

```bash
git clone https://github.com/psvc/qureai_evaluator
cd qureai_evaluator
pyenv local 3.11.3
python -m venv .venv
source .venv/bin/activate
```

### Data Structure
Organize your data files in the `data/` directory:

## Output
- **Individual Evaluation Results (e.g. gemini_groq_qureai_offlineLLM.csv):**
  - Detailed results for each bot answer and criterion.
  - Columns: bot_question, bot_answer, evaluation_criterion, llm_raw_response, score, explanation, timestamp.

- **Transposed Scores (e.g. gemini_transposed_qureai_offlineLLM.csv):**
  - Pivoted table: bot_question as index, criteria as columns, scores as values.
  - Useful for overview/visualization (e.g., radar charts for criteria comparison).

## Future Improvements
- Human-in-the-Loop Integration: UI/system for annotator score input.
- Advanced Metrics: Response length, toxicity, adherence to guidelines.
- Dynamic LLM Selection: Easily switch between Gemini, Groq, OpenAI models.
- Dashboard Integration: Visualize results with Streamlit, Dash, or BI tools.
- Parallel Processing: Use async API calls/multiprocessing for larger datasets.





 
