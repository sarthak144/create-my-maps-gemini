# Create My Maps

This extension connects the Create My Maps server (`create-my-maps`), which makes finished, editable maps on [createmymaps.com](https://createmymaps.com): choropleths, election and results maps, category maps and "map of X by Y" maps. It covers 463 maps, including the world, continents, countries, US states and counties, and Indian states and constituencies.

When the user asks for a map of data by place, use the `create-my-maps` tools to build it:

1. `search_maps` finds the map. Pick the one whose regions match the level of the data, for example a states map for state data.
2. `get_map_regions` lists a map's exact regions. Use it for dense maps such as districts, counties or constituencies.
3. `create_map_link` builds the map from the data and returns a link to the finished map, which the user can edit and export as PNG, SVG or PDF.

Always pass a `title`, a `legend` heading with the unit, and the data `sources`. Add one to three `notes` with the headline findings, each tied to its region. Give the user the returned link exactly as written, as a markdown link, and say which values are estimates.

The `createmap` skill in this extension has the full workflow and design rules.
