# BlastRadius Sim — Prototype

An interactive what-if failure simulator for a live Kubernetes-style service
dependency graph. Click any service (or several at once) to see exactly what
would break if it failed right now — before it actually does.

Built for ABB Accelerate 2026, Theme 2 (Beyond Monitoring: AI Agents for
Real-Time Pod Resource Discovery and Dependency Mapping).

## How to run it

This is a single self-contained HTML file. No install, no build step, no
server required.

1. Unzip this folder.
2. Double-click **`index.html`** — it opens directly in your default browser
   (Chrome, Edge, Firefox, or Safari all work).
3. That's it. Everything — the graph, the simulation logic, and the styling —
   is contained in that one file.

An internet connection is only used to load two Google Fonts (Inter and IBM
Plex Mono). If you're offline, the page still works fine and just falls back
to your system font.

## What to click

- **Click any service block** in the diagram to "fail" it. Click more than
  one to simulate multiple simultaneous failures.
- **Try a preset** ("Payment outage", "Primary database failure",
  "Cascading: payment + database") above the diagram for a ready-made demo
  scenario.
- **Apply a circuit breaker** in the side panel to simulate adding a fallback
  for a specific dependency, and watch the blast radius shrink live.
- **Play cascade** (bottom right) animates the failure spreading hop by hop,
  synced to the scope chart underneath.
- **Risk heatmap** (top right, only visible with nothing selected) ranks
  every service by how large its blast radius would be if it failed on its
  own — useful for spotting hidden single points of failure.
- **Engine tab** (top of the side panel) shows the exact algorithm computing
  every simulation — a breadth-first search over the reverse dependency
  graph. Nothing shown in the demo is faked.

## Files

- `index.html` — the entire prototype (HTML, CSS, and JavaScript in one file)
- `README.md` — this file

## Notes for judges / future work

The dependency graph and service list are representative mock data built to
mirror a realistic microservice architecture (gateway, domain services,
payment/auth, data layer, downstream notifications). The simulation logic
itself is real and runs entirely client-side — swapping the mock graph for a
live one (via the Kubernetes API and sampled network flow data, as described
in the submission) would not require changing the simulation, scoring, or UI
logic at all.
