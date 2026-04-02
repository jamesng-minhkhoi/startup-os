# Product Discovery Workflow

Run a full product discovery cycle. This chains customer research, jobs-to-be-done analysis, assumption identification, and experiment design.

## Steps

1. **Load Context**: Read `context/customers.md` and `context/product.md` if they exist. Understand what we already know.

2. **Customer Research** (skill: `customer-research`, `mom-test`): 
   - If we have existing research (transcripts, surveys, reviews), analyze them using the customer-research skill's five-element extraction framework (JTBD, Pain Points, Trigger Events, Desired Outcomes, Customer Language).
   - If we need new research, use the mom-test framework to design interview questions that pass The Mom Test (talk about their life, not your idea; ask about specifics in the past; talk less).
   - Score the research quality 0-10.

3. **Jobs-to-Be-Done Analysis** (skill: `jobs-to-be-done`):
   - Map functional, emotional, and social jobs customers are trying to accomplish.
   - Identify which jobs are underserved (high importance, low satisfaction).
   - Create a job map with hire/fire criteria.

4. **Assumption Mapping** (skill: `identify-assumptions-new` or `identify-assumptions-existing`):
   - List all critical assumptions about customers, problem, solution, and business model.
   - Prioritize by risk (what's most likely wrong) and impact (what matters most if wrong).

5. **Experiment Design** (skill: `brainstorm-experiments-new` or `brainstorm-experiments-existing`, `lean-startup`):
   - For each top-priority assumption, design a validation experiment.
   - Use the Lean Startup Build-Measure-Learn loop in reverse: what do we want to learn → what metric proves it → what's the minimum we can build.
   - Target Validation Ladder level 4-5 (real commitment, not just stated preference).

6. **Output**: Save discovery synthesis to `outputs/product/discovery_{date}.md`. Update `context/customers.md` with new insights.

## Arguments

$ARGUMENTS — Describe what you're discovering: a new product idea, a new feature, a new market segment, or paste research data to analyze.
