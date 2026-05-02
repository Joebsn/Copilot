# Copilot-instructions.md
Custom instructions tell the AI about your coding preferences and standards. These apply automatically to all chat interactions.

# Custom agents
Custom agents create specialized AI personas for specific tasks.
In the custom agent definition, you can define the AI's role, specific guidelines, and which tools it can use.

For example, "Reviewer" agent focuses on analysis and providing feedback on code.

# SubAgents

Use "user-invocable: false" so that the agent is a subagent and cannot bel called directly.

To invoke a subagent inside a prompt file, ensure that the runSubagent or agent tool is included in the tools frontmatter property.

Examples: TDD.agent.md, RecursiveProcessor.agent.md, FeatureBuilder.agent.md, BetterReviewer.agent.md calls SubAgents

# Skills
Teach the agent new capabilities for a specific domain or task.

# Hooks
Run custom commands at specific lifecycle points in the agent loop

# Tools
Tools extend agents in Visual Studio Code with specialized functionality for accomplishing specific tasks like searching code, running commands, fetching web content, or invoking APIs.
VS Code supports three types of tools: built-in tools, Model Context Protocol (MCP) tools, and extension tools.

Call with # when writing a command to the agent.
