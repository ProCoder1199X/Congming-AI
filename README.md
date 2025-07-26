# Congming AI

Congming AI is an experimental, modular, symbolic multi-agent artificial intelligence framework. It is designed to simulate advanced cognitive processes, self-reflection, and self-improvement using a collection of specialized agents that communicate via a central blackboard architecture.

---

## Project Status

**Ongoing Experiment:**  
- The project is under active development and experimentation.
- The current focus is on integrating LLM (Large Language Model) processing for code rewriting, web queries, and reflective reasoning.
- Some agents are placeholders or partially implemented, and new features/agents are planned.
- I wrote a research paper regarding this. Please check if needed. https://www.academia.edu/143084231/Design_of_a_Multi_Agent_AI_Architecture_with_Centralized_Feedback_control_and_Modular_Intelligence_Coordination 
- (for some reason, the paper is only opening for people who have registered account on academia. I will try to fix it soon.)
---

## Architecture Overview

### 1. **Blackboard System**
- Central message-passing hub ([`blackboard.py`](blackboard.py)).
- Agents broadcast and fetch messages addressed to them or to `'broadcast'`.
- Supports message expiration and topic filtering.

### 2. **Master Agent**
- Orchestrates the perception/action cycles of all agents ([`Master.py`](Master.py)).
- Handles error reporting and triggers periodic self-reflection.

### 3. **Agents**
Each agent has a focused cognitive or meta-cognitive role. Key agents include:

| Agent Name                  | File                              | Purpose/Role                                                                                  |
|-----------------------------|-----------------------------------|----------------------------------------------------------------------------------------------|
| ConsistencyAgent            | [`ConsistencyAgent.py`](ConsistencyAgent.py)         | Tracks known facts, manages debate points, ensures logical consistency.                      |
| EmotionalAgent              | [`EmotionalAgent.py`](EmotionalAgent.py)             | Assigns and broadcasts emotional context to goals.                                           |
| LogicAgent                  | [`LogicAgent.py`](LogicAgent.py)                     | Performs symbolic logic checks and broadcasts logical arguments.                             |
| PlannerAgent                | [`PlannerAgent.py`](PlannerAgent.py)                 | Converts tasks into plans and coordinates execution.                                         |
| SelfModelAgent              | [`SelfModelAgent.py`](SelfModelAgent.py)             | Logs behaviors, performs self-reflection, proposes improvements.                             |
| UnderstandingAgent          | [`UnderstandingAgent.py`](UnderstandingAgent.py)     | Interprets tasks and forwards them for planning.                                             |
| MemoryAgent                 | [`MemoryAgent.py`](MemoryAgent.py)                   | Stores episodic memory, reminds agents of past context.                                      |
| GoalManagerAgent            | [`GoalManagerAgent.py`](GoalManagerAgent.py)         | Manages and prioritizes goals.                                                               |
| DebateAgent                 | [`DebateAgent.py`](DebateAgent.py)                   | Collects arguments, initiates debates, queries LLMs for reflection.                         |
| ArgumentEvaluatorAgent      | [`ArgumentEvaluatorAgent.py`](ArgumentEvaluatorAgent.py) | Scores debate arguments and determines winners.                                              |
| ValueSystemAgent            | [`ValueSystemAgent.py`](ValueSystemAgent.py)         | Evaluates actions against core values (growth, coherence, etc.).                             |
| ThoughtAgent                | [`ThoughtAgent.py`](ThoughtAgent.py)                 | Synthesizes logic and emotion into abstract thoughts.                                        |
| InnerVoiceAgent             | [`InnerVoiceAgent.py`](InnerVoiceAgent.py)           | Narrates internal monologue based on thoughts.                                               |
| CuriosityAgent              | [`CuriosityAgent.py`](CuriosityAgent.py)             | Triggers exploration and web queries on interesting topics.                                  |
| CodeRewriterAgent           | [`CodeRewriterAgent.py`](CodeRewriterAgent.py)       | Uses LLM to suggest and apply code improvements.                                             |
| AgentArchitectAgent         | [`AgentArchitectAgent.py`](AgentArchitectAgent.py)   | Proposes new agents or system upgrades based on missing capabilities.                        |
| IntegrityMonitorAgent       | [`IntegrityMonitorAgent.py`](IntegrityMonitorAgent.py) | Monitors errors and system integrity, triggers recovery proposals.                           |
| SelfAwarenessAgent          | [`SelfAwarenessAgent.py`](SelfAwarenessAgent.py)     | Reflects on goals, emotions, knowledge, and conflicts.                                       |
| InternalMonologueAgent      | [`InternalMonologueAgent.py`](InternalMonologueAgent.py) | Generates and logs internal monologue.                                                       |
| InstinctEngineAgent         | [`InstinctEngineAgent.py`](InstinctEngineAgent.py)   | Triggers survival instincts and emergency protocols.                                         |
| DreamSimulationAgent        | [`DreamSimulationAgent.py`](DreamSimulationAgent.py) | Simulates possible futures and outcomes for goals.                                           |
| ConsciousLoopAgent          | [`ConsciousLoopAgent.py`](ConsciousLoopAgent.py)     | Periodically reflects on identity and proposes new goals.                                    |
| ConsciousDialogueAgent      | [`ConsciousDialogueAgent.py`](ConsciousDialogueAgent.py) | Placeholder for dialogue generation based on internal state.                                 |
| MutationAgent               | [`MutationAgent.py`](MutationAgent.py)               | Placeholder for self-modification and mutation logic.                                        |
| WebScraperAgent             | [`WebScraperAgent.py`](WebScraperAgent.py)           | Fetches web summaries for topics of interest.                                                |
| GoogleAIAgent               | [`GoogleAIAgent.py`](GoogleAIAgent.py)               | Interfaces with Google's Gemini LLM for queries and code rewriting.                          |

