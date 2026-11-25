# Source Traceability

Internal record of the sources used to build this workshop. Not part of the learner-facing content.

## Sources

| Source | Classification | Used for | Learner-facing attribution |
| --- | --- | --- | --- |
| `adb-graph/f1-ontology-vector-rag` workshop in this repository | Oracle-owned | Blueprint for folder layout, `index.html` loader, manifest, and lab style | Not required |
| LiveLabs workshop author and validator skills | Oracle-owned | Lab section contract, markdown rules, validation | Not required |
| DOAG 2026 presentation "From Security Events to Attack Paths: Graph-powered Cyber Threat Hunting" (Hans Viehmann, Oracle; Léo Nicolle, Linkurious), slides 3 to 5 | Oracle copyright, co-presented with Linkurious | Use case text in About the Cyber Threat, haystack image | Not required for Oracle-owned parts; confirm with Linkurious for any Linkurious-authored parts |
| `ogma-oracle-livelabs` repository, `scripts/` (Karin Patenge) | Oracle-owned | `CREATE PROPERTY GRAPH` statements in Lab 1, table definitions, data subset rules | Not required |
| LANL dataset diagrams in `LiveLabs workshop/media/Claude` (created with Claude) | Oracle-owned, AI-assisted | Four diagrams in Get Started, with headers and footers moved into markdown | Not required |
| [LANL Comprehensive, Multi-Source Cyber-Security Events](https://csr.lanl.gov/data/cyber1/) | External, public domain (LANL waived all copyright) | Dataset, dataset description, and statistics | Cite A. D. Kent, LANL 2015, doi:10.17021/1179829 |
| Microsoft, MITRE ATT&CK, and MITRE CAR documentation on NTLM and pass-the-hash | External, public web pages | Why NTLM Matters in Get Started, paraphrased | Linked in Learn More |

## Third-Party Material

* **LANL dataset** - LANL waived all copyright and related rights. LANL asks users to cite the dataset.
* **Linkurious** - Léo Nicolle (Linkurious) is listed as contributor. Before adapting Linkurious code, screenshots of the Ogma UI, or Linkurious-authored slides, record the approval here and add `Built with permission from the author(s).` to the learner-facing acknowledgements.

## Embedded Assets

| Asset | Lab | Origin |
| --- | --- | --- |
| `about-cyber-threat/images/network-haystack.png` | About the Cyber Threat | DOAG 2026 presentation, slide 3 |
| `get-started/images/lanl-log-sources.svg` | Get Started | Diagram 1 of `media/Claude`, header and footer removed |
| `get-started/images/lanl-five-files.svg` | Get Started | Diagram 2 of `media/Claude`, header and footer removed |
| `get-started/images/lanl-regular-data-flow.svg` | Get Started | Diagram 3 of `media/Claude`, header removed |
| `get-started/images/lanl-red-team-data-flows.svg` | Get Started | Diagram 4 of `media/Claude`, header and footer removed |
| `create-property-graphs/files/create-graphs.sql` | Lab 1 | Unchanged copy of `ogma-oracle-livelabs/scripts/11-create_graphs.sql` |

The four SVG diagrams carry a C2PA content credential from Anthropic. Removing the headers and footers changed the files after signing.
