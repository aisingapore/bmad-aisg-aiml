# Validate AI/ML Story Task

## Purpose

To comprehensively validate an ML engineering story draft before implementation begins, ensuring it contains all necessary ML-specific technical context, data requirements, model specifications, and deployment details. This specialized validation prevents technical debt, ensures ML development readiness, and validates ML-specific acceptance criteria and testing approaches.

## SEQUENTIAL Task Execution (Do not proceed until current Task is complete)

### 0. Load Core Configuration and Inputs

- Load `{root}/core-config.yaml` from the project root
- If the file does not exist, HALT and inform the user: "core-config.yaml not found. This file is required for story validation."
- Extract key configurations: `devStoryLocation`, `mlArchitecture.*`, `dataArchitecture.*`, `workflow.*`
- Identify and load the following inputs:
  - **Story file**: The drafted ML story to validate (provided by user or discovered in `devStoryLocation`)
  - **Parent epic**: The epic containing this story's requirements
  - **Architecture documents**: ML architecture, data architecture, MLOps architecture
  - **ML story template**: Template for completeness validation

### 1. ML Story Template Completeness Validation

- Load ML story template and extract all required sections
- **Missing sections check**: Compare story sections against ML story template sections to verify all ML-specific sections are present:
  - Data Requirements & Sources
  - Model Architecture & Algorithms
  - Training Configuration
  - Evaluation Metrics & Baselines
  - MLOps & Deployment Strategy
  - Monitoring & Alerting
  - Performance Requirements
  - Testing Strategy (unit, integration, model validation)
- **Placeholder validation**: Ensure no template placeholders remain unfilled
- **ML-specific sections**: Verify presence of ML development specific sections
- **Structure compliance**: Verify story follows ML story template structure and formatting

### 2. Data Requirements and Pipeline Validation

- **Data source clarity**: Are data sources, schemas, and access methods clearly specified?
- **Data quality requirements**: Are data validation rules and quality metrics defined?
- **Feature engineering**: Are feature transformations and engineering steps documented?
- **Data versioning**: Is data versioning and lineage tracking approach specified?
- **Privacy compliance**: Are PDPA and data privacy requirements addressed?
- **Data volume estimates**: Are data sizes and processing requirements estimated?
- **Pipeline architecture**: Is the data pipeline architecture clearly defined?

### 3. Model Architecture and Training Validation

- **Algorithm selection**: Is the model algorithm/architecture justified and specified?
- **Hyperparameters**: Are hyperparameters and optimization strategies defined?
- **Training configuration**: Are batch sizes, epochs, learning rates documented?
- **Compute requirements**: Are GPU/CPU requirements and memory needs estimated?
- **Framework versions**: Are ML framework versions (PyTorch, TensorFlow) specified?
- **Reproducibility**: Are random seeds and reproducibility measures defined?
- **Experiment tracking**: Is experiment tracking setup (MLflow, W&B) specified?

### 4. Evaluation and Performance Validation

- **Evaluation metrics**: Are appropriate metrics (accuracy, F1, AUC, etc.) defined?
- **Baselines**: Are baseline models or performance thresholds specified?
- **Validation strategy**: Is the validation approach (cross-validation, holdout) clear?
- **Performance targets**: Are latency, throughput, and accuracy targets defined?
- **Business metrics**: Are business KPIs and their relationship to ML metrics clear?
- **A/B testing**: Is the A/B testing or gradual rollout strategy defined?
- **Bias evaluation**: Are fairness and bias evaluation approaches specified?

### 5. MLOps and Deployment Validation

- **Deployment architecture**: Is the serving architecture (REST, gRPC, batch) specified?
- **Containerization**: Are Docker configurations and requirements defined?
- **CI/CD pipeline**: Are training and deployment pipeline stages specified?
- **Model registry**: Is model versioning and registry approach defined?
- **Rollback strategy**: Are rollback procedures and triggers specified?
- **Resource scaling**: Are auto-scaling and resource management approaches defined?
- **Infrastructure as Code**: Are Terraform/CloudFormation requirements specified?

### 6. Monitoring and Alerting Validation

- **Model monitoring**: Are drift detection and performance monitoring specified?
- **Data monitoring**: Are data quality and distribution monitoring defined?
- **System monitoring**: Are infrastructure and resource monitoring specified?
- **Alerting rules**: Are alert thresholds and escalation procedures defined?
- **Dashboard requirements**: Are monitoring dashboard specifications clear?
- **Logging strategy**: Are logging requirements and retention policies specified?
- **Debugging tools**: Are model debugging and interpretation tools identified?

### 7. Testing Strategy Validation

