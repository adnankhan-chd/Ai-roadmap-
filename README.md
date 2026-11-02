PATHFINDER // AI Technical Curriculum & Roadmap Architect
An interactive, DAG-based learning roadmap generator built with Python, Streamlit, and Google Gemini 3.8 Flash (gemini-3.8-flash via the official google-genai SDK).
Unlike generic AI wrappers that dump unformatted walls of bullet points, Pathfinder models any discipline as a Directed Acyclic Graph (DAG) of engineering milestones, complete with prerequisite gating, time-budget telemetry, mental models, anti-pattern warnings, proof-of-work capstone rubrics, and one-click exports.
Key Architectural Features
Zero Frontend Credential Exposure: Your GEMINI_API_KEY is loaded strictly on the backend via environment variables, .env, or .streamlit/secrets.toml—never rendered, echoed, or exposed in the frontend UI.
Gemini 3.8 Flash Structured Outputs (google-genai): Enforces a strict Pydantic schema (RoadmapResponseSchema) with response_mime_type="application/json" so every generated curriculum is deterministically parsed and validated.
Bespoke "Obsidian & Amber" Blueprint UI: Custom dark theme engineered with Space Grotesk, JetBrains Mono, and Inter typography, radial blueprint grid surfaces, and high-contrast status badges.
Interactive SVG Dependency Graph (DAG): Automatically computes topological layers and renders an inline vector graph illustrating Mastered (Emerald), Unlocked/Ready (Amber), and Prerequisite-Locked (Slate) phases.
Proof-of-Work Capstones & Mental Models: Every module includes concrete acceptance criteria, a verification benchmark test, core mental models, and common beginner pitfalls.
Instant Blueprint Inspection: Ships with a built-in Distributed Systems & Consensus Engineering blueprint so you can explore the DAG, progress tracker, and exporters immediately.
Multi-Format Exporters: Export any roadmap to Markdown (.md), Graphviz (.dot), or JSON Schema (.json).
Project Structure
File
Responsibility
app.py
Complete application containing Pydantic domain schemas, GeminiRoadmapService, backend secret resolver (resolve_gemini_api_key), DAG topological layout engine, SVG renderer, exporters, and Streamlit UI
requirements.txt
Minimal, production-pinned dependencies (streamlit, google-genai, pydantic, python-dotenv)
readme.md
Setup, backend secret configuration, architecture, and verification documentation
Quickstart
1. Create a Virtual Environment & Install Dependencies
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
2. Configure Your Gemini API Key (Backend Only)
Obtain an API key from Google AI Studio. To keep your key completely hidden from users on the frontend, configure it on the backend using any one of these three standard methods:
Option A — .env file (Recommended for local development): Create a .env file in the project root (and add .env to .gitignore):
GEMINI_API_KEY="your-google-ai-studio-api-key"
Option B — Streamlit Secrets (.streamlit/secrets.toml for Streamlit Cloud):
GEMINI_API_KEY = "your-google-ai-studio-api-key"
Option C — Shell Environment Variable:
export GEMINI_API_KEY="your-google-ai-studio-api-key"
3. Launch the Application
streamlit run app.py
