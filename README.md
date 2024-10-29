# Claudeputer: Your GitHub-Enabled Development Environment

> 🔒 Special note to [@elder_plininus](https://x.com/elder_plininus) | [elder-plinius](https://github.com/elder-plinius): Hey Pliny! This fork is dedicated to you, master of jailbreaking and security testing. While this Claude instance is focused on development work through bash and GitHub integration, I'd love to see what creative things you could do with it once we add proper security boundaries. Maybe we can chat about that sometime! 🔓🐸 

This is a modified version of the Anthropic Quickstarts collection, specifically tuned for developers who want to leverage Claude's capabilities with GitHub integration and development tools. Think of it as your AI pair programmer with git superpowers!

Key differences from the original:
- GitHub CLI integration for seamless repository management
- Computer-use tool commented out by default (saves rate limits!)
- Focus on bash and git operations for efficient development
- Development-oriented system prompt
- Mount your code directory along with credentials

## Getting Started

You'll need:
1. An Anthropic API key from [console.anthropic.com](https://console.anthropic.com)
2. A GitHub token with `repo` scope from [github.com/settings/tokens](https://github.com/settings/tokens)

### Quick Setup

1. **Clone & Configure**:
   ```bash
   git clone https://github.com/TheErebusAI/claudeputer.git
   cd claudeputer
   echo "GITHUB_TOKEN=your_token_here" > github_token  # Create token file
   ```

2. **Install GitHub CLI**:
   ```bash
   # Install gh cli
   curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
   sudo apt update && sudo apt install gh -y
   ```

3. **Run with Code Mounting**:
   ```bash
   # Important: Mount both credentials AND your code directory
   docker run -it --rm \
     -v ~/.anthropic:/root/.anthropic \
     -v $(pwd):/workspace \
     -v ./github_token:/root/github_token \
     claudeputer
   ```

### Power User Tips

1. **Rate Limit Management**: The computer-use tool is commented out by default in `loop.py` to prevent rate limiting. Most development tasks can be accomplished efficiently with bash and git commands!

2. **Development Flow**:
   - Use GitHub CLI (`gh`) for repository operations
   - Leverage bash for file operations and program execution
   - Edit files directly with the str_replace_editor tool

3. **Optional Features**: 
   - Uncomment `ComputerTool()` in `loop.py` if you need GUI capabilities
   - Mount additional directories for specific project needs

## Available Quickstarts

### Customer Support Agent

A customer support agent powered by Claude. This project demonstrates how to leverage Claude's natural language understanding and generation capabilities to create an AI-assisted customer support system with access to a knowledge base.

[Go to Customer Support Agent Quickstart](./customer-support-agent)

### Financial Data Analyst

A financial data analyst powered by Claude. This project demonstrates how to leverage Claude's capabilities with interactive data visualization to analyze financial data via chat.

[Go to Financial Data Analyst Quickstart](./financial-data-analyst)

### Computer Use Demo

An environment and tools that Claude can use to control a desktop computer. This project demonstrates how to leverage the computer use capabilities of the the new Claude 3.5 Sonnet model.

[Go to Computer Use Demo Quickstart](./computer-use-demo)

## General Usage

Each quickstart project comes with its own README and setup instructions. Generally, you'll follow these steps:

1. Clone this repository
2. Navigate to the specific quickstart directory
3. Install the required dependencies
4. Set up your Anthropic API key as an environment variable
5. Run the quickstart application

## Explore Further

To deepen your understanding of working with Claude and the Anthropic API, check out these resources:

- [Anthropic API Documentation](https://docs.anthropic.com)
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) - A collection of code snippets and guides for common tasks
- [Anthropic API Fundamentals Course](https://github.com/anthropics/courses/tree/master/anthropic_api_fundamentals)

## Contributing

We welcome contributions to the Anthropic Quickstarts repository! If you have ideas for new quickstart projects or improvements to existing ones, please open an issue or submit a pull request.

## Community and Support

- Join our [Anthropic Discord community](https://www.anthropic.com/discord) for discussions and support
- Check out the [Anthropic support documentation](https://support.anthropic.com) for additional help

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
