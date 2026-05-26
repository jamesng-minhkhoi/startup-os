# Startup OS

An AI-native startup management framework powered by 260+ Claude Code skills across strategy, product, marketing, sales, finance, legal, operations, HR, engineering, and design.

## What Is This?

Startup OS turns Claude Code into a full-stack startup consultant. Instead of using skills in isolation, it orchestrates them into **13 multi-skill workflows** that chain strategic thinking → planning → execution.

### 4-Layer Skill Architecture

| Layer | Source | Skills | Purpose |
|-------|--------|--------|---------|
| **Think** | [wondelai/skills](https://github.com/wondelai/skills) | 41 | Book-based strategic frameworks (Lean Startup, Mom Test, $100M Offers, EOS, etc.) |
| **Plan** | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | 114 | Department workflows with Notion/Slack integration |
| **Grow** | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | 35 | Marketing execution: CRO, copywriting, SEO, paid ads, growth |
| **Build** | [phuryn/pm-skills](https://github.com/phuryn/pm-skills) + [vasilyu1983](https://github.com/vasilyu1983/ai-agents-public) | 63 | PM tactical toolkit: canvases, experiments, GTM, prioritization |

## Quick Start

### 1. Install the skills

```bash
# Layer 1: Strategic Frameworks
npx skills add wondelai/skills -g -y

# Layer 2: Department Workflows (Anthropic official)
npx skills add anthropics/knowledge-work-plugins -g -y

# Layer 3: Marketing Execution
npx skills add coreyhaines31/marketingskills -g -y

# Layer 4: PM Toolkit
npx skills add phuryn/pm-skills -g -y
npx skills add vasilyu1983/ai-agents-public@product-management -g -y
```

### 2. Open the project

```bash
cd startup-os
claude
```

### 3. Fill in your context

Edit the files in `context/` with your company, product, market, customer, and metrics info. Every workflow reads these files to give you context-aware output.

### 4. Run a workflow

```
/validate My idea for an AI-powered invoicing tool for freelancers
/compete against FreshBooks, Wave, and Bonsai
/launch our new feature, budget is $2K, timeline is 3 weeks
/review quarterly — we missed our Q1 revenue target by 20%
```

## Workflows

| Command | What It Does | Key Skills Used |
|---------|-------------|-----------------|
| `/discover` | Full product discovery cycle | customer-research, mom-test, jobs-to-be-done, lean-startup |
| `/validate` | Idea validation with GO/ITERATE/KILL verdict | mom-test, startup-canvas, hundred-million-offers, blue-ocean-strategy |
| `/position` | Product positioning workshop | obviously-awesome, competitive-brief, storybrand-messaging |
| `/launch` | Launch planning across marketing + ops | launch-strategy, campaign-plan, copywriting, signup-flow-cro |
| `/growth` | Growth audit and bottleneck finder | metrics-review, cro-methodology, improve-retention, hooked-ux |
| `/review` | EOS business review (quarterly/annual) | traction-eos, metrics-review, roadmap-update, variance-analysis |
| `/sprint` | Sprint planning with prioritization | sprint-planning, product-management, write-spec, risk-assessment |
| `/compete` | Competitive analysis + battlecards | competitive-brief, obviously-awesome, competitive-battlecard |
| `/finance` | Financial review and runway analysis | financial-statements, variance-analysis, pricing-strategy, forecast |
| `/hire` | Hiring workflow: org design to offer | org-planning, interview-prep, comp-analysis, negotiation |
| `/canvas` | Strategic canvas (Startup/Lean/BMC) | startup-canvas, lean-canvas, business-model, lean-startup |
| `/pitch` | Investor pitch narrative + deck outline | storybrand-messaging, obviously-awesome, influence-psychology |
| `/gtm` | Go-to-market strategy | beachhead-segment, ideal-customer-profile, gtm-strategy, pricing-strategy |

## Project Structure

```
startup-os/
├── CLAUDE.md              # Master orchestrator — ties all skills together
├── TEAM-GUIDE.md          # Team onboarding (Vietnamese)
├── calendar.md            # Single source of truth for important dates
├── calendar-archive/      # Monthly archives of completed calendar items
├── weekly/                # One .md per ISO week — owners' weekly notes
│   ├── _template.md       # Template for new weeks
│   └── YYYY-WW.md         # Each week's file (auto-created Fridays)
├── .claude/commands/      # 13 slash command workflows
├── context/               # Business context (shared state across sessions)
│   ├── company.md         # Vision, team, funding stage
│   ├── product.md         # Product, positioning, business model
│   ├── market.md          # Market size, competitors, trends
│   ├── customers.md       # ICP, JTBD, interview insights
│   └── metrics.md         # North Star, OKRs, financials
├── docs/                  # Persistent team deliverables (specs, strategies, plans)
│   ├── product/features/  # Feature specs, PRDs
│   ├── strategy/          # Positioning, GTM, partnership playbooks
│   ├── marketing/         # Launch plans, growth playbooks, content strategy
│   └── finance/           # Financial models, equity proposals
└── outputs/               # Generated workflow outputs (research, one-offs)
    ├── strategy/
    ├── product/
    ├── marketing/
    ├── finance/
    ├── legal/
    ├── operations/
    ├── sales/
    └── hiring/
```

## Document Map

### `docs/` — Team Deliverables & Decisions

#### Product — "What are we building?"

| Feature | Spec | Who should read |
|---------|------|----------------|
| Onboarding & Auth | [01-onboarding-auth.md](docs/product/features/01-onboarding-auth.md) | Everyone |
| Pet Profiles | [02-pet-profiles.md](docs/product/features/02-pet-profiles.md) | Everyone |
| AI Chat | [03-ai-chat.md](docs/product/features/03-ai-chat.md) | Everyone |
| Product Scanner | [04-product-scanner.md](docs/product/features/04-product-scanner.md) | Everyone |
| Product Intelligence Pipeline | [04b-product-intelligence-pipeline.md](docs/product/features/04b-product-intelligence-pipeline.md) | Launch blocker |
| Memories | [05-memories.md](docs/product/features/05-memories.md) | Everyone |
| Health & Statistics | [06-health-statistics.md](docs/product/features/06-health-statistics.md) | James + Ngoc |
| Paywall & Subscriptions | [07-paywall-subscriptions.md](docs/product/features/07-paywall-subscriptions.md) | James |
| Scanner Share Card *(planned)* | [08-scanner-share-card.md](docs/product/features/08-scanner-share-card.md) | Ngoc + James |
| Family Sync | [09-family-sync.md](docs/product/features/09-family-sync.md) | Everyone |
| Documents | [10-documents.md](docs/product/features/10-documents.md) | Everyone |

#### Strategy — "Why are we doing this?"

| Doc | What it covers |
|-----|---------------|
| [Petio Positioning](docs/strategy/petio-positioning.md) | What Petio is, who it's for (4 segments), pricing, success metrics |
| [Competitive Edge](docs/strategy/competitive-edge.md) | Head-to-head vs ChatGPT / Hapu / AskVet / PawHub, our moat |
| [VN Distribution Partnerships](docs/strategy/vn-distribution-partnerships.md) | Rev share affiliate model (20/25/30%), outreach templates |

#### Marketing — "How do we get users?"

| Doc | What it covers |
|-----|---------------|
| [US Launch Plan](docs/marketing/us-launch-plan.md) | Channels, content formats, pre-launch checklist, launch week |
| [VN Launch Plan](docs/marketing/vn-launch-plan.md) | Vietnam-specific June 14 launch: Play Store, TikTok, FB groups, KOLs |
| [Vietnam Growth Plan](docs/marketing/vietnam-growth-plan.md) | 90-day 10K user plan: phase targets, channel playbook |

#### Finance

| Doc | What it covers |
|-----|---------------|
| [Equity Restructuring Proposal](docs/finance/equity-restructuring-proposal_2026-04-09.md) | Draft equity split proposal |

### `outputs/` — Research & Workflow Outputs

| Area | Key files |
|------|-----------|
| Product research | [Discovery (Original)](outputs/product/discovery_petio_2026-04-02.md) · [Discovery (AI Pivot)](outputs/product/discovery_petio_ai-pivot_2026-04-02.md) · [Secondary Research](outputs/product/secondary_research_petio_2026-04-02.md) |
| Strategy research | [VN Competitor Research](outputs/strategy/vietnam-competitor-research_2026-04-07.md) · [Validation Assessment](outputs/strategy/petio-validation-assessment.md) |
| Marketing research | [Growth Loops Analysis](outputs/marketing/growth-loops_petio_2026-04-12.md) |
| Operations log | [Sprint Status (Apr 2–7)](outputs/operations/sprint-status_2026-04-07.md) |

### `context/` — Business Intelligence

| File | Purpose |
|------|---------|
| [company.md](context/company.md) | Vision, mission, team, equity, finances |
| [product.md](context/product.md) | Features, tech stack, roadmap |
| [market.md](context/market.md) | TAM/SAM/SOM, competitors, trends |
| [customers.md](context/customers.md) | 4 segments, JTBD, growth roles, messaging |
| [metrics.md](context/metrics.md) | North Star, AARRR targets, OKRs, guardrails |

## Vietnam Strategy — Reading Order

1. **[Vietnam Competitor Research](outputs/strategy/vietnam-competitor-research_2026-04-07.md)** — Who we're up against (PawHub is the threat)
2. **[Vietnam Growth Plan](docs/marketing/vietnam-growth-plan.md)** — Channels, TikTok formula, blog topics, 90-day 10K plan
3. **[VN Distribution Partnerships](docs/strategy/vn-distribution-partnerships.md)** — Rev share model + decisions
4. **[VN Launch Plan](docs/marketing/vn-launch-plan.md)** — June 14 Vietnam-specific execution checklist

## How It Works

1. **Context-aware**: Every workflow reads your `context/` files before executing. Fill these in once, and all 260 skills know your business.
2. **Multi-skill chaining**: Workflows don't use one skill — they chain 4-8 skills at different altitudes (strategic thinking → planning → execution).
3. **Scored outputs**: Strategic frameworks rate your current state 0-10 and give specific improvements to reach 10/10.
4. **Persistent outputs**: All deliverables are saved to `outputs/` with dates, building a knowledge base over time.
5. **Opinionated consultant**: The CLAUDE.md instructs Claude to act as a senior consultant — it will push back on bad ideas and recommend what it would actually do.

## Requirements

- [Claude Code](https://claude.ai/code) CLI
- Node.js (for `npx skills`)
- Optional: Notion MCP + Slack MCP for deeper integrations with Anthropic workflow skills
