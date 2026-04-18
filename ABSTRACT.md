# Submission Abstract — Semantic Link: Playground


### The problem

Semantic model developers constantly face "what if?" questions: What if I change this measure's formula? How much would the number move? Which downstream KPIs would be affected? Is it safe to make this change?

Today the only option is to edit the live model, evaluate, and revert. That's risky in production, slow in development, and impossible to do side-by-side. There's no "preview" button for DAX.

### The solution

Playground gives you a safe sandbox for measure experimentation. It introduces four operations:

Explore. `explore_model()` reads every measure from the TMSL via `sempy_labs`, evaluates each one at total level, and presents a searchable catalog with DAX expressions and current values.

What-If. `whatif_measure(measure, modified_dax)` evaluates both the original and your modified DAX side-by-side using `DEFINE MEASURE` overrides in `evaluate_dax()`. The live model definition is never touched. Supports optional dimensional breakdowns via `groupby_columns`.

Impact. `impact_analysis(measure, modified_dax)` finds every downstream measure that references the one you changed (via regex-based DAX dependency parsing), re-evaluates each with your override injected, and reports the full cascade of value changes.

Compare. `compare_scenarios(measure, {"label": dax, ...})` evaluates multiple alternative formulas for the same measure in a single call, rendering a comparison table and chart.

### Why this advances developer experience

Every other tool in the Semantic Link ecosystem is read-only — it inspects, validates, diffs, or documents the model as it is. Playground is the only tool that lets you safely change a measure and see what happens, without committing to the live model. It fills the gap between "I have an idea for a formula change" and "I'm confident enough to deploy it."

### Stack

- `semantic-link` (`sempy`) — measure evaluation via `evaluate_measure` and `evaluate_dax`
- `semantic-link-labs` (`sempy_labs`) — TMSL/BIM retrieval for authoritative measure definitions
- `matplotlib` — side-by-side comparison charts and impact visualizations
- Fabric notebook — execution environment

### Included in this submission

- `2026_SemanticLink_Playground.ipynb` — the complete solution with inline documentation, working what-if/impact/compare implementations, and a runnable demo walkthrough against the Wide World Importers sample dataset.
