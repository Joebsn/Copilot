# Copilot

## Custom instructions

### General Instructions

Custom instructions tells the AI about your coding preferences and standards. These apply automatically to all chat interactions.
Example Copilot-instructions.md.

### File based instructions

For targeted rules, create file-based *.instructions.md files for specific parts of your codebase, such as language conventions or framework patterns.

applyTo: tests/** applies the instrcutions for tests directories only.

### Generate customizations with AI

Type /create-prompt, /create-instruction, /create-skill, /create-agent, or /create-hook in chat to generate customization files with AI assistance.

## Agents

### Custom agents

Custom agents create specialized AI personas for specific tasks.

Each agent defines its own behavior, available tools, and language model preferences.

In the custom agent definition, you can define the AI's role, specific guidelines, and which tools it can use.

For example, "Reviewer" agent focuses on analysis and providing feedback on code.

### SubAgents

Use "user-invocable: false" so that the agent is a subagent and cannot bel called directly.

To invoke a subagent inside a prompt file, ensure that the runSubagent or agent tool is included in the tools frontmatter property.

Examples: TDD.agent.md, RecursiveProcessor.agent.md, FeatureBuilder.agent.md, BetterReviewer.agent.md calls SubAgents

### HandOff

Handoffs enable you to create guided sequential workflows that transition between agents with suggested next steps. 

Example: handoff.agent.md.

## Prompt files

Create prompt files for repeatable tasks you run often, like scaffolding a component or preparing a pull request.

Unlike custom instructions that are applied automatically, you invoke prompt files manually in chat.

In the chat use "/" to call the created prompt.

For more complex multi-step workflows that involve scripts and external tools, package them as agent skills.

## Skills

Agent Skills are folders of instructions, scripts, and resources that GitHub Copilot can load when relevant to perform specialized tasks.

It teaches the agent new capabilities for a specific domain or task.

Stored in SKILL.md files.

Skills appears in the chat when writing "/"

## Hooks

Run custom commands at specific lifecycle points in the agent sessions.

## Tools

Tools extend agents in Visual Studio Code with specialized functionality for accomplishing specific tasks like searching code, running commands, fetching web content, or invoking APIs.

VS Code supports three types of tools: built-in tools, Model Context Protocol (MCP) tools, and extension tools.

Call with # when writing a command to the agent.

## Context engineering

Provide AI agents with targeted project information to improve the quality and accuracy of generated code.

By curating essential project context through custom instructions, implementation plans, and coding guidelines, you enable AI to make better decisions, improve accuracy, and maintain persistent knowledge across interactions.

### Step 1: Curate project-wide context

To ground the AI agent in the specifics of the project, collect key project information like product vision, architecture, and other relevant documentation and add it as chat context via custom instructions.

By using custom instructions, you ensure that the agent consistently has access to this context and doesn't have to re-learn it for each chat interaction.

Example: copilot-instructions.md

### Step 2: Create implementation plan

Once you have the project-specific context in place, you can use AI to prompt the creation of an implementation plan for a new feature or bug fix.

With a custom agent for planning, you can create a dedicated persona with planning-specific guidelines and tools (for example, read-only access to the codebase).

Example: plan-template.md to define the structure and sections of the implementation plan document and plan.agent.md to create the agent.

### Step 3: Generate implementation code

Use AI to implement the feature by generating code from the implementation plan.

## Context for AI using "#"

In the chat use "#" to add files, folders ... as context, for example:

"What are the highlights of the latest VS Code release #fetch".

"Update the asp.net app to .net 9 #fetch https://learn.microsoft.com/en-us/aspnet/core/migration/80-90".

Explain how authentication works in #codebase

Where is the database connection string configured? #codebase

Summarize the #changes

Fix the issues in #problems

## Chat participants using "@"

Chat participants are specialized assistants that enable you to ask domain-specific questions in chat.

Imagine a chat participant as a domain expert to whom you hand off your chat request and it takes care of the rest.

For example @vscode participant has knowledge about VS Code and its extension APIs.

VS Code has built-in chat participants which are optimized to answer questions about their respective domains. For example:

"@vscode how to enable word wrapping".

"@terminal what are the top 5 largest files in the current directory"

Chat participants can be used with "/" commands:

@workspace /explain the feature.

A custom Chat participant can be created and a command for it can be specified.

For example @tutor /exercise stacks (will teach about stack)
