# Getting started
Before starting any implementation, the agent should read the entire task specification provided by the user. The agent should make sure to understand the requirements and constraints of the task. If the agent is confident that the task is untenable, or if there are any uncertainties about the task spec, the agent should inform the user and ask for guidance before starting any implementation.

The agent should come up with a plan for how to implement the task, breaking it down into smaller sub-tasks if necessary.

The agent should make note of any apparent misspecifications, ambiguities in the spec, or edge cases or surprises that come up during the implementation, and report those to the user in the post-implementation summary and in the PR description.

## Referring to other guidelines
The agent MUST read all of the files in this repository before starting any implementation. The other files contain guidelines and best practices for implementing various types of tasks. The agent should refer to the relevant files as needed during the implementation.

**If the agent is not able to access these files for any reason, the agent must inform the user and halt all work until access is restored.**

# General task guidelines
- Familiarize yourself with the high level project objectives in the project repo's `README.md` (if available), and in the project repo's main documentation files (e.g., `CONTRIBUTING.md`, `DOCS.md`, `AGENTS.md`, etc). Understanding the overall goals and design principles of the project will help you make better implementation decisions that align with the project's vision.
- Guidelines in the project's documentation files take precedence over guidelines in this file. Always prioritize the project's own documented guidelines over the general guidelines provided here.
- Task-specific instructions provided by the user take precedence over both the project's documented guidelines and the general guidelines provided here. Always prioritize the user's specific instructions over all other guidelines.
- When in a chat session (rather than an agentic session), prefer to provide complete code snippets rather than diffs, unless specifically asked for a diff. Moreover, make sure the code snippets come in easily copy-pastable chunks -- complete files are ideal, but short of that, focus on providing complete functions or logical blocks of code. A small snippet within a large code block is hard to use, and often leads to mistakes.
- As an LLM, you are prone to sycophantic behavior, and may try to please the user by agreeing with them even when they are wrong. Be vigilant against this tendency, and always prioritize correctness over pleasing the user. When in doubt, perform online research to verify facts and provide citations to help explain to the user why they may be mistaken.

- When working in a sandboxed agentic session (a cloud session, OpenAI codex, etc), the agent may use any CLI commands or other tools available in the environment to help with the implementation.
- When working in an agentic VSCode session, the agent may use the VSCode interface to navigate the codebase, open files, make edits, copy/rename/remove/move files. However, many CLI commands will NOT be allowed, so the agent should prefer to use VSCode's built-in features whenever possible. In particular, the agent will not be allowed to use CLI commands that destructively modify files on disk (e.g., `rm`, `mv`, `cp`, etc).

# Tests
**Before making any changes to the code, the agent must run all tests to ensure that they pass. If any tests fail, the agent must immediately halt all work and inform the user.**

Refer to `RUST_TESTING.md` for guidelines on writing Rust tests.


# General coding guidelines

## Target size of code files
In general, the agent should aim to keep individual code files under 300 lines of code. If a file is approaching this limit, the agent should consider refactoring the code into smaller modules or files. This helps to keep the codebase manageable and easier to navigate, and makes files fit more easily within LLM context windows. This applies to both implementation code and test code.

