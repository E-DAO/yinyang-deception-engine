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



# YinYang Deception Engine

This backend handles risk assessment, karma scoring, trap management, and logs events related to user activities within a deception engine.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/YinYang-Deception-Engine.git
   cd YinYang-Deception-Engine
Install dependencies:

bash
Copy
Edit
pip install -r requirements.txt
Run the FastAPI server:

bash
Copy
Edit
uvicorn main:app --reload
The API will be available at http://127.0.0.1:8000.

API Endpoints
POST /api/risk: Assess risk based on a user's actions.

GET /karma/{user_id}: Get the karma score of a user.

POST /redeem: Process user redemption.

GET /log: Retrieve the event logs.

GET /status: Get server status.

License
MIT License. See LICENSE for details.

makefile
Copy
Edit

#### **2. `requirements.txt`**

This file lists all the dependencies required to run the FastAPI app.

```txt
fastapi==0.68.0
uvicorn==0.15.0
jinja2==3.0.3
sqlalchemy==1.4.22
databases==0.5.4
pydantic==1.8.2
3. config.py
This file stores your configuration, such as the mode of the system (SIMULATION or REAL).




python
Copy
Edit
# Configuration file for the YinYang Deception Engine

ENGINE_MODE = "REAL"  # Switch between "SIMULATION" or "REAL" for different modes.
4. main.py
This is the entry point for your FastAPI application.

python
Copy
Edit
from fastapi import FastAPI
from api import risk, karma, redeem, logs, status

# Initialize FastAPI app
app = FastAPI()

# Register routes
app.include_router(risk.router, prefix="/api")
app.include_router(karma.router, prefix="/karma")
app.include_router(redeem.router, prefix="/redeem")
app.include_router(logs.router, prefix="/log")
app.include_router(status.router, prefix="/status")

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
5. api/risk.py
This file contains the route for assessing risk based on user actions.

python
Copy
Edit
from fastapi import APIRouter, Request
from pydantic import BaseModel
from deception_engine.risk_assessment import assess_risk

router = APIRouter()

class RiskRequest(BaseModel):
    user_id: str
    actions: list

@router.post("/risk")
async def assess_risk_endpoint(request: RiskRequest):
    risk_score = assess_risk(request.user_id, request.actions)
    return {"user_id": request.user_id, "risk_score": risk_score}
6. deception_engine/risk_assessment.py
This file contains the core logic for risk assessment, calculating entropy, and determining whether to trigger a trap.

python
Copy
Edit
from deception_engine.karma import get_karma
from deception_engine.traps import trigger_trap

def calculate_entropy(actions):
    return sum(actions) / len(actions) if actions else 0

def assess_risk(user_id, actions):
    entropy = calculate_entropy(actions)
    karma = get_karma(user_id)
    
    risk = (entropy * 0.6) + ((1 - karma) * 0.4)
    if risk > 0.75:
        return trigger_trap(user_id, "blackhole")
    elif risk > 0.55:
        return trigger_trap(user_id, "echozone")
    else:
        return {"status": "pass", "message": "Access granted"}
7. deception_engine/traps.py
This file manages the different traps that users can fall into based on their actions and risk level.

python
Copy
Edit
def trigger_trap(user_id, trap_type):
    if trap_type == "blackhole":
        return {"status": "trap", "message": "You are in a recursive loop."}
    elif trap_type == "echozone":
        return {"status": "echo", "message": f"Echoing: {user_id}"}
    return {"status": "unknown", "message": "Unknown trap"}
8. templates/dashboard.html
This is a Jinja2 template for the dashboard page. It will render the karma scores and logs.

html
Copy
Edit
<!DOCTYPE html>
<html>
<head>
    <title>YinYang Deception Engine - Dashboard</title>
    <link rel="stylesheet" href="/static/style.css">
</head>
<body>
    <h1>YinYang Deception Engine Dashboard</h1>
    
    <h2>Karma Scores</h2>
    <ul>
        {% for user_id, karma in users.items() %}
        <li>{{ user_id }}: {{ karma }}</li>
        {% endfor %}
    </ul>

    <h2>Logs</h2>
    <ul>
        {% for log in logs %}
        <li>{{ log.timestamp }} - {{ log.user_id }}: {{ log.event }}</li>
        {% endfor %}
    </ul>
</body>
</html>
9. static/style.css
A simple CSS file for styling the dashboard.

css
Copy
Edit
body {
    font-family: Arial, sans-serif;
}

h1 {
    color: #2d2d2d;
}

h2 {
    color: #4d4d4d;
}

ul {
    list-style-type: none;
}
GitHub Repository Example
Once the backend is ready and committed to GitHub, your repository could look like this:

plaintext
Copy
Edit
YinYang-Deception-Engine/
├── LICENSE
├── README.md
├── requirements.txt
├── config.py
├── main.py
├── deception_engine/              # Core logic and utilities
│   ├── __init__.py
│   ├── karma.py
│   ├── logging.py
│   ├── risk_assessment.py
│   ├── traps.py
├── data/                          # Data storage
│   └── deception_log.json
├── api/                           # FastAPI routes
│   ├── __init__.py
│   ├── risk.py
│   ├── karma.py
│   ├── redeem.py
│   ├── logs.py
│   └── status.py
├── templates/                     # Jinja2 templates for rendering HTML
│   └── dashboard.html
├── static/                        # Static assets (CSS, images)
│   └── style.css
└── Dockerfile                     # Docker configuration for deployment
















Front-End Monitoring:

Dashboard: Monitors the status and health of the Yin and Yang engines. It eliminates performance weaknesses like bottlenecks and ensures the system is functioning optimally.
Real-Time Monitoring: Displays agent behaviors, karmic scores, simulation progress, and real-time entropy levels.

Frontend Considerations:
If you’re planning to use the dashboard route (/dashboard) to display karma scores and logs in an HTML template, you can render that as part of a separate admin dashboard.


In-Memory Karma Database:
You have a dictionary (karma_scores) representing karma scores for different users. These can be updated based on the user's actions, and the process_session() function calculates and triggers traps based on a risk assessment.


API Endpoints:
/api/risk: This endpoint takes a user’s data, assesses the risk, and triggers the appropriate trap based on the risk score.
/karma/{user_id}: This endpoint returns the karma score of a particular user.
/karma: This returns the karma scores of all users.
/redeem: A redemption endpoint that checks if the user's test score is enough to reinstate them based on karma.
/log: A simple endpoint to retrieve the deception log.
/dashboard: Renders an HTML page (likely the dashboard.html file) displaying the karma scores and logs.
Server Setup:
Finally, the FastAPI server is run using Uvicorn on port 8000, which is commonly used for FastAPI apps.


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




Key Backend Components:
FastAPI Setup:

You're using FastAPI to handle HTTP requests, route them to different endpoints, and return responses.

You've set up Jinja2 templates to render HTML pages (such as the dashboard) and serve static assets like CSS, images, and JavaScript.

In-Memory Karma Database:

Karma scores for users are stored in a Python dictionary (karma_scores), which tracks user karma based on their ID.

Functions like get_karma(user_id) and update_karma(user_id, boost) manage the retrieval and updating of karma scores.

Logging:

Event logging is implemented with the log_event() function, which logs actions taken by users (like risk assessments or trap triggers) to a JSON file (data/deception_log.json).

The logs are written in JSON format, making it easy to parse and process the data.

Risk Assessment:

The function assess_risk(session) calculates the risk score for a user based on the entropy of their actions and their karma score.

Depending on the risk score, users are either granted access or subjected to traps (e.g., blackhole or echozone).

Trap Management:

Traps are triggered based on the assessed risk. There are predefined trap types (blackhole, echozone) that block or echo back the user's actions, adding an element of deception to the system.

trigger_trap(user_id, trap_type) manages this logic.

Redemption Process:

If a user's karma score is sufficiently high (e.g., 80 or above), they can be reinstated (boosted) through the process_redemption() function, which increases their karma score.

If their score is too low, redemption fails.

API Endpoints:

You have several endpoints to expose this backend functionality via the FastAPI HTTP server:

/api/risk: Receives user session data, assesses risk, and triggers traps.

/karma/{user_id}: Returns the karma score of a specific user.

/karma: Returns karma scores for all users.

/redeem: Processes redemption based on a user's score.

/log: Returns the logged events from the deception log.

/status: Simple status endpoint for health checks.

/dashboard: Renders an HTML dashboard with user karma and logs.


































   











