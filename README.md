# Multi-Agent Coding + Testing System (LangGraph-style demo)

This project demonstrates a **dynamic multi-agent system** that writes, tests, and fixes code using LLM-driven agents.

Agents:
- Planner: creates a step-by-step plan
- Coder: generates code for files
- Tester: runs pytest in a sandbox workspace
- Fixer: proposes fixes for failing tests
- Coordinator: orchestrates the dynamic flow (LangGraph-like)

## How it works (demo)
- Coordinator asks Planner to create a JSON plan.
- Coordinator executes "write_file" steps using FileManager.
- When encountering "run_tests", it calls Tester which runs pytest.
- If tests fail, Coordinator asks Fixer to propose a revision and re-runs tests.

## Safety & Notes
- The included LLM client is a **DummyLLM** for offline demos. Replace `src/llm_client.py` with your Gemini / GPT-5 wrapper when demonstrating online.
- The Python execution uses `subprocess.run()` — this is **NOT** a secure production sandbox. For interviews say you'd use containers (Firecracker/gVisor), CPU/memory limits, seccomp, cgroups, and network isolation.

## How to run
1. Create virtualenv and install dependencies:
