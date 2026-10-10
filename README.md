# PathForge AI — Hackathon MVP

An interactive, AI-powered career roadmap built with Next.js, React Flow, and an OpenAI-compatible API. Designed for a 4-hour hackathon build.

## Features
- User-defined dream role, study hours/week, deadline, and known skills
- React Flow graph with pan, zoom, draggable nodes, edges, and minimap
- AI-generated roadmap via `/api/roadmap`
- Milestone details, portfolio proof, prerequisites, resources, and completion progress
- Milestone-specific action plan and interview questions via `/api/action-plan`
- Demo fallback when no API key is configured

## Requirements
- Node.js 20 or later (Node 24 should work)
- npm
- Optional: OpenAI API key with API access/credits

## Run locally
1. Extract the ZIP.
2. Open the extracted `pathforge-ai` folder in VS Code.
3. Open a terminal in that folder and run:

   ```bash
   npm install
   ```

4. Copy `.env.example` to `.env.local`.
5. Add your API key to `.env.local`:

   ```env
   OPENAI_API_KEY=your_real_api_key
   OPENAI_MODEL=gpt-4o-mini
   ```

   Do not share your key or commit `.env.local` to GitHub.

6. Start the app:

   ```bash
   npm run dev
   ```

7. Open http://localhost:3000

### If you do not have an API key
Leave `.env.local` absent or leave `OPENAI_API_KEY` empty. The app runs in demo mode with a goal-adapted fallback roadmap and working graph interactions. The demo fallback is not the same as live AI generation; use a valid API key to satisfy a strict requirement for an AI-generated roadmap.

## Four-hour demo flow
1. Enter a specific role and constraints.
2. Click **Generate path** and explain the generated nodes and prerequisite edges.
3. Select a node and show the portfolio deliverable and resources.
4. Click **AI action plan** to generate milestone-specific steps and interview questions.
5. Mark a milestone complete and show the updated progress and green dependency edge.
6. Try a different target role to demonstrate goal-specific generation.

## Architecture
- `app/page.tsx`: dashboard, graph layout, selection, progress state
- `app/api/roadmap/route.ts`: structured career roadmap generation and fallback
- `app/api/action-plan/route.ts`: milestone-specific action plan generation
- `app/globals.css`: visual design

## Important notes
- AI-generated estimates and recommendations should be checked against real job descriptions.
- The demo fallback exists for UI development and judging rehearsal, not as evidence of live AI output.
- For deployment, configure `OPENAI_API_KEY` and `OPENAI_MODEL` in your hosting provider's environment settings.
