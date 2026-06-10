# Bob Example Prompts Library

**Ready-to-use prompts for common TAM scenarios**

---

## 🎯 EXPLAIN Mode Prompts

### Prompt 1: Superposition for Business Audience
```
Bob, explain quantum superposition to a CFO who needs to understand 
why quantum is faster for optimization. Use a financial analogy.
```

**When to use:** Initial client education, executive presentations

---

### Prompt 2: Entanglement for Security Discussion
```
Bob, explain quantum entanglement to a CISO evaluating quantum key 
distribution. Focus on security benefits, not physics.
```

**When to use:** Security/cryptography discussions, QKD proposals

---

### Prompt 3: QAOA for Technical Team
```
Bob, explain QAOA to data scientists familiar with gradient descent 
and optimization. Include how it differs from classical approaches.
```

**When to use:** Technical deep-dives, algorithm selection discussions

---

### Prompt 4: Quantum Advantage Explanation
```
Bob, explain when quantum provides advantage over classical computing 
to a VP of Engineering evaluating quantum investment.
```

**When to use:** Qualification discussions, setting expectations

---

### Prompt 5: Error Mitigation for Skeptics
```
Bob, explain quantum error mitigation to a CTO concerned about 
reliability. Address "quantum computers are too error-prone" objection.
```

**When to use:** Addressing concerns, technical credibility building

---

## 🔍 EVALUATE Mode Prompts

### Prompt 6: Quick Qualification
```
Bob, quick assessment:

Client: [Industry]
Problem: [Description]
Current: [Solution and time]
Requirement: [Goal]
Budget: [Amount]

Is quantum suitable?
```

**When to use:** Initial qualification calls, opportunity screening

---

### Prompt 7: Detailed Problem Assessment
```
Bob, evaluate this use case in detail:

Client: [Company name and industry]
Problem: [Detailed description]
- Variables: [Number]
- Constraints: [List]
- Current solution: [Details]
- Time requirement: [Real-time/Batch]
- Data sensitivity: [Level]

Provide:
- Suitability score
- Algorithm recommendation
- ROI estimate
- Risk assessment
- Go/No-Go recommendation
```

**When to use:** Formal assessments, proposal preparation

---

### Prompt 8: Algorithm Selection
```
Bob, which quantum algorithm is best for:

Problem type: [Optimization/Simulation/ML/Search]
Problem size: [Variables, constraints]
Current approach: [Classical method]
Performance goal: [Target improvement]
Timeline: [When needed]
```

**When to use:** Technical planning, architecture discussions

---

### Prompt 9: Competitive Analysis
```
Bob, compare quantum vs classical for:

Problem: [Description]
Classical approach: [Method, time, cost]
Quantum approach: [Proposed algorithm]

Provide honest comparison including:
- Where quantum wins
- Where classical is better
- Break-even point
- Recommendation
```

**When to use:** Building credibility, honest assessments

---

### Prompt 10: Integration Feasibility
```
Bob, assess integration feasibility:

Client infrastructure:
- Systems: [z/OS, cloud, on-prem]
- Connectivity: [Network capabilities]
- Security: [Requirements]
- Team: [Skills available]

Quantum use case: [Description]

Can we integrate? What's needed?
```

**When to use:** Technical feasibility discussions, architecture planning

---

## 💼 TRANSLATE Mode Prompts

### Prompt 11: Executive Summary (CEO/CFO)
```
Bob, create a 1-page executive summary for:

Client: [Company]
Use case: [Description]
Quantum solution: [Algorithm]
Expected benefit: [Quantified]
Investment: [Amount]

Audience: CEO and CFO
Focus: ROI and strategic value
```

**When to use:** Executive presentations, board meetings

---

### Prompt 12: Technical Proposal (CTO/VP Eng)
```
Bob, create a technical proposal for:

Client: [Company]
Use case: [Description]
Current architecture: [Systems]
Quantum integration: [Approach]
Timeline: [Phases]

Audience: CTO and VP Engineering
Include: Architecture, integration, timeline, resources
```

**When to use:** Technical proposals, architecture reviews

---

### Prompt 13: Business Case Document
```
Bob, create a complete business case for:

Client: [Company]
Problem: [Current state and pain]
Solution: [Quantum approach]
Benefits: [Quantified]
Costs: [Detailed]
Risks: [Assessment]
Timeline: [Phases]

Include: NPV, IRR, payback period
```

**When to use:** Formal proposals, budget approval

---

### Prompt 14: Objection Response
```
Bob, create a response to this objection:

Objection: "[Client's concern]"
Context: [Situation]
Stakeholder: [Role]

Provide:
- Acknowledge
- Reframe
- Evidence
- Action
```

**When to use:** Handling concerns, negotiation

---

### Prompt 15: ROI Calculation
```
Bob, calculate ROI for:

Current state:
- Cost: $[Amount] annually
- Time: [Duration]
- Quality: [Metric]

Quantum solution:
- Expected improvement: [%]
- Investment: $[Amount]
- Timeline: [Months]

Provide detailed ROI analysis with assumptions
```

