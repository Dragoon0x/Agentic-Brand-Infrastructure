# Agentic Brand Infrastructure: Use Cases & How-To Guide

> **Experimental Project** | Everything here is exploratory. Read DISCLAIMER.md and DYOR.md before implementing anything. No warranties. No professional advice. Use at your own risk.

Built by Dragoon.

---

## Who This Is For

This guide walks through real-world use cases and step-by-step instructions for each repo. Whether you're a founder, brand lead, product designer, or developer building with AI agents, this tells you exactly what to do.

---

## REPO 01: Brand Genome Project

### Use Cases

**Use Case 1: Make your customer support agent actually sound like your brand**

You're deploying an AI agent for customer support. Right now it sounds generic. Helpful but forgettable. Your brand has a specific personality, specific ways it handles complaints, specific things it never says. The genome encodes all of that.

How to use it:

1. Copy `templates/starter-genome.yaml` to `your-brand-genome.yaml`
2. Start with the crisis genes. Fill in how your brand handles public criticism, product failures, and shipping delays
3. Fill in pricing genes: what's your discount philosophy? What tactics are banned?
4. Fill in competition genes: do you name competitors? How do you differentiate?
5. Add your "never" lists. These are the most important part for AI. What does your brand NEVER say or do?
6. Run `node validator/validate.js your-brand-genome.yaml`
7. Run `node validator/completeness-score.js your-brand-genome.yaml` and aim for 60+
8. Feed this genome to your AI agent's system prompt or configuration

```bash
cp templates/starter-genome.yaml my-brand.yaml
# Edit my-brand.yaml with your brand's actual behaviors
node validator/validate.js my-brand.yaml
node validator/completeness-score.js my-brand.yaml
```

**Use Case 2: Brand audit and consistency check**

Your brand has grown. Multiple teams make brand decisions. Things feel inconsistent. Use the genome to document what the brand actually does (not what the brand guide says it should do) and find the gaps.

How to use it:

1. Have each team lead fill out a starter genome independently
2. Compare the genomes. Where do teams disagree? Those are your inconsistencies
3. Merge into one canonical genome through discussion
4. Use this as the single source of truth for all brand behavior

**Use Case 3: M&A brand compatibility assessment**

You're acquiring a company or merging brands. Map both brand genomes. Compare them side by side. Where do decision trees conflict? Those are your integration friction points. Where do they align? Those are your strengths.

---

## REPO 02: Agent Clash Testing

### Use Cases

**Use Case 1: Prepare your sales agent for user agent negotiations**

Users will soon have personal AI agents that negotiate on their behalf. Your sales agent needs to be ready. Use the clash testing framework to simulate negotiations before they happen for real.

How to use it:

1. Define your brand agent's parameters in a scenario file: floor price, list price, discount authority, personality
2. Define a realistic user agent: budget ceiling, leverage points, walk-away price
3. Run the simulation
4. Score the outcome across fairness, efficiency, and satisfaction
5. Adjust your brand agent's parameters until outcomes are consistently fair and efficient

```bash
# Edit scenarios/pricing-negotiation.yaml.json with your real numbers
python framework/clash-runner.py scenarios/pricing-negotiation.yaml.json
# Review the log
python framework/outcome-scorer.py logs/log-price-negotiation-saas-annual.json
```

**Use Case 2: Design the UX for agent negotiation reporting**

Your user's agent just negotiated a deal on their behalf. How should the result be communicated? Read `design/agent-report-ux.md` for patterns on how to report outcomes without overwhelming users or breaking trust.

**Use Case 3: Discover negotiation failure modes before launch**

Run 100 simulations with different personality combinations. Find where deadlocks happen. Find where one side consistently gets exploited. Fix these before real users encounter them. Read `analysis/patterns.md` for patterns already identified.

---

## REPO 03: Anti-Style Guide

### Use Cases

**Use Case 1: Make your AI agents brand-safe immediately**

Your AI agent is generating content. Emails, social posts, support replies. You can't review everything. The anti-style guide gives the agent hard boundaries it must never cross.

How to use it:

1. Copy `templates/anti-guide-starter.yaml` to `my-brand-anti-guide.yaml`
2. Fill in tone refusals: what emotional registers does your brand never use? Sarcastic? Condescending? Desperate?
3. Fill in audience limits: who do you never market to? What insecurities do you never exploit?
4. Fill in pricing ethics: what tactics are banned? Fake urgency? Hidden fees?
5. Validate for completeness and conflicts

