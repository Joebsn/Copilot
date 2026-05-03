# Copilot

## Custom instructions

### General Instructions

Custom instructions tells the AI about your coding preferences and standards. These apply automatically to all chat interactions.
Example Copilot-instructions.md.

### File based instructions

For targeted rules, create file-based *.instructions.md files for specific parts of your codebase, such as language conventions or framework patterns.

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

VS Code has built-in chat participants which are optimized to answer questions about their respective domains. For example:

"@vscode how to enable word wrapping"

"@terminal what are the top 5 largest files in the current directory"
