# 🤖 ResearchMind AI Agent

A **Multi-Agent AI Research Assistant** that automates the research workflow by searching the web, reading relevant sources, generating structured research reports, and critically evaluating the final output using specialized AI agents.

## 🌐 Live Demo

🚀 **Try the application here**

[https://researchmind-ai-agent-by2hritwik.streamlit.app](https://researchmind-ai-agent-by2hritwik.streamlit.app)

## 💻 GitHub Repository

[https://github.com/hritwikrupesh/researchmind-ai-agent](https://github.com/hritwikrupesh/researchmind-ai-agent)

---

## 🌟 Features

---

- 🔎 AI-powered Web Search using Tavily
- 🤖 Multi-Agent AI Architecture
- 📖 Automated Web Page Reading & Scraping
- ✍️ AI-powered Research Report Generation
- 🧐 AI-based Report Critique
- 📊 Structured Research Output
- 📑 Source Collection
- 📥 Downloadable Research Report
- 🖥️ Interactive Streamlit Web Application
- ⚡ Groq-powered LLM inference
- 🦜 LangChain Agent Orchestration
- 🔐 Secure API Key Management
- ☁️ Streamlit Community Cloud Deployment
- 🧩 Modular Python Project Structure

---

# 🧠 Multi-Agent Architecture

ResearchMind divides the research process into specialized components.

```text
                    Research Topic
                          │
                          ▼
                 ┌─────────────────┐
                 │  Search Agent   │
                 │     Tavily      │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  Reader Agent   │
                 │ Web Scraping    │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  Writer Chain   │
                 │ Report Creation │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  Critic Chain   │
                 │ Report Review   │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  Final Output   │
                 └─────────────────┘
🔄 Research Workflow
User enters a research topic
Search Agent searches the web using Tavily
Relevant search results are collected
Reader Agent selects a relevant source
The selected webpage is scraped
Search results and scraped content are combined
Writer Chain generates a structured research report
Critic Chain evaluates the generated report
Results are displayed through Streamlit
User can download the generated report
🤖 Agents & Components
🔎 Search Agent

The Search Agent is responsible for finding relevant information from the web.

Tool
Tavily Web Search
Output
Title
URL
Search snippet
📖 Reader Agent

The Reader Agent analyzes the search results and selects a relevant URL for deeper reading.

It uses a custom web-scraping tool built with:

Requests
BeautifulSoup

The scraper removes unnecessary HTML elements such as scripts, styles, navigation, and footer content before extracting readable text.

✍️ Writer Chain

The Writer Chain combines:

Research Topic
+
Search Results
+
Scraped Content

and generates a structured research report containing:

Introduction
Key Findings
Conclusion
Sources
🧐 Critic Chain

The Critic Chain evaluates the generated research report.

The evaluation includes:

Score
Strengths
Areas to Improve
One-line Verdict

Example:

Score: X/10

Strengths:

- ...
- ...

Areas to Improve:

- ...
- ...

One line verdict:

...
🛠️ Tech Stack
Category	Technologies
Programming	Python
Web Application	Streamlit
AI Orchestration	LangChain
LLM	Groq
AI Model	openai/gpt-oss-20b
Web Search	Tavily
Web Scraping	Requests, BeautifulSoup
HTML Processing	lxml
Environment Management	python-dotenv
Data Handling	Pandas
Validation	Pydantic
Logging	Rich
Retry Handling	Tenacity
JSON Processing	orjson
Deployment	Streamlit Community Cloud
Version Control	Git, GitHub
🧠 LLM Configuration

ResearchMind currently uses:

openai/gpt-oss-20b

through the Groq API.

The model is used for:

Agent reasoning
Source selection
Research report generation
Report evaluation

The application uses:

temperature=0

for more deterministic responses.

📂 Project Structure
researchmind-ai-agent/
│
├── app.py
│   └── Streamlit web application
│
├── agents.py
│   ├── Groq LLM configuration
│   ├── Search Agent
│   ├── Reader Agent
│   ├── Writer Chain
│   └── Critic Chain
│
├── pipeline.py
│   └── End-to-end research pipeline
│
├── tools.py
│   ├── Tavily web search
│   └── URL scraping
│
├── requirements.txt
│   └── Python dependencies
│
├── README.md
│   └── Project documentation
│
└── .gitignore
    └── Environment and generated-file exclusions
⚙️ Application Workflow
User
  │
  ▼
Research Topic
  │
  ▼
Search Agent
  │
  ├── Tavily Search
  │
  ▼
Search Results
  │
  ▼
Reader Agent
  │
  ├── URL Selection
  ├── Web Scraping
  │
  ▼
Scraped Content
  │
  ▼
Writer Chain
  │
  ▼
Research Report
  │
  ▼
Critic Chain
  │
  ▼
Critic Feedback
  │
  ▼
Final Result
🖥️ Application Interface

The Streamlit application provides an interactive interface where users can enter a research topic and execute the complete research pipeline.

The application displays the major stages:

🔎 Search Agent
      ↓
📖 Reader Agent
      ↓
✍️ Writer Chain
      ↓
🧐 Critic Chain

After execution, users can view:

Search progress
Research report
Critic feedback
Sources
Downloadable report
📊 Research Report

The Writer Chain generates the following structure:

Introduction

Key Findings

1. Finding One
2. Finding Two
3. Finding Three

Conclusion

Sources

The generated report is available directly inside the Streamlit application.

📥 Report Download

The application provides an option to download the generated research report as a Markdown file.

This can be used for:

Research documentation
Project reports
Technical notes
Further analysis
Knowledge sharing
🔐 Environment Variables

The application requires two API keys:

GROQ_API_KEY
TAVILY_API_KEY

Create a .env file in the project root when running locally.

GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
Groq API

Create your API key from:

https://console.groq.com/

Tavily API

Create your API key from:

https://tavily.com/

🔒 Security

API keys should never be hard-coded into Python source files or committed to GitHub.

The local .env file should remain ignored by Git.

Recommended .gitignore entries:

__pycache__/
*.py[cod]

.venv/
venv/
env/

.env
.env.*

.streamlit/secrets.toml

.DS_Store
Thumbs.db

For the deployed application, API keys are stored using Streamlit Community Cloud Secrets rather than committing them to the repository. Streamlit recommends keeping secrets outside source control and configuring them through the application's secrets settings. (Streamlit Secrets Management)

▶️ Installation
Clone Repository
git clone https://github.com/hritwikrupesh/researchmind-ai-agent.git
Navigate to Project
cd researchmind-ai-agent
Create Virtual Environment
python -m venv .venv
Activate Virtual Environment
Windows
.\.venv\Scripts\Activate.ps1
Linux / macOS
source .venv/bin/activate
Install Dependencies
pip install -r requirements.txt
🚀 Run the Streamlit Application

After configuring the required API keys:

streamlit run app.py

The application will be available at:

http://localhost:8501
🧪 Run the Research Pipeline Directly

The project also includes a command-line pipeline.

Run:

python pipeline.py

Enter a topic when prompted:

Enter a research topic:

Example:

Latest developments in AI agents in 2026

The pipeline executes:

Search
  ↓
Reader
  ↓
Writer
  ↓
Critic
☁️ Deployment

ResearchMind is deployed using Streamlit Community Cloud.

Deployment Configuration
Property	Value
Platform	Streamlit Community Cloud
GitHub Repository	hritwikrupesh/researchmind-ai-agent
Branch	main
Main File	app.py
Python Version	3.12
Status	Deployed
Live Application	https://researchmind-ai-agent-by2hritwik.streamlit.app

Streamlit Community Cloud supports deploying an application directly from a GitHub repository by selecting the repository, branch, and application entrypoint. (Streamlit Deployment Documentation)

🔐 Streamlit Cloud Secrets

The deployed application uses:

GROQ_API_KEY = "your_groq_api_key"
TAVILY_API_KEY = "your_tavily_api_key"

These values are configured through:

Streamlit Community Cloud
        ↓
App Settings
        ↓
Secrets

The API keys are not stored in the GitHub repository. Streamlit recommends using its secrets management functionality for credentials and sensitive values. (Streamlit Secrets Management)

📦 Deployment Dependencies

The project's Python dependencies are defined in:

requirements.txt

The file is located in the repository root alongside app.py.

Streamlit Community Cloud uses dependency files such as requirements.txt to install the Python packages required by the application. (Streamlit App Dependencies)

🔄 Updating the Application

After making changes locally:

git add .
git commit -m "Update application"
git push origin main

Changes pushed to the connected GitHub repository can be reflected in the deployed Streamlit application. Changes to dependencies in requirements.txt can trigger dependency reinstallation. (Streamlit Deployment Documentation)

🧪 Example Research Topics

ResearchMind can be used with topics such as:

Latest developments in AI agents in 2026
Generative AI applications in healthcare
Recent developments in autonomous AI agents
Future of data engineering
Cloud computing trends
Applications of large language models
AI-powered cybersecurity
🌍 Use Cases
🎓 Academic Research

Research technical and academic topics and generate structured reports.

💻 Technology Research

Explore developments in:

Artificial Intelligence
Generative AI
Cloud Computing
Data Engineering
Software Engineering
Cybersecurity
Emerging Technologies
🧑‍💻 Developer Research

Research:

Frameworks
Libraries
APIs
Programming concepts
New technologies
📊 Industry Research

Gather publicly available information about industries and technologies.

📝 Report Preparation

Generate a structured starting point for technical research documentation.

⚠️ Limitations

This project is an AI-powered research assistant and should not be considered a complete autonomous fact-checking system.

Web Scraping

Some websites may:

Block automated requests
Require JavaScript
Require authentication
Restrict automated scraping
Return incomplete HTML
Search Results

The quality of the research depends partly on the results returned by the search service.

LLM Output

Generated content can contain:

Inaccuracies
Missing context
Incorrect interpretations
Unsupported claims

Important information should therefore be verified against the original sources.

Source Verification

The current system gathers and processes information but does not independently verify every claim in the final report.

Context Limitations

Only a limited amount of scraped webpage content is passed through the pipeline, so very large webpages may not be represented completely.

🚀 Future Improvements
🔎 Advanced source ranking
📚 Multiple-source research
🤖 Parallel research agents
🔍 Automated citation verification
✅ Fact-checking agent
🧠 Long-term research memory
📜 Research history
📄 PDF report generation
📝 DOCX report generation
🌐 HTML export
👤 Human-in-the-loop source approval
🧠 LangGraph-based orchestration
📊 Research analytics dashboard
🔐 User authentication
🗂️ Persistent research storage
🌐 Improved web extraction
🔬 Specialized domain research agents
📚 Learning Outcomes

This project demonstrates practical experience with:

Python
Streamlit
LangChain
Agentic AI
LLM integration
Groq API
Tavily Search
Tool Calling
Web Scraping
BeautifulSoup
Requests
Prompt Engineering
AI Report Generation
AI Report Evaluation
Sequential AI Workflows
Environment Variables
Git
GitHub
Cloud Deployment
Streamlit Community Cloud
💼 Project Highlights
🤖 Multi-Agent AI

The research workflow is divided among specialized AI components.

🔎 Tool-Based Research

The agents interact with external tools such as web search and webpage scraping.

🧠 LLM Orchestration

LangChain is used to coordinate the AI agents and chains.

✍️ Structured Generation

The Writer Chain generates reports using a predefined structure.

🧐 AI Evaluation

The Critic Chain provides a second evaluation pass over the generated report.

☁️ Cloud Deployment

The complete application is publicly accessible through Streamlit Community Cloud.

📊 Project Workflow Summary
                USER
                  │
                  ▼
          Research Topic
                  │
                  ▼
          ┌───────────────┐
          │ Search Agent  │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │ Reader Agent  │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │ Writer Chain  │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │ Critic Chain  │
          └───────┬───────┘
                  │
                  ▼
          Research Report
          + Critic Feedback
🔗 Project Links
🌐 Live Application

https://researchmind-ai-agent-by2hritwik.streamlit.app

💻 GitHub Repository

https://github.com/hritwikrupesh/researchmind-ai-agent

🦜 LangChain

https://www.langchain.com/

⚡ Groq

https://groq.com/

🔎 Tavily

https://tavily.com/

🎈 Streamlit

https://streamlit.io/

👨‍💻 Author

Hritwik Rupesh Gollu

Computer Science Engineering Student

Interested in:

Agentic AI
Generative AI
Artificial Intelligence
Data Engineering
Cloud Computing
Software Development
⭐ Support

If you found this project useful or interesting:

⭐ Give the repository a star
🍴 Fork the project
🐛 Report issues
💡 Suggest improvements
🔧 Contribute to the project
📄 License

This project is intended for educational, experimentation, and portfolio purposes.

If you reuse or extend this project, please provide appropriate attribution to the original repository.