```bash
cp templates/anti-guide-starter.yaml my-anti-guide.yaml
# Fill in your constraints
node validator/constraint-checker.js my-anti-guide.yaml
node validator/conflict-detector.js my-anti-guide.yaml
```

**Use Case 2: Run a brand constraint workshop with your team**

Follow the workshop guide in `docs/WORKSHOP-GUIDE.md`. It's a 3-hour structured session that uncovers constraints your team knows intuitively but has never documented.

The five sessions:
1. Brand Autopsy: list every brand failure from the last 5 years
2. Competitor Cringe Audit: what do competitors do that makes you uncomfortable
3. Red Team: try to create the worst possible on-brand content
4. Customer Complaint Mining: pattern match complaints into constraint categories
5. Future Proofing: imagine your brand agent going rogue, write constraints to prevent it

**Use Case 3: Protect your brand during rapid scaling**

You're hiring fast. New people create content without deep brand knowledge. The anti-style guide is faster to learn than a brand guide because it's shorter and more concrete. "Never do X" is easier to follow than "try to embody Y."

---

## REPO 04: Product Soul Contracts

### Use Cases

**Use Case 1: Build trust with users who have personal AI agents**

Users are starting to let their AI agents evaluate products on their behalf. If your product has a soul contract, the agent can quickly assess trust. If you don't have one, the agent has nothing to go on.

How to use it:

1. Copy `templates/soul-contract-starter.yaml`
2. Fill in your product's purpose and explicitly what it's NOT for
3. Document your data relationship honestly: what you collect, what you never collect, third-party sharing policy
4. Write your ethical commitments and red lines
5. Define stress behavior: what happens during outages, acquisitions, sunsets
6. Add trust signals: open source status, audits, bug bounty, public changelog
7. Calculate your trust score

```bash
cp templates/soul-contract-starter.yaml my-product-soul.yaml
# Fill in honestly
node verification/trust-score-calculator.js my-product-soul.yaml
```

**Use Case 2: Differentiate in a crowded market**

Most competitors hide behind vague privacy policies. A public soul contract that clearly states "we will never sell your data, we will never train AI on your content, we will never lock your data behind a paywall" is a competitive advantage. It's a public commitment that agents and humans can verify.

**Use Case 3: Acquisition protection for your users**

Your soul contract includes stress behavior for acquisition scenarios. If you get acquired, users (and their agents) already know what to expect: migration windows, data export guarantees, notice periods. This builds trust that survives ownership changes.

---

## REPO 05: Design Drift Tracker

### Use Cases

**Use Case 1: Monitor AI-generated marketing content**

Your team uses AI to generate social posts, email campaigns, and landing pages. Each piece looks fine individually. But over 3 months, the tone has shifted. Colors have crept off-palette. CTAs have gotten more aggressive. The drift tracker catches this.

How to use it:

1. Set up your brand baseline in `baseline/brand-baseline.yaml`: define your colors, fonts, tone parameters, layout preferences, and CTA rules
2. When AI generates content, log a snapshot with the actual measurements
3. Run the drift score against your baseline
4. Monitor the alert level: green, yellow, orange, red

```bash
# Set up your baseline
# Edit baseline/brand-baseline.yaml with your brand's actual values

# After collecting snapshots:
python core/drift-score.py --baseline baseline/brand-baseline.yaml --snapshot snapshots/latest.json
```

**Use Case 2: Monthly brand coherence reports**

Run drift scoring at the end of each month. Generate a report showing which dimensions are holding steady and which are drifting. Share with your brand director. They don't need to understand the tech. The report shows before/after comparisons and clear next steps.

**Use Case 3: Recalibrate AI tools before drift becomes visible**

If drift score hits yellow (16-35), you have time to adjust prompts, templates, or agent parameters before the drift becomes noticeable to customers. The tracker gives you early warning.

---

## REPO 06: Preference Graph Standard

### Use Cases

**Use Case 1: Cold-start personalization for new users**

A new user signs up for your product. Normally you start from zero. If they bring their preference graph, you already know they prefer minimalist design, direct communication, and long-form content. Their first experience feels personalized from minute one.

How to use it:

1. Define your product's supported preference types from the node-types schema
2. Build an importer that reads preference graphs in the standard format
3. Map incoming preferences to your product's configuration options
4. Respect the consent layer: only access preferences the user has shared

