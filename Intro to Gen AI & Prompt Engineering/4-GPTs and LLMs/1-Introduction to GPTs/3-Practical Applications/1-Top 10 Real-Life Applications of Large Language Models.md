# Advanced Prompting Techniques

This lesson moves from the fundamentals of prompt writing to more advanced techniques that help language models produce more accurate, structured, and useful outputs.

## What is Advanced Prompting?

A simple prompt such as:

```text
Generate 10 geography questions
```

will generate 10 questions, but it has several limitations:

* Geography is a very broad topic.
* The model may choose countries, rivers, capitals, or any other subtopic.
* There is no guarantee of a specific output format.

Advanced prompting techniques provide greater control over the model's responses.

---

# 1. Zero-Shot Prompting

The simplest prompting technique.

You provide only the question or instruction without any examples.

Example:

```text
What is Algebra?
```

Response:

```text
Algebra is a branch of mathematics...
```

### When to Use

Use Zero-Shot Prompting when the task is straightforward and does not require examples.

---

# 2. Few-Shot Prompting

In Few-Shot Prompting, you provide examples before asking the model to continue the pattern.

Example:

```text
The player hit an ace => Tennis
The player hit a six => Cricket
The player made a slam dunk => ?
```

Response:

```text
Basketball
```

### Why It Works

The model learns the desired pattern from the examples you provide.

---

# 3. Chain of Thought (CoT)

One of the most powerful prompting techniques.

Instead of requesting an answer directly, you encourage the model to reason through the problem step by step.

Poor Prompt:

```text
Alice has 5 apples,
throws 3,
gives 2 to Bob,
Bob gives 1 back.

How many apples?
```

The model may make mistakes.

Better Prompt:

```text
Think step by step.

Alice has 5 apples
5 - 3 = 2

2 - 2 = 0

0 + 1 = 1

Answer:
```

Result:

```text
1
```

### Common Use Cases

* Mathematics
* Programming
* Data Analysis
* Logical Reasoning

---

# 4. Generated Knowledge

This technique provides the model with external information.

Example:

```text
Products:
Car insurance = $500
Home insurance = $600

Budget = $1000

Suggest the best option
```

Instead of relying solely on training data, the model uses the information you provide.

This is the foundation behind systems such as:

* ChatGPT with uploaded files
* Retrieval-Augmented Generation (RAG)
* GitHub Copilot
* Enterprise AI systems

---

# 5. Least-to-Most Prompting

Solve complex problems by breaking them into smaller, manageable tasks.

Instead of:

```text
How do I build a startup?
```

Use:

```text
Break the problem into steps.

1. Find an idea
2. Validate the market
3. Build an MVP
4. Acquire users
5. Scale the business
```

This approach generally improves accuracy and completeness.

---

# 6. Self-Refine

A highly effective iterative prompting technique.

The process:

1. Generate a solution.
2. Critique the solution.
3. Improve the solution.

Example:

```text
Write a Flask API
```

After the model generates code:

```text
Review your code.
Suggest 5 improvements.
Apply them.
```

This often results in significantly better output.

---

# 7. Maieutic Prompting

The name may sound complex, but the idea is simple.

Do not stop at the answer itself.

Ask the model to explain and validate each component of its reasoning.

Example:

```text
How do I handle a pandemic?
```

Model:

```text
1. Identify risks
2. Identify stakeholders
...
```

Then continue:

```text
Explain risk #1 in detail.
```

Next:

```text
Why is it important?
```

Then:

```text
Are there any contradictions?
```

This method helps uncover reasoning flaws and reduce hallucinations.

---

# Controlling Randomness (Temperature)

Language models are probabilistic.

The same prompt can produce different responses depending on the temperature setting.

---

## Temperature = 0

Produces highly predictable and consistent outputs.

Best for:

* Programming
* SQL
* Data Analysis

Example:

```text
Temperature = 0.1
```

Results will be very similar across multiple runs.

---

## Temperature = 1

Produces more creative and varied outputs.

Best for:

* Storytelling
* Poetry
* Brainstorming

Example:

```text
Temperature = 0.9
```

Results may differ significantly each time.

---

# Best Practices

## 1. Provide Context

Poor:

```text
Write about security
```

Better:

```text
Write about Web Application Security
for beginner bug bounty hunters.
```

---

## 2. Define the Output Format

Poor:

```text
Explain Linux
```

Better:

```text
Explain Linux in 5 bullet points.
```

---

## 3. Specify What and How

Poor:

```text
Create API
```

Better:

```text
Create a Flask API
with routes:
/users
/products

Split code into 3 files.
```

---

## 4. Use Templates

Example:

```text
Company: {{company}}

Products:
{{products}}

Budget:
{{budget}}

Suggest the best option.
```

The variables can then be replaced automatically.

---

# Most Practical Techniques

If you work in:

* Bug Bounty
* Software Development
* Cybersecurity

The three most useful prompting techniques are:

1. **Chain of Thought (CoT)** – For step-by-step analysis.
2. **Few-Shot Prompting** – For teaching the model a specific pattern.
3. **Self-Refine** – For reviewing and improving outputs.

---

# Professional Prompt Example

```text
Act as a senior security researcher.

Analyze the following data step by step.

Explain your reasoning.

List assumptions.

Identify possible mistakes.

Review your answer and improve it.

Output the final result in a structured report.
```

This combines:

* Role Prompting
* Chain of Thought
* Self-Refine

and typically produces significantly stronger results than a direct question.
