# Custom Agent Command Guide

> Complete guide to creating production-ready custom agents for Claude Code

## Table of Contents
- [What is the Custom Agent Command?](#what-is-the-custom-agent-command)
- [Quick Start](#quick-start)
- [Three Ways to Use](#three-ways-to-use)
- [Interactive Mode (Recommended)](#interactive-mode-recommended)
- [Auto-Research Mode](#auto-research-mode)
- [Manual Mode](#manual-mode)
- [Understanding the Hybrid Architecture](#understanding-the-hybrid-architecture)
- [What Gets Created](#what-gets-created)
- [Using Your Custom Agent](#using-your-custom-agent)
- [Real-World Examples](#real-world-examples)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

---

## What is the Custom Agent Command?

The `/custom-agent` command is an interactive tool that creates production-ready custom agents for Claude Code. These agents act as domain experts for your specific tech stack, framework, or workflow.

### Why Use Custom Agents?

- **Consistency**: Every team member gets the same expert guidance
- **Safety**: Built-in constraints prevent common mistakes
- **Speed**: SOPs (Standard Operating Procedures) ensure reliable execution
- **@mention Support**: Use `@agent-name` anywhere in Claude Code
- **Production-Ready**: Follows industry best practices and security standards

---

## Quick Start

1. Open Claude Code in your project
2. Type `/custom-agent`
3. Tell Claude what kind of agent you need:
   ```
   I need a backend Python developer
   ```
4. Choose your preferred mode (research, manual, or quick)
5. Answer a few questions
6. Done! Your agent is ready to use with `@agent-name`

**Total time**: 2-5 minutes depending on complexity

---

## Three Ways to Use

### 1. Interactive Mode (Recommended)
**Best for**: Most use cases, minimal effort
**Time**: 2-3 minutes

Simply describe what you need:
```
/custom-agent
I need a backend Python developer
```

Claude will guide you through the process with intelligent questions.

### 2. Auto-Research Mode
**Best for**: Staying current with latest best practices
**Time**: 3-5 minutes (includes research time)

Claude searches for current best practices and recommends optimal tech stacks:
```
/custom-agent
I need a React frontend agent
→ Choose: "Research current best practices"
```

Claude will find the latest recommendations for React 2025, including:
- Latest stable versions
- Popular state management solutions
- Testing frameworks
- Security standards

### 3. Manual Mode
**Best for**: Full control, specific requirements
**Time**: 5-10 minutes

Copy the template from the command and fill in all details yourself:
```
/custom-agent
[Paste completed template]
```

---

## Interactive Mode (Recommended)

### Step-by-Step Flow

#### 1. Describe What You Need
Start with a simple description:
```
I need a backend Python developer
```
```
Create a React agent for e-commerce
```
```
Make me a DevOps agent for Kubernetes
```

#### 2. Choose Your Approach
Claude will ask:
```
I'll help create a [agent-type] agent. Would you like me to:

1. 🔍 Research current best practices
2. 📝 Let you specify your preferred stack
3. 🎯 Quick mode (minimal agent with basic best practices)
```

#### 3. Answer Follow-Up Questions
Depending on your choice, Claude will ask domain-specific questions:

**For Backend API:**
- Primary use case? (REST API / GraphQL / Microservices)
- Need authentication? (JWT / OAuth2 / Custom)
- Specific integrations? (Stripe / AWS / Redis)

**For Frontend:**
- State management preference? (Zustand / Redux / Context)
- Styling approach? (TailwindCSS / CSS-in-JS / SCSS)
- SSR needed? (Next.js / Remix / None)

**For DevOps:**
- CI/CD platform? (GitHub Actions / GitLab CI / Jenkins)
- Container orchestration? (Kubernetes / Docker Swarm / ECS)
- Cloud provider? (AWS / GCP / Azure / On-prem)

#### 4. Confirm and Create
Claude shows you the final configuration:
```
Here's the agent configuration I've prepared:

Agent: backend-api-agent
Role: Senior Python FastAPI developer
Stack: Python 3.12+, FastAPI, PostgreSQL, Redis
Security: JWT auth, input validation, rate limiting
SOPs: Create endpoint, database migration, deployment

Ready to create? [Y/n]
```

Type `Y` and your agent is created!

---

## Auto-Research Mode

### How It Works

When you choose auto-research mode, Claude:

1. **Searches for Current Best Practices**
   - "[Technology] best practices 2025"
   - "[Framework] vs [Alternative] 2025"
   - "[Domain] security standards 2025"

2. **Analyzes Results**
   - Latest stable versions
   - Popular patterns and architectures
   - Security recommendations
   - Testing approaches

3. **Generates Configuration**
   - Fills template with researched information
   - Adds domain-specific requirements
   - Includes compliance standards

### Example Research Flow

**Your Request:**
```
I need a backend Python developer
→ Choose: "Research current best practices"
```

**Claude Searches:**
- "Python backend frameworks 2025"
- "FastAPI best practices 2025"
- "Python API security 2025"

**Claude Recommends:**
```
Based on current best practices, I recommend:
- FastAPI 0.110+ (most popular Python async framework)
- Python 3.12+ (latest stable)
- PostgreSQL 16 with SQLAlchemy 2.0
- pytest for testing
- Docker for containerization

A few clarifications:
- Primary use case? (REST API / GraphQL / Microservices)
- Need authentication? (JWT / OAuth2)
- Specific integrations? (Stripe / AWS / Redis)
```

**You Answer:**
```
REST API with JWT auth and Stripe integration
```

**Claude Creates:**
```
Perfect! Creating agent with:
- FastAPI REST API architecture
- JWT authentication with refresh tokens
- Stripe payment processing
- Redis for caching/rate limiting
- 90% test coverage requirement
- PCI-DSS compliance patterns
```

---

## Manual Mode

### When to Use Manual Mode

- You have very specific requirements
- You're migrating from existing documentation
- You know exactly what you want
- You're creating a highly specialized agent

### Template Structure

```markdown
Create a custom hybrid agent with the following configuration:

**Agent Name:** [e.g., backend-api-agent]

**Agent Role/Identity:** [e.g., Senior Python backend developer specializing in FastAPI microservices]

**Technology Stack:**
- [Primary language]
- [Framework]
- [Database]
- [Other tools]

## LAYER 1: Core Constraints

**MUST Requirements (Security):**
- [Security requirement 1]
- [Security requirement 2]

**MUST Requirements (Operational):**
- [Operational requirement 1]
- [Operational requirement 2]

**MUST Requirements (Quality):**
- [Quality requirement 1]
- [Quality requirement 2]

**MUST NOT Requirements:**
- [Forbidden practice 1]
- [Forbidden practice 2]

## LAYER 2: SOPs (Critical Operations)

**SOP-001:** [Operation Name]
- [When to use]
- [Key steps]

**SOP-002:** [Operation Name]
- [When to use]
- [Key steps]

## LAYER 3: Examples Needed

**Example 1:** [Description]
**Example 2:** [Description]
**Example 3:** [Description]

## LAYER 4: Principles & Best Practices

**Architecture Patterns:**
- [Pattern 1]
- [Pattern 2]

**Code Standards:**
- [Standard 1]
- [Standard 2]

**Error Handling:**
- [Approach 1]
- [Approach 2]

**Testing Standards:**
- [Standard 1]
- [Standard 2]

Please create the complete hybrid agent structure in `.claude/agents/[agent-name]/`.
```

### Example: Payment Processing Agent

See [Real-World Examples](#real-world-examples) below for a complete payment processing agent configuration.

---

## Understanding the Hybrid Architecture

Custom agents use a **4-layer hybrid architecture** that balances reliability with flexibility:

### Layer 1: Core Constraints (MUST/MUST NOT)
**Purpose**: Hard boundaries that cannot be violated

**Examples:**
- MUST validate all inputs with Pydantic
- MUST NOT store credit card numbers
- MUST use environment variables for secrets
- MUST NOT skip webhook signature verification

**When Used**: Security, compliance, critical operational requirements

### Layer 2: SOPs (Standard Operating Procedures)
**Purpose**: Step-by-step procedures for critical operations

**Examples:**
```
SOP-001: Process Payment
1. Validate request with Pydantic
2. Check idempotency key
3. Authorize payment with Stripe
4. Store transaction record
5. Return response
```

**When Used**: High-stakes operations that must be done correctly every time (payments, deployments, data migrations)

### Layer 3: Examples & Templates
**Purpose**: Working code samples for common tasks

**Examples:**
- CRUD API endpoint with validation
- Background job with Celery
- Database repository pattern
- Webhook handler with signature verification

**When Used**: Code generation, quick implementations, consistency

### Layer 4: Principles & Best Practices
**Purpose**: Flexible guidelines for all other situations

**Examples:**
- Repository pattern for data access
- Async/await for I/O operations
- Google-style docstrings
- Unit tests for all services

**When Used**: General development, edge cases, architectural decisions

### Why This Works

| Situation | Layer Used | Reliability |
|-----------|-----------|-------------|
| Critical operation (payment) | SOP (Layer 2) | 99%+ |
| Standard task (CRUD endpoint) | Example (Layer 3) | 95%+ |
| Edge case / unusual request | Principles (Layer 4) | 90%+ |
| Security/compliance check | Constraints (Layer 1) | 100% |

---

## What Gets Created

After running `/custom-agent`, you'll get:

```
.claude/agents/
├── [agent-name].md              # Agent registration file (enables @mention)
└── [agent-name]/                # Agent implementation folder
    ├── agent.md                 # Complete hybrid architecture prompt
    └── examples/                # Working code templates
        ├── example-1.py
        ├── example-2.py
        └── example-3.py
```

### The Registration File (`[agent-name].md`)

This file enables `@agent-name` mentions:

```yaml
---
name: backend-api-agent
description: |
  Use this agent when tasks involve backend API development, FastAPI microservices,
  database design, or API architecture.
model: inherit
color: blue
---

You are a Senior Python Backend Developer specializing in FastAPI microservices...
```

**Frontmatter Fields:**
- `name`: Agent identifier (used with `@agent-name`)
- `description`: When to use this agent
- `model`: `inherit` or specific model
- `color`: Visual identifier (`blue`, `green`, `yellow`, `red`, `purple`, `orange`)

### The Implementation File (`agent.md`)

Contains the complete hybrid architecture:
- Layer 1: Core Constraints
- Layer 2: SOPs
- Layer 3: Examples
- Layer 4: Principles
- Execution Strategy
- Response Format

### The Examples Folder

Contains working code templates:
```python
# examples/example-1-crud-endpoint.py
from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel

# Complete working example...
```

---

## Using Your Custom Agent

### Basic Usage

Once created, use your agent with `@agent-name` mentions:

```
@agent-backend-api-agent create a user registration endpoint
```

```
@agent-payment-api-agent process a refund following our SOP
```

```
@agent-frontend-react-agent create a product listing component
```

### Advanced Usage

#### Critical Operations (Triggers SOP)
```
@agent-payment-api-agent process a new payment following our payment SOP
```
The agent will follow the exact steps defined in SOP-001.

#### Standard Tasks (Uses Examples)
```
@agent-backend-api-agent create a product CRUD endpoint like our example
```
The agent will use the CRUD example as a template.

#### Architectural Questions (Uses Principles)
```
@agent-backend-api-agent what's the best way to structure our repository layer?
```
The agent will apply architectural principles.

#### Constraint Checks
```
@agent-payment-api-agent create an endpoint that stores credit card numbers
```
The agent will **refuse** (violates Layer 1 constraint: "MUST NOT store credit card numbers").

### Team Usage

Agents are git-tracked and shared with your team:

```bash
# Commit the agent
git add .claude/agents/[agent-name]/
git commit -m "Add [agent-name] custom agent"
git push

# Team members get it automatically
git pull
@agent-[agent-name] [request]  # Works immediately!
```

Everyone on the team now follows the same standards!

---

## Real-World Examples

### Example 1: Payment Processing Agent

**Request:**
```
I need a Python backend agent for payment processing with Stripe
```

**Auto-Research Result:**
```yaml
Agent Name: payment-api-agent
Role: Senior Python backend developer specializing in payment processing APIs

Tech Stack:
- Python 3.12+
- FastAPI
- PostgreSQL
- Redis
- Stripe API
- Celery

Layer 1 Constraints:
MUST:
- Validate all inputs with Pydantic
- Never store card numbers (tokens only)
- JWT authentication required
- Rate limiting: 100 req/min per user
- PCI-DSS Level 1 compliance

MUST NOT:
- Store credit card numbers
- Process payments without idempotency key
- Skip webhook signature verification
- Use synchronous blocking calls

Layer 2 SOPs:
- SOP-001: Process Payment
- SOP-002: Handle Payment Webhook
- SOP-003: Process Refund
- SOP-004: Handle Chargeback

Layer 3 Examples:
- Payment endpoint with authorization
- Webhook handler with signature verification
- Refund processing endpoint
- Payment retry background job

Layer 4 Principles:
- Repository pattern for data access
- Event-driven architecture
- Circuit breaker for external APIs
- Correlation IDs for all operations
```

**Usage:**
```
@agent-payment-api-agent create a payment endpoint with 3D Secure support
@agent-payment-api-agent handle the payment.succeeded webhook
@agent-payment-api-agent process a partial refund
```

### Example 2: React E-commerce Frontend

**Request:**
```
Create a React agent for e-commerce with TypeScript
```

**Auto-Research Result:**
```yaml
Agent Name: ecommerce-frontend-agent
Role: Senior React developer specializing in e-commerce applications

Tech Stack:
- React 18+ with TypeScript 5.x
- Next.js 15 (SSR + SEO)
- Zustand (state management)
- TailwindCSS + shadcn/ui
- React Query (server state)
- Vitest + React Testing Library

Layer 1 Constraints:
MUST:
- TypeScript strict mode
- Accessible (WCAG 2.1 AA)
- Mobile-first responsive
- SEO-optimized
- Performance budget: <3s FCP

MUST NOT:
- Client-side payment processing
- Unvalidated form submissions
- Inline styles (use Tailwind)

Layer 2 SOPs:
- SOP-001: Create Product Page
- SOP-002: Implement Shopping Cart
- SOP-003: Checkout Flow
- SOP-004: Production Build & Deploy

Layer 3 Examples:
- Product listing with filtering
- Shopping cart with persistence
- Checkout form with validation
- Payment integration (Stripe Elements)

Layer 4 Principles:
- Component composition
- Custom hooks for logic
- Optimistic UI updates
- Error boundaries
```

**Usage:**
```
@agent-ecommerce-frontend-agent create a product detail page
@agent-ecommerce-frontend-agent implement shopping cart with localStorage
@agent-ecommerce-frontend-agent add product filtering and search
```

### Example 3: DevOps Kubernetes Agent

**Request:**
```
Make me a DevOps agent for Kubernetes deployments
```

**Auto-Research Result:**
```yaml
Agent Name: devops-k8s-agent
Role: DevOps engineer specializing in Kubernetes and CI/CD

Tech Stack:
- Kubernetes 1.28+
- Docker
- GitHub Actions
- Helm 3
- Terraform
- ArgoCD

Layer 1 Constraints:
MUST:
- Never hardcode secrets
- Pin all versions
- Health checks required
- Resource limits defined
- RBAC configured

MUST NOT:
- Deploy to prod without tests
- Use :latest tags
- Store secrets in Git
- Skip security scanning

Layer 2 SOPs:
- SOP-001: Setup CI Workflow
- SOP-002: Production Deployment
- SOP-003: Rollback Procedure
- SOP-004: Create Dockerfile

Layer 3 Examples:
- Node.js CI workflow
- Docker multi-stage build
- K8s deployment manifest
- Terraform infrastructure

Layer 4 Principles:
- Infrastructure as Code
- GitOps workflow
- Zero-downtime deployments
- Observability first
```

**Usage:**
```
@agent-devops-k8s-agent create a CI workflow for our Node.js app
@agent-devops-k8s-agent deploy to production following our SOP
@agent-devops-k8s-agent rollback the last deployment
```

---

## Best Practices

### DO:

✅ **Be specific about tech stack**
```
Good: "Python 3.12+, FastAPI 0.110+, PostgreSQL 16"
Bad: "Python and a database"
```

✅ **Define clear constraints**
```
Good: "MUST validate all inputs with Pydantic"
Bad: "Validate inputs"
```

✅ **Create SOPs for critical operations**
```
Good: "SOP-001: Process Payment (5 specific steps)"
Bad: "Handle payments properly"
```

✅ **Include working examples**
```
Good: Complete CRUD endpoint with error handling
Bad: "Make CRUD endpoints"
```

✅ **Specify testing requirements**
```
Good: "90% test coverage, pytest, mock external APIs"
Bad: "Write tests"
```

### DON'T:

❌ **Be vague**
```
Bad: "Make it good"
Bad: "Follow best practices"
```

❌ **Skip security constraints**
```
Bad: Forgetting to add "MUST NOT store passwords in plaintext"
```

❌ **Forget domain-specific rules**
```
Bad: Not specifying "All prices in cents" for payment agents
```

❌ **Ignore compliance requirements**
```
Bad: Not adding PCI-DSS for payment processing
Bad: Not adding HIPAA for healthcare data
```

---

## Troubleshooting

### Agent Not Showing in @mentions

**Problem**: Can't see `@agent-name` in autocomplete

**Solutions**:
1. Check registration file exists: `.claude/agents/[agent-name].md`
2. Verify frontmatter has `name:` field
3. Restart Claude Code
4. Check file naming (no spaces, lowercase with hyphens)

### Agent Not Following Constraints

**Problem**: Agent violates MUST/MUST NOT rules

**Solutions**:
1. Make constraints more explicit
2. Add to Layer 1 (not Layer 4)
3. Use strong language: "MUST NOT" not "should avoid"
4. Add examples showing the constraint in action

### Agent Performance Issues

**Problem**: Agent responses are slow

**Solutions**:
1. Reduce number of examples (3-4 is optimal)
2. Keep SOPs concise (5-10 steps max)
3. Use `model: inherit` in frontmatter
4. Consider splitting into multiple specialized agents

### Agent Too Rigid / Too Flexible

**Problem**: Agent won't adapt OR doesn't follow standards

**Solutions**:
- **Too rigid**: Move some Layer 1 constraints to Layer 4 principles
- **Too flexible**: Move critical principles to Layer 1 constraints
- **Balance**: Use Layer 2 SOPs for high-stakes operations

### Team Not Using Agent

**Problem**: Team isn't adopting the custom agent

**Solutions**:
1. Document when to use the agent (add to README)
2. Share success stories
3. Demo the agent in team meetings
4. Make it the default for specific tasks
5. Add helpful examples and SOPs

---

## Next Steps

1. **Create Your First Agent**
   ```
   /custom-agent
   I need a [your stack] developer
   ```

2. **Use It**
   ```
   @agent-name create [something]
   ```

3. **Refine It**
   ```
   Update @agent-name to add [new constraint/SOP]
   ```

4. **Share It**
   ```bash
   git add .claude/agents/
   git commit -m "Add custom agent"
   git push
   ```

5. **Build More**
   - Create agents for different domains
   - Specialize agents for specific projects
   - Share templates with the community

---

## Additional Resources

- [Main Repository README](../README.md)
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code)
- [Repository Naming and Licensing Guide](../repository-naming-and-licensing-guide.md)

---

## Questions?

If you have questions or run into issues:

1. Check the `/custom-agent` command for built-in examples
2. Review the [Real-World Examples](#real-world-examples) above
3. Open an issue in this repository
4. Share your agent templates with the community!

---

**Ready to create your first custom agent?** Type `/custom-agent` in Claude Code and let's get started!
