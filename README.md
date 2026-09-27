# 🔬 ResearchMind — Multi-Agent AI Research Assistant

> An AI-powered multi-agent research assistant that searches the web, extracts relevant information, generates a structured research report, and critically reviews the generated report.

ResearchMind automates a complete research workflow using specialized AI agents and LLM chains.

Instead of manually searching multiple websites, reading sources, preparing a report, and reviewing the final output, ResearchMind coordinates these tasks through a four-stage AI pipeline.

--
## ✨ Features

- 🔍 AI-powered web research
- 🤖 Specialized Search Agent
- 📄 Reader Agent for web content extraction
- 📝 Automated research report generation
- 🧐 AI-powered report criticism and feedback
- 🌐 Interactive Streamlit web interface
- ⚡ Groq LLM inference
- 🔎 Tavily web search
- 🕸️ BeautifulSoup-based web scraping
- 📥 Download generated reports as Markdown
- 🎨 Custom dark-themed research dashboard

---

## 🧠 How ResearchMind Works

ResearchMind follows a sequential multi-agent research workflow:

```text
                         ┌──────────────────────┐
                         │      User Topic      │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    Search Agent      │
                         │                      │
                         │  Web Search / URLs   │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    Reader Agent      │
                         │                      │
                         │ Scrape & Extract     │
                         │ Source Content       │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    Writer Chain      │
                         │                      │
                         │ Generate Research    │
                         │ Report               │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    Critic Chain      │
                         │                      │
                         │ Review & Evaluate    │
                         │ Generated Report     │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    Final Output      │
                         │                      │
                         │ Research Report +    │
                         │ Critic Feedback      │
                         └──────────────────────┘

🤖 Multi-Agent Architecture
1. Search Agent 🔍

The Search Agent is responsible for finding relevant information about the user's research topic.

It uses the Tavily search tool to retrieve:

Search result titles
URLs
Search snippets
Recent web information

The agent is created using LangChain's agent functionality and is given access to the web_search tool.

Workflow
Research Topic
      ↓
Search Agent
      ↓
Tavily Web Search
      ↓
Relevant Web Results
2. Reader Agent 📄

The Reader Agent takes the search results and identifies a relevant source for deeper analysis.

It uses the scrape_url tool to retrieve and clean webpage content.

The scraper:

Sends an HTTP request to the selected URL
Parses the webpage using BeautifulSoup
Removes unnecessary elements such as:
scripts
styles
navigation
footer sections
Extracts readable text
Limits the extracted content to a manageable size
Workflow
Search Results
      ↓
Reader Agent
      ↓
Relevant URL
      ↓
Web Scraping
      ↓
Clean Source Content
3. Writer Chain 📝

The Writer Chain receives:

The original research topic
Search results
Detailed scraped content

It then generates a structured research report.

The requested report structure is:

Introduction

Key Findings
    ├── Finding 1
    ├── Finding 2
    └── Finding 3+

Conclusion

Sources

The writer is instructed to produce a detailed, factual, and professional report.

4. Critic Chain 🧐

After the report is generated, the Critic Chain reviews it.

The critic produces feedback in the following structure:

Score: X/10

Strengths:
- ...
- ...

Areas to Improve:
- ...
- ...

One line verdict:
...

This creates a separate evaluation stage after report generation.

🔄 Complete Workflow

For a research topic such as:

Latest developments in AI agents in 2026

ResearchMind executes:

1. User enters research topic
             ↓
2. Search Agent searches the web
             ↓
3. Reader Agent selects and scrapes a relevant source
             ↓
4. Writer Chain combines the research
             ↓
5. Writer generates structured report
             ↓
6. Critic Chain reviews the report
             ↓
7. Streamlit displays the results
             ↓
8. User can download the report as Markdown
🛠️ Tech Stack
Technology	Purpose
Python	Core programming language
Streamlit	Interactive web application
LangChain	Agent and LLM orchestration
Groq	LLM inference
Tavily	Web search
BeautifulSoup	HTML parsing and content extraction
Requests	HTTP requests for webpage scraping
python-dotenv	Environment variable management
Rich	Terminal output and debugging
Pandas	Data handling support
Pydantic	Data validation and typing support
📁 Project Structure
researchmind-multi-agent/
│
├── app.py
│   └── Streamlit user interface
│
├── agents.py
│   └── Search Agent
│   └── Reader Agent
│   └── Writer Chain
│   └── Critic Chain
│
├── tools.py
│   └── Tavily web search tool
│   └── Web scraping tool
│
├── pipeline.py
│   └── Programmatic research pipeline
│
├── requirements.txt
│   └── Python dependencies
│
├── .gitignore
│   └── Ignored files and environment secrets
│
├── .env
│   └── Local API keys
│
└── README.md
    └── Project documentation

Note: .env is a local configuration file and should never be committed to GitHub.

📄 File Responsibilities
app.py

Contains the Streamlit application.

The interface provides:

Research topic input
Run Research Pipeline button
Pipeline status cards
Search results
Scraped content
Final research report
Critic feedback
Markdown report download

The application presents the four stages visually:

Search Agent
     ↓
Reader Agent
     ↓
Writer Chain
     ↓
Critic Chain
agents.py

Contains the AI components used by ResearchMind.

LLM

The project uses the Groq integration with:

openai/gpt-oss-20b
Components
                    ChatGroq
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
    Search Agent   Reader Agent   Chains
                                    │
                              ┌─────┴─────┐
                              ▼           ▼
                           Writer      Critic
                           Chain       Chain
tools.py

Contains the external tools used by the agents.

web_search

Uses Tavily to search the web.

The tool returns information including:

Title
URL
Snippet

for retrieved search results.

scrape_url

Uses:

Requests
+
BeautifulSoup

to retrieve and clean webpage content.

The scraper removes unnecessary HTML elements before returning readable text.

pipeline.py

Provides a programmatic version of the research workflow.

The pipeline performs:

Search
  ↓
Read
  ↓
Write
  ↓
Critique

and maintains the research state containing:

search_results
scraped_content
report
feedback

The pipeline can also be executed directly from the command line.

🎨 User Interface

ResearchMind provides a custom Streamlit interface with:

Dark research dashboard
Research topic input
Pipeline progress cards
Search results panel
Scraped content panel
Final research report
Critic feedback
Markdown report download

The interface visually represents the progress of each research stage.

⚙️ Installation
1. Clone the Repository
git clone https://github.com/YOUR_USERNAME/researchmind-multi-agent.git
cd researchmind-multi-agent

Replace:

YOUR_USERNAME

with your GitHub username.

2. Create a Virtual Environment
Windows
python -m venv .venv

Activate it:

.\.venv\Scripts\Activate.ps1
macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
3. Install Dependencies
pip install -r requirements.txt
🔐 Environment Variables

ResearchMind requires API credentials for external services.

Create a .env file in the project root:

GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
Important

Never commit your .env file to GitHub.

Your .gitignore should include:

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
▶️ Run the Application Locally

Start the Streamlit application:

streamlit run app.py

The application will normally be available at:

http://localhost:8501

Enter a research topic and click:

⚡ Run Research Pipeline
🧪 Example Usage

Enter:

Latest developments in AI agents in 2026

Then run the research pipeline.

ResearchMind will process the topic through:

Search Agent
      ↓
Reader Agent
      ↓
Writer Chain
      ↓
Critic Chain

The application then displays:

Raw Search Results
Scraped Content
Final Research Report
Critic Feedback

The generated research report can be downloaded as a Markdown file.

📊 Output
Final Research Report

The Writer Chain generates a report containing:

Introduction

Key Findings

Conclusion

Sources
Critic Feedback

The Critic Chain evaluates the generated report and returns:

Score

Strengths

Areas to Improve

One-line Verdict

This provides an additional review stage after report generation.

🌐 Deployment

ResearchMind can be deployed as a Streamlit web application.

For deployment, configure the following environment secrets:

GROQ_API_KEY
TAVILY_API_KEY

Do not upload the local .env file.

For Streamlit Community Cloud, these values should be added through the application's Secrets configuration.

🔒 Security

ResearchMind uses environment variables for API credentials.

The following should remain outside version control:

.env
.venv/
venv/
__pycache__/

Never expose API keys in:

Source code
GitHub commits
README files
Screenshots
Public documentation
⚠️ Current Limitations

ResearchMind is currently a working prototype and has several areas that can be improved.

Source Verification

The system retrieves information from web sources, but generated claims are not independently verified against multiple primary sources.

Citation Validation

The Writer Chain is instructed to include source URLs, but automated citation validation is not currently implemented.

Web Scraping Limitations

Some websites may block automated requests or return content that cannot be cleanly extracted.

Research Depth

The current Reader Agent focuses on selecting a relevant URL and extracting deeper content rather than performing comprehensive multi-source document analysis.

Error Handling

External services such as LLM APIs, search APIs, and websites can fail or return unexpected responses.

🔮 Future Enhancements

Potential future improvements include:

🔎 Multi-source research and cross-verification
📚 Improved source ranking
🔗 Automated citation validation
🧠 Better research planning
⚡ Parallel agent execution
📝 Improved report formatting
📄 PDF report generation
💾 Research history
👤 Human-in-the-loop source verification
🔐 Improved API and error handling
📊 Research quality metrics
🧪 Automated report evaluation
🌐 Improved deployment configuration
🧩 Architecture Summary
                         ResearchMind
                              │
                              ▼
                    ┌──────────────────┐
                    │   Streamlit UI   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   Search Agent   │
                    │     LangChain    │
                    └────────┬─────────┘
                             │
                       Tavily Search
                             │
                             ▼
                    ┌──────────────────┐
                    │   Reader Agent   │
                    │     LangChain    │
                    └────────┬─────────┘
                             │
                       Web Scraping
                             │
                             ▼
                    ┌──────────────────┐
                    │   Writer Chain   │
                    │     ChatGroq     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   Critic Chain   │
                    │     ChatGroq     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  Final Research  │
                    │      Report      │
                    │        +         │
                    │ Critic Feedback  │
                    └──────────────────┘
🚀 Why ResearchMind?

ResearchMind demonstrates how an LLM application can be structured as a multi-stage AI workflow where different components are responsible for different research tasks.

Instead of relying on a single prompt, the application separates the research process into:

Searching
   ↓
Reading
   ↓
Writing
   ↓
Critiquing

This separation makes the workflow easier to understand, develop, test, and extend.

📌 Project Status

Status: Working Prototype

The current implementation successfully executes the complete research workflow from topic input through:

Web Search
    ↓
Content Extraction
    ↓
Research Report Generation
    ↓
AI Critique
👨‍💻 Author

Hritwik Rupesh

Computer Science Engineering Student

⭐ Acknowledgements

Built with:

Python
LangChain
Groq
Tavily
Streamlit
BeautifulSoup
Requests#   r e s e a r c h m i n d - m u l t i - a g e n t  
 #   r e s e a r c h m i n d - m u l t i - a g e n t  
 #   r e s e a r c h m i n d - a i - a g e n t  
 