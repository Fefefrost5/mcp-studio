# Contributing to mcp-studio

Thank you for your interest in contributing! 🎉

## Quick start

```bash
git clone https://github.com/YOUR_HANDLE/mcp-studio
cd mcp-studio
open index.html  # no build step needed
```

## Ways to contribute

- 🐛 **Bug reports** — open an issue with reproduction steps
- ✨ **New features** — check the roadmap in README, open an issue first
- 🎨 **Templates** — add templates to `templates/` (see format below)
- 📝 **Docs** — improve README, add examples

## Template format

Templates live in `templates/` as JSON files:

```json
{
  "name": "weather-tools",
  "description": "Fetch weather data from an API",
  "tools": [
    {
      "name": "get_weather",
      "desc": "Get current weather for a city",
      "returns": "dict",
      "params": [
        { "name": "city", "type": "str", "desc": "City name", "required": true }
      ]
    }
  ]
}
```

## Code style

- Vanilla JS only (no framework)
- CSS custom properties for theming
- No build step required

## License

By contributing, you agree your contributions are MIT licensed.
