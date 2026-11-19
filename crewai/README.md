# AI Software Company — Multi-Agent System

A multi-agent AI software company built using CrewAI and OpenRouter.

The system simulates a software development team where four AI agents collaborate sequentially to transform a user's project idea into a complete software plan, architecture, development plan, and QA review.

## Project Overview

The system contains four specialized AI agents:

```text
                    User
                     |
                     v
              Project Manager
                     |
                     v
             Software Architect
                     |
                     v
            Full-Stack Developer
                     |
                     v
                QA Engineer
                     |
                     v
              Final Project Report
```

Each agent receives the output of the previous agent and uses it as context for its own task.

## AI Agents

### 1. Project Manager

Responsible for:

- Understanding the client's project idea
- Defining project goals and scope
- Identifying features and modules
- Defining functional requirements
- Defining non-functional requirements
- Creating the high-level project workflow
- Defining deliverables

### 2. Software Architect

Responsible for:

- Designing the system architecture
- Selecting the technology stack
- Choosing frontend and backend technologies
- Selecting the database
- Designing authentication
- Planning deployment
- Creating the project folder structure
- Explaining technology choices

### 3. Full-Stack Developer

Responsible for:

- Designing the database schema
- Defining REST API endpoints
- Planning business logic
- Planning authentication implementation
- Planning frontend pages
- Defining components
- Designing routing
- Planning UI/UX
- Creating development steps

### 4. QA Engineer

Responsible for reviewing the complete solution.

The QA agent analyzes:

- Project plan
- Architecture
- Development plan
- Security
- Performance
- Testing strategy
- Deployment
- Potential weaknesses

It then provides actionable feedback.

## Agent Workflow

The agents work using a sequential process.

```text
User Project Idea
       |
       v
+---------------------+
|  Project Manager    |
|  Project Planning   |
+----------+----------+
           |
           v
+---------------------+
| Software Architect  |
| Architecture Design |
+----------+----------+
           |
           v
+---------------------+
| Full-Stack Developer|
| Development Plan    |
+----------+----------+
           |
           v
+---------------------+
|    QA Engineer      |
|   Quality Review    |
+----------+----------+
           |
           v
      Final Output
```

### Context Flow

The system passes information between tasks:

```text
Planning Task
     |
     v
Architecture Task
     |
     v
Development Task
     |
     v
QA Task
```

The architecture task receives the Project Manager's output.

The development task receives the Architecture output.

The QA task receives all previous outputs.

## Technologies Used

- Python
- CrewAI
- OpenRouter
- LLM / OpenAI-compatible API
- python-dotenv

### Python Packages

```text
crewai==1.15.1
crewai-tools
langchain
langchain-core
langchain-community
python-dotenv
openai
```

## Project Structure

Recommended structure:

```text
ai-software-company/
|
├── main.py
├── .env
├── .gitignore
├── requirements.txt
└── README.md
```

## Installation

### 1. Create the project

```bash
mkdir ai-software-company
cd ai-software-company
```

### 2. Create a virtual environment

Windows:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## OpenRouter API Key

Create an OpenRouter API key and add it to your `.env` file.

```env
OPENROUTER_API_KEY=your_api_key_here
```

Never commit your `.env` file to GitHub.

## .gitignore

Create a `.gitignore` file:

```gitignore
venv/
.env
__pycache__/
*.pyc
```

## LLM Configuration

The project uses OpenRouter's OpenAI-compatible API.

```python
llm = LLM(
    model="openrouter/openrouter/free",
    api_key=OPENROUTER_API_KEY,
    base_url="https://openrouter.ai/api/v1",
    temperature=0.3
)
```

The `openrouter/free` model route allows OpenRouter to select an available free model.

## Running the Project

Run:

```bash
python main.py
```

You will see:

```text
OpenRouter Free Model Connected Successfully!

All 4 AI Agents Created Successfully!

Enter Project Idea:
```

Enter a project idea, for example:

```text
Build an online food delivery application
```

The agents will then execute sequentially.

## Example Input

```text
Build a student management system where
students can register, view courses, check
attendance and see their examination results.
```

The system processes the idea through:

```text
Project Manager
       |
       v
Project Plan
       |
       v
Software Architect
       |
       v
Architecture
       |
       v
Full-Stack Developer
       |
       v
Development Plan
       |
       v
QA Engineer
       |
       v
QA Review
```

## Example Output

The final output contains information such as:

```text
================================================
           AI SOFTWARE COMPANY (4 AGENTS)
================================================

PROJECT PLAN

ARCHITECTURE

TECHNOLOGY STACK

DATABASE DESIGN

REST API DESIGN

FRONTEND STRUCTURE

DEVELOPMENT PLAN

QA REVIEW

SECURITY RECOMMENDATIONS

TESTING STRATEGY

DEPLOYMENT SUGGESTIONS

================================================
PROJECT COMPLETED SUCCESSFULLY
================================================
```

## Key Concepts Demonstrated

### Multi-Agent System

Multiple specialized AI agents collaborate on one problem.

### Role-Based Agents

Each agent has a specific:

- Role
- Goal
- Backstory
- Task

### Sequential Processing

Agents execute one after another.

```text
Agent 1 -> Agent 2 -> Agent 3 -> Agent 4
```

### Context Sharing

The output of one task becomes context for another task.

```python
context=[planning_task]
```

### Task Specialization

Instead of asking one AI to perform everything, the workload is divided among specialized agents.

### LLM Integration

CrewAI is connected to an external LLM through OpenRouter.

## Future Improvements

Possible future improvements include:

- Add a Product Manager agent
- Add a Database Engineer
- Add a DevOps Engineer
- Add a Security Engineer
- Add a UI/UX Designer
- Generate actual source code
- Create project files automatically
- Add GitHub integration
- Add web search tools
- Add RAG
- Add persistent memory
- Add human approval steps
- Add automated testing
- Generate deployment configurations
- Build a web interface using Streamlit or React

A future architecture could look like:

```text
                 User
                   |
                   v
            Project Manager
                   |
          +--------+--------+
          |                 |
          v                 v
    UI/UX Designer    Software Architect
          |                 |
          +--------+--------+
                   |
                   v
          Full-Stack Developer
                   |
          +--------+--------+
          |                 |
          v                 v
      QA Engineer     DevOps Engineer
          |                 |
          +--------+--------+
                   |
                   v
              Final System
```

## Limitations

This project currently generates planning and design documentation. It does not automatically build, test, or deploy a real application.

The Full-Stack Developer agent creates a development plan rather than actually writing and executing the entire application.

## Author

Built as a learning project to explore:

```text
Agentic AI
    +
Multi-Agent Systems
    +
CrewAI
    +
LLMs
    +
OpenRouter
```

## Learning Goal

The main goal of this project is to understand how multiple AI agents can collaborate, share context, and perform specialized tasks to solve a larger problem.