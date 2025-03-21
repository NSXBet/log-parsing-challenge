# Log Parsing Challenge

A challenging, step-by-step project that transforms raw Premier League match data into actionable insights through progressive engineering tasks. Starting with basic parsing, you'll advance through containerization, Kubernetes orchestration, monitoring implementation, and resilience engineering. 

This hands-on challenge demonstrates real-world SRE skills with clear deliverables at each tier, ideal for engineers looking to showcase their ability to build and maintain sophisticated data systems.

## Dataset

This dataset originally originally sourced from [Kaggle](https://www.kaggle.com/datasets/acothaha/epl-dataset-20222023-update-every-week) which contains the information of every match in the Premier League 2022/2023.

However, for this challenge, the input will be provided as an unstructured log file in the following format:

```
0:00 ------------------------------------------------------------
0:00 GameInit: Arsenal vs Newcastle United - Matchweek 19
0:00 team1Startings: Aaron Ramsdale
0:00 team1Startings: Ben White
...
0:00 team2Startings: Nick Pope
...
0:00 GameBegin:
0:37 Event: Lineups are announced and players are warming up.
0:26 Event: Kick Off! First Half begins.
...
45:03 Event: Half-time First Half ends, Arsenal 0, Newcastle United 0.
46:04 Event: Kick Off! Second Half begins Arsenal 0, Newcastle United 0.
...
90:07 Event: Full-time Match ends, Arsenal 0, Newcastle United 0.
90:00 EndGame:
90:00 team1Subs: Matt Turner
...
90:00 team1Stat: possession% 66.8
90:00 team1Stat: shotsonTarget 4
...
90:00 team2Stat: possession% 33.2
...
90:00 Exit
90:00 ------------------------------------------------------------
```

This timestamped log format contains all the same information as the original JSON but presented sequentially with MM:SS timestamps.

You are not expected to parse every field, only the ones that are relevant to the challenge.

### Relevant Fields

- Team names (extracted from GameInit)
- Starting lineups (team1Startings, team2Startings)
- Substitutes (team1Subs, team2Subs)
- Team statistics including:
  - Possession percentage
  - Shots/shots on target
  - Touches
  - Passes
  - Tackles
  - Clearances
  - Corners
  - Offsides
  - Yellow cards
  - Fouls conceded

## Levels of the Challenge

### **Level 0 - Basic Log Parser**
✅ Objective: consider the log file as the input and implement a basic application that can parse logs and extract meaningful insights.

**Requirements:**
- Parse match data fields listed above from the unstructured log format.
- The application should receive a log file as input.
- Extract relevant information in a simple manner.
- Expose the extracted data in a structured format.
- The implementation should preferably be in Python or Go.

**Examples of insights:**
- List of all teams in the dataset.
- Total matches played by each team.
- Basic team statistics (total goals, average possession, etc.).
- Player appearances across matches.

---

### **Level 1 - Containerization**
✅ Objective: Containerize the application using Docker.

**Requirements:**
- Write a `Dockerfile` to containerize the log parser.
- Ensure the application runs correctly inside a container.

**Optional:**
- Write CI/CD pipelines to automate image deployment using GitHub Actions.

---

### **Level 2 - Kubernetes Deployment**
✅ Objective: Deploy and access the application to a Kubernetes cluster.

**Requirements:**
- Create Kubernetes manifests for deploying the application.
- Implement Infrastructure as Code (IaC) for the deployment (Helm, Kustomize, Pulumi, etc.).
- Implement a Ingress for the application to make it accessible from outside the cluster.

---

### **Level 3 - Observability & Monitoring**
✅ Objective: Implement Prometheus metrics and logging for monitoring.

**Requirements:**
- Expose application relevant metrics via a `/metrics` endpoint.
- Implement health checks (`readinessProbe` and `livenessProbe`) in Kubernetes.
- Implement structured logging.
- Create a dashboard with app health metrics.
- Set up log access and visualization solution.

**Optional:**
- Track processing time, request counts, and error rates.

---

### **Level 4 - Resilience, Automation & Best Practices**
✅ Objective: Enhance application reliability, resilience and automation.

**Requirements:**
- Configure automatic scaling (HPA) based on resource utilization.
- Set up an alerting system (using Prometheus Alertmanager, Grafana alerts, or similar).

---

### **Bonus Level - Querying Logs**
✅ Objective: Implement a query interface to query the logs.

**Requirements:**
- Allow querying logs by different fields and filters.
- Support more complex dynamic queries like:
  - Find teams with possession over X%.
  - List matches where a team completed more than Y passes.
  - Identify players who appeared in most starting lineups.
  - Compare defensive statistics between teams.

**Optional:**
- Parse the event field and extract information like:
    - Count yellow cards per team or player.
    - Find all goals scored by a specific player.
- For a double bonus use a llm to parse the event field.
---

## **Submission Guidelines**
- Share your solution via a Git repository.
- Provide a `README.md` explaining how to build, deploy, and use your application.
- Document challenges faced and any assumptions made.
- It's expected that you use a LLM as a tool for this challenge.

Good luck, and happy coding! 🚀