# Create AI/ML Story Task

## Purpose

To identify the next logical ML engineering story based on project progress and epic definitions, and then to prepare a comprehensive, self-contained, and actionable story file using the ML Story Template. This task ensures the story is enriched with all necessary technical context, ML-specific requirements, and acceptance criteria, making it ready for efficient implementation by an ML Engineer Agent with minimal need for additional research.

## SEQUENTIAL Task Execution (Do not proceed until current Task is complete)

### 0. Load Core Configuration and Check Workflow

- Load `{root}/config.yaml` from the project root
- If the file does not exist, HALT and inform the user: "core-config.yaml not found. This file is required for story creation."
- Extract key configurations: `devStoryLocation`, `aiml-design-document.*`, `aiml-architecture.*`, `workflow.*`

### 1. Identify Next Story for Preparation

#### 1.1 Locate Epic Files and Review Existing Stories

- Based on configuration, locate user-stories files (ML project phases or feature sets)
- If `devStoryLocation` has story files, load the highest `User Story {storyNum}.md`.story.md` file
- **If highest story exists:**
  - Select next sequential story in the user-stories document
- **If no story files exist:** The next story is ALWAYS User Story 1 (first story)
- Announce the identified story to the user: "Identified next story for preparation: User Story {storyNum}"

### 2. Gather Story Requirements and Previous Story Context

- Extract story requirements from the identified epic file or project documentation
- If previous story exists, review ML Engineer Record sections for:
  - Model performance achievements and limitations
  - Data pipeline implementation decisions
  - MLOps setup and deployment configurations
  - Performance optimization techniques applied
  - Monitoring and alerting configurations
- Extract relevant insights that inform the current story's preparation

### 3. Gather ML Architecture Context

#### 3.1 Determine Architecture Reading Strategy

- Read ML architecture documents based on configuration
- Follow structured reading order based on story type

#### 3.2 Read Architecture Documents Based on Story Type

**For ALL ML Stories:** aiml-architecture.md, high-level-architecture.md

**For Data Engineering Stories, additionally:** data-architecture.md, data-strategy.md

**For Model Development Stories, additionally:** model-architecture.md, experimentation-framework.md

**For MLOps/Deployment Stories, additionally:** deployment-architecture.md, mlops-desployment.md

**For Monitoring/Observability Stories, additionally:** monitoring-operations.md

**For LLM/RAG Stories, additionally:** llm-architecture.md, rag-pipeline-design.md, prompt-engineering-patterns.md, vector-database-setup.md

#### 3.3 Extract Story-Specific Technical Details

Extract ONLY information directly relevant to implementing the current story. Do NOT invent new patterns, algorithms, or standards not in the source documents.

Extract:
- Specific ML frameworks and libraries the story will use
- Python package dependencies and versions
- Data pipeline components and orchestration tools
- Model architecture specifications and hyperparameters
- Evaluation metrics and performance thresholds
- MLOps tools and deployment configurations
- Monitoring metrics and alerting thresholds
- Resource requirements (GPU, memory, storage)
- Performance targets (latency, throughput, accuracy)
- Compliance requirements (PDPA, fairness, explainability)

ALWAYS cite source documents: `[Source: ml-architecture/{filename}.md#{section}]`

### 4. ML-Specific Technical Analysis

#### 4.1 Framework and Library Analysis

- Identify ML frameworks required (PyTorch, TensorFlow, JAX, Scikit-learn)
- Document framework versions and compatibility requirements
- Note framework-specific APIs and patterns being used
- List additional ML libraries (transformers, lightgbm, xgboost)
- Identify data processing libraries (pandas, numpy, polars)

#### 4.2 Data Pipeline Planning

- Identify data sources and ingestion methods
- List data transformation and feature engineering steps
- Document data validation and quality checks
- Specify data versioning and lineage tracking
- Note data storage and retrieval patterns

#### 4.3 Model Development Architecture

- Define model architecture and algorithm selection
- Specify training configurations and hyperparameters
- Document experiment tracking setup
- Identify evaluation metrics and validation strategies
- Note model versioning and registry requirements

#### 4.4 MLOps and Deployment Planning

- List containerization requirements (Docker specifications)
- Define CI/CD pipeline stages and triggers
- Document model serving architecture (REST, gRPC, batch)
- Specify monitoring and logging requirements
- Note rollback and A/B testing strategies

### 5. Populate Story Template with Full Context

- Create new story file: `{devStoryLocation}/User Story {storyNum}.md` using ML Story Template
- Fill in basic story information: Title, Status (Draft), Story statement, Acceptance Criteria
- **`Dev Notes` section (CRITICAL):**
  - CRITICAL: This section MUST contain ONLY information extracted from ML architecture documents. NEVER invent technical details.
  - Include ALL relevant technical details from Steps 2-4, organized by category:
    - **Previous Story Insights**: Key learnings from previous story implementation
    - **Framework Dependencies**: ML frameworks, versions, configurations [with source references]
    - **Data Pipeline Specs**: Data sources, transformations, validation [with source references]
    - **Model Architecture**: Algorithm, hyperparameters, training config [with source references]
    - **Evaluation Strategy**: Metrics, validation approach, baselines [with source references]
    - **MLOps Configuration**: Deployment, monitoring, rollback [with source references]
    - **Performance Targets**: Latency, accuracy, resource usage [with source references]
    - **Compliance Requirements**: PDPA, fairness, explainability [with source references]
  - Every technical detail MUST include its source reference: `[Source: ml-architecture/{filename}.md#{section}]`
  - If information for a category is not found in the architecture docs, explicitly state: "No specific guidance found in architecture docs"
- **`Tasks / Subtasks` section:**
  - Generate detailed, sequential list of technical tasks based ONLY on: Epic Requirements, Story AC, Reviewed Architecture Information
  - Include ML-specific tasks:
    - Data exploration and validation
    - Feature engineering implementation
    - Model training and evaluation
    - Hyperparameter optimization
    - Model deployment and testing
    - Monitoring setup and validation
    - Performance profiling and optimization
  - Each task must reference relevant architecture documentation
  - Include testing as explicit subtasks
  - Link tasks to ACs where applicable (e.g., `Task 1 (AC: 1, 3)`)
- Add notes on ML project structure alignment or discrepancies found

### 6. Story Draft Completion and Review

- Review all sections for completeness and accuracy
- Verify all source references are included for technical details
- Ensure ML-specific requirements are comprehensive:
  - All data sources documented
  - Model architecture specified
  - Evaluation metrics defined
  - Deployment strategy clear
  - Monitoring approach defined
- Update status to "Draft" and save the story file
- Execute appropriate ML checklist for validation
- Provide summary to user including:
  - Story created: `{devStoryLocation}/User Story {storyNum}.md`
  - Status: Draft
  - Key ML components and frameworks included
  - Data pipeline modifications required
  - Model architecture and training approach
  - MLOps and deployment strategy
  - Any deviations or conflicts noted between requirements and architecture
  - Checklist Results
  - Next steps: For Complex stories, suggest the user carefully review the story draft and also optionally have the ml-engineer run the task `{root}/tasks/validate-aiml-story`
  - If yolo mode run task `{root}/tasks/create-next-aiml-story` automatically.
  - If no more user stories left to create. End Run.
### 7. ML-Specific Validation

Before finalizing, ensure:
- [ ] All required ML frameworks are documented with versions
- [ ] Data pipeline stages are clearly defined
- [ ] Model architecture is completely specified
- [ ] Training configurations are comprehensive
- [ ] Evaluation metrics and thresholds are defined
- [ ] Deployment approach is specified
- [ ] Monitoring and alerting rules are documented
- [ ] Resource requirements are estimated
- [ ] Performance targets are measurable
- [ ] Compliance requirements are addressed
- [ ] Testing strategy covers unit, integration, and model validation

## Singapore AI/ML Context

This task ensures ML engineering stories are immediately actionable and enable efficient AI-driven development while considering:
- Singapore's PDPA requirements for data privacy
- IMDA Model AI Governance Framework compliance
- MAS FEAT principles for financial services
- Local cloud infrastructure (GovTech, local providers)
- Multi-language support requirements
- Regional deployment considerations