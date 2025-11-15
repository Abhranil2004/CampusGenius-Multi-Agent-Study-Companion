# 📘 **CampusGenius – Multi-Agent Study Companion**
<p align="center">
  <img src="https://github.com/Abhranil2004/CampusGenius-Multi-Agent-Study-Companion/blob/general/Banner.png" width="560" height="280">
</p>

*A multi-agent system powered by Google ADK and the A2A protocol, designed to help students learn faster with auto-generated notes, explanations, flashcards, and study plans.*

## 🚀 **Overview**

**CampusGenius** is a two-agent learning assistant built using the **Google Agent Development Kit (ADK)** and the **A2A (Agent-to-Agent) protocol**.
It showcases how specialized agents can communicate and collaborate to solve real educational problems.

The system consists of:

### 🔹 **1. NotesMaster — Remote A2A Agent**

A content-focused agent that generates:

* Exam-oriented notes
* Topic explanations
* Flashcards

It is exposed as an A2A microservice using ADK’s `to_a2a()` helper and publishes a standards-compliant agent card.

### 🔹 **2. CampusGenius — Main User-Facing Agent**

A decision-making assistant that:

* Understands student queries
* Chooses whether to call NotesMaster
* Delegates content generation tasks
* Creates structured study plans
* Maintains conversation context

CampusGenius consumes NotesMaster via a `RemoteA2aAgent`, exactly like calling an external service.

---

## 🧠 **What the System Can Do**

### 📚 Generate Notes

Well-structured, exam-focused notes on any topic.

### ✏️ Explain Topics

Beginner to advanced explanations depending on what the student needs.

### 🧾 Create Flashcards

For revision and quick memorization.

### 🗓️ Produce Study Plans

Day-wise study schedules based on time remaining before exams.

### 🔄 Maintain Conversations

Using ADK’s session service for conversational continuity.

---

## ⚙️ **Technical Architecture**

This project demonstrates:

* **Google ADK** (`LlmAgent`, `Runner`, `RemoteA2aAgent`)
* **Gemini models** for generation
* **A2A protocol** for cross-agent communication
* **FastAPI server** auto-generated via `to_a2a()`
* **Agent cards** exposed through `/.well-known/agent-card.json`
* **Session management** using `InMemorySessionService`

### 🏗️ Architecture Diagram

```
┌───────────────────────────┐
│      CampusGenius         │
│  (Main user-facing agent) │
│                           │
│  - Interprets user intent │
│  - Creates study plans    │
│  - Delegates to remote    │
└───────────▲───────────────┘
            │ A2A Protocol
            │
┌───────────┴───────────────┐
│       NotesMaster          │
│  (Remote A2A agent)        │
│                            │
│  - Generates notes         │
│  - Explains topics         │
│  - Builds flashcards       │
└────────────────────────────┘
```

---

## 📦 **Features & Tools**

### 🔧 NotesMaster Tools

| Tool                                   | Description                     |
| -------------------------------------- | ------------------------------- |
| `generate_notes(topic, extra_context)` | Creates exam-ready notes        |
| `explain_topic(topic, level)`          | Explains topics in simple terms |
| `create_flashcards(topic, num_cards)`  | Produces flashcards             |

### 🌐 A2A Exposure

NotesMaster is exposed via:

```
to_a2a(notes_master_agent, port=8001)
```

This automatically provides:

* `/tasks` endpoint
* `/.well-known/agent-card.json`

### 🔗 Remote Consumption

CampusGenius uses:

```python
RemoteA2aAgent(agent_card="http://localhost:8001/.well-known/agent-card.json")
```

---

## 🎯 **Why This Project Matters**

Students struggle with:

* Finding quality notes
* Understanding difficult concepts
* Creating study plans
* Revising efficiently

CampusGenius provides:

* Instant structured notes
* Clear explanations
* Flashcards
* Personalized plans

It demonstrates *how multi-agent AI systems can improve education*, aligning with the **Agents for Good** mission.

---

## 🌟 **Why This Project Stands Out**

* Real multi-agent collaboration
* Clean responsibility separation
* A2A protocol usage
* Production-like architecture
* Practical educational impact
* Easy to extend

---

## 🔮 **Future Enhancements**

* Student profile personalization
* Math-solver and code-explanation agents
* Integration with real syllabi or LMS systems
* Web or mobile UI
* Cloud deployment (Cloud Run / Agent Engine)

---

## 🧪 **How to Run (Kaggle / Local)**

1. Install ADK:

```bash
pip install -q google-adk --no-deps
```

2. Set your `GOOGLE_API_KEY`.

3. Start NotesMaster A2A server.

4. Start CampusGenius agent.

5. Interact using `Runner`.

---

## 🤝 **Acknowledgements**

* Google ADK team
* Gemini API
* Kaggle 5-Day Agents Intensive

