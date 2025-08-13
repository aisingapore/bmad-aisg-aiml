# BMad Knowledge Base - AI/ML Engineering

## Overview

This is the AI/ML engineering expansion of BMad-Method (Breakthrough Method of Agile AI-driven Development), specializing in machine learning model development, MLOps pipelines, and AI system deployment. The system provides a modular architecture with comprehensive support for both research and production environments, specifically optimized for Singapore's AI ecosystem and AI Singapore (AISG) programs.

### Key Features for AI/ML Engineering

- **Specialized Agent System**: 4 streamlined AI agents for each ML engineering role
- **MLOps-First Build System**: Automated pipelines for model training, deployment, and monitoring
- **Dual Environment Support**: Optimized for both research notebooks and production systems
- **AI/ML Resources**: Specialized templates, tasks, and checklists for ML projects
- **Singapore-Context Approach**: Built-in compliance with local regulations and AISG standards

### AI/ML Engineering Focus

- **Target Frameworks**: PyTorch, TensorFlow, JAX with Python 3.8+
- **Platform Strategy**: Cloud-native (GCP, AWS, Azure) with on-premise support
- **Development Approach**: Agile experimentation with production-ready deployment
- **Performance Target**: Model inference under 100ms for real-time applications
- **Architecture**: Microservices-based with containerized deployment

### When to Use BMad for AI/ML Engineering

- **New ML Projects (Greenfield)**: Complete end-to-end ML system development from research to production
- **Existing ML Systems (Brownfield)**: Model improvements, pipeline enhancements, and system scaling
- **AI Team Collaboration**: Data scientists, ML engineers, and architects working together
- **MLOps Implementation**: Automated training, deployment, monitoring, and retraining pipelines
- **Compliance & Documentation**: Model cards, ethics reviews, regulatory compliance documentation

## How BMad Works for AI/ML Engineering

### The Core Method

BMad transforms you into an "AI Product Owner" - directing a team of specialized AI/ML engineering agents through structured workflows. Here's how:

1. **You Direct, AI Executes**: You provide business requirements; agents handle technical implementation
2. **Specialized ML Agents**: Each agent masters one ML engineering role
3. **ML-Focused Workflows**: Proven patterns guide you from data to deployed models
4. **Clean Handoffs**: Fresh context windows ensure agents stay focused on specific ML tasks

### The Two-Phase ML Development Approach

#### Phase 1: Research & Design (Web UI - Cost Effective)

- Use large context windows for comprehensive ML system design
- Generate complete technical architecture and experiment plans
- Leverage multiple agents for model selection and approach validation
- Create once, use throughout ML development

#### Phase 2: Implementation & Deployment (IDE - Development)

- Shard technical documents into manageable pieces
- Execute focused Data Scientist → ML Engineer cycles
- One model feature at a time, sequential progress
- Real-time model training, testing, and deployment operations

### The ML Development Loop

```text
1. Data Scientist Agent → Analyzes data and designs experiments
2. You → Review and approve approach
3. ML Engineer Agent → Implements model and MLOps pipeline
4. Security/Ethics Agent → Reviews for bias and vulnerabilities
5. You → Verify model performance and compliance
6. Repeat until production deployment
```

### Why This Works for ML

- **Context Optimization**: Clean chats = better AI performance for complex ML logic
- **Role Clarity**: Agents don't context-switch = higher quality ML implementations
- **Incremental Progress**: Small iterations = manageable complexity
- **Quality Oversight**: You validate each model version = performance control
- **Data-Driven**: Experiments guide everything = evidence-based decisions

### Core ML Engineering Philosophy

#### Production-First Development

You are building ML systems as an "AI Product Owner" - thinking strategically with production requirements in mind from day one.

#### ML Engineering Principles

1. **MAXIMIZE_MODEL_PERFORMANCE**: Push for optimal accuracy while maintaining latency requirements
2. **MLOPS_QUALITY_CONTROL**: Automated testing, monitoring, and retraining pipelines
3. **ETHICAL_AI_OVERSIGHT**: Continuous bias monitoring and fairness evaluation
4. **ITERATIVE_EXPERIMENTATION**: Systematic A/B testing and model comparison
5. **CLEAR_EVALUATION_METRICS**: Define success criteria before training
6. **DOCUMENTATION_IS_CRITICAL**: Model cards and decision logs for audit trails
7. **START_SIMPLE_SCALE_SMART**: Baseline models first, then complexity
8. **EMBRACE_FAILURE_LEARN_FAST**: Failed experiments provide valuable insights

## Getting Started with AI/ML Engineering

### Quick Start Options

