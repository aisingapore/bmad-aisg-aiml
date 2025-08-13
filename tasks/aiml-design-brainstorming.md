# AI/ML Design Brainstorming Techniques Task

This task provides a comprehensive toolkit of creative brainstorming techniques specifically designed for ML system design ideation and innovative thinking. ML architects and data scientists can use these techniques to facilitate productive brainstorming sessions focused on model architecture, data strategies, and ML solutions.

## Process

### 1. Session Setup

[[LLM: Begin by understanding the ML problem context and goals. Ask clarifying questions if needed to determine the best approach for ML-specific ideation.]]

1. **Establish ML Context**
   - Understand the business problem and success metrics
   - Identify data availability and constraints
   - Determine session goals (algorithm selection vs. architecture design)
   - Clarify scope (single model vs. end-to-end system)

2. **Select Technique Approach**
   - Option A: User selects specific ML design techniques
   - Option B: ML Architect recommends techniques based on context
   - Option C: Random technique selection for creative variety
   - Option D: Progressive technique flow (problem definition to solution architecture)

### 2. ML Design Brainstorming Techniques

#### Problem Formulation Techniques

1. **"What If" ML Scenarios**
   [[LLM: Generate provocative what-if questions that challenge ML assumptions and expand thinking beyond current approaches.]]
   
   - What if we had unlimited labeled data?
   - What if we could only use unsupervised learning?
   - What if model interpretability was more important than accuracy?
   - What if we had to deploy on edge devices only?
   - What if the data distribution changed daily?

2. **ML Problem Reframing**
   [[LLM: Help user reframe the business problem as different ML tasks to reveal new solution approaches.]]
   
   - Classification → Regression → Ranking → Recommendation
   - Supervised → Semi-supervised → Unsupervised → Reinforcement
   - Batch → Streaming → Real-time → Hybrid
   - Single model → Ensemble → Multi-task → Transfer learning

3. **Constraint Inversion**
   [[LLM: Flip traditional ML constraints to reveal new possibilities.]]
   
   - What if compute was free but data was expensive?
   - What if we optimized for fairness over accuracy?
   - What if models had to be explainable to regulators?
   - What if we couldn't store any user data?

4. **Success Metric Evolution**
   [[LLM: Explore different success metrics to drive different solution approaches.]]
   - Business metrics vs. ML metrics alignment
   - Leading vs. lagging indicators
   - Multi-objective optimization approaches
   - Cost-sensitive learning considerations

#### Architecture Innovation Frameworks

1. **SCAMPER for ML Systems**
   [[LLM: Guide through each SCAMPER prompt specifically for ML architecture.]]
   
   - **S** = Substitute: What models/algorithms can be substituted?
   - **C** = Combine: What models can be ensembled or stacked?
   - **A** = Adapt: What techniques from other domains apply?
   - **M** = Modify/Magnify: What can be scaled up or down?
   - **P** = Put to other uses: What else could this model predict?
   - **E** = Eliminate: What features/steps can be removed?
   - **R** = Reverse/Rearrange: What if we changed the pipeline order?

2. **ML Complexity Spectrum**
   [[LLM: Explore different levels of model complexity and system sophistication.]]
   
   - Simple baselines: Linear models, decision trees, rules
   - Classical ML: Random forests, SVMs, gradient boosting
   - Deep learning: CNNs, RNNs, Transformers
   - Advanced architectures: GANs, VAEs, Neural ODEs
   - Hybrid systems: Combining multiple approaches

3. **Deployment Pattern Exploration**
   [[LLM: Explore different deployment architectures and serving patterns.]]
   
   - Batch prediction vs. real-time inference
   - Edge deployment vs. cloud serving
   - Model-as-a-service vs. embedded models
   - Single model vs. model cascade/ensemble
   - Static vs. online learning

#### Data Strategy Ideation

1. **Data Source Expansion**
   [[LLM: Brainstorm unconventional data sources and feature engineering approaches.]]
   
   - Internal data: Logs, transactions, user behavior
   - External data: APIs, web scraping, public datasets
   - Synthetic data: Simulation, augmentation, GANs
   - Weak supervision: Heuristics, knowledge bases, crowd-sourcing
   - Multi-modal data: Text + images + structured data

2. **Feature Engineering Creativity**
   [[LLM: Generate innovative feature engineering and representation learning ideas.]]
   
   - Domain-specific transformations
   - Interaction and polynomial features
   - Embedding and representation learning
   - Time-based and seasonal features
   - Graph and network features

3. **Data Quality Trade-offs**
   [[LLM: Explore different data quality vs. quantity trade-offs.]]
   
   - More noisy data vs. less clean data
   - Real-time approximate vs. batch accurate
   - Synthetic augmentation vs. real data collection
   - Active learning vs. random sampling

#### MLOps and System Design