**When to use:** Financial justification, budget discussions

---

## 🎭 Scenario-Based Prompts

### Scenario 1: Cold Call Follow-Up
```
Bob, I just had a call with [Company] in [Industry]. They mentioned 
[problem]. I have 30 minutes to prepare a follow-up email with:
- Is quantum suitable?
- What's the potential value?
- What are next steps?

Help me qualify this opportunity quickly.
```

---

### Scenario 2: Executive Presentation Prep
```
Bob, I'm presenting to [Company]'s executive team tomorrow. They want 
to understand quantum computing potential for [use case]. I need:

1. Simple explanation (no jargon)
2. Business value (quantified)
3. Risk assessment
4. Recommendation

Audience: CEO, CFO, CTO (30-minute meeting)
```

---

### Scenario 3: Technical Deep-Dive
```
Bob, [Company]'s engineering team wants technical details on quantum 
integration with their [system]. They're skeptical about [concern].

I need:
1. Technical architecture
2. Integration approach
3. Address their concern
4. Proof points

Audience: Senior engineers and architects (1-hour meeting)
```

---

### Scenario 4: Competitive Situation
```
Bob, [Company] is evaluating quantum vendors. They're comparing IBM 
Quantum with [competitor]. For [use case], help me position IBM by:

1. Technical advantages
2. Integration with IBM ecosystem (z/OS, cloud)
3. Support and services
4. Proof points

Be honest about trade-offs.
```

---

### Scenario 5: Budget Justification
```
Bob, [Company] likes the quantum proposal but CFO needs stronger ROI 
justification. Current proposal shows [X]% ROI. Help me:

1. Strengthen financial case
2. Add intangible benefits
3. Compare to alternatives
4. Address risk concerns

Make it CFO-friendly.
```

---

## 🔄 Multi-Step Workflows

### Workflow 1: New Opportunity
```
Step 1 (EVALUATE):
Bob, quick assessment for [Company] - [problem summary]

Step 2 (EXPLAIN):
Bob, explain [quantum concept] to [stakeholder role]

Step 3 (TRANSLATE):
Bob, create executive summary for [stakeholder]
```

---

### Workflow 2: Pilot to Production
```
Step 1 (EVALUATE):
Bob, assess pilot results: [metrics achieved]

Step 2 (TRANSLATE):
Bob, create production business case based on pilot

Step 3 (EXPLAIN):
Bob, explain production architecture to engineering team
```

---

### Workflow 3: Objection Handling
```
Step 1 (EXPLAIN):
Bob, explain why [objection] is/isn't valid

Step 2 (TRANSLATE):
Bob, create response addressing [objection] for [stakeholder]

Step 3 (EVALUATE):
Bob, reassess opportunity given [objection/concern]
```

---

## 💡 Pro Tips

### Making Prompts More Effective

**Be Specific:**
- ❌ "Tell me about quantum"
- ✅ "Explain quantum superposition to a CFO using financial analogies"

**Provide Context:**
- Include: Industry, problem size, current solution
- Include: Stakeholder role and concerns
- Include: Timeline and budget constraints

**Set Expectations:**
- Specify output format (summary, proposal, technical doc)
- Specify length (1-page, detailed, quick)
- Specify audience (technical, business, executive)

**Iterate:**
- Start broad (EVALUATE)
- Get specific (EXPLAIN details)
- Create deliverable (TRANSLATE)

---

## 📋 Prompt Templates

### Template 1: Problem Assessment
```
Bob, evaluate quantum for:

Client: [Name] ([Industry])
Problem: [Type] with [X] variables, [Y] constraints
Current: [Solution], [Time], $[Cost]
Goal: [Target improvement]
Budget: $[Amount]
Timeline: [When needed]
Concerns: [List]

Provide: Suitability, algorithm, ROI, risks, recommendation
```

---

### Template 2: Stakeholder Communication
```
Bob, create [document type] for:

Audience: [Role(s)]
Topic: [Quantum use case]
Key message: [Main point]
Length: [Short/Medium/Detailed]
Tone: [Technical/Business/Executive]

Include: [Specific requirements]
```

---

### Template 3: Technical Question
```
Bob, explain [quantum concept/algorithm] to [audience]:

Context: [Why they're asking]
Their background: [Technical level]
Focus on: [Specific aspect]
Avoid: [What not to include]
```

---

## 🎯 Quick Reference

| Need | Mode | Prompt Starter |
|------|------|----------------|
| Understand concept | EXPLAIN | "Bob, explain [concept] to [audience]..." |
| Qualify opportunity | EVALUATE | "Bob, quick assessment: [problem]..." |
| Create proposal | TRANSLATE | "Bob, create [document] for [stakeholder]..." |
| Technical details | EXPLAIN | "Bob, explain how [algorithm] works for [use case]..." |
| ROI calculation | TRANSLATE | "Bob, calculate ROI for [scenario]..." |
| Handle objection | TRANSLATE | "Bob, respond to objection: [concern]..." |

---

**Remember:** The best prompts are specific, contextual, and action-oriented. Bob works best when you provide clear requirements and expected outcomes.