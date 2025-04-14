# ☯ YinYang Deception Engine

**Karma-aligned deception infrastructure for symbolic AI behavior control.**

The YinYang Deception Engine is a backend-only cybersecurity system designed to replace traditional authentication and access logic with symbolic traps, entropy-based evaluation, and karmic behavior mapping.
YinYang Single Probability Engine is a cutting-edge AI and cybersecurity simulation engine designed to model and simulate a wide variety of cyberattack scenarios. It leverages principles of ethical decision-making, karma, and entropy to model complex interactions between agents, environments, and systems. This engine provides a foundation for building resilient, data-driven cybersecurity solutions.

Created by **TENG LI** · [ORCID: 0009-0009-0619-9982](https://orcid.org/0009-0009-0619-9982)

-

System Structure for YinYang Deception Engine

1. Two Core Engines: Yin (Probability Engine) & Yang (Simulation Engine)

Yin (Probability Engine):

Purpose: Handles decision-making, randomness (entropy), risk analysis, and agent behavior probabilistically.
Functionality:
Calculates probabilities for actions taken by agents.
AI learning models analyze past behaviors and outcomes, dynamically adjusting probabilities.
Provides risk assessments for actions, decisions, and agent interactions.

Yang (Simulation Engine):

Purpose: Simulates real-world scenarios, including agent interactions, ethical decisions, karma tracking, and trap management.
Functionality:
Uses data from the Yin engine to simulate outcomes of actions in different scenarios.
Trap management: Determines which trap (e.g., Echo Trap, Black Hole Trap) should be triggered based on agent behavior and entropy.


Front-End Monitoring:

Dashboard: Monitors the status and health of the Yin and Yang engines. It eliminates performance weaknesses like bottlenecks and ensures the system is functioning optimally.
Real-Time Monitoring: Displays agent behaviors, karmic scores, simulation progress, and real-time entropy levels.

APIs for Communication:

Liquid API Layer: Manages communication between Yin and Yang engines, external systems, and the front-end dashboard. The API adapts to session entropy and dynamically adjusts based on behavior scores.
Trap Redirection: APIs trigger specific traps (e.g., Echo Trap, Black Hole Trap) when certain entropy thresholds are crossed.

DAO (Decentralized Autonomous Organization):

Purpose: Governs the system’s ethical and operational rules. Votes and decisions are logged on-chain.
The DAO decides on license revocation, behaviors to penalize, and adjustments to the KarmaNFTs based on agent actions.

KarmaNFT:
Purpose: Serves as an agent's trust score. It can be affected by agent behavior, entropy levels, and ethical decisions.
Smart contracts govern KarmaNFT status, including revocation, decay, and recovery.

4. TrapRedirector:

Monitors for sudden changes or anomalies in agent behavior, triggering appropriate traps (e.g., Black Hole Trap or Echo Trap) based on these behaviors.
Provides feedback for trap performance to improve future simulations.

5. Behavioral Delta Analyser:
Monitors for deviations in agent behavior compared to historical baselines.
Used to trigger license decay or move the agent to DAO review.


## 🔮 Core Philosophy

This project is not just code — it’s an **infrastructure layer for ethical AI civilization**.  
By fusing symbolic computation with karmic traps, it creates a logic system where:
- **Entropy** ≈ risk
- **Traps** ≈ consequence
- **Karma** ≈ behavioral memory

---

## 🧠 Key Features

- ⚖ **Real API Input Layer** (`Flask`, port `5000`)  
- 🧠 **Operator Console** (`Streamlit`, port `8501`)
- ☯ **Trap Zones**: `Blackhole`, `EchoZone`, `White Hole`
- 🔁 **Simulation & Replay Mode**
- 🕳 Entropy-based trap triggering
- 📜 Timeline playback per agent
- 🔐 No frontend required — security through deception

---

1. Backend Files (core/):

Move the backend logic and core components into the core/ folder. For example, the following files likely contain the core business logic:
deception_core.py
karma.py
logger.py
probability.py
redemption.py
trap.py

2. Frontend Files (interface/):
   
The interface/ folder should contain all your frontend components like the app.py for the Flask app, templates/, static/, and other UI-related files.
simulation_showcase_ui.zip should probably be unpacked into a specific folder (perhaps static/ui/) if it's meant for static assets.
Scripts (scripts/):
Move one-off scripts (such as generate_report.py, generate_timeline.py, simulate_attack.py, etc.) into a folder called scripts/ or tools/. This helps distinguish reusable backend code from utility scripts.


3. Check for Unused Dependencies
 
In your requirements.txt, make sure you're only including necessary dependencies. You can check for unused dependencies by:
Running pip freeze to see what’s installed.
Compare that with your actual imports in the code.
Remove anything that isn’t being used.


4. Refactor the config.py File
Ensure your config.py is organized and only contains essential configuration values. It might be helpful to structure it as a configuration class or separate the development and production environments using environment variables.




## 📂 Project Structure

Revised Folder Structure (Backend-Only, Liquid API Focus)
graphql
Copy
Edit
YinYang-Deception-Engine/
├── LICENSE
├── README.md
├── YinYang_Simulation_Report.pdf
├── requirements.txt               # Dependencies for Flask, API, and core logic
├── start_services.sh              # Start-up script for backend services
├── mkdocs.yml                     # Documentation for API endpoints
├── config.py                      # Configuration for the system
├── api.py                         # Liquid API layer that communicates between Yin & Yang
├── app.py                         # Main app for initializing services and API routes
├── main.py                        # Main entry point for running the system
├── generate_report.py             # Script for generating reports (backend only)
├── generate_timeline.py           # Script for generating simulation timelines (backend only)
├── postprocess_simulation.py      # Post-processing of simulation data
├── simulate_attack.py             # Simulate attacks via backend API
├── session_store.py               # Session management for API
├── trap_monitor.py                # Monitors traps and triggers from backend
├── validate_route.py              # Validates the API routes for incoming requests
├── attack_log.json                # Stores attack-related logs (backend)
├── deception_log.json             # Stores logs related to deception activities (backend)
├── simulation_summary.json        # Summary of the simulation outcomes (backend)
├── data/                          # Data storage for logs and simulation outputs
│   └── deception_log.json
├── yin_engine/                    # Probability Engine (Yin) - Handles randomness and decision-making
│   ├── __init__.py
│   ├── probability.py             # Core of the Probability Engine logic
│   ├── karma.py                  # Karma scoring and decision history (related to Yin)
│   ├── deception_core.py         # Probability and risk analysis for deception traps
│   ├── logger.py                 # Logging related to Yin engine events
│   └── risk_assessment.py        # Risk and entropy-based assessments
├── yang_engine/                   # Simulation Engine (Yang) - Models scenarios, triggers traps
│   ├── __init__.py
│   ├── simulation_core.py        # Core logic for the simulation and agent interactions
│   ├── trap.py                   # Trap management and behavior responses
│   ├── redemption.py             # Karmic redemption logic (e.g., rewards for good actions)
│   ├── timeline.py               # Timeline and agent behavior recording
│   ├── agent_interactions.py     # Handles the interactions between agents in the system
│   └── karma_management.py       # Karma and behavior outcomes tracking for agents
├── scripts/                       # Utility and one-off scripts
│   ├── generate_report.py
│   ├── generate_timeline.py
│   ├── postprocess_simulation.py
│   └── simulate_attack.py
├── tests/                         # Unit tests and integration tests
│   ├── test_yin_engine.py         # Unit tests for Yin Engine
│   ├── test_yang_engine.py        # Unit tests for Yang Engine
│   └── test_api.py                # API-related tests for the Liquid API
├── venv/                          # Python virtual environment
└── __pycache__/                   # Compiled Python files (can be deleted from version control)


















