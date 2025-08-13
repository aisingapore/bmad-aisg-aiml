# AI Singapore Program Workflows

## Overview

This directory contains specialized workflows for AI Singapore's various program types. Each workflow is tailored to specific program objectives, timelines, and team compositions, utilizing our 4 streamlined AI/ML agents.

## The 4 Core Agents

1. **Marcus Tan Wei Ming** - ML/AI Engineer & MLOps Specialist
2. **Rizwan bin Abdullah** - ML/AI System Architect
3. **Sophia D'Cruz** - Senior Data Scientist
4. **Priya Sharma** - ML Security & Ethics Specialist

## Available Workflows

### 1. [6-Month MVP Project](aisg-mvp-6month.md)
- **Duration**: 24 weeks
- **Team**: 1 AI Engineer + 2-6 Apprentices
- **Objective**: Build production-ready MVP with comprehensive features
- **Key Phases**: Discovery, Experimentation, Productionization, Validation
- **All 4 agents activated across phases**

### 2. [3-Month POC Project](aisg-poc-3month.md)
- **Duration**: 12 weeks
- **Team**: 1 AI Engineer + 2-4 Apprentices
- **Objective**: Validate technical feasibility and business value
- **Key Phases**: Rapid Discovery, Prototyping, Deployment, Validation
- **All 4 agents with varied allocation**

### 3. [Short Industry Projects (SIP)](aisg-short-industry.md)
- **Duration**: 12 weeks (3 months)
- **Team**: 1-2 AI Engineers (NO apprentices)
- **Objective**: Build production-ready MVP without training overhead
- **Key Phases**: Discovery, Development, Productionization, Validation
- **All 4 agents activated for MVP delivery**

### 4. [LADP Programme](aisg-ladp.md)
- **Duration**: 4 months part-time (8-10 hrs/week) or 1-3 days full-time
- **Team**: Learners with mentor guidance (mentors guide but don't code)
- **Objective**: Build real-world LLM applications with company SOW
- **Key Phases**: Self-directed learning, Design, Development, Deployment
- **3 agents activated as mentors across different months**

## Workflow Selection Guide

| Criteria | MVP (6-month) | POC (3-month) | SIP (3-month) | LADP (4-month) |
|----------|--------------|---------------|----------------|------|
| **Primary Goal** | Production system | Feasibility study | Production MVP | LLM app training |
| **Team Size** | 1 AI Eng + 2-6 Apprentices | 1 AI Eng + 2-4 Apprentices | 1-2 AI Engineers only | Learners + Mentors |
| **Complexity** | High | Medium | Medium-High | Beginner-friendly |
| **Output** | Full production system | Working prototype | Production MVP | LLM application |
| **Documentation** | Comprehensive | Focused | Complete | Educational |
| **Testing Rigor** | Full suite | Basic validation | Production tests | Learning exercises |
| **Training** | Yes (apprentices) | Yes (apprentices) | No | Yes (self-directed) |

## Common Workflow Patterns

### Sequential Handoff
Used in longer projects (MVP, POC) where phases have clear dependencies:
```
Data Scientist → ML Engineer → Security Specialist
```

### Parallel Execution
Used for independent tasks that can run simultaneously:
```
ML Engineer + Data Scientist (concurrent development)
Architect + Security Specialist (parallel review)
```

### Rapid Iteration
Used in short projects for fast delivery:
```
Problem → Solution → Implementation → Delivery (1 week each)
```

### Mentored Learning
Used in LADP for guided education:
```
Instruction → Practice → Feedback → Application
```

## Quality Gates

All workflows include quality gates at phase transitions:

- **Data Quality Gate**: Ensures sufficient, quality data
- **Model Performance Gate**: Validates model meets requirements
- **Integration Gate**: Confirms system components work together
- **Security Gate**: Verifies security and compliance standards

## Agent Activation Schedule

### MVP Project (All 4 Agents)
- **Weeks 1-4**: Sophia (lead), Rizwan (support)
- **Weeks 5-12**: Marcus (lead), Sophia (support)
- **Weeks 13-20**: Marcus (lead), Rizwan & Priya (support)
- **Weeks 21-24**: Priya (lead), Marcus & Sophia (support)

### POC Project (4 Agents with varied allocation)
- **Weeks 1-2**: Sophia (40%), Rizwan (10%)
- **Weeks 3-8**: Marcus (40%), Sophia (40%)
- **Weeks 9-11**: Marcus (lead), Rizwan (support)
- **Week 12**: Priya (lead), All agents review

### Short Industry (3 Agents)
- **Week 1**: Sophia (30%)
- **Weeks 2-3**: Marcus (60%), Sophia (30%)
- **Week 4**: Marcus (60%), Rizwan (10%)

### LADP (3 Agents as Mentors - Guide, Not Code)
- **Month 1**: Self-directed learning + Workshop 1
- **Month 2**: Rizwan (architecture & design guidance)
- **Month 3**: Marcus (implementation guidance)
- **Month 4**: Priya (security) + Workshop 3

## Success Metrics by Workflow

### MVP Success Criteria
- Model performance meets business KPIs
- System deployed and stable
- Security audit passed
- Documentation complete
- Handover successful

### POC Success Criteria
- Technical feasibility proven
- Business value validated
- Go/No-go decision made
- Next steps defined

### Short Industry Success Criteria
- Working prototype delivered
- Core requirements met
- Knowledge transferred
- On-time completion

### LADP Success Criteria
- >80% learner completion
- All projects deployed
- Skills acquired
- Satisfaction >4.5/5

## Workflow Customization

Each workflow can be customized based on:

1. **Project Requirements**
   - Adjust agent allocation percentages
   - Modify phase durations
   - Add/remove quality gates

2. **Team Capabilities**
   - Scale agent involvement based on human team skills
   - Adjust mentoring vs. execution balance

3. **Timeline Constraints**
   - Compress phases for faster delivery
   - Extend for more thorough validation

4. **Risk Tolerance**
   - Add more security/ethics review for sensitive projects
   - Streamline for low-risk prototypes

## Best Practices

1. **Start with the Right Workflow**
   - Match workflow to project objectives
   - Consider team size and skills
   - Align with timeline constraints

2. **Clear Agent Responsibilities**
   - Define deliverables for each agent
   - Document handoff artifacts
   - Establish review criteria

3. **Regular Checkpoints**
   - Weekly progress reviews
   - Phase-gate assessments
   - Stakeholder updates

4. **Flexibility Within Structure**
   - Adapt to discoveries during project
   - Adjust agent allocation as needed
   - Maintain focus on outcomes

## Support

For detailed workflow specifications, refer to individual workflow files in this directory. For agent capabilities, see `/agents/` directory.