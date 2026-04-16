# Science Experiment Generator — Spec

## Objective

Build a static, browser-based tool that generates grade-appropriate science experiments based on user-provided inputs, using the OpenAI API.

## Deliverables

1. **Static webpage** (`index.html`) — HTML, CSS, and JavaScript only. No server, Node.js, or npm. Runs entirely in the browser and is deployed to the class GitHub organization.

2. **User inputs:**
   - Grade level dropdown (K–2, 3–5, 6–8, 9–12)
   - Text field for available classroom supplies

3. **API integration:**
   - OpenAI only (no Anthropic/provider switching — CORS limitation)
   - API key loaded via `.env` file upload, stored in memory only, never persisted

4. **Output rendering:**
   - Model response rendered as formatted HTML (not raw text or markdown strings)

5. **Reference folder:**
   - `temp/` contains the LLM Switchboard project for Claude Code to study patterns (API calls, key management, error handling)

## Technical Notes

- OpenAI-only due to CORS — Anthropic blocks direct browser requests
- Interface style matches the LLM Switchboard: IBM Plex Sans, forest green accent, off-white card layout
- `.env` parser handles `OPENAI_API_KEY=sk-...` format and raw `sk-` prefixed keys

## Stretch Challenges (optional)

- Save and display previously generated experiments
- Quick-select list of common household supplies
- Supply substitution suggestions
- Printable observation worksheet output
- Difficulty ratings per experiment
