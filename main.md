# Official AKN Data Sharing Levels Definition

The Avian Knowledge Network (AKN) uses Data Sharing Levels (DSLs) to express how every
sampling event—defined as the observations collected at a named sampling unit on a given
visit—may be visualized, summarized, and distributed. DSLs are assigned and maintained by
Project Leaders on behalf of the data owner. All AKN tools (data entry portals, warehouses,
summaries, downloaders, and partner APIs) honor these levels, ensuring that a change made by a
Project Leader immediately cascades through the platform. Sampling unit coordinates are shared
openly by default; if a location must be hidden, use the location-visibility controls in addition to
the DSLs.

## Lifecycle Overview
1. **In Review stage** – controls internal workflows while data are being entered and proofed.
   Records remain visible only to project members. Once a visit is marked AVAILABLE, it can be
   promoted to the Ready for Use levels below.
2. **Ready for Use stage** – governs distribution outside the project. These levels inherit all
   protections from prior stages and broaden access to metadata, summaries, and raw records.
   Project Leaders may switch between Ready for Use levels at any time; lowering access only
   affects future distribution because downstream users may already possess past exports.

## In Review Stage (project-internal)
| Level | Intent | Key Rules |
| --- | --- | --- |
| `RAW` | Fresh entry (default) | Adds any upload or manual entry. Editable by project members only. |
| `CLEAN` | Proofed by data enterer | First-pass review complete; still only visible within the project. |
| `AVAILABLE` | Analysis-ready | Fully reviewed; locked for editing by non-leads and ready to promote. |
| `RESTRICTED` | Internal only | Project name/description/contact remain public, but no metadata, summaries, or observations leave the project; use when a dataset must never be shared. |

## Ready for Use Stage (external distribution)
| Level | Scope | What end users see |
| --- | --- | --- |
| `METADATA ONLY` (legacy Level 1) | Discoverability | Publishes project description, contacts, survey locations, methods, and the taxa surveyed. No observation details. |
| `SUMMARIZE ONLY` (legacy Level 2) | Aggregated insights | Inherits Metadata Only and feeds public summaries (e.g., Observations Map, Phenology Tool). Counts/effort remain hidden and locations may be obfuscated. |
| `SHARE WITH PERMISSION` (legacy Levels 3–4) | Controlled access | Inherits Summarize Only and authorizes full record access for users covered by a data sharing agreement. Occurrence data may be syndicated to trusted bioinformatic portals (e.g., GBIF) when permitted. |
| `SHARE OPENLY` (legacy Level 5) | Open data | Makes full observation and metadata detail downloadable without additional approval, aligning with historical CADC Level 5 guidance. |

**Summarize Only in practice** – The 2018–2021 guidance defines summaries as visualizations where individual visits cannot be reverse engineered. Acceptable examples include (a) a monthly heat map of Dunlin presence that bins counts into qualitative categories such as “few,” “many,” “abundant,” (b) a map showing the percentage of surveys detecting a species within a 10 km hex grid, and (c) annual trend lines that plot effort-normalized indices aggregated across multiple projects. Not considered summary outputs: CSV downloads of visit-level counts, tables listing exact survey effort (party-hours, distance traveled), point maps that include precise timestamps or coordinates for single visits, or any export where a single project’s raw fields (counts, observers, effort) can be read directly. When unsure, apply a four-question check—can the visualization be filtered down to one visit, does it show exact counts, does it reveal survey effort, or could it enable a third party to reconstruct the original rows? If any answer is “yes,” the output is not eligible for SUMMARIZE ONLY.

## Tool and API Behavior
- **Project apps & bulk uploader** – accept data at RAW; Project Leaders can promote or roll back
  DSLs per visit in bulk. Once a visit leaves RAW/CLEAN, biologists can no longer edit it.
- **Analyst workbenches** – may query any non-RAW data for QA/QC, reflecting the 2019–2021
  workflow guidance.
- **Data Catalog** – always lists project title/description; includes extra metadata only when DSL
  is Level 1 or higher. DSL changes do not retroactively hide catalog text supplied by the owner.
- **Phenology Tool, Observations Map, and IPaC** – only visualize data at `SUMMARIZE ONLY`
  or above.
- **Data Downloader** – Project Leaders can export their own data at `SHARE WITH PERMISSION`
  and higher; the general public can export only `SHARE OPENLY` content. Downloads must remind
  users that Level 3/4 data require honoring the owner’s agreement.

## Implementation Guidance
- Assign DSLs at the **sampling-event granularity** to keep analytical units intact; mixed levels
  within a visit are not supported.
- **Default to RAW**, advance to CLEAN after self-proofing, and promote to AVAILABLE once
  steward review is complete. This establishes provenance for audits.
- Use `RESTRICTED` for reviewed but non-shareable data; it satisfies organizational needs where
  projects must be discoverable but details withheld.
- When granting `SHARE WITH PERMISSION`, maintain a log of agreements and configure nightly
  warehouse-sync notifications so that revocations propagate quickly.
- For geographically sensitive data, pair the DSL with sampling-unit obfuscation or hiding; DSLs
  alone do not mask coordinates in internal tools.
- Legacy CADC requests mapped to Levels 1–5 remain honored: the historical 2012 PFSS agreement
  equates Levels 3–4 with “available upon request” and Level 5 with “downloadable via the internet.”
  Use those descriptions when communicating with partners familiar with earlier terminology.
