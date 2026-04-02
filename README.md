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
├── .claude/commands/      # 13 slash command workflows
├── context/               # Business context (shared state across sessions)
│   ├── company.md         # Vision, team, funding stage
│   ├── product.md         # Product, positioning, business model
│   ├── market.md          # Market size, competitors, trends
│   ├── customers.md       # ICP, JTBD, interview insights
│   └── metrics.md         # North Star, OKRs, financials
└── outputs/               # Generated deliverables organized by function
    ├── strategy/
    ├── product/
    ├── marketing/
    ├── finance/
    ├── legal/
    ├── operations/
    ├── sales/
    └── hiring/
```

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
