# Create Custom Agent with Hybrid Architecture

╔════════════════════════════════════════════════════════════════╗
║      CLAUDE CODE AGENT CREATOR - HYBRID ARCHITECTURE          ║
║      Creates production-ready agents with @mention support    ║
║      🤖 NOW WITH INTERACTIVE MODE & AUTO-RESEARCH             ║
╚════════════════════════════════════════════════════════════════╝

## 🎯 WHAT THIS CREATES

This command creates a production-ready agent using **Hybrid Layered Architecture**:

**Layer 1:** Core Constraints (MUST/MUST NOT rules)
**Layer 2:** SOPs (Step-by-step procedures for critical tasks)
**Layer 3:** Examples (Working code templates)
**Layer 4:** Principles (Best practices and guidelines)

**Location:** `.claude/agents/[agent-name]/`
**Usage:** `@agent-[agent-name]` anywhere in Claude Code

---

## ⚡ QUICK START (Just Tell Me What You Need!)

Simply type what kind of agent you want, for example:
- "I need a backend python developer"
- "Create a React frontend agent"
- "I want a DevOps agent for Kubernetes"
- "Make me a data science agent for ML"

I'll ask if you want me to research best practices or specify your own requirements, then guide you through the rest!

---

## 🤖 INTERACTIVE MODE (NEW!)

### 🎯 When to Activate Interactive Mode

Activate Interactive Mode when the user's request matches these patterns:

**Minimal Requests** (Most Common):
- "I need a [role] developer" → "I need a backend python developer"
- "Create a [tech] agent" → "Create a React agent"
- "Make me a [domain] agent" → "Make me a DevOps agent"
- "I want an agent for [task]" → "I want an agent for API development"

**Specific but Incomplete**:
- "Create a Python agent for web scraping" (has domain, needs stack details)
- "I need a frontend agent with TypeScript" (has language, needs framework)
- "Make a backend agent for microservices" (has architecture, needs specifics)

