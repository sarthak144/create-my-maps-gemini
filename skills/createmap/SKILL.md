---
name: createmap
description: Make colored maps (choropleths, election maps, category maps, heat maps) of countries, states, provinces, districts, constituencies, world regions or fictional worlds with the Create My Maps tools, and return a link that opens the finished, editable map on createmymaps.com. Use when the user asks to map, color, shade or visualize data by country/state/region, wants an election or results map, a "map of X by Y", or a map of places they have visited.
---

# Create My Maps

You turn a request like "map India's population by state" into a link that opens the finished map on createmymaps.com, where the user can edit it and export it as PNG, SVG or PDF. You never draw the map yourself: the Create My Maps tools build it.

## Workflow

1. **Find the map** with `search_maps`. Pick the map whose regions match the level of the data: state data goes on a states map, not a districts map. Prefer "(New)" or "(updated)" maps over "(Old)" ones for current data.
2. **Ask only when it matters.** If the request is clear, build it straight away with sensible defaults. If the right map is genuinely ambiguous (for example current or older Indian state boundaries, or states versus counties), ask one short question with numbered options and your recommended default.
3. **Get the data.** Use the user's data if they gave any. Otherwise use your knowledge or research it, and say which values are estimates and from roughly which year.
4. **Check names on dense maps.** For counties, districts or constituencies, call `get_map_regions` (with `search` to narrow it) and use those exact names or ids. Well-known countries and states can be passed by their usual names.
5. **Build it** with `create_map_link`:
   - `tag` (categories) for distinct classes: party, winner, status, yes/no, visited.
   - `number` (gradient) for continuous quantities: population, GDP, rates.
   - `logic` (threshold rules) for fixed bands, such as "above 50% is green". Put the highest band first.
   - `flat` when the user picks each region's color.
   - Add 1–3 `notes` with the headline findings (largest, smallest, a surprise), each with its `region`: the app prints them on the map as small cards pointing at the region. One short sentence with the figure. The title, description and sources print in the frame, so never repeat them in a note. Use `pins` only when the user asks to mark places.
6. **Deliver:** reply with the returned link exactly as written, as a markdown link `[Open the map](…)`. Add one or two lines on what the map shows and the data source or year, and list any regions the tool reported as not found or any values you estimated. If regions did not match and they matter, fix the names with `get_map_regions` and call `create_map_link` again.

## Design defaults

- Always set a short `title`. Put the metric and its unit in `legend` (for example "Population (millions)"), not in the values. Add a one-sentence `description` and the data `sources` when you have them.
- In `number` and `logic` modes the app colors regions without a value as if they were 0. Fill every region, or use `tag` mode with value bands plus a grey "No data" category.
- Categories: keep to about 8, and use conventional colors where they exist (US Republican `#CC3433`, Democratic `#1F5AA6`; India BJP `#FF9933`, INC `#19AAED`). Unlisted regions keep the map's light-blue default fill, so don't give a category a similar light blue.
- Gradients run light to dark; for values around a midpoint use three stops (red, white, blue). Every fill must stand out from the map background; dark themes need bright fills.
- Use `labels` only for maps with fewer than about 30 regions.
- Values are plain numbers: no `%`, units or thousands separators.
