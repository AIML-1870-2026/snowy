# Blackjack Agent — Spec

## Objective

Build a static, browser-based Blackjack game where an AI agent uses an LLM to recommend whether to hit or stand based on the current game state.

## Deliverables

1. **Static webpage** (`index.html`) — HTML, CSS, and JavaScript only. No server, Node.js, or npm. Runs entirely in the browser and is deployed to the class GitHub organization.

2. **Full Blackjack mechanics:**
   - Deck creation and shuffling
   - Dealing cards to player and dealer
   - Accurate scoring (Ace = 1 or 11)
   - Win/loss/bust/push detection
   - Balance tracking

3. **AI agent integration:**
   - OpenAI only (no Anthropic — CORS limitation)
   - API key loaded via `.env` file upload, stored in memory only, never persisted
   - Agent receives: player's full hand + dealer's visible (face-up) card
   - Agent returns a **structured JSON response** to avoid keyword-search ambiguity
     - Example: `{ "action": "hit", "reasoning": "..." }`
   - Game executes the recommended action and updates state

4. **Structured JSON output (critical):**
   - Do NOT parse the action by keyword-searching the response text
   - A plain-text response like "you should not hit, you should stand" contains both keywords and breaks keyword matching
   - Prompt the LLM to respond only in JSON; read `response.action` directly

5. **Console logging:**
   - Log the full prompt sent to the LLM and the raw response received
   - Useful for debugging and understanding agent behavior

6. **Reference folder:**
   - `temp/` contains the LLM Switchboard for reference on: `.env` parsing, `fetch()` structure for OpenAI API calls, and error handling patterns
   - **Do NOT deploy `temp/` to GitHub Pages**

## Technical Notes

- OpenAI-only due to CORS — Anthropic blocks direct browser requests
- Interface style matches prior projects: IBM Plex Sans, forest green accent, off-white card layout
- `.env` parser handles `OPENAI_API_KEY=sk-...` format and raw `sk-` prefixed keys

## Stretch Challenges (optional, 2+ required)

- Strategy visualization — show basic strategy chart and highlight current hand
- Performance analytics — track win/loss record, AI accuracy over multiple hands
- Explainability controls — toggle verbose vs. brief AI reasoning display
- Risk tolerance settings — let user set conservative/neutral/aggressive style and pass it to the AI
