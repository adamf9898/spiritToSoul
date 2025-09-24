# spiritToSoul

Web game that procedurally derives ALL game assets (modules, entities, quests, mechanics, maps, images, sounds, cards, code snippets) from King James Version (KJV) scripture. Core loop: load scripture + meta JSON -> generate structured content -> update systems each frame -> render via HTML5 Canvas.

---
## Quick Start (Agent)
1. Identify entry: index.html -> boot script (e.g. src/main.js or src/index.js) -> Game.init().
2. Init flow: load scripture data (data/ or assets/scripture/), build caches, register systems, start requestAnimationFrame loop.
3. Systems pattern: each system exposes init(data), update(dt), render(ctx), dispose(). Keep rendering side‑effects inside render only.
4. Content pipeline: scripture verse -> tokenization -> semantic tags -> generators (names, stats, lore, quests) -> cached JSON objects -> referenced by systems.
5. Never hardcode scripture text in logic; reference IDs / keys.

---
## Repository Conventions
- Directories (expected):
  - src/engine: loop, timing, event bus, utils.
  - src/systems: gameplay subsystems (Input, World, Quest, Audio, Combat, UI, Persistence).
  - src/render: canvas layers, sprite/text rendering helpers.
  - src/data: loaders, parsers, scripture indexing, procedural generators.
  - src/scenes: high-level scene/state management (Title, World, Battle, Menu).
  - assets/: raw media (images, audio). Keep metadata JSON adjacent where helpful.
  - data/: scripture + derived JSON (chapters, verses, index, generated entities).
  - docs/: generated docs, diagrams, tutorials; docs/modules, docs/wiki, docs/diagrams.
  - tests/: unit/integration (mirror src tree where possible).
- All source files begin with the adamf9898 header comment.
- Tabs for indentation; camelCase for functions/properties; PascalCase for classes/enums.
- Use async/await; avoid promise chains.
- Pure functions for data transforms; systems manage state.

---
## Coding Patterns
- Game loop: centralized (GameLoop or Engine). Systems registered in deterministic order; order matters for dependencies (Input -> AI -> Physics -> Quests -> World -> Render UI overlay last).
- Data-first: scripture JSON is immutable input; derived game objects are cached (e.g. verseId -> ItemDefinition).
- Separation: logic (systems) vs presentation (render module) vs data (parsers/generators).
- Avoid globals: export factory or singleton accessor from each system module.
- Use JSDoc for every public function/class; summarize side-effects + data shape.
- Externalization: any user-visible scripture or generated text should originate from data pipeline, not literals sprinkled across code.

---
## Typical Tasks (Invoke Only When User Requests)
When user asks:
- "Summarize architecture" -> provide high-level diagram + system list.
- "List entry points" -> index.html, boot script, Game.init, loop file.
- "Generate docstrings" -> add JSDoc to uncovered functions/classes (commit minimal diffs).
- "Create purpose files" -> produce <filename>.purpose.md describing role.
- "Create tutorials" -> produce <filename>.tutorial.md with step-by-step usage.
- "Module docs" -> docs/modules/<module>.md (APIs, data flows, examples).
- "Schema diagrams" -> docs/diagrams/*.md (Mermaid for flows: data ingestion, generation, loop sequencing).
- Requests referencing ${userInput}: locate occurrences, list modifying functions, suggest extraction into its own system (folder skeleton + registration strategy).
- "Draft wiki" -> docs/wiki structure (Overview, Systems, Data Pipeline, Extending, Glossary, FAQ).
- "Hierarchy" -> tasks → services → processes → commands tree.
- "Glossary" -> stable domain terms (VerseToken, GenerationSeed, QuestArc, EntityArchetype, etc.).
- "Config files" -> enumerate configs (package.json, bundler/ts config, lint, env) with roles.
- "Draft README" -> root README.md with setup, run, build, test, contribute, links to docs.

Keep placeholders (${userInput}) literal unless a concrete value is provided.

---
## Quality Gates
- No console errors/warnings during gameplay startup.
- Frame loop stable (< 16ms average on desktop baseline if possible).
- Data loaders fail fast with descriptive errors (include scripture reference ID, not raw text substring).
- Generators deterministic when given same seed.
- Tests (if present) pass; add new tests mirroring existing pattern.

---
## Extension / New Feature Workflow
1. Define data need (JSON schema) next to generator or in docs/schema.md.
2. Add loader/parser (pure) -> create generator (pure where possible) -> integrate via system or scene.
3. Register system in engine bootstrap; document order sensitivity.
4. Add purpose/tutorial docs; update README or wiki if conceptually new.
5. Validate performance (no large synchronous scripture scans every frame; pre-index on init).

---
## Documentation Automation Hints
- Aggregate un-documented symbols via simple grep for `function ` / `class ` lacking preceding /**.
- Purpose docs: single paragraph + bullet of key exports.
- Tutorials: scenario-driven ("How to create a new Quest generator").
- Diagrams: prefer Mermaid sequence or flowchart: scripture -> tokenizer -> generator -> cache -> system -> render.

---
## Open Questions (Maintain Separately in TODO.md)
- Confirm actual directory names and presence of TypeScript vs plain JS.
- Provide real scripture data schema (fields, indexing strategy, size).
- Specify asset pipeline (pre-processing? atlas packing?).
- Define save format + persistence location.

---
## Usage Safeguards (AI)
- Do NOT remove adamf9898 headers.
- Do NOT introduce unrelated large frameworks without approval.
- Minimize diff size; prefer surgical edits.
- Ask for clarification before assuming missing architecture.

---
## Trigger: TODO Generation
On request: scan for TODO/FIXME, compile root TODO.md with file:line and concise action item.

---
## Learnings
* Added explicit Learnings section placeholder for future adaptive guidance (1)

<!-- adamf9898 -->
