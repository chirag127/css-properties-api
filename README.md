# CSS Properties

All 652 CSS properties MDN tracks — from `-moz-float-edge` and `align-content` to `zoom` — with a one-paragraph description, the formal syntax parsed from the defining spec, initial value, inheritance and first-support versions for Chrome, Firefox, Safari and Edge.

No authentication. No server. No rate limit. The committed JSON is the database.

    curl https://chirag127.github.io/css-properties-api/api/v1/data.json

## What you get

| Field | Example | Notes |
| --- | --- | --- |
| `id` / `name` | `"align-content"` | Property name, the same in both fields. |
| `description` | `"The CSS align-content property sets the distribution of space…"` | First paragraph of the MDN page. `null` for 67 properties, mostly vendor-prefixed, that have no page. |
| `syntax` | `"normal \| <baseline-position> \| …"` | Formal grammar taken from the spec by webref. `null` for 95 properties. |
| `initial` / `inherited` / `appliesTo` | `"normal"` / `"no"` / `"block containers, …"` | Straight from the spec. `null` where the spec does not state it. |
| `status` | `"standard"` | 473 `standard`, 110 `experimental`, 46 `nonstandard`, 23 `deprecated`. |
| `support.chrome.added` | `"29"` | First version without a prefix. `false` means never supported, `null` means no data. `prefixed` holds the first `-webkit-`/`-moz-` version. |
| `specUrl` | `["https://drafts.csswg.org/css-align/#align-justify-content"]` | Defining anchors, all of them, not just the first. |
| `mdnUrl` | `"https://developer.mozilla.org/docs/…/align-content"` | Where the description came from. |

## Endpoints

| Endpoint | Description | Size |
| --- | --- | --- |
| `/api/v1/data.json` | All 652 records, in property-name order | 687,543 bytes |
| `/api/v1/individual/{id}.json` | One record, e.g. `/api/v1/individual/display.json` | 576–1,638 bytes each |
| `/api/v1/search-index.json` | The same records keyed by `id`, for a single-fetch lookup | 747,230 bytes |
| `/api/v1/meta.json` | Record count, source, retrieval time | 593 bytes |

## Data source and accuracy

Three sources, joined on the property name.

*Browser support, status, spec links* come from MDN browser-compat-data. BCD no longer ships a single `css/properties.json` — the directory of one file per property is read instead, 652 properties in total, at commit `07c6595` (2026-11-10).

*Descriptions* are the first paragraph of the matching MDN page, fetched 2026-11-10 at commit `3116241`; markup and links are stripped, the wording is not otherwise edited.

*Formal syntax, initial value, inheritance and applicability* come from the W3C CSS specs as parsed by webref (`ed/css`, commit `8446664`, 2026-11-10). Only the first spec to define a property supplies the grammar.

Licences: browser-compat-data is CC0 1.0. MDN prose is CC-BY-SA 2.5 (© Mozilla and MDN contributors). webref is MIT; the definitions it carries are W3C specification text.

## Limits, stated plainly

- `syntax` is a grammar, not a dictionary. It tells you `<content-distribution>` is allowed; it does not list the keywords behind it.
- 67 properties have no description and 95 no formal syntax — vendor-prefixed properties and pages MDN has not written. They are `null`, not filled in.
- Support is *first version that shipped the property*, not *first version that works*. Per-value and per-bug support notes in BCD are flattened away.
- Partial implementations are not expressed. A browser that supports the property only for one value still shows the property's first version.
- The 52 `-webkit-*` and `-moz-*` entries are vendor properties BCD tracks. They are not standard CSS and may never be.

## Contract

[openapi.yaml](./openapi.yaml) describes all four endpoints. The record type:

```ts
type CssProperty = {
  id: string;                 // "align-content"
  name: string;
  description: string | null;
  syntax: string | null;      // "normal | <baseline-position> | ..."
  initial: string | null;
  inherited: string | null;
  appliesTo: string | null;
  status: 'standard' | 'experimental' | 'nonstandard' | 'deprecated' | 'obsolete';
  specUrl: string[];
  mdnUrl: string | null;
  support: {
    chrome:  EngineSupport;
    firefox: EngineSupport;
    safari:  EngineSupport;
    edge:    EngineSupport;
  };
};

type EngineSupport = {
  added: string | boolean | null;   // "29"; false = unsupported; null = unrecorded
  removed: string | null;
  prefixed: string | null;          // first prefixed version
};
```

## Licence

Code: MIT — see [LICENSE](./LICENSE). Data: browser-compat-data is CC0 1.0; MDN prose is [CC-BY-SA 2.5](https://creativecommons.org/licenses/by-sa/2.5/), © Mozilla and MDN contributors; specification syntax is W3C text, retrieved through webref (MIT).

---

## About the author

**Chirag Singhal** — building free, open APIs and tools. Everything here is free, no
authentication, no rate limits, no telemetry. If it saves you time and you want to work
together, that is exactly what this is for.

- **Email — the fastest way to reach me:** [chirag@oriz.in](mailto:chirag@oriz.in)
- **GitHub:** [github.com/chirag127](https://github.com/chirag127)
- **LinkedIn:** [linkedin.com/in/chirag127](https://www.linkedin.com/in/chirag127/)
- **X:** [x.com/singhal127](https://x.com/singhal127)
- **YouTube:** [@ChiragSinghal127](https://www.youtube.com/@ChiragSinghal127)
- **Instagram:** [chiragsinghal127](https://www.instagram.com/chiragsinghal127/)
- **Reddit:** [Far_Macaron_9910](https://www.reddit.com/user/Far_Macaron_9910/)
- **Buy me a coffee:** [buymeacoffee.com/chirag127](https://buymeacoffee.com/chirag127)

**Hiring?** I build developer tooling, data APIs and web platforms. Email me — I reply to
everything.
