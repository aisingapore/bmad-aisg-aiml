# BMAD AI/ML Engineering - Quick Reference Card

## 🚀 Agent Activation Commands

| Agent | Name | Quick Command | Full Commands |
|-------|------|---------------|---------------|
| 🤖 ML/AI Engineer & MLOps | Marcus Tan Wei Ming | `@marcus` | "Activate Marcus", "ML Engineer mode" |
| 🏛️ ML/AI System Architect | Rizwan bin Abdullah | `@rizwan` | "Switch to Rizwan", "ML Architect mode" |
| 📊 Senior Data Scientist | Sophia D'Cruz | `@sophia` | "Activate Sophia", "Data Scientist mode" |
| 🛡️ Security & Ethics Specialist | Priya Sharma | `@priya` | "Switch to Priya", "Security/Ethics mode" |

## 📋 Workflow Selection Matrix

| Situation | Workflow | Duration | Command |
|-----------|----------|----------|---------|
| Building production system | MVP | 6 months | "Start AISG MVP workflow" |
| Validating feasibility | POC | 3 months | "Start AISG POC workflow" |
| Quick industry project | Short | 4 weeks | "Start Short Industry workflow" |
| Training/Education | LADP | 4 weeks | "Start LADP workflow" |

## 🎯 Task Quick Commands

### Data Analysis (Sophia)
```
"Explore data"          → data-exploration.md
"Analyze statistics"    → statistical-analysis.md
"Engineer features"     → feature-engineering.md
"Test hypothesis"       → hypothesis-testing.md
```

### ML Engineering & MLOps (Marcus)
```
"Develop model"        → model-development.md
"Tune hyperparameters" → hyperparameter-tuning.md
"Setup CI/CD"          → ci-cd-setup.md
"Deploy model"         → model-serving-setup.md
```

### Architecture (Rizwan)
```
"Design architecture"  → architecture-design.md
"Select model"         → model-selection.md
"Design LLM app"       → llm-application-architecture.md
"Design RAG"           → rag-system-design.md
```

### Security & Ethics (Priya)
```
"Security testing"     → security-assessment.md
"Bias detection"       → bias-detection.md
"Ethics review"        → ethics-assessment.md
"Compliance check"     → compliance-validation.md
```

## 🔄 Common Workflows

### Starting a New ML Project
```
1. @rizwan  → Architecture design
2. @sophia  → Data exploration
3. @marcus  → Model development
4. @marcus  → Deployment setup
5. @priya   → Ethics review
```

### Data to Model Pipeline
```
1. @sophia  → EDA & feature engineering
2. @marcus  → Model training
3. @marcus  → API implementation
4. @marcus  → Production deployment
```

### Security & Compliance Check
```
1. @priya   → Security testing
2. @priya   → Ethics assessment
3. @marcus  → Security hardening
```

## 📊 Agent Specialization Map

```
Data Pipeline:     Sophia → Marcus → Marcus
Architecture:      Rizwan → Marcus → Sophia  
Security:          Priya → Marcus → Priya
Implementation:    Marcus → Marcus → Marcus
Ethics:            Priya → Sophia → Rizwan
```

## 🛠️ Template Quick Access

| Need | Template | Command |
|------|----------|---------|
| Document model | model-card-tmpl.yaml | "Generate model card" |
| Design system | ml-architecture-tmpl.yaml | "Create ML architecture" |
| Setup deployment | deployment-config-tmpl.yaml | "Generate deployment config" |
| Ethics report | ethics-assessment-tmpl.yaml | "Create ethics assessment" |
| Monitor system | monitoring-dashboard-tmpl.yaml | "Setup monitoring dashboard" |

## ✅ Essential Checklists

| Phase | Checklist | Command |
|-------|-----------|---------|
| Before Training | data-quality-checklist.md | "Run data quality check" |
| After Training | model-validation-checklist.md | "Validate model" |
| Before Deploy | ml-model-readiness-checklist.md | "Check production readiness" |
| Ethics Review | ai-ethics-checklist.md | "Run ethics checklist" |
| Infrastructure | mlops-readiness-checklist.md | "Validate MLOps" |

## 🚦 Phase Transitions

### MVP Project (6 months)
```
Discovery (W1-4)    → @sophia, @rizwan, @priya
Experiment (W5-12)  → @sophia, @marcus  
Production (W13-20) → @marcus, @rizwan, @sophia
Validation (W21-24) → @priya, @priya
```

### POC Project (3 months)
```
Discovery (W1-2)  → @sophia, @rizwan
Prototype (W3-8)  → @marcus, @sophia
Deploy (W9-11)    → @marcus
Validate (W12)    → @priya
```

## 💡 Pro Tips

### Agent Switching
- Sequential: "Handoff to [agent]"
- Parallel: "Consult with [agent]"
- Team: "Team review with [agents]"

### Task Execution
- List tasks: "[Agent], show tasks"
- Execute: "[Agent], run [task]"
- Status: "Check task progress"

### Workflow Navigation
- Current: "Where are we?"
- Next: "What's next?"
- Jump: "Skip to [phase]"

## 🔥 Hotkeys (IDE)

| Action | Command |
|--------|---------|
| List agents | `/agents` |
| Current agent | `/whoami` |
| Switch agent | `/switch [name]` |
| List tasks | `/tasks` |
| Run task | `/run [task]` |
| Help | `/help` |

## 🎯 Decision Trees

### Which Agent to Start With?
```
Have requirements? → @rizwan (Architecture)
Have data?        → @sophia (Analysis)
Ready to build?   → @marcus (Development)
Ready to deploy?  → @marcus (MLOps)
Need review?      → @priya (Ethics/Security)
```

### Which Workflow?
```
Budget > $200k?     → MVP (6 months)
Proof needed?       → POC (3 months)  
Quick win?          → Short (4 weeks)
Training team?      → LADP (4 weeks)
```

## 📈 Success Metrics

| Metric | MVP Target | POC Target | Short Target |
|--------|------------|------------|--------------|
| Model Performance | >95% | >85% | >80% |
| Deployment Time | 2 weeks | 1 week | 2 days |
| Documentation | Complete | Essential | Minimal |
| Testing Coverage | >90% | >70% | >60% |
| Ethics Review | Full | Standard | Quick |

## 🆘 Emergency Commands

```
"Stop current task"
"Reset agent state"
"Show all options"
"Explain what you're doing"
"Rollback last action"
"Get help"
```

## 🔗 Integration Points

### With Core BMAD
```
PM (John) → ML Architect (Rizwan)
Architect (Winston) → ML Architect (Rizwan)
Developer (James) → ML Engineer (Marcus)
QA (Quinn) → Security/Ethics (Priya)
```

### Cross-Functional
```
Data Scientist ↔ ML Engineer
ML Architect ↔ ML Engineer
Security/Ethics ↔ All Agents
ML Engineer ↔ Data Scientist
```

---

**Remember**: Agents know their tasks, templates, and checklists. Just ask!

*Quick Start*: "I need to [build/deploy/test] a [type] model for [use case]"