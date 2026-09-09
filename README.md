# Quiz CLI

An interactive command-line quiz game for learning JavaScript and programming fundamentals. The application runs in a Node.js terminal, presents programming questions by category, provides immediate feedback and explanations, tracks progress, and displays a final score.

## Features

- Interactive terminal-based gameplay
- Programming quiz categories:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Quiz length selection:
  - All available questions
  - Three questions when at least three are available
  - Five questions when at least five are available
- Randomized question order
- Numbered answer selection
- Input validation and retry prompts
- Immediate correct or incorrect feedback
- Question explanations
- Visual progress bar
- Score and percentage calculation
- Performance messages based on the final percentage
- Review of incorrect answers
- Option to start another quiz
- ANSI-colored terminal output
- No external runtime dependencies

## Technologies

- JavaScript
- Node.js
- ECMAScript modules
- JSON
- Node.js built-in modules:
  - `node:fs/promises`
  - `node:url`
  - `node:path`
  - `node:readline`

This is a standalone Node.js CLI application and does not use an application framework.

## Requirements

- Node.js `18.0.0` or newer
- An interactive terminal capable of reading standard input

The application uses Node.js `readline` for user interaction. It emits ANSI color codes directly; color rendering behavior on terminals without ANSI support has not been separately verified.

## Project Structure

```text
.
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

- `index.js`  
  Application entry point. Loads the question data, creates the terminal interface, handles category and quiz-length selection, runs the quiz, displays results, and manages replay and errors.

- `src/quiz.js`  
  Defines the `Quiz` class, including question randomization, answer tracking, progress reporting, scoring, feedback, and incorrect-answer review.

- `src/input.js`  
  Provides terminal input helpers for prompts, numbered selections, yes/no confirmations, and waiting for Enter.

- `src/colors.js`  
  Provides ANSI color and text-style helpers without external dependencies.

- `data/questions.json`  
  Contains the quiz categories and questions.

- `package.json`  
  Contains package metadata, the Node.js version requirement, npm scripts, module configuration, and license information.

The repository also contains a `.DS_Store` macOS metadata file, which is not used by the application.

## Setup

Clone the repository and enter its directory:

```bash
git clone https://github.com/Sureshhere/elitea-ai-test.git
cd elitea-ai-test
```

The project declares no external npm dependencies, so no dependency installation is required for the application to run. If desired, you may still run:

```bash
npm install
```

No lockfile was found in the repository.

The bundled question data is expected at:

```text
data/questions.json
```

This file is included in the repository and is loaded automatically relative to `index.js`.

## Configuration

No environment variables or configuration files are required according to the repository contents.

The application does not require:

- API keys
- Tokens
- Passwords
- Database configuration
- External services

Do not add secrets to the question data or source files.

## How to Run

Start the quiz with the defined npm script:

```bash
npm start
```

This runs:

```bash
node index.js
```

You can also start the application directly with:

```bash
node index.js
```

The program will:

1. Display a welcome banner.
2. Ask you to choose a quiz category.
3. Ask you to choose the number of questions.
4. Present questions with numbered options.
5. Provide immediate feedback and explanations.
6. Display progress throughout the quiz.
7. Show your score and performance message.
8. Review incorrect answers when applicable.
9. Ask whether you want to play again.

The entry point includes a Unix-style Node.js shebang, but executable file permissions were not verified. Running `node index.js` or `npm start` is therefore the documented usage.

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

This runs Node.js’s built-in test runner:

```bash
node --test
```

## Question Data Format

Quiz content is stored in `data/questions.json`.

The top-level structure contains a `categories` object. Each category has a display name and a list of questions:

```json
{
  "categories": {
    "category-id": {
      "name": "Category display name",
      "questions": [
        {
          "question": "Question text",
          "options": [
            "Option 1",
            "Option 2",
            "Option 3"
          ],
          "answer": 0,
          "explanation": "Explanation text"
        }
      ]
    }
  }
}
```

### Fields

- `categories`  
  Object containing the available category entries.

- Category ID  
  Identifier used by the application for a category, such as `javascript`, `nodejs`, or `general`.

- `name`  
  Display name shown to the user.

- `questions`  
  Array of question objects.

- `question`  
  The question text displayed during the quiz.

- `options`  
  Array of possible answers displayed as numbered choices.

- `answer`  
  Zero-based index of the correct answer within the `options` array. For example, `0` identifies the first option.

- `explanation`  
  Explanation shown after the user answers. The application supports displaying this field when present.

### Bundled Categories

| Category ID | Display name | Questions |
|---|---|---:|
| `javascript` | JavaScript Basics | 5 |
| `nodejs` | Node.js Fundamentals | 5 |
| `general` | General Programming | 5 |

The repository contains 15 bundled questions in total.

When modifying or adding questions, the `answer` value must correspond to a valid zero-based position in that question’s `options` array. Validation behavior for malformed custom question data is not documented or separately verified.

## How the Quiz Works

Questions are copied and shuffled using a Fisher-Yates-style algorithm before the quiz begins. The original input array is not modified.

For each question, the application:

1. Displays the current progress.
2. Displays the question and its answer options.
3. Prompts for a numbered answer.
4. Compares the selected option index with the `answer` index.
5. Records the response.
6. Displays correctness feedback.
7. Displays the explanation when available.
8. Advances to the next question.

At the end, the application displays the category, score, percentage, and a performance message:

- `100%`: Perfect score
- `80–99%`: Great job
- `60–79%`: Good effort
- `40–59%`: Room for improvement
- Below `40%`: Keep practicing

Incorrect-answer reviews show the selected answer and the correct answer.

## Dependencies

No external npm dependencies are declared in `package.json`.

The application uses only Node.js built-in modules and local source files. The project is configured as an ECMAScript module package through:

```json
{
  "type": "module"
}
```

## Build

No build step is defined or required by the repository contents.

The repository contains:

- No build script
- No transpiler
- No bundler
- No compiled output

## Testing Status

The package defines the following test command:

```bash
npm test
```

It invokes Node.js’s built-in test runner:

```bash
node --test
```

No test files or test directories were found in the inspected repository. As a result, the repository does not currently contain an implemented automated test suite.

The result of executing `npm test` was not independently verified. This README does not claim that the test command passes.

## License

The `package.json` metadata identifies the project as licensed under the **MIT License**.

No separate license file was found in the inspected repository. Refer to the repository metadata and package configuration for the declared license.

## Limitations and Unknowns

The following details were not verified through execution or repository configuration:

- Actual runtime behavior of `npm start`
- Actual output of `npm test`
- Whether any tests are discovered by Node’s test runner
- ANSI color rendering across different terminal environments
- Executable permissions for `index.js`
- Supported operating systems
- Manual testing status
- Validation behavior for malformed or custom question data
- Deployment or release procedures
- CI/CD behavior
- Whether GitHub explicitly marks `main` as the default branch

The repository contains no verified:

- Automated test files
- README or other documentation files
- Environment template
- Docker or container configuration
- GitHub Actions workflow
- Deployment configuration
- Database or migration files
- Contribution guidelines
- Changelog

## Repository

[https://github.com/Sureshhere/elitea-ai-test](https://github.com/Sureshhere/elitea-ai-test)