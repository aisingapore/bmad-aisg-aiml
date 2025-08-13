# Agent Teams Configuration

This directory contains team configurations for various AI/ML project types, with special focus on AI Singapore (AISG) programs.

## Overview

The agent teams are configured using 4 streamlined AI/ML agents to support different project scales, timelines, and objectives. Each configuration specifies which agents to activate, when to use them, and how they collaborate.

## The 4 Core Agents

### 1. Marcus Tan Wei Ming - ML/AI Engineer & MLOps Specialist
- **Expertise**: End-to-end ML development, MLOps pipelines, infrastructure automation
- **Focus**: Model training, deployment, monitoring, production systems
- **Key Skills**: PyTorch/TensorFlow, Kubernetes/Docker, CI/CD, cloud platforms

### 2. Rizwan bin Abdullah - ML/AI System Architect
- **Expertise**: ML system design, scalable architectures, infrastructure planning
- **Focus**: System design, model architecture selection, technical strategy
- **Key Skills**: Distributed systems, transformer architectures, RAG systems

### 3. Sophia D'Cruz - Senior Data Scientist
- **Expertise**: Statistical analysis, experimental design, recommendation systems
- **Focus**: EDA, hypothesis testing, insights generation, model evaluation
- **Key Skills**: Causal inference, A/B testing, feature engineering

### 4. Priya Sharma - ML Security & Ethics Specialist
- **Expertise**: ML security, adversarial testing, AI ethics, compliance
- **Focus**: Security audits, ethical reviews, regulatory compliance
- **Key Skills**: Red teaming, bias detection, privacy protection

## Team Configurations

### 1. Full AI/ML Team (`ai-ml-team-full.yaml`)
**Purpose**: Complete end-to-end AI/ML projects with comprehensive coverage

**Key Features**:
- All 4 specialized agents working in coordination
- Full MLOps pipeline implementation
- Complete security and ethics review
- Production-ready deployments

**Workflow**:
- Discovery → Design → Development → Validation → Deployment → Monitoring

### 2. AISG 100E MVP Team (`aisg-mvp-team.yaml`)
**Program**: 6-Month MVP Projects (100 Experiments)
**Team Size**: 1 AI Engineer + 2-6 Apprentices
**Duration**: 24 weeks

**Agent Utilization**:
- **Weeks 1-4 (Discovery)**: Sophia (lead), Rizwan (support)
- **Weeks 5-12 (Experimentation)**: Marcus (lead), Sophia (support)
- **Weeks 13-20 (Productionization)**: Marcus (lead), Rizwan & Priya (support)
- **Weeks 21-24 (Validation)**: Priya (lead), Marcus & Sophia (support)

**Deliverables**: Production-ready MVP with full MLOps, security audit, and ethics compliance

### 3. AISG AIAP For Industry POC Team (`aisg-poc-team.yaml`)
**Program**: 3-Month POC Projects
**Team Size**: 1 AI Engineer + 2-4 Apprentices
**Duration**: 12 weeks

**Agent Allocation**:
- Sophia D'Cruz: 40% (data analysis, validation)
- Marcus Tan: 40% (development, deployment)
- Rizwan bin Abdullah: 10% (architecture guidance)
- Priya Sharma: 10% (quick security/ethics check)

**Focus**: Rapid prototyping and feasibility validation

### 4. AISG Short Industry Project Team (`aisg-short-industry-team.yaml`)
**Program**: Short Industry Projects (SIP)
**Team Size**: 1-2 AI Engineers (no apprentices)
**Duration**: 4 weeks

**Agent Allocation**:
- Marcus Tan: 60% (rapid implementation)
- Sophia D'Cruz: 30% (data analysis)
- Rizwan bin Abdullah: 10% (advisory)

**Focus**: Ultra-rapid prototype delivery and skill development

### 5. AISG LADP Team (`aisg-ladp-team.yaml`)
**Program**: LLM Application Developer Programme
**Team Size**: 20-30 Learners + Instructors
**Duration**: 4 weeks

**Teaching Agents**:
- Marcus Tan: LLM implementation, deployment, hands-on coding
- Rizwan bin Abdullah: LLM architecture, RAG systems, design patterns

**Focus**: Education and hands-on LLM application development

## Usage Guide

### Selecting the Right Team Configuration

| Scenario | Team Config | Duration | Agents Used | Outcome |
|----------|------------|----------|-------------|----------|
| Full production system | MVP Team | 6 months | All 4 agents | Deployed product |
| Validate feasibility | POC Team | 3 months | 4 agents (varied allocation) | Go/No-go decision |
| Quick prototype | SIP Team | 4 weeks | 3 agents | Working prototype |
| LLM training | LADP Team | 4 weeks | 2 agents (teaching) | Skilled developers |
| Custom project | Full Team | Varies | All 4 agents | Tailored solution |

### Agent Collaboration Patterns

#### Sequential Handoff
- Data Scientist → Engineer → Security Specialist
- Used in: MVP projects

#### Parallel Collaboration
- Engineer + Data Scientist working simultaneously
- Used in: POC projects

#### Lead-Support Model
- One agent leads, others provide targeted support
- Used in: SIP projects

#### Teaching Mode
- Agents act as instructors and mentors
- Used in: LADP programme

## Best Practices

### For Long Projects (MVP - 6 months)
- Use all 4 agents with clear phase transitions
- Deep specialization in each phase
- Comprehensive documentation at each handoff
- Full security and ethics review

### For Medium Projects (POC - 3 months)
- Focus on 2-3 primary agents
- Light touch from security/ethics
- Rapid iterations over perfection
- Clear go/no-go criteria

### For Short Projects (SIP - 4 weeks)
- 1-2 primary agents only
- Skip extensive reviews
- Focus on core functionality
- Basic documentation

### For Training Programs (LADP)
- Agents as instructors/mentors
- Focus on knowledge transfer
- Hands-on learning emphasis
- Simplified architectures

## File Structure

```
agent-teams/
├── README.md                        # This file
├── ai-ml-team-full.yaml            # Complete team reference
├── ai-ml-team-core.yaml            # Core 4-agent configuration
├── aisg-mvp-team.yaml              # 6-month MVP projects
├── aisg-poc-team.yaml              # 3-month POC projects
├── aisg-short-industry-team.yaml   # 4-week rapid projects
└── aisg-ladp-team.yaml             # 4-week training program
```

## Key Principles

1. **Right-sized teams**: Use only the agents needed for the project scope
2. **Clear responsibilities**: Each agent has defined roles and deliverables
3. **Efficient handoffs**: Documented artifacts between phases
4. **Flexible allocation**: Adjust agent involvement based on project needs
5. **Outcome-focused**: Every configuration targets specific deliverables

## Support

For questions about team configurations or agent utilization, refer to:
- Individual agent definitions in `/agents/`
- Workflow specifications in `/workflows/`
- Task descriptions in `/tasks/`
- The main expansion pack README