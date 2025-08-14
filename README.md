# BMAD AI/ML Engineering Expansion Pack (v2.0)

This expansion pack extends the BMAD Method framework to support AI/ML engineering projects. It provides agents, workflows, templates, and best practices in a consolidated architecture.

## Project History

**Founder**: Laurence Liew - Developed the initial workflows and agent framework. His contributions established the core methodology and approach.

**Current Maintainers**: 
- **Najib Ninaba** ([@najibninaba](https://github.com/najibninaba)) - Core Team Member
- **Siavash Sakhavi** ([@ssakhavi](https://github.com/ssakhavi)) - Core Team Member

## Project Timelines

BMAD frameworks support different project timelines:
- **Traditional Timeline**: 6-12 months
- **BMAD Timeline**: 3-12 weeks
- **Iteration Speed**: Prototyping and testing cycles
- **Deployment Frequency**: Multiple deployments per day

## Overview

The streamlined AI/ML Engineering expansion pack provides specialized agents, workflows, templates, and best practices for:

- Machine Learning model development and deployment
- Large Language Model (LLM) and RAG application development
- Comprehensive MLOps pipeline implementation
- Unified AI security, ethics, and governance
- Data science and analytics workflows
- AI Singapore program-specific workflows

## Installation

### Prerequisites

Your target project must be BMAD-enabled with instructions from [BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD).

### 1. Clone This Repository

```bash
# Clone the expansion pack
git clone https://github.com/najibninaba/bmad-aisg-aiml.git
cd bmad-aisg-aiml
```

### 2. Install the [BMAD Pack Installer](https://github.com/najibninaba/bmad-pack-installer) via `uv`

```bash
# Install once (recommended for regular use)
uv tool install bmad-pack-installer

# Or run directly without installation
uvx --from bmad-pack-installer bmad-pack-installer deploy . /path/to/project
```

### 3. Deploy This Pack

```bash
# Basic installation (from cloned repo directory)
bmad-pack-installer deploy . /path/to/project

# Preview changes without installing
bmad-pack-installer deploy . /path/to/project --dry-run

# Force reinstall over existing pack
bmad-pack-installer deploy . /path/to/project --force
```

### Validation

```bash
# Check if target is valid BMAD project
bmad-pack-installer check /path/to/project

# Validate this expansion pack (from cloned repo directory)
bmad-pack-installer validate .
```

The installer creates:
- Hidden directory: `.bmad-aisg-aiml/`
- Claude commands: `.claude/commands/bmadAISG/`
- Updated manifests and symbolic links

## Usage

### Choose Your Program

```
Decision Tree:
├── Need to train apprentices?
│   ├── Yes → 6 months available? → MVP
│   └── Yes → 3 months only? → POC
├── Need fast MVP without training?
│   └── Yes → SIP (3 months)
└── Learning LLM development?
    └── Yes → LADP (4 months)
```

### Follow the Workflow

```bash
# Navigate to installed workflows
cd .bmad-aisg-aiml/workflows/
# Choose your program-specific workflow
cat aisg-[mvp|poc|sip|ladp].md
```

### Quick Commands

#### Agent Activation
```
@marcus - ML Engineering & MLOps
@rizwan - System Architecture
@sophia - Data Science
@priya - Security & Ethics
```

#### Workflow Selection
```
"Start 6-month MVP with 4 apprentices"
"Begin 3-month POC for feasibility"
"Launch 3-month SIP for fast MVP"
"Start LADP programme for LLM training"
```

## Core Agent Team

### 4 Agents

1. **Marcus Tan Wei Ming** - ML/AI Engineer & MLOps Specialist (`ml-engineer`)
   - **Heritage**: Singaporean Chinese
   - **Expertise**: End-to-end ML development, MLOps pipelines, infrastructure automation
   - **Technical Skills**: PyTorch/TensorFlow, Kubernetes/Docker, CI/CD, cloud platforms
   - **Focus Areas**: Model training, deployment, monitoring, production systems

2. **Rizwan bin Abdullah** - ML/AI System Architect (`ml-architect`)
   - **Heritage**: Singaporean Malay
   - **Expertise**: ML system design, scalable architectures, infrastructure planning
   - **Technical Skills**: Distributed systems, transformer architectures, RAG systems
   - **Focus Areas**: System design, model architecture selection, technical strategy

3. **Sophia D'Cruz** - Senior Data Scientist (`ml-data-scientist`)
   - **Heritage**: Singaporean Eurasian
   - **Expertise**: Statistical analysis, experimental design, recommendation systems
   - **Technical Skills**: Causal inference, A/B testing, feature engineering
   - **Focus Areas**: EDA, hypothesis testing, insights generation, model evaluation

4. **Priya Sharma** - ML Security & Ethics Specialist (`ml-security-ethics-specialist`)
   - **Heritage**: Singaporean Indian
   - **Expertise**: ML security, adversarial testing, AI ethics, compliance
   - **Technical Skills**: Red teaming, bias detection, privacy protection
   - **Focus Areas**: Security audits, ethical reviews, regulatory compliance

## Workflows

### Standard ML Workflows
- **ML Development**: End-to-end model development process
- **ML Deployment**: Production deployment with monitoring
- **ML Experimentation**: Systematic experimentation framework

### AI Singapore (AISG) Program Workflows

| Program | Duration | Team Structure | Deliverable | Key Difference |
|---------|----------|---------------|-------------|----------------|
| **MVP** | 6 months | 1 AI Engineer + 2-6 Apprentices | Full production system | Comprehensive with training |
| **POC** | 3 months | 1 AI Engineer + 2-4 Apprentices | Proof of concept | Feasibility with training |
| **SIP** | 3 months | 1-2 AI Engineers (NO apprentices) | Production MVP | Fast delivery, no training |
| **LADP** | 4 months | Learners + Mentors (guide only) | LLM application | Self-directed learning |

#### 1. 6-Month MVP Projects (`aisg-mvp-workflow`)
- **Team**: 1 AI Engineer + 2-6 Apprentices
- **Objective**: Build comprehensive production system with apprentice training
- **Phases**: Discovery → Experimentation → Productionization → Validation
- **All 4 agents** activated across phases

#### 2. 3-Month POC Projects (`aisg-poc-workflow`)
- **Team**: 1 AI Engineer + 2-4 Apprentices
- **Objective**: Validate technical feasibility and business value
- **Phases**: Rapid Discovery → Prototyping → Deployment → Validation
- **All 4 agents** for comprehensive validation

#### 3. 3-Month SIP - Short Industry Projects (`aisg-sip-workflow`)
- **Team**: 1-2 AI Engineers only (NO apprentices)
- **Objective**: Deliver production MVP without training overhead
- **Phases**: Discovery → Development → Productionization → Handover
- **All 4 agents** for fast MVP delivery

#### 4. 4-Month LADP - LLM Application Developer Programme (`aisg-ladp-workflow`)
- **Duration**: 4 months part-time (8-10 hrs/week) or 1-3 days full-time
- **Team**: Learners with mentor guidance (mentors guide but DON'T code)
- **Objective**: Build real-world LLM applications with company SOW
- **Structure**: Month 1 (Self-learning) → Month 2 (Design) → Month 3 (Development) → Month 4 (Deployment)
- **3 workshops** + project implementation

### Program Outcomes
- **MVP**: Production systems completed in 6 months with training
- **POC**: Proof of concepts completed in 3 months with learning
- **SIP**: Production MVPs completed in 3 months
- **LADP**: LLM applications developed in 4 months

## Resources

### Tasks
1. `advanced-elicitation.md` - Requirements gathering
2. `correct-aiml-design.md` - Design correction and validation
3. `create-aiml-story.md` - User story creation
4. `aiml-design-brainstorming.md` - Solution ideation
5. `validate-aiml-story.md` - Story validation

### Checklists
1. `aiml-architect-checklist.md` - Architecture review
2. `aiml-change-checklist.md` - Change management
3. `aiml-design-checklist.md` - Design validation
4. `aiml-story-dod-checklist.md` - Definition of done

### Templates
1. `aiml-architecture-tmpl.yaml` - System architecture
2. `aiml-brief-tmpl.yaml` - Project brief
3. `aiml-design-doc-tmpl.yaml` - Design documentation
4. `aiml-story-tmpl.yaml` - User stories
5. `aiml-ethics-governance-tmpl.yaml` - AI ethics
6. `aiml-security-compliance-tmpl.yaml` - Security & compliance
7. `aiml-model-card-tmpl.yaml` - Model transparency
8. `aiml-workflow-tmpl.yaml` - Workflow definitions

### Data
1. `bmad-kd.md` - Complete BMAD knowledge base
2. `development-guidelines.md` - Python standards, ML patterns, MLOps requirements

## Web Bundles

Bundles for web-based AI platforms:

1. **`ai-ml-team-full.txt`** - All 4 agents for flexible use
2. **`aisg-mvp-team.txt`** - 6-month MVP workflow
3. **`aisg-poc-team.txt`** - 3-month POC workflow
4. **`aisg-short-industry-team.txt`** - 3-month SIP workflow (NEW)
5. **`aisg-ladp-team.txt`** - 4-month LADP programme

## Singapore Context
All agents include:
- Local regulatory knowledge (PDPA, IMDA, MAS)
- AISG program experience
- Understanding of local market dynamics
- Government standards compliance

## File Structure

```
bmad-ai-ml-engineering/
├── agents/                    # 4 core agents
│   ├── ml-engineer.md
│   ├── ml-architect.md
│   ├── ml-data-scientist.md
│   └── ml-security-ethics-specialist.md
├── agent-teams/              # 5 team configurations
├── checklists/              # 4 checklists
├── templates/               # 8 templates
├── tasks/                   # 5 tasks
├── workflows/               # Standard + 4 AISG workflows
├── data/                    # 2 reference files
├── web-bundles/            # 5 ready-to-use bundles
└── config.yaml             # Configuration
```

## Dependencies

- **Required**: bmad-core >= 4.0.0
- **Recommended**: Python >= 3.8, Docker, Kubernetes
- **Optional**: Terraform, MLflow, Kubeflow

## Compliance & Standards

### Singapore Regulations
- **PDPA**: Personal Data Protection Act compliance
- **IMDA**: Model AI Governance Framework aligned
- **MAS FEAT**: Fairness, Ethics, Accountability, Transparency

### International Standards
- ISO/IEC 23053: Framework for AI using ML
- ISO/IEC 23894: AI risk management

## Contributing

Contribution process:
- **Core Team**: Direct commit access for maintenance and development
- **External Contributors**: Submit contributions via pull requests
- **Review Process**: All PRs require approval from core team members

See our [Contributing Guidelines](CONTRIBUTING.md) for detailed information on how to contribute.

For a complete list of contributors, see [CONTRIBUTORS.md](CONTRIBUTORS.md).

## Training & Support

### Documentation
- **Quick Start**: This README
- **Workflows**: `/workflows/README.md`
- **Web Bundles**: `/web-bundles/WEB-BUNDLE-INSTRUCTIONS.md`
- **Agents**: Individual agent files in `/agents/`

### Support Channels
- Review `REFACTORING-SUMMARY.md` for v2.0 changes
- Check agent-specific documentation
- Consult workflow guides
- Raise issues in the repository

---

## Version History

### v2.0.0 (Current)
- 4 core agents
- Added SIP workflow for MVP delivery
- Updated LADP to 4-month programme
- Added Singapore context

### v1.0.0
- Initial release
- Basic AISG workflows