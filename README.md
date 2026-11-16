# Create My Maps for Gemini

![Create My Maps](assets/logo.png)

Ask Gemini for a map in plain words, such as "map India's population by state" or "color the 2024 US election by winner", and get a link that opens the finished map on [createmymaps.com](https://createmymaps.com), ready to edit and export as PNG, SVG or PDF.

## What it covers

- 463 maps, including the world, continents, countries, US states and counties, Indian states and constituencies, and a few fictional worlds.
- Four coloring styles: categories (for example election winners), gradients (for example population), threshold rules (for example percentage bands) and flat colors.
- Titles, legends, descriptions, cited sources, 16 color themes, region labels, insight callouts and pins.
- Short links even for maps with thousands of regions, such as every US county.

## Install

### Gemini CLI

```bash
gemini extensions install https://github.com/sarthak144/create-my-maps-gemini
```

### Antigravity CLI

Install the extension with the Gemini CLI command above, then import it:

```bash
agy plugin import gemini
```

### Gemini app

The Gemini app doesn't install extensions. Add the server as a custom connector instead: **Customize → Connectors → Custom**, with the URL `https://createmymaps.com/mcp/gemini`. Custom connectors may not be available on every Google account or plan.

## How it works

The extension connects Gemini to the Create My Maps MCP server at `https://createmymaps.com/mcp/gemini`, which needs no account or sign-in. It has three tools:

- `search_maps` finds the right map.
- `get_map_regions` lists a map's exact regions.
- `create_map_link` matches the data to the regions and returns the map link.

`GEMINI.md` and the `createmap` skill tell Gemini when to use the tools and how to design a clear map. More setup options, including Claude and ChatGPT, are at [createmymaps.com/ai](https://createmymaps.com/ai).

## Data

The server receives only what the assistant sends to build the map: the map chosen, region names and values, and the title, legend, description, sources and colors. It doesn't receive your conversation or account. Most maps travel entirely inside the link. A map too large for a link is stored on createmymaps.com so the link stays short. See the [privacy policy](https://createmymaps.com/privacy) and [terms](https://createmymaps.com/terms).

## Support

[createmymaps.com/contact](https://createmymaps.com/contact)

## License

MIT
