# Quiz CLI

An interactive Node.js command-line quiz for practicing JavaScript, Node.js, and general programming fundamentals.

The application runs in a terminal, presents multiple-choice questions, provides immediate feedback and explanations, tracks quiz progress and scores, reviews incorrect answers, and lets users start another quiz.

## Technologies

- JavaScript
- Node.js 18 or newer
- ECMAScript modules
- JSON
- Node.js built-in modules:
  - `node:fs/promises`
  - `node:url`
  - `node:path`
  - `node:readline`
- ANSI terminal escape sequences for styling

The project has no external runtime or development dependencies.

## Project Structure

```text
.
├── .DS_Store
├── README.md
├── data/
│   └── questions.json
├── index.js
├── package.json
└── src/
    ├── colors.js
    ├── input.js
    └── quiz.js
```

### Important Files

- `index.js` — Application entry point and interactive quiz loop.
- `package.json` — Project metadata, npm scripts, ECMAScript module configuration, license metadata, and Node.js version requirement.
- `data/questions.json` — Bundled quiz categories and questions.
- `src/quiz.js` — Quiz state, question shuffling, answer evaluation, progress rendering, result display, and incorrect-answer review.
- `src/input.js` — Terminal input, numbered selection, confirmation, and prompt helpers.
- `src/colors.js` — ANSI color and text-style utilities.
- `.DS_Store` — macOS filesystem metadata; it is not used by the application.

## Prerequisites

- Node.js 18 or newer
- An interactive terminal with standard input and output
- A terminal capable of displaying ANSI escape sequences for the intended color formatting

The application does not require:

- Environment variables
- API keys or authentication tokens
- Passwords
- Database credentials
- External services
- Network access

## Setup

Clone the repository and move into its directory:

```bash
git clone https://github.com/Sureshhere/elitea-ai-test.git
cd elitea-ai-test
```

No package installation is required because `package.json` does not declare any dependencies. If desired, you can run:

```bash
npm install
```

No lockfile is included in the repository.

## Configuration

No environment variables or configuration files are required.

The application loads its question data from:

```text
data/questions.json
```

The path is resolved relative to the application module, so the question file is not dependent on the current working directory.

### Question Data Format

The question file contains a top-level `categories` object. Each category has a category identifier, a display name, and a list of questions.

Each question contains:

- `question` — The question text.
- `options` — An array of answer choices.
- `answer` — The zero-based index of the correct option.
- `explanation` — The explanation shown after the user answers.

The `answer` index must correspond to an item in the `options` array.

## How to Run

Start the application using npm:

```bash
npm start
```

This runs:

```bash
node index.js
```

You can also run the entry point directly:

```bash
node index.js
```

The application flow is:

1. Select a quiz category.
2. Select the number of questions.
3. Press Enter to begin.
4. Answer each question using its option number.
5. Review immediate correctness feedback and explanations.
6. View progress during the quiz.
7. Review the final score, percentage, and incorrect answers.
8. Choose whether to play again.

The available question-count options depend on how many questions exist in the selected category. The application offers all questions, plus three- and five-question options when enough questions are available.

## Key Features

- Interactive terminal-based quiz experience.
- Categories for:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Fifteen bundled questions in total.
- Category selection.
- Configurable question count.
- Numbered answer input with validation and retry prompts.
- Randomized question order using a Fisher–Yates-style shuffle.
- Immediate correct or incorrect feedback.
- Explanations after answering.
- Thirty-character visual progress bar.
- Score and percentage calculation.
- Performance messages:
  - `100%` — Perfect score
  - `80–99%` — Great job
  - `60–79%` — Good effort
  - `40–59%` — Room for improvement
  - Below `40%` — Keep practicing
- Incorrect-answer review showing the selected and correct answers.
- Replay option after completing a quiz.
- ANSI terminal colors and text styles without an external color library.
- Error handling with a stack trace and exit status `1`.
- Readline cleanup in a `finally` block.

## Bundled Categories

| Category ID | Display Name | Questions |
|---|---|---:|
| `javascript` | JavaScript Basics | 5 |
| `nodejs` | Node.js Fundamentals | 5 |
| `general` | General Programming | 5 |

The bundled questions cover topics including:

- JavaScript constants, arrays, strict equality, primitive types, and `typeof null`
- Node.js filesystem APIs, event loop behavior, npm initialization, `process.argv`, and ES module imports
- APIs, recursion, JSON, callbacks, and version control

## Available Commands

| Command | Description |
|---|---|
| `npm start` | Starts the interactive quiz using `node index.js`. |
| `node index.js` | Runs the application directly. |
| `npm test` | Runs Node.js’s built-in test runner with `node --test`. |

## Build

No build step is required or defined.

The repository contains:

- No build script
- No bundler
- No transpiler
- No compiled output

## Testing

The project defines the following test command:

```bash
npm test
```

This executes:

```bash
node --test
```

No test files or test directories are currently present in the repository. The test command was not executed during repository inspection, so its runtime result has not been independently verified.

## License

The project declares the MIT license in `package.json`. A separate license file was not found in the repository.

## Limitations and Notes

- Supported operating systems were not specified in the repository.
- ANSI color rendering may vary depending on the terminal environment.
- Direct execution through the Node.js shebang depends on executable permissions being configured; `npm start` and `node index.js` are the reliable commands.
- Behavior with malformed or customized question data has not been independently verified.
- No deployment or release procedure is included.
- No database, container, CI/CD, or hosting configuration is included.
