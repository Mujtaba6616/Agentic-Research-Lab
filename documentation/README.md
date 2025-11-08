# Research Agent – Agentic AI for Accelerated Research

A multi-agent AI system that analyzes research papers through specialized agents working together to extract insights, critique findings, synthesize hypotheses, identify gaps, and generate comprehensive research reports.

## 🎯 Overview

This system implements a collaborative multi-agent workflow where specialized AI agents work together to analyze research content, generating insights and explaining their reasoning in a clear, verifiable way. Each agent has a distinct role and contributes to a comprehensive research analysis.

## 🔄 Workflow

```
START
  ↓
[RESEARCHER] - Analyzes papers, extracts key findings
  ↓
[REVIEWER] - Critiques findings, identifies strengths/weaknesses
  ↓
[SYNTHESIZER] - Generates hypotheses and synthesizes insights
  ↓
[QUESTIONER] - Identifies gaps and generates research questions
  ↓
[FORMATTER] - Compiles comprehensive report
  ↓
END
```

## 🤖 Agents

### 1. RESEARCHER Agent
- **Role**: Analyzes research papers and extracts key findings
- **Responsibilities**:
  - Extracts key findings, methodologies, and conclusions
  - Identifies main contributions of each paper
  - Notes limitations or gaps mentioned in papers
  - Cites specific sources for every finding

### 2. REVIEWER Agent
- **Role**: Critiques findings and identifies strengths/weaknesses
- **Responsibilities**:
  - Evaluates research findings
  - Identifies methodological strengths and weaknesses
  - Looks for potential biases or limitations
  - Checks for consistency and logical coherence

### 3. SYNTHESIZER Agent
- **Role**: Synthesizes insights and generates testable hypotheses
- **Responsibilities**:
  - Combines findings and critiques
  - Generates testable, specific hypotheses
  - Connects findings from different sources
  - Identifies patterns and relationships
  - Proposes actionable research directions

### 4. QUESTIONER Agent
- **Role**: Identifies research gaps and generates follow-up questions
- **Responsibilities**:
  - Identifies knowledge gaps
  - Generates specific, answerable research questions
  - Focuses on gaps evident from the research
  - Prioritizes questions that would advance the field

### 5. FORMATTER Agent
- **Role**: Compiles comprehensive research report
- **Responsibilities**:
  - Organizes information clearly and logically
  - Includes all key findings, critiques, hypotheses, and questions
  - Maintains accuracy with proper citations
  - Creates professional, readable format

## 🚀 Quick Start

### Prerequisites

1. Python 3.8+
2. Google API Key (for Gemini models)
3. Documents in `uploaded_documents/` folder

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd "new hackathon"
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Create a `.env` file with your Google API key:
```
GOOGLE_API_KEY=your_api_key_here
```

4. Process your documents (if not already done):
```bash
python src/document_processor.py
```

### Usage

#### Option 1: Command Line

Run the multi-agent system with a research query:

```bash
python src/multi_agent_system.py --query "What are the latest advances in transformer architectures?"
```

Options:
- `--query`: Research query or topic (required)
- `--vector-db`: Path to vector database (default: "vector_db")
- `--collection`: ChromaDB collection name (default: "research_documents")
- `--model`: LLM model name (default: "gemini-2.5-flash")
- `--temperature`: LLM temperature (default: 0.3)
- `--output`: Output file path for report (default: "research_report.txt")
- `--no-save`: Don't save report to file

#### Option 2: Python Script

```python
from src.multi_agent_system import MultiAgentResearchSystem

# Initialize system
system = MultiAgentResearchSystem(
    vector_db_path="vector_db",
    collection_name="research_documents"
)

# Run research workflow
workflow_data = system.run_research_workflow(
    query="What are the latest advances in transformer architectures?",
    verbose=True
)

# Save report
if workflow_data.get("status") == "success":
    system.save_report(workflow_data, "research_report.txt")
    print(workflow_data.get("report"))
```

#### Option 3: Using the Example Script

```bash
python example_multi_agent.py
```

## 📁 Project Structure

```
.
├── src/
│   ├── __init__.py
│   ├── document_loader.py      # Document loading and chunking
│   ├── document_processor.py   # Document processing orchestration
│   ├── vector_store.py         # Vector database management
│   ├── rag_pipeline.py         # RAG pipeline for document retrieval
│   ├── agents.py               # Individual agent implementations
│   └── multi_agent_system.py   # Multi-agent orchestrator
├── uploaded_documents/         # Research papers (PDFs, etc.)
├── vector_db/                  # Vector database storage
├── requirements.txt            # Python dependencies
├── example_multi_agent.py      # Example usage script
└── README.md                   # This file
```

## 🔍 Key Features

### 1. Multi-Agent Collaboration
- Specialized agents with distinct roles
- Sequential workflow with data passing between agents
- Each agent uses RAG for document retrieval

### 2. Accuracy and Verification
- Agents are instructed to only use information from provided context
- Source citations for all findings
- Lower temperature settings for factual accuracy
- No hallucination - agents reference actual documents

### 3. Comprehensive Analysis
- Key findings extraction
- Critical analysis and critique
- Hypothesis generation
- Gap identification
- Research question generation

### 4. Professional Reports
- Well-structured research reports
- Executive summaries
- Proper citations and source references
- All agent outputs included

## 🛠️ Technical Details

### Technology Stack
- **LLM**: Google Gemini 2.5 Flash
- **Embeddings**: Google Generative AI Embeddings
- **Vector Database**: ChromaDB
- **Framework**: LangChain
- **Language**: Python 3.8+

### Agent Configuration
- **RESEARCHER**: Temperature 0.2 (high accuracy)
- **REVIEWER**: Temperature 0.3 (balanced)
- **SYNTHESIZER**: Temperature 0.4 (creative synthesis)
- **QUESTIONER**: Temperature 0.4 (creative questioning)
- **FORMATTER**: Temperature 0.3 (clear formatting)

### RAG Integration
- All agents use the RAG pipeline for document retrieval
- Retrieval augmented generation ensures accuracy
- Source tracking and citation throughout

## 📊 Output Format

The system generates a comprehensive research report including:

1. **Executive Summary**
2. **Key Findings** (from RESEARCHER)
3. **Critical Analysis** (from REVIEWER)
4. **Synthesized Insights** (from SYNTHESIZER)
5. **Hypotheses** (from SYNTHESIZER)
6. **Research Gaps and Questions** (from QUESTIONER)
7. **Conclusions**
8. **Sources** (with citations)

## 🎯 Use Cases

- Research paper analysis
- Literature reviews
- Hypothesis generation
- Research gap identification
- Academic research assistance
- Knowledge synthesis

## 🔒 Accuracy Guarantees

- **No Hallucination**: Agents are explicitly instructed to only use information from provided documents
- **Source Citation**: All findings include source references
- **Verification**: Each agent's output is based on retrieved document context
- **Temperature Control**: Lower temperatures for factual accuracy

## 📝 Notes

- Ensure documents are processed before running the multi-agent system
- The system works best with 5-20 research papers
- Processing time depends on document size and number of papers
- All agents share the same RAG pipeline for consistency

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

[Add your license here]

## 🙏 Acknowledgments

- Built for VC Big Bets Hackathon
- Uses Google Gemini for LLM capabilities
- LangChain for agent framework
- ChromaDB for vector storage