**Use Case 2: Let users carry preferences between your own products**

You have multiple products or features. Users set preferences in one and start from scratch in another. Implement the preference graph standard internally so preferences carry across your own product ecosystem first.

**Use Case 3: Build a preference-aware AI agent**

Your AI agent recommends products, content, or designs. Instead of learning from scratch through trial and error, it reads the user's preference graph. It knows they prefer quality over price, visual content over text, and sustainability-conscious brands. Recommendations are better from the first interaction.

---

## REPO 07: Phantom Personas

### Use Cases

**Use Case 1: Test a price increase before announcing it**

You're planning a 15% price increase. Instead of guessing how customers will react, run the simulation. Load the grudge-holder archetype, the silent-churner, the loyal-skeptic, and the price-sensitive persona. Simulate 90 days. See which archetypes churn, which complain, and which stay.

How to use it:

```bash
# Run each archetype through a price increase scenario
python engine/persona-engine.py archetypes/grudge-holder.yaml --simulate 90
python engine/persona-engine.py archetypes/silent-churner.yaml --simulate 90
python engine/persona-engine.py archetypes/loyal-skeptic.yaml --simulate 90
```

Review the output in `output/simulation-latest.json`. Look at which days trigger churn, what the trust levels are at the end, and how many complaints were generated.

**Use Case 2: Stress-test your onboarding flow**

Load the newcomer-confused archetype. Simulate their first 7 days. Where does frustration spike? Where does engagement drop? Where does boredom set in? Use this to find the weak points in your onboarding before real users hit them.

**Use Case 3: Predict churn patterns by customer type**

Run all 8 archetypes through a 90-day simulation with your actual product events (feature launches, outages, emails, price changes). Compare which archetypes churn and when. This tells you which customer segment to watch and what interventions to prioritize.

**Use Case 4: Test competitor launch impact**

A competitor just launched a similar product. Load the competitor-curious archetype. Simulate 30 days of normal interactions with the additional event of a competitor launch. See how loyalty holds up and where defection risk peaks.

---

## REPO 08: Ritual Library

### Use Cases

**Use Case 1: Design the moment before your agent acts**

Your agent is about to spend money, send an email, or change a setting on behalf of the user. This moment matters more than any button color. Read `rituals/pre-action/the-pause.yaml` and implement the pattern.

The key insight: a 1.5-3 second breathing animation (not a spinner) with the copy "About to [action]. This feels right?" and the interaction "tap to proceed, wait to cancel" creates witnessed consent without confirmation fatigue.

**Use Case 2: Design failure communication**

Your agent tried something and fell short. Don't apologize excessively. Don't deflect. Read `rituals/post-action/honest-miss.yaml` and implement the pattern.

The structure:
- What happened: "Tried [action]. Got [result] instead of [goal]."
- What I'd change: "Here's what I'd adjust."
- Next steps: "Want me to try again or take it from here?"

**Use Case 3: Design the disagreement recovery**

A user overrides your agent's recommendation. The agent shouldn't defend itself or act hurt. Read `rituals/relationship/disagreement.yaml` for the pattern.

The structure:
- Acknowledge: "Got it. You see this differently."
- Learn: "Want to tell me what you'd prefer so I adjust?"
- Adapt: "Updated. I'll approach this differently next time."

**Use Case 4: Train your product team on a new design discipline**

Share `principles/MANIFESTO.md` with your design team. It introduces the five principles of ritual design: witnessed consent, proportional drama, honest emotion, repair over prevention, and silence as ritual. This reframes how your team thinks about human-agent interaction.

---

## REPO 09: Brand Memory Architecture

### Use Cases

**Use Case 1: Give your brand agent institutional knowledge**

Your brand agent is handling a shipping crisis. Instead of generating a generic response, it queries brand memory for past shipping crises. It finds that proactive transparency plus 20% discount reduced churn by 75% last time. It recommends the same approach with adjustments for the current situation.

How to use it:

1. Start logging brand decisions using the `schema/memory-entry.schema.json` format
2. Include context, decision, outcome, and lesson for each entry
3. Build a retrieval layer that matches current situations against stored memories
4. Let agents query memory before making recommendations

**Use Case 2: Prevent repeating mistakes**

Your brand made a pricing mistake 6 months ago. Without memory, a new team member (or agent) could make the same mistake. With memory, the system surfaces the lesson: "Last time we raised prices without notice, churn spiked 40% in the SMB segment. 30-day notice reduced it to 8%."

