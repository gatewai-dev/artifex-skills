# @gatewai.studio/artifex-skills

<p align="center">
  <img src="https://raw.githubusercontent.com/gatewai-dev/Gatewai/main/packages/artifex-skills/assets/logo.png" alt="Gatewai Logo" width="128" />
</p>

> **The Ultimate GPU Harness & AI Canvas Node Skills for Autonomous Agents**

`@gatewai.studio/artifex-skills` is the official, bundled skill package containing structured markdown instructions (`SKILL.md`), triggers, and capability metadata for Gatewai Artifex—the ultimate GPU harness and media rendering engine built for AI agents. 

It teaches AI agents (such as Claude Code, Cursor, MCP callers, or custom agency scripts) how to leverage local GPU capabilities to programmatically compose, validate, configure, and render target media output using the Artifex CLI.

---

## 🚀 Experience workflows on the Infinite Canvas

While the CLI executes canvases headlessly, you can visually build, interact, and preview your nodes, custom shaders, and audio pipelines on the state-of-the-art **Gatewai Infinite Canvas** with the help of our AI Agent.

👉 **Build and see your assets in real-time at [gatewai.studio](https://gatewai.studio)**

---

## 📦 Installation & Integration

### A. Vercel Skills CLI
To install this capability to your agent workspace:
```bash
npx skills add gatewai-dev/artifex-skills
```

### B. TanStack Intent (@tanstack/intent)
For package-bundled intent mappings, add this library to your package dependencies and configure your `package.json`:
```json
{
  "intent": {
    "skills": ["@gatewai.studio/artifex-skills"]
  }
}
```
Then run:
```bash
npx @tanstack/intent install
```

### C. Manual Usage
AI agents can read the core skill instructions at [SKILL.md](./SKILL.md) and individual node capabilities located inside the [references/](./references) directory.

---

## 🛠 Prerequisites

- **Node.js**: Version 22 or higher.
- **GPU Harness**: Access to WebGPU compatible drivers for offline hardware-accelerated renders.
- **API Keys**:
  - `GATEWAI_FAL_API_KEY`: Required for generative media nodes (`ImageGen`, `VideoGen`, etc.)
  - `GATEWAI_OPENROUTER_API_KEY`: Required for advanced LLM and text processing nodes.
