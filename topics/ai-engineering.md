# AI Engineering

AI features should be designed as reliable software systems rather than simple model API calls.

## Core Flow

```text
User Input
    ↓
Validation
    ↓
Context / Prompt
    ↓
AI Model
    ↓
Structured Output
    ↓
Validation
    ↓
Application Logic
```

## Practical Patterns

### Structured Output

Prefer predictable schemas when application logic depends on model responses.

### Tool Calling

Use tools when the model needs to interact with application data or external services.

### Retrieval

Use retrieval when responses need information from a controlled knowledge source.

### Guardrails

Validate model output before allowing it to trigger important application actions.

## Production Checklist

* Keep API keys server-side
* Validate model output
* Handle timeouts and failures
* Monitor token usage
* Set usage limits
* Track AI-related costs
* Protect sensitive data
* Log important AI operations
* Evaluate critical workflows

## Common Mistakes

### Trusting Model Output

Model responses should not automatically be treated as trusted application data.

### Sending Too Much Context

More context is not always better. Keep retrieved and supplied context relevant.

### Ignoring Costs

Production AI features need usage monitoring and sensible limits.

### Building Without Evaluation

A workflow that works in a few manual tests may still fail on real user inputs.

## Engineering Principle

> Treat AI as one component inside a software system, not as the entire system.
