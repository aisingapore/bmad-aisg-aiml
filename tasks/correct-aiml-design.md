# Correct Course Task - AI/ML Engineering

## Purpose

- Guide a structured response to ML project change triggers using the ML-specific change checklist
- Analyze the impacts of changes on model performance, data pipelines, and deployment
- Explore ML-specific solutions (e.g., model retraining, architecture changes, data augmentation)
- Draft specific, actionable proposed updates to affected ML artifacts (e.g., model specs, MLOps configs)
- Produce a consolidated "ML Engineering Change Proposal" document for review and approval
- Ensure clear handoff path for changes requiring fundamental model redesign or data strategy updates

## Instructions

### 1. Initial Setup & Mode Selection

- **Acknowledge Task & Inputs:**
  - Confirm with the user that the "ML Engineering Correct Course Task" is being initiated
  - Verify the change trigger (e.g., model drift, new data requirements, performance degradation, compliance issue)
  - Confirm access to relevant ML artifacts:
    - ML Architecture documentation
    - Model specifications and evaluation reports
    - Data pipeline configurations
    - MLOps pipeline definitions
    - Performance benchmarks and SLAs
    - Current sprint's ML stories and epics
    - Monitoring dashboards and alerts
  - Confirm access to ML change checklist

- **Establish Interaction Mode:**
  - Ask the user their preferred interaction mode:
    - **"Incrementally (Default & Recommended):** Work through the ML change checklist section by section, discussing findings and drafting changes collaboratively. Best for complex model or pipeline changes."
    - **"YOLO Mode (Batch Processing):** Conduct batched analysis and present consolidated findings. Suitable for straightforward retraining or hyperparameter adjustments."
  - Confirm the selected mode and inform: "We will now use the ML change checklist to analyze the change and draft proposed updates specific to our ML/AI engineering context."

### 2. Execute ML Engineering Checklist Analysis

- Systematically work through the ML change checklist sections:

  1. **Change Context & ML Impact**
  2. **Model/Pipeline Impact Analysis**
  3. **Data & Feature Engineering Evaluation**
  4. **Performance & Resource Assessment**
  5. **Path Forward Recommendation**

- For each checklist section:
  - Present ML-specific prompts and considerations
  - Analyze impacts on:
    - Model accuracy and performance metrics
    - Data pipeline dependencies
    - Feature engineering processes
    - Training/retraining schedules
    - Inference latency and throughput
    - Resource utilization (GPU, memory, storage)
    - Monitoring and alerting systems
  - Discuss findings with clear technical context
  - Record status: `[x] Addressed`, `[N/A]`, `[!] Further Action Needed`
  - Document ML-specific decisions and constraints

### 3. Draft ML-Specific Proposed Changes

Based on the analysis and agreed path forward:

- **Identify affected ML artifacts requiring updates:**
  - Model architecture specifications
  - Data pipeline configurations (ingestion, processing, feature engineering)
  - MLOps pipeline definitions (CI/CD, training, deployment)
  - Experiment tracking configurations
  - Model registry entries
  - Monitoring and alerting rules
  - Performance benchmarks and SLAs

- **Draft explicit changes for each artifact:**
  - **ML Stories:** Revise story text, ML-specific acceptance criteria, evaluation metrics
  - **Model Specs:** Update architecture diagrams, hyperparameters, training configs
  - **Pipeline Configs:** Modify DAGs, data transformations, feature engineering steps
  - **MLOps Updates:** Change deployment strategies, rollback procedures, A/B test configs
  - **Monitoring Rules:** Adjust drift detection thresholds, performance alerts, data quality checks
  - **Documentation:** Update model cards, experiment logs, decision records

- **Include ML-specific details:**
  - Algorithm selection rationale
  - Hyperparameter optimization results
  - Cross-validation strategies
  - Evaluation metric definitions
  - Bias and fairness assessments
  - Resource utilization projections

### 4. Generate "ML Engineering Change Proposal"

- Create a comprehensive proposal document containing:

  **A. Change Summary:**
  - Original issue (drift, performance, data quality, compliance)
  - ML components affected
  - Business impact and urgency
  - Chosen solution approach

  **B. Technical ML Impact Analysis:**
  - Model performance implications (accuracy, F1, AUC changes)
  - Data pipeline modifications needed
  - Retraining requirements and schedule
  - Computational resource changes
  - Deployment rollout strategy

  **C. Specific Proposed Edits:**
  - For each ML story: "Change Story ML-X.Y from: [old] To: [new]"
  - For model specs: "Update Model Architecture Section X: [changes]"
  - For pipelines: "Modify Pipeline Stage [name]: [updates]"
  - For MLOps: "Change Deployment Config: [old_value] to [new_value]"

  **D. Implementation Considerations:**
  - Experiment tracking approach
  - A/B testing strategy
  - Rollback procedures
  - Performance monitoring plan
  - Data versioning requirements

### 5. Finalize & Determine Next Steps

- Obtain explicit approval for the "ML Engineering Change Proposal"
- Provide the finalized document to the user

- **Based on change scope:**
  - **Minor adjustments (can be handled in current sprint):**
    - Confirm task completion
    - Suggest handoff to ML Engineer agent for implementation
    - Note any required model validation steps
  - **Major changes (require replanning):**
    - Clearly state need for deeper technical review
    - Recommend engaging ML Architect or Data Scientist
    - Provide proposal as input for architecture revision
    - Flag any SLA/performance impacts

## Output Deliverables

- **Primary:** "ML Engineering Change Proposal" document containing:
  - ML-specific change analysis
  - Model and pipeline impact assessment
  - Performance and resource considerations
  - Clearly drafted updates for all affected ML artifacts
  - Implementation guidance and constraints

- **Secondary:** Annotated ML change checklist showing:
  - Technical decisions made
  - Performance trade-offs considered
  - Data quality accommodations
  - ML-specific implementation notes

## ML-Specific Considerations

### Model Lifecycle Management
- Version control for models and data
- Experiment tracking and reproducibility
- Model registry updates
- Feature store modifications

### Performance Optimization
- Inference latency requirements
- Training time constraints
- Resource utilization targets
- Cost optimization strategies

### Data Management
- Data versioning and lineage
- Feature engineering pipeline updates
- Data quality monitoring
- Privacy and compliance (PDPA)

### Deployment Strategies
- Blue-green deployments for models
- Canary releases with traffic splitting
- Shadow mode testing
- Gradual rollout with monitoring

### Singapore Context
- PDPA compliance requirements
- IMDA AI governance guidelines
- MAS FEAT principles (for FinTech)
- Local infrastructure considerations