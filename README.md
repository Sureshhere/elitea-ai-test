# Quiz CLI

An interactive terminal-based quiz application for practicing JavaScript fundamentals, Node.js fundamentals, and general programming concepts.

The application runs locally with Node.js, uses only built-in Node.js modules, and does not require a database, web server, external API, authentication, or network connection.

## Features

- Interactive command-line quiz experience
- Category selection
- Configurable question count
- Randomized question order
- Numbered multiple-choice answers
- Input validation with retry prompts
- Immediate correct or incorrect feedback
- Correct-answer display for incorrect responses
- Explanations for individual questions
- Visual progress bar and percentage
- Final score and performance feedback
- Review of incorrect answers
- Option to start another quiz
- ANSI terminal styling without an external color library
- Asynchronous loading of question data
- ECMAScript module-based JavaScript

## Technology Stack

- JavaScript
- Node.js 18 or newer
- ECMAScript modules
- JSON
- Node.js built-in modules:
  - `node:fs/promises`
  - `node:url`
  - `node:path`
  - `node:readline`

No runtime or development dependencies are declared in `package.json`.

## Prerequisites

- Node.js version 18 or newer
- An interactive terminal with standard input and output
- A terminal with ANSI escape-sequence support for the intended colors and formatting

Operating-system compatibility was not explicitly specified in the repository. ANSI styling may vary depending on the terminal environment.

## Installation

Clone the repository and change into its directory:

```bash
git clone https://github.com/Sureshhere/elitea-ai-test.git
cd elitea-ai-test
```

No dependency installation is required because the project has no declared dependencies.

Running the following command is optional, but it is not necessary for this project:

```bash
npm install
```

There is no package-manager lockfile in the repository.

## Configuration

No environment configuration is required.

The repository does not contain:

- `.env` or `.env.example` files
- API keys or service URLs
- Authentication configuration
- Database credentials
- Runtime configuration templates

Question data is loaded from:

```text
data/questions.json
```

The application resolves this path relative to `index.js`, rather than relative to the directory from which the command is executed.

## Running the Application

Start the application with:

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

The executable entry point includes a Node.js shebang:

```text
#!/usr/bin/env node
```

Direct execution through the shebang may require executable permissions. `npm start` or `node index.js` are the reliable commands.

## Usage

When the application starts, it:

1. Displays a welcome banner.
2. Lists the available quiz categories.
3. Prompts you to select a category.
4. Prompts you to select the number of questions.
5. Waits for you to press Enter to begin.
6. Presents each question with numbered answer options.
7. Displays immediate feedback and an explanation.
8. Shows progress during the quiz.
9. Displays the final score and percentage.
10. Reviews any incorrect answers.
11. Asks whether you want to play again.

For numeric selections, enter the number corresponding to the desired option. Invalid selections are rejected and the application prompts again.

## Quiz Categories

The bundled question data contains three categories with five questions each:

| Category ID | Display Name | Questions |
|---|---|---:|
| `javascript` | JavaScript Basics | 5 |
| `nodejs` | Node.js Fundamentals | 5 |
| `general` | General Programming | 5 |

There are 15 bundled questions in total.

### JavaScript Basics

Topics include:

- `const`
- Array `push()`
- Strict equality with `===`
- Primitive and non-primitive types
- `typeof null`

### Node.js Fundamentals

Topics include:

- File system APIs
- The event loop
- `npm init`
- `process.argv`
- ES module imports

### General Programming

Topics include:

- APIs
- Recursion
- JSON
- Callback functions
- Version control

## Question Data

Questions are stored in:

```text
data/questions.json
```

The top-level structure contains a `categories` object. Each category includes a display name and a list of questions.

Each question contains:

- `question` — The question text
- `options` — An array of multiple-choice answer strings
- `answer` — The zero-based index of the correct option
- `explanation` — The explanation displayed after answering

A question follows this general structure:

