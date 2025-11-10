---
title: "Event 2"
date: "2025-10-03"
weight: 1
chapter: false
pre: " <b> 4.2. </b> "

---

# Summary Report: “AWS GenAI Builder Club - AI-Driven Development Life Cycle: Reimagining Software Engineering”

### Event Objectives

- Explore AI-Driven Development Lifecycle (AI-DLC) and its application in modern software engineering  
- Understand the **Vibe Coding methodology** as a structured approach for AI collaboration  
- Experience hands-on demonstrations of **Kiro**, the AI-powered IDE for code generation and context management  
- Learn how AI tools such as **Amazon Q Developer** and **Kiro** can accelerate productivity while maintaining quality  

### Event Information

- **Date & Time:** 2:00 PM, Friday, October 3rd, 2025  
- **Location:** AWS Event Hall, L26 Bitexco Tower, Ho Chi Minh City  
- **Instructors:** Toan Huynh & My Nguyen  
- **Coordinators:** Diem My, Dai Truong, Dinh Nguyen  
- **Role:** Attendee  
- **Theme:** AI-Driven Development using Amazon Q Developer and Kiro  

---

### Key Highlights

- Deep dive into **AI-Driven Development Lifecycle (AI-DLC)** methodology  
- Introduction of **Vibe Coding** – a human-in-the-loop, multi-step problem-solving framework  
- Demonstrations of **Kiro IDE** generating code, documentation, and test cases from natural language  
- Practical examples of structuring development using AI context and standardized markdown templates  

---

### Vibe Coding Methodology & AI-DLC Workflow

#### Never Single-shot a Multi-step Problem
Vibe Coding emphasizes that complex problems should never be handled in a single step. Instead, development is decomposed into smaller, reviewable tasks where AI assists at each stage.  
Key principles include:
- **Decompose:** Break problems into structured tasks (aligned with AI-DLC’s 8 steps).  
- **Plan:** Ask AI to propose a plan (`plan.md`) for each step.  
- **Review & Refine:** Human architects validate and improve AI outputs iteratively.  

> **Philosophy:** *Guardrails, not autopilot* — AI provides guidance while developers stay in control.

![Vibe Coding principle – Never single-shot a multi-step problem](/images/event-2/vibe_single_shot.png)

---

#### AI-DLC Phases
1. **Inception:** Define requirements → User Stories → Independent Units.  
2. **Construction:** Domain Model → Logical Design → Implementation Plan.  
3. **Operation:** Code → Deployment Units → Continuous Improvement.  

Each phase includes continuous human review, ensuring accountability, context integrity, and traceability from requirement to deployment.

![AI-DLC Workflow Steps Overview](/images/event-2/ai_dlc_steps.png)

---

#### Inception Phase – Grouping User Stories into Units
The Inception phase focuses on decomposing user requirements into modular, independent **Units**.  
Each unit encapsulates cohesive functionality that can be built and deployed separately, improving scalability and team autonomy.

![AI-DLC Inception phase – Grouping user stories into units](/images/event-2/ai_dlc_inception_units.png)

---

#### Workflow Features
- **Role Separation:** Business → Architecture → Implementation with clear hand-offs.  
- **AI-Enhanced:** AI augments each role’s expertise through context-driven prompts.  
- **Iterative Feedback Loops:** Continuous refinement across all development stages.  
- **Template-Driven Artifacts:** Standardized markdown templates (`user_stories.md`, `plan.md`, `integration_contract.md`) ensure uniform documentation.  

![AI-DLC Key Workflow Features slide](/images/event-2/ai_dlc_key_workflow.png)

---

#### Full AI-DLC Process Diagram
This diagram illustrates how the roles (Product Owner, Developer, AI) collaborate across Inception, Construction, and Operation, producing standardized artefacts such as user stories, services, and deployment units.

![Full AI-DLC Roles and Phases Diagram](/images/event-2/ai_dlc_full_diagram.png)

---

### Kiro – The AI-Powered Development Environment

#### Overview
**Kiro** serves as the central IDE for implementing AI-DLC and Vibe Coding workflows. It transforms **natural language into production-ready code**, automatically generating:
- API endpoints and models  
- Documentation and inline comments  
- Unit and integration tests  

#### Key Capabilities
- **Context Awareness:** Reads and maintains understanding across files like `overview_user_stories.md`, `units/`, and `plan.md`.  
- **Automation:** Generates test suites, refactors legacy code, and updates documentation in real time.  
- **Integration:** Works seamlessly with Git, CI/CD pipelines, Bedrock models (Claude, Llama), and IDEs such as VS Code.  

---

#### Prompt-driven Development
Developers interact with Kiro through structured markdown prompts defining:
- **Role & Task:** e.g., “You are an expert architect…”  
- **Plan File:** Checklist-based `plan.md` outlining sequential steps.  
- **User Stories:** Grouped into units (`unit_user_management_service.md`, etc.) for modular, parallel development.  

![Prompt Template used in Kiro IDE](/images/event-2/kiro_prompt_template.png)

![Kiro IDE workspace showing plan.md and user stories](/images/event-2/kiro_vscode_prompt.png)

---

### Learning Experience

#### Practical Demonstrations
- **Kiro in Action:** Showcased building a REST API, adding new features, and refactoring for performance—all through natural language.  
- **AI-DLC in Practice:** Visual diagrams illustrated how Vibe Coding orchestrates collaboration among Product Owners, Developers, and AI at every stage.  
- **Prompt Template Design:** Participants learned how structured markdown prompts guide AI in both planning and execution phases.

![AI-DLC Full Process from Intent to Deployment](/images/event-2/ai_dlc_intent_to_deploy.png)

---

### Technical Takeaways
- **AI-DLC ensures structure:** Every decision and artifact is traceable through markdown templates.  
- **Kiro enhances speed & quality:** Code generation, testing, and documentation occur simultaneously.  
- **Context management is key:** Continuous AI learning improves accuracy over time.  
- **Human-in-the-loop workflow:** Ensures trust, compliance, and correctness across AI-assisted tasks.  

---

### Personal Reflections

The session provided a clear, practical vision for **AI-native software development**.  
Vibe Coding redefines the collaboration between humans and AI, turning the software engineer into an **architect-in-the-loop**, while tools like Kiro translate that architecture into executable, validated code.

> *AI doesn’t replace developers — it elevates them. The future of software engineering lies in structured collaboration, contextual intelligence, and iterative co-creation between human expertise and AI assistance.*

---

### Event Photos

![Event highlights – AWS GenAI Builder Club at Bitexco Tower](/images/event-2/event2_vibecoding.png)

> Overall, this event offered a hands-on understanding of how **Vibe Coding** and **Kiro** operationalize AI-DLC — transforming software engineering from manual coding to intelligent, collaborative design.
