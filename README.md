# Semantic Link – Playground

A safe what-if sandbox for Power BI semantic model measures in Microsoft Fabric.

> "What would Total Sales be if I excluded returns? What if I changed the discount logic? Which other measures would be affected?"

## What it does

Playground lets you experiment with any measure's DAX expression — see the impact instantly — without touching the production model. Four core operations:

- Explore — Browse every measure in your model with its DAX and current value.
- What-If — Modify any measure's DAX in a sandbox. Evaluates both original and modified side-by-side. The live model is never touched.
- Impact — See which downstream measures reference the one you changed, and how their values shift.
- Compare — Test multiple formula alternatives in a single chart.

## How it works

All "what-if" evaluations use `fabric.evaluate_dax()` with `DEFINE MEASURE` overrides — your modified DAX is injected into the query text, not written to the model. The live model definition is untouched throughout.

## Screenshots

### What-If: Original vs Modified
![What-If Demo](screenshots/whatif_demo.png)

### Scenario Comparison
![Scenario Comparison](screenshots/scenario_comparison.png)

### Dimensional Breakdown
![Dimensional Breakdown](screenshots/dimensional_breakdown.png)

## Quick start

1. Import the notebook into any Fabric workspace.
2. Edit the config cell — set `WORKSPACE_NAME` and `DATASET_NAME`.
3. Run all cells. `explore_model()` loads your measure catalog.
4. Call `whatif_measure()`, `impact_analysis()`, or `compare_scenarios()` with any measure.

## Stack

- `semantic-link` (`sempy`) — measure evaluation via `evaluate_measure` and `evaluate_dax`
- `semantic-link-labs` (`sempy_labs`) — TMSL/BIM retrieval for authoritative measure definitions
- `matplotlib` — side-by-side comparison charts and impact visualizations
- Fabric notebook — execution environment

## Submission

Submitted to the [Fabric Semantic Link Developer Experience Challenge](https://community.fabric.microsoft.com), April 2026.

## License

MIT