- **Unit tests**: Are unit tests for data processing and model components specified?
- **Integration tests**: Are pipeline integration tests defined?
- **Model validation tests**: Are model performance validation tests specified?
- **Load testing**: Are performance and load testing approaches defined?
- **Data validation tests**: Are data quality and schema validation tests specified?
- **Security testing**: Are security and adversarial testing approaches defined?
- **Smoke tests**: Are deployment smoke tests and health checks specified?

### 8. Security and Compliance Validation

- **Data privacy**: Are PDPA compliance measures specified?
- **Model security**: Are adversarial robustness measures defined?
- **Access control**: Are authentication and authorization requirements clear?
- **Audit logging**: Are audit trail and compliance logging requirements specified?
- **Encryption**: Are data encryption (at rest/in transit) requirements defined?
- **Regulatory compliance**: Are IMDA/MAS guidelines addressed (if applicable)?
- **Ethical considerations**: Are bias mitigation and fairness measures specified?

### 9. Development Task Sequence Validation

- **Task dependencies**: Are task dependencies and sequencing logical?
- **Data pipeline first**: Are data pipeline tasks properly prioritized?
- **Incremental validation**: Are validation checkpoints throughout development?
- **Integration points**: Are integration tasks properly sequenced?
- **Testing integration**: Are tests integrated throughout development?
- **Documentation tasks**: Are documentation tasks included?

### 10. Anti-Hallucination Verification

- **Framework accuracy**: Every ML framework reference must be verified
- **Algorithm validity**: All algorithm specifications must be valid
- **Metric appropriateness**: All evaluation metrics must be appropriate for the problem
- **Performance realism**: All performance targets must be realistic
- **Resource estimates**: All resource requirements must be reasonable
- **Tool availability**: All specified tools must be available/approved

### 11. ML Development Agent Implementation Readiness

- **Technical completeness**: Can the story be implemented without additional research?
- **Data accessibility**: Are all data sources accessible and documented?
- **Environment setup**: Are development environment requirements clear?
- **Dependency clarity**: Are all dependencies and versions specified?
- **Testing executability**: Can all tests be implemented and executed?
- **Deployment readiness**: Is the deployment process fully specified?

### 12. Generate ML Story Validation Report

Provide a structured validation report including:

#### Story Template Compliance Issues
- Missing ML-specific sections
- Unfilled placeholders
- Structural formatting issues

#### Critical ML Issues (Must Fix - Story Blocked)
- Missing essential data requirements
- Undefined model architecture
- Incomplete evaluation criteria
- Missing MLOps specifications
- Unrealistic performance targets

#### ML-Specific Should-Fix Issues (Important Quality Improvements)
- Unclear data pipeline specifications
- Incomplete monitoring requirements
- Missing experiment tracking details
- Insufficient testing coverage
- Incomplete security measures

#### ML Nice-to-Have Improvements (Optional Enhancements)
- Additional performance optimization context
- Enhanced debugging capabilities
- Extended documentation
- Additional evaluation metrics
- Supplementary monitoring dashboards

#### Anti-Hallucination Findings
- Unverifiable ML framework claims
- Invalid algorithm specifications
- Inappropriate metric selections
- Unrealistic performance targets
- Non-existent tool references

#### ML System Validation
- **Data Pipeline Assessment**: Completeness of data specifications
- **Model Architecture Review**: Adequacy of model design
- **MLOps Readiness**: Deployment and monitoring preparedness
- **Performance Feasibility**: Realism of performance targets
- **Compliance Check**: PDPA and regulatory compliance

#### Final ML Development Assessment
- **GO**: Story is ready for ML implementation
- **NO-GO**: Story requires fixes before implementation
- **ML Readiness Score**: 1-10 scale based on completeness
- **Development Confidence Level**: High/Medium/Low
- **Risk Assessment**: Technical, data, and deployment risks
- **Estimated Effort**: Story points or time estimate

#### Recommended Next Steps

Based on validation results, provide specific recommendations for:
- Data preparation and exploration needs
- Model architecture refinements
- MLOps setup requirements
- Testing strategy improvements
- Monitoring enhancements
- Documentation additions

## Singapore Context Considerations

### Regulatory Compliance
- PDPA (Personal Data Protection Act) requirements
- IMDA Model AI Governance Framework
- MAS FEAT principles (for financial services)
- Healthcare data regulations (if applicable)

### Local Infrastructure
- Singapore cloud regions and data residency
- GovTech cloud considerations
- Local CDN and edge requirements
- Network latency considerations

### Multi-language Support
- Support for English, Chinese, Malay, Tamil
- Language model considerations
- Localization requirements
- Cultural sensitivity in model outputs

This validation ensures ML stories are production-ready and aligned with Singapore's AI governance standards.