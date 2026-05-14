# Contributing to Gitbun

First off, thank you for considering contributing to Gitbun! We are participating in **GSSoC '24**, and we want to make your open-source journey as smooth as possible.

##  System Architecture

To help you understand how Gitbun works before you write code, here is a breakdown of the pipeline.

Gitbun operates in 5 main stages (You can see this in `src/index.ts`):
1. **Validation (`src/git/`)**: Checks if you are in a repo and have staged files.
2. **Extraction (`src/git/`)**: Pulls the diff stats (additions/deletions).
3. **Heuristics (`src/analyzer/`)**: Our rule-based engine. It detects the `scope` (folder names), `type` (feat, fix, refactor), and generates a baseline commit message *without* needing the internet.
4. **AI Enhancement (`src/llm/`)**: If enabled and Ollama/API is running, we pass the baseline message to an LLM to make it human-like and descriptive.
5. **UI & Commit (`src/ui/`)**: Prompts the user using Inquirer and executes the git command.

##  Development Workflow

### 1. Branch Naming Convention
Please create a branch for your work. Use the following prefixes:
- `feat/your-feature-name` (for new features)
- `fix/bug-description` (for bug fixes)
- `docs/what-you-changed` (for documentation)

### 2. Running the CLI Locally
You do not need to build the project every time you make a change. Use `ts-node` to run the code:
```sh
npm install
npm run dev

```

### 3. Testing

We use Vitest. Please ensure you write tests for any new analyzer rules or utility functions.

```sh
npm test

```

### 4. Making a Pull Request

1. Ensure your code is formatted and passes linting (`npm run lint`).
2. Write a clear PR description explaining *what* you changed and *why*.
3. Link the PR to an active issue (e.g., "Fixes #12").
4. Wait for a maintainer to review!

##  Frontend Contributions

If you are working on the Next.js playground (`frontend/`):

* All UI components are in `src/components/ui/`.
* Colors and themes are strictly defined in `src/styles/palette.ts`. Please use these tokens (`cream`, `steel`, `ink`) instead of raw hex codes.
