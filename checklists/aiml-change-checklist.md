# AI/ML Change Navigation Checklist

**Purpose:** To systematically guide the ML team through analysis and planning when a significant change (model drift, performance degradation, data quality issue, compliance requirement) is identified during ML system operation.

**Instructions:** Review each item with the user. Mark `[x]` for completed/confirmed, `[N/A]` if not applicable, or add notes for discussion points.

[[LLM: INITIALIZATION INSTRUCTIONS - ML CHANGE NAVIGATION

Changes in ML systems are inevitable - model drift, data distribution shifts, performance degradation, and new requirements are part of the ML lifecycle.

Before proceeding, understand:
1. This checklist is for SIGNIFICANT changes affecting model performance or system architecture
2. Minor hyperparameter tweaks don't require this process
3. The goal is to maintain system reliability while adapting to new realities
4. Business continuity and model performance are paramount

Required context:
- The triggering issue (drift metrics, performance alerts, compliance notice)
- Current system state (model version, recent deployments, performance metrics)
- Access to ML architecture docs, model cards, and monitoring dashboards
- Understanding of business SLAs and compliance requirements

APPROACH:
This is an interactive process. Discuss technical implications, business impact, and risk mitigation. The user makes final decisions, but provide expert ML/MLOps guidance.

REMEMBER: ML systems evolve continuously. Changes often lead to better models and more robust systems.]]

---

## 1. Understand the Trigger & Context

[[LLM: Start by understanding the ML-specific issue. Ask technical questions:
- What metrics triggered this? (accuracy drop, latency increase, drift score)
- Is this gradual degradation or sudden failure?
- Can we pinpoint when the issue started?
- What monitoring data do we have?
- Is this affecting all predictions or specific segments?

Focus on measurable impacts and data-driven evidence.]]

- [ ] **Identify Triggering Element:** Clearly identify the ML component/metric revealing the issue
- [ ] **Define the Issue:** Articulate the core problem precisely
  - [ ] Model performance degradation (accuracy, F1, AUC)?
  - [ ] Data drift (feature drift, label drift, concept drift)?
  - [ ] System performance issue (latency, throughput)?
  - [ ] Compliance/regulatory requirement change?
  - [ ] Data quality degradation?
  - [ ] Security vulnerability or adversarial attack?
- [ ] **Assess Business Impact:** Document specific business metrics affected
- [ ] **Gather Technical Evidence:** Note monitoring data, drift scores, performance metrics, error logs

## 2. ML System Impact Assessment

[[LLM: ML systems have complex dependencies. Evaluate systematically:
1. Can we retrain with existing data?
2. Do we need new features or data sources?
3. Are downstream systems affected?
4. Does this affect our SLAs?

Consider both technical and business impacts.]]

- [ ] **Analyze Current Model:**
  - [ ] Can the model be retrained with current data?
  - [ ] Does the model architecture need changes?
  - [ ] Are hyperparameters still optimal?
- [ ] **Analyze Data Pipeline:**
  - [ ] Review all data sources for quality issues
  - [ ] Are feature engineering pipelines affected?
  - [ ] Do data validation rules need updating?
  - [ ] Is the feature store impacted?
- [ ] **Analyze Downstream Systems:**
  - [ ] Which services consume model predictions?
  - [ ] Are decision thresholds still appropriate?
  - [ ] Do monitoring alerts need adjustment?
  - [ ] Are dependent systems resilient to changes?
- [ ] **Summarize System Impact:** Document effects on ML pipeline and dependent systems

## 3. ML Artifact Conflict & Impact Analysis

[[LLM: ML documentation drives reproducibility. Check each artifact:
1. Does this invalidate model assumptions?
2. Are performance benchmarks still valid?
3. Do SLAs need renegotiation?
4. Are compliance certifications affected?

Missing conflicts cause production issues later.]]