1. **Monitoring-First Design**
   [[LLM: Start with monitoring requirements and work backward to system design.]]
   
   - What drift do we need to detect?
   - What failures must we catch immediately?
   - What business metrics need tracking?
   - What debugging capabilities do we need?

2. **Failure Mode Analysis**
   [[LLM: Brainstorm failure scenarios and design resilient systems.]]
   
   - Data quality degradation
   - Model performance decay
   - Infrastructure failures
   - Adversarial attacks
   - Compliance violations

3. **Scalability Patterns**
   [[LLM: Explore different approaches to scaling ML systems.]]
   
   - Horizontal vs. vertical scaling
   - Model compression and quantization
   - Caching and precomputation strategies
   - Federated and distributed learning
   - Progressive model complexity

#### Innovation Through Constraints

1. **Platform-Specific Design**
   [[LLM: Generate ideas that leverage or work around platform constraints.]]
   
   - Mobile: On-device inference, model compression
   - Edge: Distributed inference, model splitting
   - Cloud: Auto-scaling, spot instances, serverless
   - Hybrid: Edge preprocessing + cloud inference

2. **Regulatory-Driven Innovation**
   [[LLM: Use regulatory requirements as innovation catalysts.]]
   
   - PDPA compliance driving privacy-preserving ML
   - Explainability requirements driving interpretable models
   - Fairness requirements driving bias mitigation techniques
   - Audit requirements driving reproducibility solutions

### 3. ML-Specific Technique Selection

[[LLM: Help user select appropriate techniques based on their specific ML needs.]]

**For Initial Problem Definition:**
- What If ML Scenarios
- ML Problem Reframing
- Success Metric Evolution

**For Architecture Design:**
- SCAMPER for ML Systems
- ML Complexity Spectrum
- Deployment Pattern Exploration

**For Data Strategy:**
- Data Source Expansion
- Feature Engineering Creativity
- Data Quality Trade-offs

**For Production Systems:**
- Monitoring-First Design
- Failure Mode Analysis
- Scalability Patterns

**For Constrained Environments:**
- Platform-Specific Design
- Regulatory-Driven Innovation
- Constraint Inversion

### 4. ML Design Session Flow

[[LLM: Guide the brainstorming session with appropriate pacing for ML exploration.]]

1. **Problem Understanding Phase** (10-15 min)
   - Clarify business objectives and constraints
   - Identify available data and resources
   - Define success metrics and requirements

2. **Divergent Exploration** (25-35 min)
   - Generate many ML approaches and architectures
   - Use expansion and reframing techniques
   - Encourage unconventional solutions

3. **Technical Filtering** (15-20 min)
   - Assess technical feasibility
   - Consider data and resource constraints
   - Evaluate implementation complexity

4. **Solution Synthesis** (15-20 min)
   - Combine complementary approaches
   - Design end-to-end systems
   - Plan validation strategies

### 5. ML Design Output Format

[[LLM: Present brainstorming results in a format useful for ML development.]]

**Session Summary:**
- Techniques used and focus areas
- Total solutions/approaches generated
- Key insights and patterns identified

**ML Solution Categories:**

1. **Model Architectures** - Algorithm and model design options
2. **Data Strategies** - Data collection and feature engineering approaches
3. **Training Approaches** - Optimization and learning strategies
4. **Deployment Architectures** - Serving and scaling patterns
5. **MLOps Solutions** - Monitoring and maintenance approaches

**Feasibility Assessment:**

**Prototype-Ready Ideas:**
- Solutions that can be tested immediately
- Required data and resources available
- Clear evaluation metrics defined

**Research-Required Ideas:**
- Approaches needing investigation
- Data collection or labeling required
- Technical feasibility studies needed

**Future Innovation Pipeline:**
- Ideas requiring new technology
- Long-term research directions
- Strategic capability building

**Next Steps:**
- Which approaches to prototype first
- Required experiments and validations
- Data collection and preparation needs
- Architecture documentation requirements

## ML-Specific Considerations

### Algorithm and Model Selection
- Always consider simple baselines first
- Balance model complexity with interpretability
- Consider ensemble and hybrid approaches
- Think about transfer learning opportunities

### Data and Feature Engineering
- Focus on data quality over quantity initially
- Consider feature importance and selection
- Plan for data versioning and lineage
- Design for data drift detection

### Production Readiness
- Design for monitoring from the start
- Consider model retraining strategies
- Plan for A/B testing and gradual rollouts
- Think about debugging and explainability

### Singapore Context
- Consider PDPA and data privacy requirements
- Think about multi-language support needs
- Plan for regional deployment strategies
- Consider local infrastructure constraints

## Important Notes for ML Design Sessions

- Start with business problem, not technology
- Consider the full ML lifecycle, not just training
- Balance innovation with practical constraints
- Document assumptions and risks clearly
- Plan for model maintenance and updates
- Consider ethical implications early
- Design for monitoring and observability
- Think about team skills and capabilities
- Consider buy vs. build for components
- Plan for regulatory compliance from the start