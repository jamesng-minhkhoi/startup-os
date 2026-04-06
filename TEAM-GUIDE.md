# Team Guide — Using Startup OS with Claude Desktop + ClaudeCowork

This guide is for team members using **Claude Desktop** (not the CLI). With ClaudeCowork pointing at this repo, you get ~90% of the full experience.

## Setup (One-Time, ~10 Minutes)

### 1. Install Skills

Open Terminal and run these 5 commands:

```bash
npx skills add wondelai/skills -g -y
npx skills add anthropics/knowledge-work-plugins -g -y
npx skills add coreyhaines31/marketingskills -g -y
npx skills add phuryn/pm-skills -g -y
npx skills add vasilyu1983/ai-agents-public@product-management -g -y
```

This installs 260+ specialized skills that Claude Desktop can use.

### 2. Set Up ClaudeCowork

In Claude Desktop, create a project pointing at this `startup-os/` directory. This gives Claude:
- Access to `CLAUDE.md` (the master instructions)
- Read/write access to `context/` (shared business state)
- Read/write access to `outputs/` (deliverables)

### 3. Pull the Repo

Make sure you have a local clone and keep it updated:

```bash
git clone [repo-url]
git pull  # before each session
```

After Claude writes outputs, commit and push so the team can see them.

---

## How It Works

### The Context System (Read This First)

Before your first session, read through these files to understand what Petio's "shared brain" already knows:

| File | What's In It |
|------|-------------|
| `context/company.md` | Vision, mission, team, funding |
| `context/product.md` | Product details, features, roadmap, tech stack |
| `context/market.md` | Market size, competitors, trends |
| `context/customers.md` | Personas, JTBD, interview insights |
| `context/metrics.md` | KPIs, OKRs, North Star metric |

**Every workflow reads these files first.** When you learn something new (customer insight, metric change, competitive move), update the relevant context file and commit it. This improves outputs for the whole team.

### Running Workflows

In the CLI, James runs workflows with slash commands (`/discover`, `/launch`). In Claude Desktop, you use **prompt templates** instead.

Go to `prompts/` and find the workflow you want. Copy the prompt, paste it into Claude Desktop, and fill in the `[BRACKETS]`.

### Available Workflows

| Prompt File | What It Does | Best For |
|-------------|-------------|----------|
| `prompts/discover.md` | Customer discovery cycle | Vy |
| `prompts/validate.md` | Idea validation (GO/ITERATE/KILL) | Anyone |
| `prompts/position.md` | Positioning workshop | Vy, James |
| `prompts/launch.md` | Launch planning | Vy |
| `prompts/growth.md` | Growth audit + bottleneck finder | Vy |
| `prompts/compete.md` | Competitive analysis + battlecards | Anyone |
| `prompts/sprint.md` | Sprint planning | James |
| `prompts/review.md` | EOS quarterly business review | James |
| `prompts/canvas.md` | Startup/Lean/Business Model Canvas | Anyone |
| `prompts/pitch.md` | Investor pitch narrative | James |
| `prompts/finance.md` | Financial review + runway | James |
| `prompts/gtm.md` | Go-to-market strategy | Vy, James |
| `prompts/hire.md` | Hiring workflow | James |

### Using Individual Skills

You don't always need a full workflow. Call any skill by name in conversation:

> "Use the `copywriting` skill to write App Store copy for Petio's new food safety scanner feature"

> "Use `design-critique` to review this onboarding screen" (attach screenshot)

> "Use `mom-test` to help me prepare questions for our next user interview"

---

## Role-Specific Quick Reference

### Trang Ha Vy (Product / Marketing)

**Your highest-value skills:**

| Skill | When To Use |
|-------|------------|
| `customer-research` | Planning or synthesizing user interviews |
| `copywriting` | App Store copy, landing pages, feature descriptions |
| `content-strategy` | Deciding what content to create and where |
| `email-sequence` | Building drip campaigns or announcement emails |
| `social-content` | Creating LinkedIn, Instagram, TikTok posts |
| `launch-strategy` | Planning any feature or product release |
| `metrics-review` | Analyzing weekly/monthly performance |
| `mom-test` | Preparing for customer interviews |
| `jobs-to-be-done` | Understanding what users really need |
| `seo-audit` | Checking petiogo.com SEO health |

**Your go-to workflows:** `discover`, `growth`, `launch`, `position`

### Xuan Ngoc (Designer)

**Your highest-value skills:**

| Skill | When To Use |
|-------|------------|
| `design-critique` | Getting structured feedback on a screen or flow |
| `ux-audit-rethink` | Full UX review using IxDF 7-factor framework |
| `refactoring-ui` | Fixing spacing, hierarchy, color, depth |
| `onboarding-cro` | Improving the first-run experience |
| `design-system` | Auditing component consistency |
| `ios-hig-design` | Reviewing against Apple Human Interface Guidelines |
| `microinteractions` | Designing triggers, feedback, loops |
| `ux-writing` | Microcopy, error messages, empty states, CTAs |
| `design-handoff` | Generating developer specs from a design |
| `top-design` | Creating award-worthy web experiences |

**Tip:** Attach screenshots or describe screens in detail — Claude will give specific, actionable feedback.

---

## Team Coordination

### The Git Workflow

This repo is our coordination layer:

1. **Pull before working** — `git pull` to get latest context and outputs
2. **Do your work** — run workflows, update context files
3. **Commit with clear messages** — `git commit -m "context: update customers.md with interview insights from pet parents"`
4. **Push for the team** — `git push` so others benefit

### What Goes Where

| I want to... | Put it in... |
|--------------|-------------|
| Update what we know about customers | `context/customers.md` |
| Save a competitive analysis | `outputs/strategy/` |
| Save marketing copy | `outputs/marketing/` |
| Save a sprint plan | `outputs/product/` |
| Save a financial review | `outputs/finance/` |

### File Naming

Date your outputs: `competitive-brief_2026-04-06.md`, `launch-plan_2026-04-06.md`

---

## First Session Checklist

- [ ] Skills installed (5 commands above)
- [ ] ClaudeCowork pointing at `startup-os/`
- [ ] Read through all 5 context files
- [ ] Run one workflow from `prompts/` to see how it works
- [ ] Update one context file with something you know that's missing
- [ ] Commit and push
