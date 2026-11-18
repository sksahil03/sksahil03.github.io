# Instructions for AI assistants

Read `README.md` first: it holds the full project context, the content schema, the design rules and the decisions log.

When working on this repository:

1. **Content changes** (new project, job, task, number, review): edit only `content.js`. Keep the schema in README section 2. Never invent metrics, quotes, logos or employers; use only what the owner gives you or what is in `resume.pdf`.
2. **Design or feature changes**: edit `index.html` (single file, no build step). Keep the Hallmark rules in README section 4: colours only through `:root` tokens, SVG icons from the `ICON` map (no emoji), no tracked-capital or eyebrow labels, no em dashes in visible copy, 4px spacing, hover/active/focus-visible states, reduced-motion fallbacks.
3. If `edit.html` must support a new content field, add it to its `LISTS` spec or the Basics section.
4. Verify locally with any static server (for example `npx http-server . -p 5173`), check the browser console for errors, and run `node ~/.claude/skills/hallmark/scripts/sloplint.mjs index.html edit.html` if Hallmark is installed.
5. Deploy = commit and push to `main`. GitHub Pages publishes in about a minute at https://sksahil03.github.io. Ask the owner before pushing.
6. Update `README.md` (decisions log, ideas) when something meaningful changes, so the next assistant has the context.
7. The repo is public: never commit phone numbers, passwords, tokens or private data beyond what the owner chose to show.