#### Option 1: Web UI for ML System Design

**Best for**: ML architects and data scientists planning complex systems

1. Navigate to expansion pack agents folder
2. Load agent configurations for your project type
3. Use orchestrator for multi-agent collaboration
4. Generate comprehensive ML system documentation

#### Option 2: IDE Integration for ML Development

**Best for**: ML engineers and data scientists implementing models

```bash
# Installation
npm install -g bmad-method
bmad init
# Select bmad-ai-ml-engineering expansion pack
```

**Installation Steps**:

- Choose "Install expansion pack" when prompted
- Select "bmad-ai-ml-engineering" from the list
- Select your IDE (VS Code, Cursor, etc.)
- Configure for your ML framework preferences

**Verify Installation**:

- `.bmad-core/` folder with base agents
- `.bmad-ai-ml-engineering/` folder with ML agents
- IDE-specific integration files
- ML agents available with configured prefix

### Environment Selection Guide

**Use Web UI for**:

- ML system architecture design
- Cost-effective comprehensive planning
- Multi-agent design consultation
- Ethics and compliance reviews

**Use IDE for**:

- Model development and training
- MLOps pipeline implementation
- Experiment tracking and validation
- Production deployment

## Core Configuration (config.yaml)

```yaml
# ML-specific configuration
mlProject:
  experimentTracking: mlflow
  modelRegistry: mlflow
  dataVersioning: dvc
  pipelineOrchestration: kubeflow
  
architecture:
  architectureFile: docs/ml-architecture.md
  dataFile: docs/data-architecture.md
  mlopsFile: docs/mlops-architecture.md
  
experiments:
  location: experiments/
  notebookLocation: notebooks/
  resultsLocation: results/
  
models:
  location: models/
  servingLocation: serving/
  
monitoring:
  metricsBackend: prometheus
  loggingBackend: elasticsearch
  
compliance:
  ethicsReviewLocation: docs/ethics/
  modelCardsLocation: docs/model-cards/
  
slashPrefix: bmad-ml
```

## Complete ML Engineering Workflow

### Planning Phase (Web UI Recommended)

1. **Problem Definition**: Define business objectives and ML requirements
2. **Data Assessment**: Evaluate data availability and quality
3. **Architecture Design**: Design scalable ML system architecture
4. **Experiment Planning**: Define evaluation metrics and success criteria
5. **MLOps Design**: Plan deployment and monitoring strategy

### Development Phase (IDE)

1. **Data Preparation**:
   - Data validation and cleaning
   - Feature engineering
   - Dataset creation and versioning

2. **Model Development**:
   - Baseline model creation
   - Hyperparameter optimization
   - Model evaluation and comparison

3. **MLOps Implementation**:
   - Training pipeline automation
   - Model deployment pipeline
   - Monitoring and alerting setup

4. **Production Deployment**:
   - A/B testing setup
   - Gradual rollout
   - Performance monitoring

## ML Agent System

### Core ML Team (4 Streamlined Agents)

| Agent | Role | Primary Functions | When to Use |
|-------|------|------------------|-------------|
| `ml-engineer` | ML/AI Engineer & MLOps | Model training, deployment, monitoring | All implementation tasks |
| `ml-architect` | System Architect | System design, scalability planning | Architecture decisions |
| `ml-data-scientist` | Data Scientist | EDA, experiments, insights | Analysis and validation |
| `ml-security-ethics-specialist` | Security & Ethics | Compliance, bias detection, security | Reviews and audits |

### Agent Interaction Patterns

**Sequential Workflow**:
```
Data Scientist → ML Engineer → Security Specialist
```

**Parallel Collaboration**:
```
ML Engineer + Data Scientist (concurrent development)
Architect + Security (parallel review)
```

## AI Singapore Program Support

### 6-Month MVP Projects (100E)

- Full team of 4 agents across all phases
- Comprehensive MLOps implementation
- Production-ready deployment
- Complete documentation and handover

### 3-Month POC Projects (AIAP)

- 3 primary agents with security review
- Rapid prototyping focus
- Feasibility validation
- Go/no-go decision support

### 4-Week Short Industry Projects (SIP)

- 2-3 agents for rapid delivery
- Focused implementation
- Basic deployment
- Knowledge transfer

### LADP Programme

- 2 agents as instructors
- LLM application focus
- Hands-on learning
- Simplified architectures

## ML-Specific Standards

### Model Development

- **Reproducibility**: Version control for code, data, and models
- **Documentation**: Comprehensive experiment tracking
- **Testing**: Unit tests for data processing and model logic
- **Validation**: Cross-validation and holdout testing