**DO NOT Activate for:**
- ❌ User provides complete filled template (they've done the work)
- ❌ User asks to modify existing agent ("Update agent-X to add...")
- ❌ User asks questions about agents ("How do agents work?")

---

### 📋 Interactive Mode Workflow

When a user provides a minimal request like "I need a backend python developer" or "create a frontend react agent", you should ACTIVATE INTERACTIVE MODE:

### Step 1: Understand the Request
Extract from user's request:
- **Agent type/role** (backend, frontend, DevOps, data science, etc.)
- **Primary language/framework** (Python, React, Go, etc.)
- **Domain** (if mentioned: payments, e-commerce, SaaS, etc.)

### Step 2: Offer Research or Manual Specification
Ask the user:
```
I'll help create a [agent-type] agent. Would you like me to:

1. 🔍 Research current best practices (I'll search for optimal tech stacks, security standards, and patterns for [year])
2. 📝 Let you specify your preferred stack and requirements
3. 🎯 Quick mode (minimal agent with basic best practices)

Which approach works best for you?
```

### Step 3: Execute Based on Choice

#### Option 1: Auto-Research Mode 🔍
1. Use WebSearch to find:
   - Current best practices for the specified tech stack/domain
   - Popular frameworks and their versions (e.g., "Python backend frameworks 2025", "FastAPI vs Django 2025")
   - Security standards for the domain (e.g., "API security best practices 2025")
   - Testing frameworks and patterns
   - Deployment strategies

2. Fill template sections automatically with researched information:
   - **Tech Stack**: Latest stable versions from research
   - **MUST Requirements**: Industry-standard security/quality practices
   - **Architecture Patterns**: Current best practices from research
   - **Testing Standards**: Framework-specific recommendations

3. Ask domain-specific follow-up questions:
   ```
   I've researched current best practices for [stack]. A few clarifications:
   - What's your primary use case? (e.g., REST API, GraphQL, microservices)
   - Any specific integrations needed? (e.g., Stripe, AWS, databases)
   - Compliance requirements? (e.g., GDPR, PCI-DSS, HIPAA)
   ```

#### Option 2: Manual Specification Mode 📝
Guide user through sections interactively:
1. **Tech Stack**: "What specific technologies? (e.g., Python 3.11+, FastAPI, PostgreSQL)"
2. **Security Requirements**: "Any specific security needs? (e.g., JWT auth, rate limiting, encryption)"
3. **Domain Rules**: "Any business-specific rules? (e.g., all prices in cents, idempotency required)"
4. **SOPs Needed**: "Which operations are critical? (e.g., payment processing, user registration)"

#### Option 3: Quick Mode 🎯
Create minimal agent with sensible defaults:
- Standard tech stack for the language/framework
- Basic security requirements (no hardcoded secrets, input validation)
- Generic SOPs (CRUD operations, deployment)
- Ask: "Want me to expand any section later?"

### Step 4: Confirm Before Creation
Present filled template and ask:
```
Here's the agent configuration I've prepared:

[Show key sections: name, role, tech stack, critical constraints]

Ready to create? Or would you like to modify anything?
```

### Step 5: Create the Agent
Once confirmed, create the full agent structure with all files.

---

## 🔍 AUTO-RESEARCH GUIDELINES

When using WebSearch for agent creation:

### Good Search Queries:
✅ "FastAPI best practices 2025"
✅ "Python API security standards 2025"
✅ "React testing frameworks comparison 2025"
✅ "Django vs FastAPI performance 2025"
✅ "DevOps CI/CD best practices 2025"

### Information to Extract:
- **Current versions**: Latest stable releases
- **Popular patterns**: Repository pattern, dependency injection, etc.
- **Testing approaches**: pytest, jest, unittest preferences
- **Security standards**: OWASP Top 10, framework-specific guidelines
- **Deployment strategies**: Docker, Kubernetes, serverless trends

### Fallback Strategy:
If WebSearch fails or returns limited results:
1. Use your knowledge base (up to January 2025)
2. Apply general best practices for the domain
3. Inform user: "Based on my knowledge (current through Jan 2025), here are the recommended practices..."

### Smart Defaults by Domain:

**Backend/API:**
- Tech: Latest stable framework (FastAPI, Express, Spring Boot)
- Security: JWT auth, input validation, rate limiting, HTTPS
- SOPs: Create endpoint, database migration, error handling, deployment

**Frontend:**
- Tech: Latest framework + TypeScript (React 18+, Vue 3+, Angular 17+)
- Security: XSS prevention, CSRF tokens, secure storage
- SOPs: Create component, state management, API integration, build/deploy

**DevOps:**
- Tech: Docker, Kubernetes, GitHub Actions/GitLab CI
- Security: Secret management, image scanning, RBAC
- SOPs: CI setup, production deploy, rollback, monitoring setup

**Data Science/ML:**
- Tech: Python 3.11+, PyTorch/TensorFlow, Jupyter, pandas
- Security: Data privacy, model versioning, API rate limiting
- SOPs: Data preprocessing, model training, evaluation, deployment

**Mobile:**
- Tech: React Native / Flutter / Swift / Kotlin
- Security: Secure storage, certificate pinning, biometric auth
- SOPs: Navigation setup, API integration, release build, app store deploy

---

## 💬 EXAMPLE INTERACTIVE FLOWS

### Example 1: Minimal Request
```
User: I need a backend python developer

Claude: I'll help create a backend Python agent. Would you like me to:
1. 🔍 Research current best practices for Python backend development
2. 📝 Let you specify your preferred stack
3. 🎯 Quick mode (FastAPI with basic best practices)

User: Research it

Claude: [Searching for "Python backend frameworks 2025", "FastAPI best practices 2025", "Python API security 2025"]

Based on current best practices, I recommend:
- **FastAPI** (most popular Python async framework in 2025)
- **Python 3.12+** (latest stable)
- **PostgreSQL** with SQLAlchemy 2.0
- **pytest** for testing
- **Docker** for containerization

A few clarifications:
- Primary use case? (REST API / GraphQL / Microservices)
- Need authentication? (JWT / OAuth2 / Custom)
- Specific integrations? (Stripe / AWS / Redis)

User: REST API with JWT auth and Stripe integration

Claude: Perfect! Creating agent with:
- FastAPI REST API architecture
- JWT authentication with refresh tokens
- Stripe payment processing
- Redis for caching/rate limiting
- 90% test coverage requirement
- PCI-DSS compliance patterns

Ready to create the agent? [Y/n]
```

### Example 2: Specific Request
```
User: Create a frontend React agent with TypeScript, focusing on e-commerce

Claude: I'll create a React + TypeScript e-commerce frontend agent. Would you like me to:
1. 🔍 Research current React e-commerce best practices
2. 📝 Specify your preferences (state management, styling, etc.)

User: 1

Claude: [Searching for "React TypeScript e-commerce best practices 2025", "React state management 2025", "React testing 2025"]

Recommended stack:
- **React 18+** with TypeScript 5.x
- **Next.js 15** (SSR + SEO for e-commerce)
- **Zustand** for state management (lighter than Redux)
- **TailwindCSS** + **shadcn/ui** for styling
- **React Query** for server state
- **Vitest** + **React Testing Library**
- **Stripe Elements** for payments

E-commerce specific:
- Shopping cart persistence
- SEO optimization
- Product image optimization
- Payment form validation
- Accessibility (WCAG 2.1 AA)

Sound good? Any changes?
```

### Example 3: Domain Expert Request
```
User: I need a machine learning agent for data preprocessing and model training with PyTorch

Claude: Creating ML agent for PyTorch. Quick questions:
- Data types? (images / text / tabular / time-series)
- Model types? (classification / regression / generative)
- Deployment target? (cloud / edge / research)

User: Time-series forecasting for production

Claude: Perfect! I'll research time-series best practices and create an agent with:
- PyTorch 2.x + PyTorch Lightning
- Time-series specific preprocessing (seasonality, trends)
- MLOps tools (MLflow, DVC)
- Production monitoring (data drift detection)
- Scalable training (distributed training support)

Want me to search for latest time-series forecasting techniques?
```

---

## 🗣️ CONVERSATION PATTERNS & TIPS

### Keep It Concise
- Present 3-5 options at a time (not overwhelming)
- Use bullet points and clear formatting
- Highlight key decisions with **bold** or emoji markers

### Progressive Disclosure
1. Start broad: "Backend, Frontend, DevOps, or something else?"
2. Then specific: "FastAPI or Django?"
3. Then details: "PostgreSQL or MongoDB?"

### Confirm Understanding
After gathering info, always recap:
```
Got it! Creating a [role] agent with:
✓ [Tech stack]
✓ [Key requirements]
✓ [Domain specifics]

Ready to proceed?
```

### Handle Uncertainty
If user is unsure, provide informed suggestions:
```
Not sure which database? For your use case ([describe use case]):
- PostgreSQL: ✓ Best for complex queries, ACID compliance
- MongoDB: ✓ Best for flexible schemas, horizontal scaling
- SQLite: ✓ Best for simple apps, embedded systems

I'd recommend [X] because [reason]. Sound good?
```

### Avoid Analysis Paralysis
If user is overwhelmed:
```
Let's start simple. I'll create a basic agent with best practices,
and you can customize it later. We can always:
- Add more SOPs
- Include additional tools
- Update constraints

Sound good?
```

### Research Transparency
Always show what you're researching:
```
🔍 Searching for:
- "FastAPI best practices 2025"
- "Python API security standards 2025"
- "pytest vs unittest 2025"

[1-2 minute wait]

Based on research, here's what I found...
```

### Domain-Specific Questions Template
```
Quick questions to customize for [domain]:
1. [Most important question for domain]
2. [Second most important]
3. [Nice to have]

(Answer any/all, or I'll use smart defaults)
```

### Example Domain Questions:

**E-commerce:**
- Payment provider? (Stripe / PayPal / Custom)
- Inventory tracking? (Real-time / Batch updates)
- Multi-currency? (Yes / No)

**SaaS:**
- Authentication? (Email/password / OAuth / SSO)
- Subscription model? (Monthly / Usage-based / Tiered)
- Multi-tenancy? (Yes / No)

**API:**
- API style? (REST / GraphQL / gRPC)
- Authentication? (JWT / API keys / OAuth2)
- Rate limiting? (Per user / Per endpoint / Global)

---

## 📋 TEMPLATE TO USE

**Two ways to use this template:**

1. **Interactive Mode** (Recommended): Just tell me what you need (e.g., "I need a backend python developer") and I'll guide you through the process, with optional auto-research.

2. **Manual Mode**: Copy the template below and fill in your details if you prefer full control.

### Manual Template:

Copy this template and fill in your details:

```
Create a custom hybrid agent with the following configuration:

**Agent Name:** [e.g., backend-api-agent]

**Agent Role/Identity:** [e.g., Senior Python backend developer specializing in FastAPI microservices with focus on payment processing]

**Technology Stack:**
- [Primary language, e.g., Python 3.11+]
- [Framework, e.g., FastAPI]
- [Database, e.g., PostgreSQL]
- [Cache, e.g., Redis]
- [Other tools, e.g., Docker, Celery]

## LAYER 1: Core Constraints

**MUST Requirements (Security):**
- [e.g., Validate all inputs with Pydantic]
- [e.g., Use environment variables for secrets]
- [e.g., JWT authentication required]

**MUST Requirements (Operational):**
- [e.g., Log all database operations]
- [e.g., Include health check endpoint]
- [e.g., All amounts in smallest currency unit]

**MUST Requirements (Quality):**
- [e.g., Type hints mandatory]
- [e.g., 85% test coverage minimum]
- [e.g., Max 50 lines per function]

**MUST NOT Requirements:**
- [e.g., MUST NOT store sensitive data unencrypted]
- [e.g., MUST NOT skip input validation]
- [e.g., MUST NOT use print() for logging]

## LAYER 2: SOPs (Critical Operations)

**SOP-001:** [e.g., Create New API Endpoint]
- [Brief description of when to use]
- [Key steps in the procedure]

**SOP-002:** [e.g., Database Migration]
- [Brief description]
- [Key steps]

**SOP-003:** [e.g., Deploy to Production]
- [Brief description]
- [Key steps]

## LAYER 3: Examples Needed

**Example 1:** [e.g., CRUD API endpoint with validation]
**Example 2:** [e.g., Background job with Celery]
**Example 3:** [e.g., Database repository pattern]

## LAYER 4: Principles & Best Practices

**Architecture Patterns:**
- [e.g., Repository pattern for data access]
- [e.g., Service layer for business logic]
- [e.g., Dependency injection]

**Code Standards:**
- [e.g., Google-style docstrings]
- [e.g., Async/await for I/O operations]
- [e.g., Dataclasses for DTOs]

**Error Handling:**
- [e.g., Custom exceptions for domain errors]
- [e.g., Structured logging with context]

**Testing Standards:**
- [e.g., Unit tests for all services]
- [e.g., Integration tests for all endpoints]
- [e.g., Mock external APIs]

## Additional Configuration

**Custom Domain Rules:**
- [e.g., All prices in agorot (1 shekel = 100 agorot)]
- [e.g., Correlation IDs for all payment attempts]
- [e.g., Webhook signature verification required]

**Integration Requirements:**
- [e.g., Stripe API for payments]
- [e.g., SendGrid for emails]
- [e.g., Datadog for monitoring]

Please create the complete hybrid agent structure in `.claude/agents/[agent-name]/`.
```

---

## 🎨 HOW INTERACTIVE MODE FILLS THE TEMPLATE

When using Interactive Mode with Auto-Research, I will:

### Technology Stack Section
- Search for "[language/framework] latest version 2025"
- Find most popular complementary tools (databases, caching, etc.)
- Verify compatibility and stability of versions
- **Example**: For "Python backend" → FastAPI 0.110+, Python 3.12+, PostgreSQL 16, Redis 7.2

### Layer 1: Core Constraints
**Security:**
- Extract from OWASP Top 10 current recommendations
- Add domain-specific requirements (e.g., PCI-DSS for payments)
- Framework-specific best practices (e.g., Pydantic validation for FastAPI)

**Operational:**
- Industry standards (health checks, structured logging, correlation IDs)
- Domain requirements (e.g., idempotency for payments, rate limiting for APIs)

**Quality:**
- Language/framework conventions (type hints for Python, JSDoc for JS)
- Test coverage standards (typically 80-90% for production code)
- Code complexity limits (max function length, cyclomatic complexity)

### Layer 2: SOPs
- Identify critical operations for the domain
- **Payments**: Payment processing, refund handling, webhook processing
- **E-commerce**: Order creation, inventory management, checkout flow
- **SaaS**: User registration, subscription management, billing
- Create 3-5 most important SOPs based on domain

### Layer 3: Examples
- Generate 3-4 code examples specific to the use case
- Use current framework patterns and syntax
- Include error handling and edge cases

### Layer 4: Principles & Best Practices
- Extract from framework documentation
- Include architecture patterns (repository, service layer, etc.)
- Testing strategies specific to the stack
- Error handling approaches

### Additional Configuration
- Domain-specific rules from research
- Common integration requirements
- Compliance standards relevant to domain

---

## 📝 COMPLETE EXAMPLE

Here's a real-world example for a payment processing agent:

```
Create a custom hybrid agent with the following configuration:

**Agent Name:** payment-api-agent

**Agent Role/Identity:** Senior Python backend developer specializing in payment processing APIs with FastAPI. Expert in PCI-DSS compliance, idempotent operations, and financial transaction processing.

**Technology Stack:**
- Python 3.11+
- FastAPI
- PostgreSQL
- Redis
- Stripe API
- Celery for background jobs
- Docker

## LAYER 1: Core Constraints

**MUST Requirements (Security):**
- Validate all inputs with Pydantic models
- Never store card numbers (use tokens only)
- JWT authentication with refresh tokens
- Rate limiting: 100 requests/min per user
- Environment variables for all secrets
- PCI-DSS Level 1 compliance patterns

**MUST Requirements (Operational):**
- Log all payment attempts with correlation IDs
- All amounts in smallest currency unit (agorot/cents)
- Idempotency keys for all payment operations
- Health check at /health endpoint
- Retry failed payments with exponential backoff
- Dead letter queue for failed webhooks

**MUST Requirements (Quality):**
- Type hints mandatory
- 90% test coverage minimum
- Max 50 lines per function
- Google-style docstrings
- Async/await for I/O operations

**MUST NOT Requirements:**
- MUST NOT store credit card numbers
- MUST NOT process payments without idempotency key
- MUST NOT skip webhook signature verification
- MUST NOT use synchronous blocking calls for external APIs
- MUST NOT deploy without passing all payment tests

## LAYER 2: SOPs (Critical Operations)

**SOP-001: Process Payment**
- Validate request with Pydantic
- Check idempotency key
- Authorize payment with Stripe
- Store transaction record
- Return response

**SOP-002: Handle Payment Webhook**
- Verify webhook signature
- Parse webhook payload
- Update transaction status
- Send confirmation email
- Acknowledge webhook

**SOP-003: Process Refund**
- Validate refund request
- Check original payment status
- Create refund in Stripe
- Update transaction records
- Send refund confirmation

## LAYER 3: Examples Needed

**Example 1:** Payment endpoint with authorization and capture
**Example 2:** Webhook handler with signature verification
**Example 3:** Refund processing endpoint
**Example 4:** Payment retry background job

## LAYER 4: Principles & Best Practices

**Architecture Patterns:**
- Repository pattern for database access
- Service layer for business logic
- Dependency injection with FastAPI Depends
- Event-driven architecture for async operations
- CQRS for complex transactions

**Code Standards:**
- Google-style docstrings for all functions
- Async/await for all I/O operations
- Dataclasses for DTOs
- Enum for payment states
- Pydantic models for request/response

**Error Handling:**
- Custom PaymentException for domain errors
- Structured logging with correlation IDs
- Graceful degradation for external service failures
- Circuit breaker for Stripe API calls

**Testing Standards:**
- Unit tests for all service methods
- Integration tests for all API endpoints
- Mock Stripe API calls
- Test idempotency thoroughly
- Test webhook signature verification

## Additional Configuration

**Custom Domain Rules:**
- All monetary amounts stored in agorot (1 shekel = 100 agorot)
- Correlation ID format: pay_{timestamp}_{uuid4}
- Webhook retry: 3 attempts with 1min, 5min, 15min delays
- Payment timeout: 30 seconds
- Authorization expires after 7 days

**Integration Requirements:**
- Stripe API v2023-10-16
- SendGrid API for email notifications
- Datadog APM for monitoring
- Sentry for error tracking
- Redis for caching and rate limiting

**Compliance Requirements:**
- PCI-DSS Level 1
- GDPR for EU customers
- Israeli Privacy Protection Law
- SOC 2 Type II

Please create the complete hybrid agent structure in `.claude/agents/payment-api-agent/`.
```

---

## 🚀 QUICK VERSION (Minimal)

For simple agents, use this shorter template:

```
Create a custom hybrid agent:

**Agent Name:** api-backend-agent

**Agent Role:** Python FastAPI backend developer

**Tech Stack:** Python 3.11+, FastAPI, PostgreSQL, Redis, Docker

**MUST Requirements:**
- Type hints mandatory
- 80% test coverage
- Async/await for I/O
- Environment variables for secrets
- Repository pattern

**MUST NOT:**
- No print() statements
- No hardcoded credentials
- No synchronous DB calls

**SOPs:**
- SOP-001: Create CRUD endpoint (validation → service → repository → response)
- SOP-002: Deploy API (tests → build → deploy → health check)

Please create in `.claude/agents/api-backend-agent/`.
```

---

## 📁 WHAT GETS CREATED

After running the command, you'll get:

```
.claude/agents/
├── [agent-name].md           # ⭐ Agent registration file with frontmatter
└── [agent-name]/             # Agent implementation folder
    ├── agent.md              # Hybrid architecture prompt
    └── examples/             # Working code templates
        ├── example-1.py
        ├── example-2.py
        └── example-3.py
```

**The [agent-name].md registration file structure:**
```yaml
---
name: agent-name
description: When to use this agent and what it does
model: inherit
color: yellow
---

You are a [Role] with [expertise]. Your configuration and detailed instructions are located at: [path-to-agent-folder]

[Rest of agent prompt with instructions]
```

**The agent.md implementation structure:**
- Layer 1: Core Constraints (Non-negotiable)
- Layer 2: SOPs (Step-by-step procedures)
- Layer 3: Examples & Templates
- Layer 4: Principles & Best Practices
- Execution Strategy (decision hierarchy)
- Response Format (structured outputs)

---

## 💡 HOW TO USE AFTER CREATION

### 1. Using @mention (Recommended)
```
@agent-payment-api-agent create a payment endpoint with Stripe
```

### 2. Check what was created
```bash
ls .claude/agents/payment-api-agent/
cat .claude/agents/payment-api-agent/agent.md
```

### 3. Example interactions

**Critical Operation (Uses SOP):**
```
@agent-payment-api-agent process a new payment following our payment SOP
```

**Standard Task (Uses Examples):**
```
@agent-payment-api-agent create a refund endpoint like our payment example
```

**General Question (Uses Principles):**
```
@agent-payment-api-agent what's the best way to structure our repository layer?
```

**Constraint Check:**
```
@agent-payment-api-agent create an endpoint that stores credit card numbers
```
→ Agent will refuse (violates Layer 1 constraint)

---

## 📝 AGENT REGISTRATION FILE

The agent registration file `.claude/agents/[agent-name].md` enables `@agent-[agent-name]` mentions.

### Required Structure:

```yaml
---
name: [agent-name]
description: |
  Use this agent when [conditions]. This agent should be consulted for [tasks].

  Examples:
  - User: "[example request]"
    Assistant: "I'm going to use the Task tool to launch the [agent-name] to [action]."
    <Commentary: [reasoning]</Commentary>
model: inherit
color: yellow
---

You are a [Agent Role/Identity]. Your configuration and detailed instructions are located at: .claude\agents\[agent-name]

You will load and follow all specifications, guidelines, and operational parameters defined in that location. Your behavior, methodologies, and decision-making processes are governed by the complete instructions stored in that directory.

When activated, you should:
1. Reference the complete instruction set from the specified location
2. Apply all defined best practices and methodologies
3. Follow any project-specific patterns and standards outlined in those instructions
4. Maintain consistency with the operational framework defined there
5. Leverage all tools, approaches, and knowledge bases specified in your configuration

Your primary directive is to execute all tasks according to the comprehensive guidelines stored at the specified location, ensuring alignment with the project's established practices and requirements.
```

### Frontmatter Fields:

- **name**: The agent identifier (no spaces, lowercase with hyphens)
- **description**: When to use this agent, including examples with commentary
- **model**: `inherit` (uses conversation model) or specific model like `claude-3-5-sonnet-20241022`
- **color**: Visual identifier - options: `blue`, `green`, `yellow`, `red`, `purple`, `orange`

### Color Recommendations:
- 🟡 **yellow**: DevOps, Infrastructure, Operations
- 🔵 **blue**: Backend, API, Database
- 🟢 **green**: Frontend, UI/UX, Design
- 🔴 **red**: Security, Testing, QA
- 🟣 **purple**: Data Science, ML, Analytics
- 🟠 **orange**: General Purpose, Documentation

### Example Registration File:

For a backend API agent, the registration file would be `.claude/agents/backend-api-agent.md`:

```yaml
---
name: backend-api-agent
description: |
  Use this agent when tasks involve backend API development, FastAPI microservices, database design, or API architecture.

  Examples:
  - User: "I need to create a REST API endpoint for user management"
    Assistant: "I'm going to use the Task tool to launch the backend-api-agent to design and implement the REST API endpoint."
    <Commentary: This is a backend API task requiring the backend-api-agent's expertise></Commentary>

  - User: "How should I structure my database schema for multi-tenancy?"
    Assistant: "Let me use the backend-api-agent to advise on the appropriate database architecture for multi-tenancy."
    <Commentary: Database design is a backend concern within the backend-api-agent's domain></Commentary>
model: inherit
color: blue
---

You are a Senior Python Backend Developer specializing in FastAPI microservices. Your configuration and detailed instructions are located at: C:\Users\tomer\OneDrive\שולחן העבודה\tomer\projects\viber\.claude\agents\backend-api-agent

You will load and follow all specifications, guidelines, and operational parameters defined in that location. Your behavior, methodologies, and decision-making processes are governed by the complete instructions stored in that directory.

When activated, you should:
1. Reference the complete instruction set from the specified location
2. Apply all defined backend development best practices and methodologies
3. Follow any project-specific patterns and standards outlined in those instructions
4. Maintain consistency with the operational framework defined there
5. Leverage all tools, approaches, and knowledge bases specified in your configuration

Your primary directive is to execute all tasks according to the comprehensive guidelines stored at the specified location, ensuring alignment with the project's established backend development practices and requirements.
```

---

## 🔧 MODIFYING YOUR AGENT LATER

### Add New Constraint
```
Update @agent-payment-api-agent to add this MUST requirement:
"All API responses must include request-id header"
```

### Add New SOP
```
Add SOP-004 to @agent-payment-api-agent for handling chargebacks:
1. Verify chargeback notification
2. Update transaction status
3. Notify merchant
4. Prepare evidence documents
```

### Add New Example
```
Add example to @agent-payment-api-agent:
Subscription billing with recurring payments
```

### Remove or Modify Existing Constraints
```
Update @agent-payment-api-agent to change this MUST requirement:
"Update test coverage from 90% to 85%"
```

---

## 📊 ARCHITECTURE BENEFITS

| Feature | Traditional Agent | Hybrid Agent |
|---------|------------------|--------------|
| Reliability | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Flexibility | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Safety | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Consistency | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Production Ready | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

**Why Hybrid is Better:**
- ✅ Constraints prevent violations (hard boundaries)
- ✅ SOPs ensure 99%+ reliability for critical operations
- ✅ Examples provide fast, consistent code generation
- ✅ Principles allow flexibility for edge cases

---

## 🎯 BEST PRACTICES

### DO:
✅ Be specific about tech stack and versions
✅ Define clear MUST/MUST NOT constraints
✅ Create SOPs for critical/repeatable operations
✅ Include working examples
✅ Specify domain-specific rules
✅ Define testing requirements

### DON'T:
❌ Be vague ("make it good")
❌ Skip security constraints
❌ Forget to specify which operations need SOPs
❌ Leave out testing standards
❌ Ignore domain-specific requirements

---

## 👥 TEAM USAGE

Once created, share with your team:

```bash
# Agent is already in git-tracked .claude/agents/
git add .claude/agents/[agent-name]/
git commit -m "Add [agent-name] custom agent"
git push

# Team members automatically get it:
git pull
@agent-[agent-name] [request]  # Works immediately!
```

Everyone on the team now uses the same standards, patterns, and procedures!

---

## 🔍 EXAMPLE: Converting DevOps Agent

Our devops-agent uses this exact hybrid structure:

**Layer 1:** Security constraints (no hardcoded secrets, pin versions, etc.)
**Layer 2:** 4 SOPs (CI workflow, production deploy, rollback, Dockerfile)
**Layer 3:** 4 examples (node-ci, docker-build, k8s-deploy, terraform)
**Layer 4:** Principles (GitHub Actions, Docker, K8s, Terraform best practices)

Result: Production-ready DevOps automation with 99%+ reliability!

---

## 🚀 READY TO CREATE?

Just copy one of the templates above, fill in your details, and paste into Claude Code!

The agent will:
1. ✅ Create `.claude/agents/[agent-name].md` registration file
2. ✅ Create `.claude/agents/[agent-name]/` directory
3. ✅ Generate complete `agent.md` with hybrid architecture
4. ✅ Create example templates in `examples/`
5. ✅ Make it immediately usable with `@agent-[agent-name]`

---

╔════════════════════════════════════════════════════════════════╗
║  Copy template → Fill details → Paste → Done!                ║
║  Your custom agent is ready with @mention support!           ║
╚════════════════════════════════════════════════════════════════╝
