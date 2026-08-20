# Decision Making Skills

A collection of Claude skills for working through hard decisions — personal, professional, strategic, or team-based — using two complementary Stanford GSB frameworks:

- **Professor Paul Pfleiderer's analytical framework**: objectives, alternatives, risk identification, decision trees, tradeoffs, game theory, and group decision dynamics.
- **Professor Baba Shiv's neuroscience framework**: how emotion shapes decisions, how to build decision confidence, and how to bring other people along with a decision once it's made.

Each file in this repo is a self-contained skill. They can be used one at a time for a narrow problem (e.g. "I only need to expand my alternatives") or chained together to run a full decision process from framing a problem to executing on the choice.

## Skills

| File | Skill | What it's for |
|---|---|---|
| `objective-identification.md` | Objective Identification | Surfaces what you're actually trying to achieve before you look at options. Catches objectives that are secretly solutions in disguise ("hire a new manager") rather than real goals ("reduce team overload"), and separates true objectives from constraints. |
| `alternatives.md` | Alternatives Expansion | Breaks narrow framing — the single biggest cause of bad decisions. Uses techniques like eliminating your starting options, interrogating assumed constraints, and decomposing by objective to get you past the two options you walked in with. |
| `decision-trees.md` | Decision Trees | For decisions with real uncertainty about outcomes. Builds a full decision tree (decision nodes, chance nodes, payoffs, probabilities), solves it by backward induction, runs sensitivity analysis, and evaluates whether it's worth gathering more information before deciding. |
| `tradeoffs.md` | Addressing Tradeoffs | For decisions where no option wins on every dimension. Converts competing criteria into a common monetary unit via a penalty method, eliminates dominated options, and stress-tests the result — a more rigorous alternative to a weighted scoring matrix. |
| `game-theory.md` | Strategic Decision Making (Game Theory) | For decisions where the outcome depends on what another party does too — negotiations, competitive moves, pricing, partnerships. Covers dominated-strategy elimination, cooperation vs. reneging, first-mover advantage, and Nash Equilibrium. |
| `uncertainty-navigator-skill.md` | Uncertainty Navigator | Stress-tests a decision — before or after it's made — using pre-mortem (assume the favored option failed completely, work out why) and pre-celebration (assume a rejected option was a huge success, work out why) techniques, plus indirect bias detection. |
| `group-decision.md` | Group Decision Facilitator | For decisions made by a team, committee, or cross-functional group. Diagnoses group-specific failure modes (tribal dynamics, groupthink, buried information, the "watermelon" effect) and builds a concrete facilitation plan: widening phase, narrowing phase, and critical-evaluation tools like devil's advocate or red-teaming. |
| `decision-shaping-1on1.md` | Decision Shaping, 1:1 | For getting a specific stakeholder to say yes once the substance of a proposal is already solid. Builds an influence strategy around four levers — familiarity, trust, validation, and the IKEA effect — grounded in how risk-averse, comfort-seeking decision-makers actually process new ideas. |
| `tradeoff-decision.md` | Decision Making (Full Process) | The orchestrating skill that runs the whole journey end to end: understand the decision → clarify objectives → expand alternatives → surface risks → analyze (tree / tradeoffs / game theory, chosen to fit the situation) → decide → build confidence and execute, including bringing others along. The other skills act as deep-dive companions to specific stages of this one. |

## How the skills fit together

`tradeoff-decision.md` is the front door. It walks through seven stages — understanding the decision, clarifying objectives, expanding alternatives, surfacing risks, analyzing the options, committing, and executing — and at each stage it can hand off to one of the specialist skills for a deeper pass:

1. **Objectives** get a dedicated deep dive from `objective-identification.md` when the goal isn't yet clear.
2. **Alternatives** get expanded with `alternatives.md` when the user is stuck choosing between only two options.
3. **Analysis** picks whichever tool fits the shape of the decision:
   - Meaningful uncertainty about outcomes → `decision-trees.md`
   - Competing criteria with no dominant option → `tradeoffs.md`
   - Another party's choices affect the outcome → `game-theory.md`
4. **Stress-testing** the leading option, at any point before or after committing, runs through `uncertainty-navigator-skill.md`.
5. **Multi-person decisions** are handed off entirely to `group-decision.md`, which builds a facilitation plan rather than coaching one person.
6. **Bringing a specific stakeholder on board** once the analysis is done is `decision-shaping-1on1.md`.
7. `growth_analysis.md` stands apart from the rest — it's a company/stock evaluation skill (growth quality and relative valuation) rather than a step in the general decision process, useful when the decision at hand is an investment or equity analysis.

## Shared design principles

All of the coaching skills follow the same discipline: they are Socratic, asking one focused question at a time rather than lecturing, and they never generate the answer for the user — objectives, alternatives, penalties, probabilities, and influence tactics all have to come from the user's own reasoning, because inputs a person discovers themselves get taken seriously and inputs handed to them get quietly discarded. Each skill also closes with an explicit signal for when to move to the next stage and, where relevant, a handoff to the skill that should run next.
