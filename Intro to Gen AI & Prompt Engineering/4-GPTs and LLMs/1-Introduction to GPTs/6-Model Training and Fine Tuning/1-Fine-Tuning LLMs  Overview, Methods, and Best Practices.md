# Advanced Prompting Techniques

This chapter marks the transition from writing **good prompts** to building **professional and advanced prompts**.

The previous chapter focused on the fundamentals.
This chapter builds directly on top of those foundations.

To make it practical, this guide connects advanced prompting techniques to real-world workflows—especially in **security research, reconnaissance, and API analysis**.

---

## Fundamentals vs Advanced Prompting

In the fundamentals chapter, we learned:

* What a prompt is
* How to write clear requests
* Why context matters
* Zero-shot vs Few-shot prompting
* The importance of specificity

Basic example:

Instead of:

```text
Analyze this API.
```

Write:

```text
Analyze this REST API for authentication flaws, rate-limit weaknesses, and IDOR possibilities. Return findings in bullet points.
```

This improves clarity.

But advanced prompting goes beyond clarity.

It controls:

* How the model thinks
* How the response is built
* How the response is reviewed
* How much creativity or stability the output has

---

## 1. Zero-shot Prompting

Zero-shot is the simplest form of prompting.

You provide a direct instruction.

Example:

```text
Find security issues in this JavaScript file.
```

The model relies entirely on its internal knowledge.

Bug bounty example:

```text
Analyze this HTTP request for vulnerabilities.
```

The results are often useful—but usually shallow.

Improved version:

```text
Analyze this request for:

- IDOR
- SSRF
- Privilege Escalation
- Broken Access Control
```

This is still Zero-shot.

But much stronger.

---

## 2. Few-shot Prompting

Few-shot is one of the strongest techniques.

Instead of explaining how to think, you show examples.

Example:

```text
Example:
GET /api/user/123 -> Possible IDOR

GET /api/admin/logs -> Sensitive endpoint

Now classify:
GET /api/orders/999
```

The model learns the pattern.

Practical recon example:

If you have many Burp requests:

```text
Example vulnerable patterns:

/api/user/{id}
/api/order/{id}
/api/profile/{uuid}

These often indicate IDOR.

Now analyze these endpoints:
[paste endpoints]
```

This dramatically improves extraction quality.

---

## 3. Chain of Thought (Step-by-Step Reasoning)

This is extremely useful for analysts.

Instead of:

```text
Is this endpoint vulnerable?
```

Use:

```text
Analyze step by step:

1. Identify user-controlled parameters
2. Check authorization logic
3. Check object references
4. Determine exploitability
```

This forces the model to reason like a pentester.

GraphQL example:

```text
Analyze this GraphQL mutation step by step:

- identify inputs
- identify privilege boundaries
- detect mass assignment
- detect hidden fields
```

Traffic analysis example:

```text
Analyze these 50 requests step by step:

1. Group by function
2. Detect auth tokens
3. Identify internal APIs
4. Detect admin actions
5. Rank attack surface
```

This turns AI into a recon assistant.

---

## 4. Generated Knowledge

Generated Knowledge means feeding external knowledge into the prompt.

Instead of relying only on model memory.

Example:

```text
Platform: Whatnot

Known technologies:
- GraphQL
- Cloudflare
- JWT
- Redis
- Firebase

Analyze this request based on this stack.
```

Now the model understands the environment.

This makes the output much more accurate.

Privilege escalation example:

```text
Known roles:
- buyer
- seller
- admin

Known endpoints:
...

Analyze privilege escalation paths.
```

This is powerful for business logic testing.

---

## 5. Least-to-Most Prompting

Break large goals into smaller tasks.

Instead of:

```text
Find vulnerabilities in this app.
```

Use stages:

### Stage 1

```text
Enumerate attack surface.
```

### Stage 2

```text
Classify endpoints by sensitivity.
```

### Stage 3

```text
Analyze authentication logic.
```

### Stage 4

```text
Find exploit chains.
```

### Stage 5

```text
Generate POCs.
```

This is much stronger than one massive request.

JavaScript example:

```text
Step 1:
Extract endpoints.

Step 2:
Extract secrets.

Step 3:
Extract internal APIs.

Step 4:
Rank by exploitability.
```

This is a professional workflow.

---

## 6. Self-refine

Self-refine means making the model review itself.

First:

```text
Find vulnerabilities.
```

Then:

```text
Critique your findings.
Identify false positives.
Improve confidence.
```

Then:

```text
Re-rank by severity.
```

This reduces hallucinations.

Security example:

```text
Review your previous SSRF findings.
Challenge your assumptions.
Only keep exploitable cases.
```

Very useful for higher-confidence analysis.

---

## 7. Maieutic Prompting

This is deep verification.

Instead of asking:

```text
Is this an IDOR?
```

Ask:

```text
Why do you think this is IDOR?
```

Then:

```text
Explain the authorization bypass.
```

Then:

```text
Show the exact exploit path.
```

If the reasoning collapses, it is likely hallucination.

Excellent for validation.

---

## Temperature (Critical)

Temperature controls creativity.

```text
0.0 = Highly stable
1.0 = Highly creative
```

Recommended for security:

```text
0.1 -> Precise analysis
0.2 -> Code review
0.3 -> Log analysis
0.8 -> New attack ideas
0.9 -> Creative exploit scenarios
```

Examples:

For API analysis:

```text
temperature = 0.1
```

For offensive brainstorming:

```text
temperature = 0.9
```

---

# Professional Security Workflow

## Phase 1: Recon

```text
Extract all endpoints from this JS.
Group by:
- public
- authenticated
- admin
```

Technique used:

**Least-to-Most**

---

## Phase 2: Classification

```text
Example:
GET /user/123 = possible IDOR

Now classify:
[list]
```

Technique used:

**Few-shot**

---

## Phase 3: Deep Analysis

```text
Analyze step by step:

- auth
- object access
- role boundaries
- hidden parameters
```

Technique used:

**Chain-of-Thought**

---

## Phase 4: Validation

```text
Critique your own findings.
Remove false positives.
```

Technique used:

**Self-refine**

---

## Phase 5: Exploit Generation

```text
Generate exploitation paths based on confirmed issues.
Think creatively.
```

Technique used:

**High Temperature**

---

# Final Summary

Fundamentals teach you:

**How to write a good prompt.**

Advanced Prompting teaches you:

**How to make AI think like an expert.**

For bug bounty, reconnaissance, and API hacking, the four most powerful techniques are:

* Few-shot
* Chain-of-Thought
* Least-to-Most
* Self-refine

Mastering these four will significantly improve the quality of your analysis.
