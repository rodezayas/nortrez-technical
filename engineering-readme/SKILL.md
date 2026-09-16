---
name: engineering-readme
description: Create or update README.md files for software and AI engineering repositories. Use this skill whenever a repository needs a README written, rewritten, or updated. The README must document the business problem, business rules, system design, architecture, technology stack, data flow, engineering decisions, reliability, testing, and limitations, and must always include at least one Mermaid architecture diagram.
---

When writing or updating a README:

1. Inspect the repository before writing anything
2. Understand the actual implementation, dependencies, entry points, services, databases, APIs, and execution flow
3. Never invent technologies, architecture, business rules, or capabilities that are not supported by the repository
4. If important information cannot be determined from the repository, mark it as `TBD — requires confirmation`
5. Write the README following this structure:

# Project Name

One-sentence description of what the system does.

## Overview

Brief explanation of:

- What the system is
- Who uses it
- What it does
- Why it exists

Keep this section concise.

## What Problem Does It Solve?

Explain the problem from the user's or business's perspective.

Include:

- Current problem
- Existing workflow
- Pain point
- Consequence
- How the system improves the workflow

Do not invent business metrics.

## Business Rules

Document the rules that define how the system must behave.

Use this format:

| Rule | Description | Enforcement |
|------|-------------|-------------|
| BR-001 | Description of the rule | How the system enforces it |
| BR-002 | Description of the rule | How the system enforces it |

Business rules should describe system behavior, not merely implementation details.

Examples:

- Responses require supporting evidence
- Unauthorized documents cannot be retrieved
- Failed jobs must be retryable
- Duplicate documents must not create duplicate records
- AI responses must contain citations

Only document rules that actually exist or are explicitly defined by the project.

## System Design

Explain the architecture and responsibilities of the major components.

### Components

For each major component explain:

- Name
- Responsibility
- Inputs
- Outputs
- Dependencies

Example:

- API — receives client requests
- Orchestrator — controls agent execution
- Retriever — performs vector search
- PostgreSQL — stores application state
- pgvector — stores and searches embeddings
- LLM — generates responses

Do not create artificial components just to make the architecture look more complex.

### Architecture

Every README MUST contain at least one Mermaid diagram.

The diagram must:

- Represent the actual implementation
- Show major components
- Show important dependencies
- Show the direction of data flow
- Use valid Mermaid syntax

Example:

```mermaid
flowchart TD
    User --> API
    API --> Orchestrator
    Orchestrator --> Retriever
    Retriever --> VectorDB
    Retriever --> LLM
    LLM --> API
    API --> User