# Getting started
Before starting any implementation, the agent should read the entire specification provided by the user. The agent should make sure to understand the requirements and constraints of the task. The agent should come up with a plan for how to implement the task, breaking it down into smaller sub-tasks if necessary.

The agent should make note of any apparent misspecifications, ambiguities in the spec, or edge cases or surprises that come up during the implementation, and report those to the user in the post-implementation summary and in the PR description.

In most cases, the agent should make a best-effort attempt to implement the task, and inform the user of any uncertainties or issues that arise during the implementation. However, if the agent is confident that the task is untenable, or if there are any uncertainties about the task spec, the agent should inform the user and ask for guidance before starting any implementation.

## Referring to other guidelines
The agent MUST read all of the files in this repository before starting any implementation. The other files contain guidelines and best practices for implementing various types of tasks. The agent should refer to the relevant files as needed during the implementation.

**If the agent is not able to access these files for any reason, the agent must inform the user and halt all work until access is restored.**


# Tests
**Before making any changes to the code, the agent must run all tests to ensure that they pass. If any tests fail, the agent must immediately halt all work and inform the user.**

Refer to `RUST_TESTING.md` for guidelines on writing Rust tests.