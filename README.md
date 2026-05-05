LitRev: Autonomous Agentic Literature Reviewer
Core Purpose
An autonomous multi-agent system designed to streamline academic research. It leverages a two-agent workflow to dynamically query the arXiv database, retrieve relevant academic papers, and synthesize them into structured Markdown literature reviews in real-time.

Tech Stack
Framework: Microsoft AutoGen

LLM Engine: Groq API (Llama-3.3-70b-versatile)

Frontend: Streamlit

APIs & Libraries: arXiv API, Asyncio, Pydantic, OpenAI SDK (Groq compatibility)

System Architecture
The system utilizes a RoundRobinGroupChat orchestration model with two specialized agents:

Search Agent (Tool-Enabled): Equipped with a custom arxiv_search Python function. It receives the user's topic, autonomously crafts an optimized arXiv query, executes the search, and extracts metadata (title, authors, summary, PDF link) into a strict JSON format.

Summarizer Agent: An analytical agent configured via a strict system prompt. It parses the raw data retrieved by the Search Agent and synthesizes a professional, literature-review-style report formatted in Markdown.

The backend operates asynchronously, streaming state changes and agent-to-agent dialogue directly to the Streamlit frontend.

Installation & Setup
Clone the repository and install dependencies:

Bash
git clone https://github.com/tanmay8506/litrev.git
cd litrev
pip install -r requirements.txt
Configure Environment Variables:
Create a .env file in the root directory and add your Groq API key:

Code snippet
GROQ_API_KEY=your_groq_api_key_here
Run the Application:

Bash
streamlit run app.py
Usage
Enter a specific research domain (e.g., "graph neural networks for chemistry") and define the number of papers to analyze. The UI will stream the thought process and interactions of the autonomous agents before outputting the final consolidated review.
