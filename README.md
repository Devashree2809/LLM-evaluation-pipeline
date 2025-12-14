LLM Evaluation Pipeline
1. Local Setup
Python 3.9+
Install dependencies:
pip install -r requirements.txt
Set API key in .env

Run:
python evaluate.py --conversation conversation.json --context context.json

2. Architecture

Flow:
User Query → LLM Response → Vector DB Context → Evaluation Pipeline
Modules:

Relevance & Completeness (embedding similarity)
Hallucination Detection (claims vs retrieved context)
Latency Tracking
Cost Estimation
Outputs a single evaluation JSON with scores.

3. Design Decisions
Modular design for easy scaling and maintenance
Context-grounded evaluation to reduce evaluator hallucinations
Minimal LLM calls to keep cost and latency low
Hybrid of deterministic metrics + lightweight LLM reasoning

4. Scale, Latency & Cost
Async and parallel execution
Embedding caching and batching
Small evaluation models
Stateless workers (K8s / serverless)
Skip deep evaluation for low-risk responses