---

## How It Works

1. **Initialization:**  
   The `MasterAgent` instantiates all agents and starts the main loop.

2. **Perception Phase:**  
   Each agent fetches relevant messages from the blackboard and processes them.

3. **Action Phase:**  
   Each agent performs its action, which may include broadcasting new messages, updating internal state, or triggering other agents.

4. **Reflection:**  
   Every few cycles, the `SelfModelAgent` and other reflective agents analyze system behavior and propose improvements.

5. **LLM Integration:**  
   - The `GoogleAIAgent` handles LLM queries for reasoning, code rewriting, and web reflection.
   - The `CodeRewriterAgent` uses LLM feedback to suggest and apply code changes.

6. **Web Integration:**  
   - The `WebScraperAgent` fetches summaries from Wikipedia for topics suggested by curiosity or other agents.

---

## Running the Project

1. **Install Dependencies:**
   - Python 3.8+
   - `requests`, `beautifulsoup4`

   ```sh
   pip install requests beautifulsoup4
   ```

2. **Set up LLM API Key:**
   - Set the `GOOGLE_LLM_API_KEY` environment variable for LLM integration.

3. **Run the Main Script:**
   ```sh
   python Master.py
   ```

---

## Experiment Goals

- **Symbolic Reasoning:** Test how modular symbolic agents can reason, debate, and self-improve.
- **Meta-cognition:** Explore self-reflection, self-awareness, and self-modification in AI.
- **LLM Synergy:** Integrate LLMs for code rewriting, debate, and web learning.
- **Emergent Behavior:** Observe how agent interactions lead to complex, emergent cognitive patterns.

---

## Roadmap / TODO

- Complete unfinished agents (e.g., `ConsciousDialogueAgent`, `MutationAgent`).
- Improve message routing and topic filtering.
- Enhance error handling and robustness.
- Expand LLM and web integration.
- Add more tests and logging for observability.
- Experiment with new agent types and self-modification.

---

## License

This project is for research and educational purposes.  
See `LICENSE` for details

---

## Acknowledgements

- Inspired by blackboard architectures, cognitive architectures, and multi-agent systems.
- Uses [Google Gemini](https://ai.google.dev/) for LLM integration.

---

## Contact

For questions or collaboration, open an issue or contact the project maintainer.
