# Sales Lead Scoring and Email Engagement Pipeline

![banner](data/Banner%20Agent%20sales%20pipeline.png)
This project automates sales lead qualification and email engagement using AI agents powered by CrewAI.

It scores potential leads, drafts engagement emails, and estimates token usage costs — all organized in a structured, scalable flow.

## 🛠️ Setup
1. Requirements
Make sure you have installed all necessary Python packages:

```
pip install -r requirements.txt
```
2. Environment Variables
This project uses environment variables for API keys and model settings.
You can set them by editing your .env file and loading it using:

```
from helper import load_env
load_env()
```

Important environment variables:

**GROQ_API_KEY**

**SERPER_API_KEY**



## 📚 Project Structure

**config/**	YAML files defining Agents and Tasks configs
requirements.txt	Python dependencies
main.ipynb 	Main flow implementation
## 🧩 How It Works
Agents and Tasks Loading

Loads YAML files to create specialized agents for lead qualification and email engagement.

Pydantic Models

Ensures structured output for leads using strongly typed models like LeadPersonalInfo, CompanyInfo, LeadScore, and LeadScoringResult.

Tools

Uses SerperDevTool (search engine) and ScrapeWebsiteTool (web scraping) for enriching data.

## Crew Setup
Creates two main crews:

**Lead Scoring Crew**: Collects lead data, analyzes cultural fit, scores the lead.

**Email Engagement Crew**: Drafts and optimizes engagement emails.

## Flow Creation

Using CrewAI's Flow system, it orchestrates the full pipeline:

Fetch leads ➡️ Score leads ➡️ Store scores ➡️ Filter high-quality leads ➡️ Write engagement emails ➡️ Send emails.

Metrics and Costs

Calculates token usage and estimated API costs for the Groq API calls.

Results Inspection

Displays lead scoring results in a readable format.

🚀 How to Run
In your notebook or script:


# Load environment and configs
load_env()

# Initialize and plot the flow
flow = SalesPipeline()
flow.plot()

# Kick off the flow
emails = await flow.kickoff()
📋 Note: You can visualize the process flow by opening the generated crewai_flow.html file.

📊 Cost Estimation
The project provides token usage metrics after running:

Lead Scoring

Email Drafting

Costs are estimated based on:


📦 Example Output
Example fields you will get for each lead:

Field	Example
Name	João Moura
Job Title	Director of Engineering
Role Relevance	9
Professional Background	10+ years in SaaS leadership
Company Name	Clearbit
Industry	Data Enrichment
Company Size	200
Revenue	$30M
Market Presence	8
Lead Score	85
Scoring Criteria	Relevance, Budget, Timing
Validation Notes	Strong alignment with use case
## 💡 Notes
Edit the leads database inside the fetch_leads method.

Customize YAML configs to add more agents or tweak task behavior.

Add real database storage and email-sending logic in the respective methods.

