# mcp-studio

> Visual builder for Model Context Protocol (MCP) servers. Define tools, auto-generate Python and TypeScript boilerplate, deploy in minutes.

[![MCP Compatible](https://img.shields.io/badge/MCP-compatible-blue)](https://modelcontextprotocol.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Open Source](https://img.shields.io/badge/Open%20Source-yes-brightgreen)](https://github.com/Fefefrost5/mcp-studio)

![mcp-studio screenshot](docs/screenshot.png)

## What is MCP?

[Model Context Protocol (MCP)](https://modelcontextprotocol.io) is the open standard adopted by Anthropic, OpenAI, Google, and Microsoft to connect AI models to external tools and data. As of 2026, it has 97M+ monthly SDK downloads and 81k GitHub stars.

**Problem**: Building an MCP server still requires writing Python/TypeScript boilerplate from scratch, setting up transport layers, and manually crafting tool definitions.

**mcp-studio** solves this.

## Features

- 🎨 **Visual tool builder** — define tools and parameters with a clean UI
- ⚡ **Instant code generation** — Python (FastMCP) and TypeScript (official SDK)
- 📄 **Auto README** — production-ready documentation generated automatically
- 📦 **Zero dependencies** — pure HTML/JS, works offline, no install needed
- 🌐 **Self-hosted or browser** — deploy on GitHub Pages or run locally

## Quick Start

### Option 1: Use online (GitHub Pages)

Visit: `https://Fefefrost5.github.io/mcp-studio`

### Option 2: Run locally

```bash
git clone https://github.com/Fefefrost5/mcp-studio
cd mcp-studio
# Open index.html in your browser — no server needed
open index.html
```

### Option 3: Self-host with Docker

```bash
docker run -p 8080:80 ghcr.io/Fefefrost5/mcp-studio
```

## How It Works

1. **Configure** your server (name, description, version)
2. **Add tools** with parameters, types, and descriptions
3. **Generate** Python or TypeScript code
4. **Copy** and deploy — your MCP server is ready

## Generated Code Example

Given a tool `get_weather(city: str, units: str = "celsius") -> dict`, mcp-studio generates:

**Python (FastMCP)**
```python
from fastmcp import FastMCP

mcp = FastMCP("weather-tools")

@mcp.tool()
def get_weather(city: str, units: str = None) -> dict:
    """
    Get current weather for a city

    Args:
        city (str): City name
        units (str): celsius or fahrenheit (optional)
    """
    # TODO: implement
    raise NotImplementedError("get_weather not yet implemented")

if __name__ == "__main__":
    mcp.run()
```

**TypeScript (official SDK)**
```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { z } from "zod";

const server = new McpServer({ name: "weather-tools", version: "0.1.0" });

server.tool(
  "get-weather",
  "Get current weather for a city",
  {
    city: z.string().describe("City name"),
    units: z.string().optional().describe("celsius or fahrenheit"),
  },
  async ({ city, units }) => {
    // TODO: implement
    throw new Error("get_weather not yet implemented");
  }
);

server.run();
```

## Deploying to Claude Desktop

After generating and implementing your server:

```json
{
  "mcpServers": {
    "my-server": {
      "command": "python",
      "args": ["/path/to/server.py"]
    }
  }
}
```

## Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md).

## Roadmap

- [ ] Resources builder (MCP Resources tab)
- [ ] Prompts builder (MCP Prompts tab)
- [ ] Remote server deploy (one-click to Render/Railway)
- [ ] Template gallery (30+ ready-to-use templates)
- [ ] VS Code extension
- [ ] CLI: `npx mcp-studio init`

## License

MIT — see [LICENSE](LICENSE)

---

Built with ❤️ to make MCP accessible to every developer.
