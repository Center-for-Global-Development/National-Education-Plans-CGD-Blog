# SP/TaRL Interactive Mentions Embed

This folder contains a standalone CGD-style HTML embed for two stacked-bar charts:

- Structured Pedagogy mentions in national education plans
- Targeted Instruction / TaRL mentions in national education plans

Main file:

- `sp_tarl_interactive_mentions.html`

Supporting files:

- `build_sp_tarl_interactive.py` regenerates the HTML from the local CSV outputs.
- `TRACKING.md` documents the analytics events sent from the iframe.

## Data Inputs

The build script reads the public repo CSVs when it is run from the GitHub checkout:

- `graph html/data/structured-pedagogy-evidence.csv`
- `graph html/data/targeted-instruction-tarl-evidence.csv`

If those richer evidence files are not present, it falls back to:

- `graph data/Figure 2 SP.csv`
- `graph data/Figure 3 TARL.csv`

When it is run from the local analysis project, it falls back to:

- `output/bb_structped_datawrapper_mentions_english_french_spanish_combined.csv`
- `output/bb_targeted_datawrapper_mentions_english_french_spanish_combined.csv`
- `output/bb_sp_tarl_research_timeline_events_english_french_spanish_combined.csv`

If the timeline CSV is not present, the script uses embedded timeline metadata. The richer evidence CSVs include the matched evidence quote and longer surrounding text. The script aggregates mention-level rows to country-year stacked segments while preserving the underlying rows for tooltips.

## Regenerate

From the project root:

```bash
python3 figures/interactive/build_sp_tarl_interactive.py
```

From the public GitHub repo root:

```bash
python3 "graph html/build_sp_tarl_interactive.py"
```

The generated HTML embeds the processed data inline, so it can be hosted as a single static file.

## Embed Snippet

After publishing the file to GitHub Pages, use an iframe like this:

```html
<iframe
  src="https://center-for-global-development.github.io/National-Education-Plans-CGD-Blog/graph%20html/sp_tarl_interactive_mentions.html"
  title="Interactive chart of structured pedagogy and TaRL mentions in national education plans"
  style="width: 100%; height: 760px; border: 0; display: block;"
  loading="lazy">
</iframe>
```

The HTML implements the CGD iframe resize postMessage contract, so the fixed starting height should be replaced by the parent page once embedded on `cgdev.org`.

## Technical Notes

- Built with vanilla HTML, CSS, and SVG; no third-party JavaScript dependency or build step.
- Uses the CGD palette and tooltip/iframe guidance from `cgd-interactive-toolkit`.
- Sends CGD analytics postMessages for initial view, topic tab changes, pinned detail opens/closes, and source-link clicks.
- Tooltips work on hover, keyboard focus, click, and tap. Click/tap pins the tooltip and exposes links.
- Each tooltip shows the matched evidence first and, where available, a collapsible longer surrounding excerpt.

## Publishing Notes

The uploaded GitHub location is `graph html/`. If the folder is moved, update the iframe `src` above to match the final GitHub Pages path.
