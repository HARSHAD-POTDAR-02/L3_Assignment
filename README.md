ISSUES FACED DURING RUNNING SCIRA MCP CHAT LOCALLY AND THE SOLUTIONS

✅ Issue 1: Project Setup and Node/Package Environment
🛠 Initial Setup
Project identified as a Next.js app using TypeScript and pnpm

Checked package.json and overall structure

Created .env.local from .env.example

Required env variables:

OPENAI_API_KEY

DATABASE_URL

XAI_API_KEY

Installed pnpm globally

Installed dependencies using pnpm install

Upgraded Node.js from v18.16.1 to v22.17.0

❌ Issues
Old Node.js version incompatible with dependencies

pnpm not available globally

Network timeouts during package installation

Missing or optional API keys causing errors

Gemini model not showing in UI

✅ Solutions
Upgraded Node.js to resolve compatibility issues

Installed pnpm globally using npm install -g pnpm

Verified network and proxy settings, then retried

Added Gemini as an alternative to OpenAI

Modified logic to make API keys optional

Added Gemini to the model selector config in UI

Used Groq api key to ue the models in the Scria MCP Chat 



✅ Issue 2: Gemini Integration and Multi-Provider Support
🛠 Initial Setup
Installed @ai-sdk/google for Gemini

Set up unified environment with:

GOOGLE_GENERATIVE_AI_API_KEY

Groq API keys

Created a provider system to support Groq and Gemini

Added support for:

Llama 3 8B, Llama 3 70B, Mixtral 8x7B, Qwen QWQ 32B (Groq)

Gemini Pro (Google)

❌ Issues
Google API key loading failed initially

Complex TypeScript types for dynamic model loading

Race conditions during model initialization

Gemini missing in UI dropdown

Poor error messages for missing API keys

✅ Solutions
Standardized to GOOGLE_GENERATIVE_AI_API_KEY with proper error handling

Added strict TypeScript types and used assertions

Restructured model initialization for safe loading

Registered Gemini model in model picker and UI model details

Added user-friendly error messages and logging

🎯 Final Decision: Removed Gemini support and focused only on Groq models for stability.



✅ Issue 3: Gemini Model Error – Thinking Configuration
🛠 Initial Setup
Integrated Gemini support with thinkingConfig (used by Claude)

Attempted to unify configuration across models

❌ Issue
Gemini returned an error:

"Unable to submit request because thinking is not supported by this model"

This was caused by sending thinkingConfig to Gemini, which doesn't support it

✅ Solutions
Initial Fix: Conditioned the thinkingConfig only for Claude and excluded for Gemini

Final Fix: Completely removed thinkingConfig from all Google models

Only Claude and Qwen models retain this setting


✅ Outcome
No more errors with Gemini or other Google models

Clean, future-proof configuration without unsupported parameters

Prevents similar issues for future model integrations

![Screenshot 2025-06-26 195420](https://github.com/user-attachments/assets/96f1991e-ac36-4d6c-8b5b-5625c32d1c20)
![Screenshot 2025-06-26 203320](https://github.com/user-attachments/assets/fb538297-9f95-4aea-95f4-295a2b38784c)
![Screenshot 2025-06-26 203304](https://github.com/user-attachments/assets/bd27c898-94e3-4694-a799-e5de91febb73)
![Screenshot 2025-06-26 203250](https://github.com/user-attachments/assets/1873acc4-2412-4b39-a43c-d268f87ec7f6)
![Screenshot 2025-06-26 203243](https://github.com/user-attachments/assets/1fded80b-bbb7-49de-863f-5de7ce1da7b4)

