# LLM Switchboard — Specification

## Overview

A single-page web application that lets users send prompts to AI models from OpenAI or Anthropic. Users provide their own API keys, choose a provider and model, and toggle between free-form text output and structured JSON output. The app includes example prompts and schema templates for convenience, and gracefully handles Anthropic's CORS restriction.

---

## Functional Requirements

### 1. API Key Input
- Two input methods supported:
  - **Manual entry:** A text input field (type=`password`) where the user pastes their API key
  - **File upload:** A file input that accepts a `.env` or `.csv` file; the app parses the key from the file contents (e.g., `OPENAI_API_KEY=sk-...`)
- A brief privacy notice is displayed: "Your API key is stored in memory only and is never saved or transmitted outside of the selected provider's API."
- Key is stored in memory only (JavaScript variable) — never sent anywhere except the selected provider's API
- Key is cleared when the page is refreshed or closed
- No key is pre-filled or hardcoded

### 2. Provider & Model Selection
- A dropdown to select the provider: **OpenAI** or **Anthropic**
- A second dropdown for model selection, populated based on the chosen provider:
  - **OpenAI:** `gpt-4o`, `gpt-4o-mini`, `gpt-3.5-turbo`
  - **Anthropic:** `claude-opus-4-6`, `claude-sonnet-4-6`, `claude-haiku-4-5`
- When Anthropic is selected, a visible notice is shown (see CORS Handling below)

### 3. Output Mode Toggle
- A toggle or tab control to switch between two modes:
  - **Unstructured** — the model returns a plain text response
  - **Structured** — the model is instructed to return a response as valid JSON matching a user-defined schema

### 4. Prompt Input
- A textarea where the user types or edits their prompt
- A dropdown of pre-loaded example prompts (selecting one fills the textarea):
  - "Summarize the following text in three bullet points: [paste text here]"
  - "List five creative names for a product that does [describe product]"
  - "Explain this concept to a beginner: [concept]"
  - "Write a short poem about [topic]"
  - "What are the pros and cons of [topic]?"

### 5. Schema Input (Structured Mode Only)
- Visible only when Structured mode is active
- A textarea for the user to define their desired JSON schema
- A dropdown of pre-loaded schema templates (selecting one fills the textarea):
  - **Sentiment Analysis:** `{ "sentiment": "string", "confidence": "number", "summary": "string" }`
  - **Book Info:** `{ "title": "string", "author": "string", "genre": "string", "year": "number" }`
  - **Task List:** `{ "tasks": ["string"], "priority": "string", "deadline": "string" }`
  - **Product Review:** `{ "rating": "number", "pros": ["string"], "cons": ["string"], "verdict": "string" }`
- After a response is received, the app validates that the returned JSON matches the expected keys from the schema and displays a notice if there is a mismatch:
  > "Warning: the response does not fully match the provided schema."

### 6. Submit & Response
- A **Send** button that triggers the API call
- While waiting: button is disabled and shows a loading indicator
- On success: the response is displayed in a read-only output area
  - Unstructured: plain text
  - Structured: pretty-printed JSON (syntax highlighted if possible)
- On error: a clear, human-readable error message is shown in the output area covering:
  - **Invalid API key:** "Authentication failed. Please check your API key."
  - **Rate limit:** "Rate limit reached. Wait a moment before trying again."
  - **Timeout:** "The request timed out. The model may be busy — try again."
  - **CORS (Anthropic):** See CORS Handling section below
  - **Malformed JSON (Structured mode):** "The model returned a response that isn't valid JSON. Try rephrasing your prompt or simplifying your schema."

---

## CORS Handling (Anthropic)

Anthropic's API does not allow calls directly from a browser due to CORS policy. The app handles this gracefully:

- When the user selects **Anthropic** as their provider, a banner is displayed:
  > "Anthropic's API blocks direct browser requests (CORS restriction). The request will be attempted, but may fail depending on your environment. A backend server or proxy would be required for reliable use."
- The app still attempts the request so the user can see the actual error if they are in a permissive environment (e.g., a browser with CORS disabled, or a local dev proxy)
- If the request fails due to CORS, the error message in the output area reads:
  > "Request blocked: Anthropic does not allow direct browser API calls. This is a known CORS limitation, not an issue with your key or prompt."

---

## UI Layout

```
+-----------------------------------------------------+
|  LLM Switchboard                                    |
+-----------------------------------------------------+
|  Provider: [OpenAI v]   Model: [gpt-4o v]          |
|  API Key:  [.....................]                   |
|                                                     |
|  Output Mode: [ Unstructured ] [ Structured ]       |
+-----------------------------------------------------+
|  Example Prompts: [Select a prompt v]               |
|  +---------------------------------------------+   |
|  | Prompt textarea                             |   |
|  +---------------------------------------------+   |
|                                                     |
|  [Structured mode only]                             |
|  Schema Templates: [Select a template v]            |
|  +---------------------------------------------+   |
|  | Schema textarea                             |   |
|  +---------------------------------------------+   |
|                                                     |
|                              [ Send ]               |
+-----------------------------------------------------+
|  Output                                             |
|  +---------------------------------------------+   |
|  | Response appears here                       |   |
|  +---------------------------------------------+   |
+-----------------------------------------------------+
```

---

## Technical Constraints

- Single `index.html` file — no build tools, no frameworks, no backend
- Vanilla JavaScript only
- CSS written inline or in a `<style>` block within the HTML file
- API calls made via `fetch()` directly from the browser
- No API keys stored in localStorage, sessionStorage, or cookies
- No external dependencies except optional CDN-hosted syntax highlighter (e.g., highlight.js)

---

## Stretch Goals (Optional)

These are not required but listed as possible enhancements:

- **Side-by-side comparison** — send the same prompt to two models simultaneously and display responses in columns
- **Response metrics** — show time elapsed, estimated token count, and response length after each call
- **In-memory library** — let users save and name custom prompts and schemas within the session (cleared on refresh)

---

## Out of Scope

- Backend proxy or server
- Streaming responses
- Conversation history / multi-turn chat
- Image or file inputs
- Saving or exporting responses
