<!-- adamf9898 -->
# spiritToSoul

A browser-based JS/HTML5 Canvas game that procedurally generates all assets from King James Version (KJV) scripture. Runs in modern browsers on desktop and mobile. Content is data-driven via JSON.

## Quick start
- Prereqs: Node 18+, npm 9+, a modern browser
- Clone: git clone <repo-url> && cd spiritToSoul
- Install: npm install (if package.json present)
- Run:
	- With dev server (if available): npm run dev or npm start
	- Without dev server: npx http-server . and open http://localhost:8080/index.html

## Project layout (expected)
- index.html: Bootstraps main script and Canvas
- src/
	- engine/: primitives (loop, timing)
	- systems/: gameplay systems (Rendering, Input, Audio, GameState, Quest, World/Scenes)
	- render/: Canvas drawing
	- data/: loaders/parsers for scripture JSON and configs
	- scenes/: scene management
- assets/: images/audio
- data/: scripture/config JSON; keep small composable records
- docs/: general docs; docs/modules/, docs/diagrams/, docs/wiki/
- tests/: unit/integration (if present)
- scripts/: helper scripts

## Development
- Tabs for indentation; camelCase for functions/properties; PascalCase for classes/enums/types
- Prefer async/await; avoid globals; small modules
- Add JSDoc to all functions/classes/methods
- All files must include the adamf9898 header
- Renderer pure (draw only); logic in systems; data comes from JSON

## Build/Test
- Build: npm run build (if defined)
- Lint: npm run lint (if defined)
- Test: npm test (if defined)
- Manual: open index.html in a browser; watch console for errors; keep frame rate stable

## Data pipeline
Scripture JSON → procedural generators → asset cache → systems → renderer

## Contributing
- Keep diffs minimal/localized; do not commit temp files
- Document schemas alongside data files
- Place docs in docs/ and wiki pages in docs/wiki/
- Submit PRs with clear descriptions and testing notes

## Docs and Wiki
- Start at .github/copilot-instructions.md for AI guidance
- Module docs in docs/modules/
- Diagrams in docs/diagrams/ (Mermaid preferred)
- Wiki pages in docs/wiki/

## Open questions
- Confirm dev/build commands and toolchain (none/parcel/vite/webpack)
- Provide KJV data location and schema
- Provide main entry file paths and game loop location