```json
{
  "question": "Which value represents the correct answer?",
  "options": [
    "First option",
    "Second option",
    "Third option"
  ],
  "answer": 1,
  "explanation": "The second option is correct."
}
```

The `answer` value is zero-based. In the example above, `1` refers to the second item in the `options` array.

When adding or modifying questions, ensure that:

- `options` is an array of answer strings.
- `answer` refers to an existing option.
- `explanation` contains the intended feedback text.

The application does not explicitly validate malformed question data, so invalid structures may cause runtime problems or incorrect quiz behavior.

## Score Feedback

The application selects performance feedback based on the final percentage:

| Percentage | Feedback |
|---:|---|
| `100%` | Perfect score |
| `80–99%` | Great job |
| `60–79%` | Good effort |
| `40–59%` | Room for improvement |
| Below `40%` | Keep practicing |

The quiz also displays a 30-character visual progress bar while questions are being answered.

## Project Structure

```text
.
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

### Key Files

#### `index.js`

The application entry point. It:

- Creates the terminal `readline` interface
- Loads `data/questions.json`
- Displays the welcome screen
- Handles category and question-count selection
- Creates and runs a `Quiz`
- Displays results and replay prompts
- Reports errors and closes the readline interface

#### `src/quiz.js`

Defines the `Quiz` class and contains the main quiz logic, including:

- Question shuffling
- Quiz state management
- Score tracking
- Answer evaluation
- Progress calculation
- Feedback and explanations
- Incorrect-answer review

#### `src/input.js`

Provides terminal input helpers:

- `createInterface()`
- `prompt()`
- `select()`
- `confirm()`
- `pressEnter()`

The selection helper validates numeric input and requires users to choose a valid option.

#### `src/colors.js`

Provides ANSI styling and convenience functions such as:

- `red`
- `green`
- `yellow`
- `blue`
- `cyan`
- `magenta`
- `bold`
- `dim`
- `success`
- `error`
- `warning`
- `info`
- `highlight`

#### `data/questions.json`

Contains the quiz categories and question data.

#### `package.json`

Contains project metadata, the ECMAScript module configuration, Node.js engine requirement, and npm scripts.

## Available Commands

### Start the application

```bash
npm start
```

Equivalent command:

```bash
node index.js
```

### Run the test command

```bash
npm test
```

This executes:

```bash
node --test
```

## Testing

The project defines an npm test script, but no test files or test directories were found in the inspected `main` branch.

Therefore:

- `npm test` is the configured test command.
- No repository tests were identified.
- The command was not executed during repository inspection.
- Its runtime result is unverified.

## Build and Deployment

No build step is required.

The repository does not contain:

- A build script
- A bundler
- A transpiler
- Compiled output
- A distribution directory
- A Dockerfile
- Docker Compose configuration
- GitHub Actions workflows
- Cloud hosting configuration
- Process manager configuration
- Infrastructure-as-code files
- Deployment or release scripts

This project is documented as a local terminal application. No deployment procedure is provided.

## Development Notes

The project demonstrates several Node.js and JavaScript concepts, including:

- ECMAScript modules
- Classes
- `async`/`await`
- Promises
- File-system access
- Array methods
- Destructuring
- Template literals
- Error handling
- Terminal input handling
- Fisher–Yates-style question shuffling

The selected question count is taken from the beginning of the selected category’s question list before the quiz’s internal shuffle. If question data is edited, maintain valid zero-based answer indexes and matching options.

## License

`package.json` declares the project license as **MIT**.

No separate `LICENSE` file was found in the repository. Consult the repository metadata or add a formal license file if the project is intended to distribute the MIT license text.

## Known Limitations

- No automated test files are currently present.
- The test command has not been independently verified.
- No explicit operating-system support matrix is provided.
- ANSI color behavior depends on terminal support.
- Direct shebang execution may require executable permissions.
- Question data is not explicitly validated before use.
- No database, network service, authentication, or external API integration is included.
- No deployment or hosting workflow is documented.