### MLOps Requirements

- **CI/CD**: Automated training and deployment pipelines
- **Monitoring**: Model performance and data drift detection
- **Versioning**: Model registry with semantic versioning
- **Rollback**: Ability to revert to previous model versions

### Security & Ethics

- **Bias Detection**: Regular fairness evaluations
- **Privacy**: Data anonymization and access controls
- **Adversarial Testing**: Robustness validation
- **Compliance**: PDPA, IMDA, and MAS guidelines

## Success Metrics

### Technical Metrics

- Model performance (accuracy, F1, AUC)
- Inference latency (<100ms for real-time)
- Training time and cost optimization
- System reliability (>99.9% uptime)

### Business Metrics

- Business KPI improvement
- ROI on ML investment
- User satisfaction scores
- Time to market reduction

### Process Metrics

- Experiment velocity
- Model deployment frequency
- Issue resolution time
- Documentation completeness

## Common ML Patterns

### Experiment Management

```python
# Structured experiment tracking
import mlflow

with mlflow.start_run():
    # Log parameters
    mlflow.log_params({"learning_rate": 0.01, "batch_size": 32})
    
    # Train model
    model = train_model(params)
    
    # Log metrics
    mlflow.log_metrics({"accuracy": 0.95, "loss": 0.05})
    
    # Log model
    mlflow.sklearn.log_model(model, "model")
```

### Model Serving

```python
# FastAPI model serving
from fastapi import FastAPI
import joblib

app = FastAPI()
model = joblib.load("model.pkl")

@app.post("/predict")
async def predict(data: dict):
    prediction = model.predict(data)
    return {"prediction": prediction}
```

### Pipeline Orchestration

```yaml
# Kubeflow pipeline example
apiVersion: argoproj.io/v1alpha1
kind: Workflow
spec:
  templates:
  - name: ml-pipeline
    steps:
    - - name: data-prep
        template: prepare-data
    - - name: train-model
        template: train
    - - name: deploy
        template: deploy-model
```

## Regulatory Compliance

### Singapore-Specific Requirements

**PDPA Compliance**:
- Personal data protection measures
- Consent management
- Data retention policies
- Breach notification procedures

**IMDA Model AI Governance**:
- AI ethics principles implementation
- Transparency and explainability
- Human oversight mechanisms
- Regular audits and reviews

**MAS FEAT Principles** (for FinTech):
- Fairness in AI decisions
- Ethics in AI development
- Accountability measures
- Transparency requirements

## Best Practices

### Development

1. **Start with Baselines**: Simple models for quick validation
2. **Version Everything**: Code, data, models, and configs
3. **Automate Early**: CI/CD from the beginning
4. **Monitor Continuously**: Track model and data drift
5. **Document Thoroughly**: Decisions, experiments, and results

### Collaboration

1. **Clear Ownership**: Define responsibilities per agent
2. **Regular Reviews**: Code, model, and ethics reviews
3. **Knowledge Sharing**: Document learnings and patterns
4. **Incremental Delivery**: Small, frequent deployments

### Production

1. **Gradual Rollouts**: A/B testing and canary deployments
2. **Fallback Strategies**: Graceful degradation plans
3. **Performance Monitoring**: Real-time metrics and alerts
4. **Regular Retraining**: Scheduled and trigger-based updates

## Technology Stack

### Core ML Frameworks
- **Deep Learning**: PyTorch, TensorFlow, JAX
- **Classical ML**: Scikit-learn, XGBoost, LightGBM
- **LLMs**: Transformers, LangChain, LlamaIndex

### MLOps Tools
- **Experiment Tracking**: MLflow, Weights & Biases, Neptune
- **Model Registry**: MLflow, Seldon, BentoML
- **Pipeline Orchestration**: Kubeflow, Airflow, Prefect
- **Model Serving**: TorchServe, TensorFlow Serving, Triton

### Infrastructure
- **Containerization**: Docker, Kubernetes
- **Cloud Platforms**: GCP (Vertex AI), AWS (SageMaker), Azure (ML Studio)
- **Data Storage**: GCS, S3, Azure Blob, MinIO
- **Monitoring**: Prometheus, Grafana, ELK Stack

## Getting Help

- **Commands**: Use `*help` to see available commands
- **Agent Switching**: Use orchestrator for role changes
- **Documentation**: Check expansion pack docs folder
- **Community**: AISG community and forums
- **Contributing**: See CONTRIBUTING.md for guidelines

This knowledge base provides the foundation for effective AI/ML engineering using the BMad-Method framework with specialized focus on production ML systems and Singapore's AI ecosystem.