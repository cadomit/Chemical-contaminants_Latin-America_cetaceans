# Chemical contaminants in cetaceans of Latin America

Internal exercise to gather data on chemical contaminants recorded in cetacean species (dolphins, whales and porpoises) in Latin America, with a global comparative context.

This repository holds a literature-review dataset and an interactive dashboard. They cover heavy metals, metalloids, legacy persistent organic pollutants (POPs), flame retardants, contaminants of emerging concern (PFAS, UV filters, pyrethroids, phthalates, PAHs), organotins, plastic ingestion and underwater noise.

**Credit:** [Laboratório de Ecologia e Conservação (LEC), Universidade Federal do Paraná (UFPR)](https://www.lecufpr.net) · www.lecufpr.net

## Dashboard

| Version | Link | Notes |
|---|---|---|
| Public version (GitHub Pages) | https://cadomit.github.io/Chemical-contaminants_Latin-America_cetaceans/ | Static copy of the dashboard served from [`docs/`](docs/). Becomes available once GitHub Pages is enabled for the `main` branch and `/docs` folder (see below). |
| Working version (Claude) | https://claude.ai/artifact/VbttzCzVzmjbMPyQsLQ4VU | Version maintained in Claude. Private by default; it opens only for people with whom it has been shared. |
| PDF report | [`docs/Cetacean_Contaminants_LatAm_Review_LEC-UFPR.pdf`](docs/Cetacean_Contaminants_LatAm_Review_LEC-UFPR.pdf) | Printable export of all dashboard sections (A4, 17 pages). |

The dashboard is organised in six sections:

1. **Overview.** Headline figures, key findings, coverage by contaminant group and country, and a species × contaminant matrix that shows the gaps.
2. **Species synthesis.** Minimum, maximum and mean of study means by species and tissue, on a logarithmic scale and filtered by contaminant, basis (wet, dry or lipid weight), tissue and region. Whether each study reports a standard deviation is shown as a yes/no indicator.
3. **Focal species: maps and trends.** Approximate sampling locations and a timeline of studies for *Sotalia guianensis*, *Pontoporia blainvillei*, *Inia* spp. and *Sotalia fluviatilis*. It also shows temporal patterns of ΣPCB, ΣDDT and ΣPBDE in Guiana dolphins and franciscanas, with an explicit caution on methodological bias, and the within-study trends reported by the authors.
4. **Plastics and noise.** Descriptive findings on plastic ingestion, underwater noise, vessel traffic and seismic surveys.
5. **Studies and downloads.** Full list of studies with links for individual appraisal, and CSV downloads.
6. **Data provenance and interpretation.** Search strategy, screening, extraction rules, interpretive notes and knowledge gaps.

### Enabling the public version

In the repository on GitHub, go to **Settings → Pages**. Under *Build and deployment*, select **Deploy from a branch**, choose the branch **`main`** and the folder **`/docs`**, then press **Save**. The page is published at the address above within a few minutes.

## Repository structure

```
├── README.md
├── LICENSE                      CC0 1.0 Universal
├── data/                        Spreadsheet-ready CSV files (UTF-8)
│   ├── concentrations.csv
│   ├── studies.csv
│   ├── focal_species_records.csv
│   ├── pressures.csv
│   └── author_reported_trends.csv
└── docs/                        Public dashboard (GitHub Pages)
    ├── index.html
    ├── Cetacean_Contaminants_LatAm_Review_LEC-UFPR.pdf
    └── data/                    JSON copies read by the dashboard, plus the basemap
```

## Data dictionary

### `concentrations.csv`: one row per reported value

| Column | Description |
|---|---|
| `id` | Record identifier |
| `cite`, `year`, `link` | Short citation, publication year and link (DOI, PubMed, SciSpace or Consensus) |
| `scope` | `Latin America` or `Global` (comparison only) |
| `country`, `area` | Country and area as named in the abstract |
| `species`, `common` | Scientific and common name |
| `group`, `analyte` | Contaminant group and analyte (for example, Metals / Hg; Legacy POPs / ΣPCB) |
| `tissue` | Tissue analysed; `n.s.` = not specified in the abstract |
| `unit` | µg/g for metals and metalloids; ng/g for organic compounds. Basis: `ww` wet weight, `dw` dry weight, `lw` lipid weight |
| `stat` | Statistic reported (mean, median, geometric mean, range, maximum, < LOD) |
| `mean`, `min`, `max` | Central value (mean or median) and range limits as reported |
| `sd_reported` | `Yes` / `No`: whether the study reports a standard deviation |
| `n` | Sample size, where reported |
| `note` | Additional remarks |

### Other files

- **`studies.csv`**: deduplicated list of the 119 studies and reviews, with country, topics, type, the database of first retrieval and the number of values extracted.
- **`focal_species_records.csv`**: study-by-area records for the four focal taxa. `lat` and `lon` are **approximate centroids** of the area named in each abstract, assigned by the reviewer; they are not exact sampling coordinates. `mapped = No` marks areas described too broadly to locate.
- **`pressures.csv`**: plastics, noise, vessel traffic and other pressures, with frequency of occurrence where available.
- **`author_reported_trends.csv`**: temporal trends stated by the authors within individual studies.

## Methods (summary)

- **Sources:** PubMed, SciSpace and Consensus, searched on 18 November 2026.
- **Search terms:** cetacean terms (dolphin, whale, porpoise, cetacean, *Sotalia*, *Pontoporia*, *Inia*) combined with contaminant terms (mercury, metals, trace elements, PCB, DDT, organochlorine, PBDE, PFAS, microplastic, PAH, organotin, pharmaceuticals, UV filters, noise, vessel traffic) and the names of Latin American countries. Additional searches targeted global reviews.
- **Screening:** records were deduplicated by normalised title and DOI. Where a preprint and its peer-reviewed version coexisted, only the latter was retained. Studies from the northern Gulf of Mexico (United States) were considered outside the regional scope.
- **Extraction:** all values were transcribed from abstracts. Studies that report results only in full-text tables are listed without values. Values originally in µg/g for organic compounds were converted to ng/g (× 1,000).

## Interpretive caveats

- **Standard deviation:** recorded only as reported or not. Standard deviations were not pooled or recomputed across studies.
- **Species means:** in the species synthesis, the mean is the arithmetic mean of study means or medians. It is a descriptive summary, not a weighted meta-analytic estimate.
- **Basis of expression:** for the same tissue, dry-weight concentrations are typically three to five times higher than wet-weight concentrations. Lipid-normalised values are not comparable with either.
- **Temporal patterns:** comparisons across studies use publication year, not sampling year. They combine different statistics, regions, sample origins (stranded or bycaught versus biopsied animals) and analytical methods, so they should be read with caution. Within-study trends reported by the authors provide more reliable evidence.
- **Coverage:** most values come from Brazil and from two coastal species. No studies were retrieved for Guyana or Suriname, and French Guiana is represented by a single plastic-ingestion record.

## How to cite

> Laboratório de Ecologia e Conservação (LEC), Universidade Federal do Paraná (UFPR). *Chemical contaminants in cetaceans of Latin America: literature review dataset and dashboard.* GitHub repository, 2026. https://github.com/cadomit/Chemical-contaminants_Latin-America_cetaceans

Please also cite the original studies; each record links to its source.

## Licence and third-party data

Released under [CC0 1.0 Universal](LICENSE). Country outlines in the map come from [Natural Earth](https://www.naturalearthdata.com/) (public domain), via the `world-atlas` package. The concentration values summarise published studies, which remain the property of their authors and publishers.

## Resumo em português

Exercício interno do LEC/UFPR para reunir dados sobre contaminantes químicos registrados em cetáceos da América Latina. O repositório traz:

- uma base de 191 valores de concentração extraídos de 119 estudos (PubMed, SciSpace e Consensus, busca em 18/11/2026);
- um dashboard público em [`docs/`](docs/), com síntese por espécie, mapas e linha do tempo para boto-cinza, toninha e botos de rio, tendências temporais com alertas de viés metodológico, e informações sobre plásticos e ruído;
- os dados em CSV na pasta [`data/`](data/);
- um relatório em PDF.

Os valores foram retirados dos resumos dos artigos, e o desvio-padrão é indicado apenas como relatado ou não.
