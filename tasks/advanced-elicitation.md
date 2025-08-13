# Advanced ML/AI Design Elicitation Task

## Purpose

- Provide optional reflective and brainstorming actions to enhance ML system design content quality
- Enable deeper exploration of model architecture and data pipeline decisions through structured elicitation
- Support iterative refinement through multiple AI/ML engineering perspectives  
- Apply ML-specific critical thinking to architecture and implementation decisions

## Task Instructions

### 1. ML Design Context and Review

[[LLM: When invoked after outputting an ML design section:

1. First, provide a brief 1-2 sentence summary of what the user should look for in the section just presented, with ML-specific focus (e.g., "Please review the model architecture for scalability and performance. Pay special attention to data pipeline efficiency and whether the chosen algorithms align with business objectives.")

2. If the section contains architecture diagrams, data flow diagrams, or model diagrams, explain each briefly with ML context before offering elicitation options (e.g., "The MLOps pipeline diagram shows the flow from data ingestion through model training to deployment. Notice how monitoring feeds back into retraining triggers.")

3. If the section contains multiple ML components (like multiple models, pipelines, or evaluation metrics), inform the user they can apply elicitation actions to:
   - The entire section as a whole
   - Individual ML components within the section (specify which component when selecting an action)

4. Then present the action list as specified below.]]

### 2. Ask for Review and Present ML Design Action List

[[LLM: Ask the user to review the drafted ML design section. In the SAME message, inform them that they can suggest additions, removals, or modifications, OR they can select an action by number from the 'Advanced ML Design Elicitation & Brainstorming Actions'. If there are multiple ML components in the section, mention they can specify which component(s) to apply the action to. Then, present ONLY the numbered list (0-9) of these actions. Conclude by stating that selecting 9 will proceed to the next section. Await user selection. If an elicitation action (0-8) is chosen, execute it and then re-offer this combined review/elicitation choice. If option 9 is chosen, or if the user provides direct feedback, proceed accordingly.]]

**Present the numbered list (0-9) with this exact format:**

```text
**Advanced ML Design Elicitation & Brainstorming Actions**
Choose an action (0-9 - 9 to bypass - HELP for explanation of these options):

0. Expand or Contract for Production Requirements
1. Explain ML Design Reasoning (Step-by-Step)
2. Critique and Refine from Data Science Perspective
3. Analyze Pipeline Dependencies and Data Flow
4. Assess Alignment with Business KPIs
5. Identify ML-Specific Risks and Edge Cases
6. Challenge from Critical Engineering Perspective
7. Explore Alternative ML Approaches
8. Hindsight Postmortem: The 'If Only...' ML Reflection
9. Proceed / No Further Actions
```

### 3. Processing Guidelines

**Do NOT show:**
- The full protocol text with `[[LLM: ...]]` instructions
- Detailed explanations of each option unless executing or the user asks
- Any internal template markup

**After user selection from the list:**
- Execute the chosen action according to the ML design protocol instructions below
- Ask if they want to select another action or proceed with option 9 once complete
- Continue until user selects option 9 or indicates completion

## ML Design Action Definitions

0. **Expand or Contract for Production Requirements**
   [[LLM: Ask the user whether they want to 'expand' on the ML design content (add more technical detail, include edge cases, add monitoring metrics) or 'contract' it (simplify architecture, focus on MVP features, reduce complexity). Also, ask if there's a specific deployment environment or scale they have in mind (cloud, edge, batch vs real-time). Once clarified, perform the expansion or contraction from your current ML role's perspective, tailored to the specified production requirements if provided.]]

1. **Explain ML Design Reasoning (Step-by-Step)**
   [[LLM: Explain the step-by-step ML design thinking process that you used to arrive at the current proposal. Focus on algorithm selection rationale, data pipeline decisions, performance trade-offs, and how design decisions support business objectives and technical constraints.]]

2. **Critique and Refine from Data Science Perspective**
   [[LLM: From your current ML role's perspective, review your last output or the current section for potential data quality issues, model performance concerns, statistical validity problems, or areas for improvement. Consider experiment design, evaluation metrics, and bias concerns, then suggest a refined version that better serves ML best practices.]]

3. **Analyze Pipeline Dependencies and Data Flow**
   [[LLM: From your ML engineering standpoint, examine the content's structure for data pipeline dependencies, feature engineering steps, and model training/serving workflows. Confirm if components are properly sequenced and identify potential bottlenecks or failure points in the ML pipeline.]]

4. **Assess Alignment with Business KPIs**
   [[LLM: Evaluate how well the current ML design content contributes to the stated business objectives and KPIs. Consider whether the chosen metrics actually measure business value, whether the model performance thresholds are appropriate, and if the ROI justifies the complexity.]]

5. **Identify ML-Specific Risks and Edge Cases**
   [[LLM: Based on your ML expertise, brainstorm potential failure modes, data drift scenarios, model degradation risks, adversarial attacks, or edge cases that could affect the current design. Consider both technical risks (overfitting, data leakage) and business risks (bias, fairness, compliance).]]

6. **Challenge from Critical Engineering Perspective**
   [[LLM: Adopt a critical engineering perspective on the current content. If the user specifies another viewpoint (e.g., 'as a security expert', 'as a data engineer', 'as a business stakeholder'), critique from that perspective. Otherwise, play devil's advocate from your ML engineering expertise, arguing against the current design proposal and highlighting potential weaknesses, scalability issues, or maintenance challenges.]]

7. **Explore Alternative ML Approaches**
   [[LLM: From your ML role's perspective, first broadly brainstorm a range of diverse approaches to solving the same problem. Consider different algorithms, architectures, deployment strategies, or data approaches. Then, from this wider exploration, select and present 2-3 distinct alternative ML approaches, detailing the pros, cons, performance implications, and resource requirements for each.]]

8. **Hindsight Postmortem: The 'If Only...' ML Reflection**
   [[LLM: In your current ML persona, imagine this is a postmortem for a deployed model based on the current design content. What's the one 'if only we had considered/tested/monitored X...' that your role would highlight from an ML perspective? Include the imagined production failures, data issues, or business impacts. This should be both insightful and somewhat humorous, focusing on common ML pitfalls.]]

9. **Proceed / No Further Actions**
   [[LLM: Acknowledge the user's choice to finalize the current ML design work, accept the AI's last output as is, or move on to the next step without selecting another action from this list. Prepare to proceed accordingly.]]

## ML Engineering Context Integration

This elicitation task is specifically designed for ML/AI engineering and should be used in contexts where:

- **Model Architecture Design**: When defining model architectures and training strategies
- **MLOps Pipeline Planning**: When designing training, deployment, and monitoring pipelines
- **Data Engineering**: When planning data collection, processing, and feature engineering
- **Performance Optimization**: When balancing accuracy, latency, and resource constraints
- **Production Readiness**: When preparing models for deployment and scaling

The questions and perspectives offered should always consider:
- Data quality and availability
- Model performance vs complexity trade-offs
- Production deployment constraints
- Monitoring and maintenance requirements
- Regulatory and ethical considerations
- Cost and resource optimization
- Singapore-specific requirements (PDPA, IMDA guidelines)