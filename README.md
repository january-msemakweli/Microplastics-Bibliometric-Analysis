# Mapping Global Research on Microplastic Sources, Environmental Pathways, and Health Implications: A Bibliometric Analysis (2000–2025)

Reproducible Web of Science–based bibliometrics for this study, implemented in R with [bibliometrix](https://www.bibliometrix.org/).

The full narrative, methods, code, and figures live in [`microplastics_bibliometric_analysis.Rmd`](microplastics_bibliometric_analysis.Rmd).

## Authors

Amelia Chebyala (1), January G. Msemakweli (2\*), Oscar Punguti (3), Edson Protas (1), Iddi Mapande (1), Nelson Joseph Msacky (4), and Novatus Tesha (5)

1. Muhimbili University of Health and Allied Sciences, Dar es Salaam, Tanzania, United Republic of, Department of Environmental and Occupational Health
2. Johns Hopkins Bloomberg School of Public Health, Baltimore, United States, Department of Epidemiology
3. Mbeya University of Science and Technology, Mbeya, Tanzania, United Republic of, Department of Medical Sciences and Technology
4. Institute of Rural Development Planning, Dodoma, Tanzania, United Republic of, Department of Environmental Planning
5. Muhimbili University of Health and Allied Sciences, Dar es Salaam, Tanzania, United Republic of, Department of Development Studies

**Corresponding author.** E-mail: jmsemak1@jh.edu

## What this project does

The analysis script:

- Imports WoS **plain text** exports from `data/`, merges them, and cleans duplicates (`duplicatedMatching` on titles) and publication years (2000–2025).
- Runs descriptive bibliometrics, annual and cumulative publication trends, top countries and journals, and highly cited papers.
- Builds **collaboration** networks (countries, institutions), **keyword** co-occurrence (Keywords Plus and author keywords), a **thematic map**, **thematic evolution** (three periods: 2000–2010, 2011–2017, 2018–2025), and **co-citation** networks (with matrix reduction for the reference network to keep plotting feasible).
- Adds **trend topics**, **conceptual structure (MCA)** on Keywords Plus, and **health-related** text analyses (keyword trends and carcinogenic/chronic proportions over time).

Country-level publication counts are also written to `country_publication_frequencies.csv` in the project directory when you knit the document.

## Data

Place Web of Science Core Collection exports as **plain text** (`.txt`) files under **`data/`**. The notebook loads every `*.txt` in that folder whose name contains `savedrecs` (typical WoS export names). Document types in the search should match your inclusion criteria (the manuscript describes **Articles** and **Review Articles** only).

The Boolean query and date range used for retrieval are documented in the Methods section of the R Markdown file.

## Requirements

- [R](https://www.r-project.org/) (recent version recommended)
- R packages: **bibliometrix**, **ggplot2**, **dplyr**, **stringr** (and **Matrix**, used for co-citation preprocessing—usually installed with bibliometrix dependencies)

Install packages in R:

```r
install.packages(c("bibliometrix", "ggplot2", "dplyr", "stringr", "Matrix"))
```

## How to run

1. Clone or download this repository.
2. Ensure your WoS `.txt` exports are in **`data/`** as described above.
3. Open `microplastics_bibliometric_analysis.Rmd` in RStudio (or your preferred environment) and **Knit** to HTML.

The code assumes the **knit directory is the folder that contains the Rmd** (the project root), so paths like `data/` and output CSV names resolve correctly.

Chunk caching is enabled (`cache = TRUE`); clear the cache folder if you change inputs or code and need a full rebuild.

## Repository layout

| Path                                        | Role                                        |
| ------------------------------------------- | ------------------------------------------- |
| `microplastics_bibliometric_analysis.Rmd` | Main analysis notebook                      |
| `data/`                                   | WoS plain text exports (`savedrecs*.txt`) |

## License

See [LICENSE](LICENSE) in this repository.
