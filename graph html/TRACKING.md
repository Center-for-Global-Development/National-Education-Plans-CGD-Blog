# Tracking

Interactive name:

- `national-education-plans-sp-tarl-mentions`

The embed sends analytics events to the CGD parent page using the toolkit postMessage contract.

## Events

| Event | Action type | Action label | Action value |
|---|---|---|---|
| `interactive_view` | | | |
| `interactive_engagement` | `navigate` | `topic_tab` | `structured_pedagogy` or `targeted_instruction_tarl` |
| `interactive_engagement` | `detail_open` | `mention_segment` | `structured_pedagogy` or `targeted_instruction_tarl` |
| `interactive_engagement` | `detail_open` | `timeline_event` | `structured_pedagogy` or `targeted_instruction_tarl` |
| `interactive_engagement` | `detail_close` | `tooltip` | omitted |
| `interactive_engagement` | `external_link` | `source_url` | `structured_pedagogy` or `targeted_instruction_tarl` |
| `interactive_engagement` | `external_link` | `timeline_source` | `structured_pedagogy` or `targeted_instruction_tarl` |

Hover-only tooltip events are not tracked.
