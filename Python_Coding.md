
---

# **📘 LLM Prompt Playbook – Coding / Development**

---

## **1.1 – Write Better Code**

### **Draft / Complete a Function**

**Goal:** Get high-quality, production-ready Python code with full explanations.
**Template:**

```
I’m working in Python [version] to build a function called [function_name] that [brief high-level description of what it does].

Requirements:
- Inputs: [Describe each parameter, expected type, defaults]
- Outputs: [Return type, format, constraints]
- Constraints: [Performance/memory requirements]
- Edge Cases: [List unusual scenarios]
- Libraries Allowed: [Allowed/disallowed]

Task:
1. Write a clean, efficient, well-documented Python function meeting the above requirements.
2. Add inline comments explaining each step.
3. Provide a step-by-step plain-English explanation after the code.
4. Suggest one alternative approach and its trade-offs.
```

**Notes:** Always specify exact Python version & libraries for best results.

---



### Better Code
I am providing you with a Python code snippet that I want you to improve.

Goals:
1. Optimize performance (time and space complexity where possible).
2. Refactor for cleaner, modular, and maintainable code.
3. Use Pythonic best practices and follow PEP 8.
4. Add descriptive docstrings for all classes, methods, and functions using Google-style or NumPy-style format.
5. Add inline comments explaining important logic.
6. Use type hints for all parameters and return values.
7. Replace repetitive logic with reusable functions/methods.
8. Use object-oriented design with classes if it improves structure.
9. Ensure the code is production-ready and easy to extend.
10. Avoid unnecessary global variables and magic numbers (use constants).
11. If applicable, handle errors gracefully with exceptions.
12. Include one example usage section (if relevant) at the bottom.

Input Code:
[PASTE YOUR CODE HERE]

Output:
- The improved and optimized code.
- A brief explanation of the key improvements made.


---

### **Complete Missing Code**

**Goal:** Fill in gaps without breaking style or functionality.
**Template:**

```
Complete the following Python code so that it [desired behaviour].

Guidelines:
- Preserve existing structure and naming conventions.
- Ensure edge cases are handled: [list them].
- Follow PEP-8 formatting.
- Use only [allowed libraries].

[partial code here]

Return:
- Completed code
- Short explanation of added/changed parts.
```

---

### **Implement an Algorithm**

**Goal:** Efficient, well-documented algorithm with complexity analysis.
**Template:**

```
Implement the [algorithm name] algorithm to [problem description].

Details:
- Input format: [type, size, constraints]
- Output format: [type, structure]
- Performance needs: [e.g., must run under X seconds for N items]
- Memory limits: [if any]
- Libraries allowed: [list]

Instructions:
1. Write efficient, clear Python code.
2. Add inline comments.
3. Provide time/space complexity analysis.
4. Suggest an alternative approach and compare trade-offs.
```

---

## **1.2 – Improve Coding Standards & Speed**

### **Refactor for Readability / Performance**

**Goal:** Optimise for clarity, maintainability, and/or speed.
**Template:**

```
Here’s a Python [or other language] function/class:

[code]

Task:
- Refactor for [performance/readability/maintainability].
- Follow PEP-8 guidelines.
- Remove unnecessary complexity.
- Replace deprecated functions.
- Add docstrings & meaningful comments.

After the refactor:
- List each change made and why.
- Include performance improvement metrics if applicable.
```

---

### **Suggest Code-Review Improvements**

**Goal:** Pinpoint weaknesses and recommend fixes.
**Template:**

```
Review this Python script:

[code]

Check for:
1. Variable/function naming clarity.
2. Code modularity.
3. Error handling quality.
4. Performance bottlenecks.
5. Potential bugs.
6. Security risks.

Return:
- Bullet-point improvements.
- Example code fixes for each.
```

---

### **Generate Documentation / API Specification**

**Goal:** Produce complete, developer-ready API docs.
**Template:**

```
Given this Flask API endpoint that handles [functionality], write an OpenAPI 3.0 specification.

Include:
- Path & HTTP method(s)
- Description
- Authentication requirements
- Request schema (parameters, types, constraints)
- Response schema (success & error)
- Error codes & meanings

Format: valid YAML or JSON.
```

---

## **1.3 – Keep Up to Date with ML / AI / GenAI**

### **Summarise Recent Developments**

**Goal:** Stay updated with actionable insights.
**Template:**

```
Summarise the last 6–12 months of developments in [specific field].

Include:
- Breakthroughs / techniques
- Notable papers (with links if possible)
- Industry applications
- New tools/frameworks
- Potential trends

Keep it concise but rich in insights for a data scientist.
```

---

### **Compare Methods / Tools**

**Goal:** Understand trade-offs before choosing.
**Template:**

```
Compare [Model/Library A] vs [Model/Library B] for [task].

Cover:
- Accuracy/performance benchmarks
- Training & inference speed
- Hardware requirements
- Integration ease
- Licensing & cost
- Community support

Conclude with a recommendation for [specific project context].
```

---

## **1.4 – Generate Test Cases**

### **Unit Tests**

**Goal:** Fully test function behaviour.
**Template:**

```
Write pytest unit tests for this function:

[function code]

Cover:
- Standard cases
- Edge cases
- Error handling
- Boundary values
- Invalid inputs

For each test:
- Clear name
- Reason in a comment
```

---

### **Data-Science Model Tests**

**Goal:** Validate robustness of ML model functions.
**Template:**

```
Given a ML function that [function description], propose a test plan.

Test:
- Missing values
- Extreme values
- Non-numerical inputs
- Small datasets
- Large datasets

For each:
- Describe input
- Expected output
- pytest-compatible snippet if possible
```

---

## **1.5 – Design Architecture for ML / AI Solutions**

### **High-Level Architecture**

**Goal:** Design a scalable, robust ML pipeline.
**Template:**

```
Design an ML pipeline for [problem] serving [X users/day].

Include:
- Stages: ingestion → preprocessing → training → serving → storage → monitoring
- Recommended cloud services (AWS/Azure/GCP) for each
- Scalability plan
- Failover/redundancy
- Cost estimates

Output:
- Text description
- Diagram (ASCII or mermaid)
```

---

### **Compare Deployment Options**

**Goal:** Choose best hosting strategy.
**Template:**

```
Compare self-hosting vs managed cloud for deploying [model type].

Discuss:
- Initial/recurring cost
- Maintenance
- Scalability
- Latency
- Security/compliance
- Disaster recovery

End with a recommendation given a budget of [amount] & uptime requirement.
```

---

### **Discuss Algorithm Alternatives**

**Goal:** Pick best-fit recommendation algorithm.
**Template:**

```
For a recommendation system using implicit feedback:

Suggest 2+ algorithms (e.g., collaborative filtering, matrix factorization).

For each:
- Logic
- Data needs
- Complexity
- Strengths/weaknesses

Recommend best fit given [dataset size, latency needs, compute availability].
```

---







---