- [ ] **Review Model Documentation:**
  - [ ] Does the issue conflict with model card assumptions?
  - [ ] Are documented performance metrics still achievable?
  - [ ] Do model limitations need updating?
  - [ ] Are ethical considerations affected?
- [ ] **Review MLOps Architecture:**
  - [ ] Does the issue conflict with pipeline design?
  - [ ] Are deployment strategies still appropriate?
  - [ ] Do monitoring thresholds need adjustment?
  - [ ] Are rollback procedures adequate?
- [ ] **Review Performance SLAs:**
  - [ ] Are latency requirements still achievable?
  - [ ] Do accuracy targets need revision?
  - [ ] Are throughput commitments realistic?
  - [ ] Do we need to renegotiate SLAs?
- [ ] **Review Compliance Documentation:**
  - [ ] Does this affect PDPA compliance?
  - [ ] Are IMDA guidelines still met?
  - [ ] Do audit trails need enhancement?
  - [ ] Is model explainability impacted?
- [ ] **Summarize Artifact Impact:** List all ML documents requiring updates

## 4. Path Forward Evaluation

[[LLM: Present ML-specific solutions with trade-offs:
1. What's the expected performance improvement?
2. How long will retraining/deployment take?
3. What's the business risk during transition?
4. Are there quick wins vs long-term fixes?
5. What's the rollback strategy?

Be specific about ML implementation details and timelines.]]

- [ ] **Option 1: Model Retraining:**
  - [ ] Can performance be restored through retraining?
    - [ ] With existing data?
    - [ ] With new/additional data?
    - [ ] With different sampling strategy?
    - [ ] With updated hyperparameters?
  - [ ] Define retraining approach and timeline
  - [ ] Estimate performance improvement potential
- [ ] **Option 2: Feature Engineering:**
  - [ ] Can new features address the issue?
  - [ ] Identify specific features to add/modify/remove
  - [ ] Define feature engineering pipeline changes
  - [ ] Assess impact on inference latency
- [ ] **Option 3: Architecture Change:**
  - [ ] Would a different model architecture help?
  - [ ] Identify specific architectural changes:
    - [ ] Different algorithm?
    - [ ] Ensemble approach?
    - [ ] Transfer learning?
    - [ ] Online learning?
  - [ ] Estimate development and deployment effort
- [ ] **Option 4: Data Strategy Change:**
  - [ ] Do we need new data sources?
  - [ ] Should we change data collection methods?
  - [ ] Do we need data augmentation?
  - [ ] Should we implement active learning?
- [ ] **Select Recommended Path:** Choose based on impact vs effort analysis

## 5. ML Change Proposal Components

[[LLM: The proposal must include ML-specific details:
1. Performance metrics (before/after projections)
2. Training and deployment timeline
3. Resource requirements (compute, data, team)
4. Risk mitigation strategies
5. Success criteria and validation approach

Make it actionable for ML engineers and data scientists.]]

(Ensure all points from previous sections are captured)

- [ ] **Technical Issue Summary:** ML problem with specific metrics
- [ ] **System Impact Summary:** Affected ML components and dependencies
- [ ] **Performance Projections:** Expected improvements from chosen solution
- [ ] **Implementation Plan:** ML-specific technical approach
  - [ ] Data preparation requirements
  - [ ] Training infrastructure needs
  - [ ] Experiment tracking setup
  - [ ] Validation methodology
- [ ] **Deployment Strategy:** Rollout approach
  - [ ] A/B testing plan
  - [ ] Canary deployment percentage
  - [ ] Monitoring enhancements
  - [ ] Rollback triggers
- [ ] **Resource Requirements:** Compute, storage, and team needs
- [ ] **Risk Assessment:** Technical and business risks with mitigation
- [ ] **Timeline:** Detailed schedule with milestones

## 6. Validation & Testing Strategy

[[LLM: ML changes require rigorous validation. Define:
1. How will we validate the fix works?
2. What metrics prove success?
3. How do we test edge cases?
4. What's the A/B testing approach?
5. How do we ensure no regression?

Be specific about validation methodology and success criteria.]]

