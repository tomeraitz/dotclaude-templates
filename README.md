<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="https://i.imgur.com/ZG0iECp.png" alt="dotclaude logo"></a>
</p>

<h3 align="center">dotclaude-templates</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![GitHub Issues](https://img.shields.io/github/issues/tomeraitz/dotclaude-templates.svg)](https://github.com/tomeraitz/dotclaude-templates/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/tomeraitz/dotclaude-templates.svg)](https://github.com/tomeraitz/dotclaude-templates/pulls)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---

<p align="center"> Production-ready .claude templates for Claude Code: custom agents, commands, hooks, and skills to supercharge your AI-powered development workflow.
    <br>
</p>

## 🧐 About the Project

**dotclaude-templates** is a production-ready collection of `.claude` templates that extend Claude Code's capabilities through the `.claude/` directory structure. Think of it as your AI development toolkit - reusable, shareable, and designed to supercharge your workflow.

Here's why you should use it:

- **Save Time**: Create production-ready custom agents in 2-5 minutes instead of hours
- **Consistency**: Share the same standards, patterns, and SOPs across your entire team
- **Safety**: Built-in constraints prevent common mistakes and security issues
- **Flexibility**: Works with any tech stack - Backend, Frontend, DevOps, ML, and more

Use this repository as a starting point - fork it, customize it, and make it your own!

## 🏁 Getting Started

### Prerequisites

[Claude Code](https://docs.claude.com/en/docs/claude-code) installed

### Installation

**Step 1: Clone the repository**

```bash
git clone https://github.com/tomeraitz/dotclaude-templates.git
cd dotclaude-templates
```

**Step 2: Copy `.claude/` to your project**

On Linux/macOS:
```bash
cp -r .claude/ /path/to/your/project/.claude/
```

On Windows:
```cmd
xcopy .claude /path/to/your/project/.claude/ /E /I
```


## 📚 Documentation

- **[Custom Agent Command Guide](docs/custom-agent.doc.md)** - Complete guide to creating custom agents with the `/custom-agent` command
- **[Hooks Guide](docs/hooks-guide.md)** - Understanding and configuring hooks in `.claude/settings.json` for automated workflows

---