**Use Case 3: Strategic forgetting**

Review `forgetting/forget-policy.yaml`. Your brand memory shouldn't remember everything equally. Old resolved crises should fade. Outdated competitive intel should deprioritize. But trust violations should never be forgotten. The forgetting policy prevents fear-based decision making from old events.

---

## REPO 10: Negotiable Interface

### Use Cases

**Use Case 1: Let user agents negotiate pricing**

Instead of showing a fixed price, your product exposes a negotiable pricing element. The user's agent sees the range (floor to list) and negotiates based on the user's budget and leverage. The interface shows the negotiation state visually: shimmer while negotiating, locked when agreed.

How to use it:

1. Define negotiable elements using `protocol/negotiation-protocol.schema.json`
2. Set your floor prices, list prices, and discount budgets
3. Implement the visual states from `design-system/tokens/negotiable-tokens.json`: in-progress, agreed, failed
4. Build agent endpoints that accept negotiation rounds

**Use Case 2: Personalize content density automatically**

Some users want sparse, scannable layouts. Others want dense, comprehensive content. Instead of building settings pages, let the user's agent negotiate content density with your product. The interface adapts automatically based on the user's preference graph.

**Use Case 3: Negotiate data sharing transparently**

Instead of a binary "accept all cookies" or "reject all," the user's agent negotiates the specific data sharing arrangement. Zero tracking in exchange for generic experience. Full analytics in exchange for deep personalization. The user's agent makes this decision based on their ethical preferences.

**Use Case 4: Design for the transition period**

Right now most users don't have personal agents. The negotiable interface needs fallback states. When no agent is present, elements show their default values. When an agent connects, elements become negotiable. Read `design-system/patterns/negotiation-failed.md` for the fallback design pattern.

---

## How All 10 Repos Work Together

Here's the full picture of how these connect:

**Setting up your brand for agents:**
1. Map your brand behavior with **Brand Genome Project**
2. Document your constraints with **Anti-Style Guide**
3. Declare your product's trust contract with **Product Soul Contracts**
4. Build institutional memory with **Brand Memory Architecture**

**Building the user side:**
5. Give users portable preferences with **Preference Graph Standard**
6. Design the emotional moments with **Ritual Library**

**Testing and monitoring:**
7. Stress-test with **Phantom Personas**
8. Simulate agent negotiations with **Agent Clash Testing**
9. Monitor brand coherence with **Design Drift Tracker**

**Building the future interface:**
10. Create fluid, negotiated experiences with **Negotiable Interface**

The Foundation Layer (repos 1-3) should be implemented first. They're the base everything else depends on. The Intelligence Layer (repos 4-6) adds context and knowledge. The Experience Layer (repos 7-10) designs the interactions and catches problems.

---

## Getting Started Today (30 Minutes)

If you want to start right now with minimal time investment, do this:

1. Clone **Brand Genome Project** (5 min)
2. Copy the starter template (1 min)
3. Fill in just the crisis genes and pricing genes (15 min)
4. Run the validator and scorer (2 min)
5. Feed it to your existing AI tools as context (7 min)

That alone will make your AI-generated content noticeably more brand-consistent. Everything else builds from there.

---

## Quick Reference: Repo Commands

```bash
# Brand Genome Project
node validator/validate.js my-brand.yaml
node validator/completeness-score.js my-brand.yaml
python agents/behavior-simulator.py my-brand.yaml

# Agent Clash Testing
python framework/clash-runner.py scenarios/pricing-negotiation.yaml.json
python framework/outcome-scorer.py logs/log-file.json

# Anti-Style Guide
node validator/constraint-checker.js my-anti-guide.yaml
node validator/conflict-detector.js my-anti-guide.yaml

# Product Soul Contracts
node verification/trust-score-calculator.js my-product-soul.yaml

# Design Drift Tracker
python core/drift-score.py --baseline baseline/brand-baseline.yaml --snapshot snapshots/latest.json

# Phantom Personas
python engine/persona-engine.py archetypes/loyal-skeptic.yaml --simulate 90
python engine/persona-engine.py archetypes/grudge-holder.yaml --simulate 90
python engine/persona-engine.py archetypes/silent-churner.yaml --simulate 90
```

---

*Built by Dragoon. Shared freely. Go build something with it.*