- [ ] **Offline Validation:**
  - [ ] Historical data backtesting approach
  - [ ] Cross-validation strategy
  - [ ] Performance metrics and thresholds
  - [ ] Bias and fairness evaluation
- [ ] **Online Validation:**
  - [ ] A/B testing configuration
  - [ ] Shadow mode deployment
  - [ ] Gradual rollout strategy
  - [ ] Business metric monitoring
- [ ] **Edge Case Testing:**
  - [ ] Outlier handling validation
  - [ ] Adversarial testing approach
  - [ ] Data quality degradation scenarios
  - [ ] System failure recovery testing
- [ ] **Regression Testing:**
  - [ ] Existing functionality validation
  - [ ] Performance benchmark comparison
  - [ ] Integration testing scope
  - [ ] End-to-end testing scenarios

## 7. Singapore Compliance Considerations

[[LLM: Singapore has specific AI governance requirements. Ensure:
1. PDPA compliance is maintained
2. IMDA guidelines are followed
3. MAS FEAT principles upheld (for FinTech)
4. Audit trails are comprehensive
5. Model explainability is preserved

Address any regulatory impacts explicitly.]]

- [ ] **Data Privacy (PDPA):**
  - [ ] Personal data handling changes documented
  - [ ] Consent requirements still met
  - [ ] Data retention policies followed
  - [ ] Cross-border data transfer compliance
- [ ] **AI Governance (IMDA):**
  - [ ] Model transparency maintained
  - [ ] Bias mitigation measures in place
  - [ ] Human oversight mechanisms functional
  - [ ] Accountability framework updated
- [ ] **Financial Services (MAS FEAT):**
  - [ ] Fairness principles upheld
  - [ ] Ethics guidelines followed
  - [ ] Accountability measures documented
  - [ ] Transparency requirements met
- [ ] **Audit & Documentation:**
  - [ ] Change logs comprehensive
  - [ ] Decision rationale documented
  - [ ] Model lineage tracked
  - [ ] Compliance artifacts updated

## 8. Final Review & Handoff

[[LLM: ML changes require careful orchestration. Before concluding:
1. Are success metrics clearly defined?
2. Is the implementation plan detailed enough?
3. Do we have rollback procedures?
4. Are all stakeholders informed?
5. Is monitoring enhanced for the change?

Get explicit approval on approach and timeline.

FINAL REPORT:
Provide an ML-focused summary:
- Issue identification and root cause
- Chosen solution with expected outcomes
- Implementation approach and timeline
- Validation and monitoring plan
- Risk mitigation strategies

Keep it technically precise and business-aware.]]

- [ ] **Review Checklist:** Confirm all ML aspects discussed
- [ ] **Review Change Proposal:** Ensure implementation details are clear
- [ ] **Success Criteria:** Define measurable success metrics
- [ ] **Stakeholder Approval:** Obtain approval from:
  - [ ] Business stakeholders
  - [ ] ML/Data Science team
  - [ ] MLOps/Platform team
  - [ ] Compliance/Legal team
- [ ] **Handoff Preparation:** Ensure teams have:
  - [ ] Technical specifications
  - [ ] Resource allocations
  - [ ] Timeline commitments
  - [ ] Success metrics
  - [ ] Monitoring dashboards

---

## Change Categories Reference

### Model Drift
- Feature drift: Input distribution changes
- Label drift: Output distribution changes
- Concept drift: Relationship between features and labels changes
- Response: Retrain, adapt features, or change architecture

### Performance Degradation
- Accuracy decline over time
- Latency increase due to load
- Throughput bottlenecks
- Response: Optimize, scale, or redesign

### Data Quality Issues
- Missing data increases
- Data schema changes
- Noise in labels
- Response: Fix pipeline, add validation, or change strategy

### Compliance Changes
- New regulations
- Updated guidelines
- Audit findings
- Response: Adjust processes, enhance documentation, or modify models