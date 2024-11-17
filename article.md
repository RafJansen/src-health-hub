---
# File metadata may be provided as frontmatter YAML
title: La Palma Seismicity 2021
subtitle: An analysis of earthquake swarms in relation to the 2021 eruption
description: Analysis of the seismic earthquake data during the eruption
date: 2021-11-10
tags:
  - volcano
  - seismicity
  - la-palma
thumbnail: images/la-palma-eruption-2022-paper.png
abstract: |
  In September 2021, a significant jump in seismic activity on the island of La Palma (Canary Islands, Spain) signaled the start of a volcanic crisis that still continues at the time of writing. Earthquake data is continually collected and published by the Instituto Geográphico Nacional (IGN). We have created an accessible dataset from this and completed preliminary data analysis which shows seismicity originating at two distinct depths, consistent with the model of a two reservoir system feeding the currently very active volcano.
summary: |
  In September 2021, heightened seismic activity on La Palma signaled an ongoing volcanic crisis; analysis of Instituto Geográfico Nacional data reveals seismicity at two depths, supporting a dual-reservoir system for the active volcano.
# AGU requires a Data Availability Statement for the underlying data needed to understand, evaluate, and build upon the reported research at the time of peer review and publication.
data_availability: |
  A web scraping script was developed to pull data into a machine-readable form for analysis. That code tool [is available on GitHub](https://github.com/stevejpurves/ign-earthquake-data) along with a copy of recently updated data.
acknowledgments: |
  The authors would like to thank the Notebooks Now working groups for their help on creating these templates and advising on metadata.
keypoints:
  - You may specify 1 to 3 keypoints for this PDF template
  - These keypoints are complete sentences and less than or equal to 140 characters
  - They are specific to this PDF template, so they will not appear in other exports plain
---

# Introduction

La Palma is one of the west most islands in the Volcanic Archipelago of the Canary Islands, a Spanish territory situated is the Atlantic Ocean where at their closest point are 100km from the African coast [Figure %s](#map) The island is one of the youngest, remains active and is still in the island forming stage.

<!-- > Figures may be added to your article using the [figure directive](https://mystmd.org/guide/figures). They may refer to images saved in your `images/` folder, images from the web, or notebook cell outputs [referenced by label](https://mystmd.org/guide/cross-references#targeting-cells). The `:name:` is used to reference the figure in your text; a reference to the following figure is found in the paragraph above. The figure caption is given as the body of this directive. -->

```{figure} images/la-palma-map.png
:name: map
:align: center
:width: 100%

Map of La Palma in the Canary Islands. Image credit [NordNordWest](https://commons.wikimedia.org/w/index.php?curid=76638603)
```

La Palma has been constructed by various phases of volcanism, the most recent and currently active being the _Cumbre Vieja_ volcano, a north-south volcanic ridge that constitutes the southern half of the island.

# Eruption History

A number of eruptions were recorded since the colonization of the islands by Europeans in the late 1400s, these are summarized in [Table %s](#history).

<!-- > Simple tables may be created using the [list-table directive](https://mystmd.org/guide/tables). Similar to figures, tables may be referenced in the text by their `name`. The caption for this table is the first line of the directive. -->

```{list-table} Recent historic eruptions on La Palma
:header-rows: 1
:name: history
* - Name
  - Year
* - Current
  - 2021
* - Teneguía
  - 1971
* - Nambroque
  - 1949
* - El Charco
  - 1712
* - Volcán San Antonio
  - 1677
* - Volcán San Martin
  - 1646
* - Tajuya near El Paso
  - 1585
* - Montaña Quemada
  - 1492
```

This equates to an eruption on average every 79 years up until the 1971 event. The probability of a future eruption can be modeled by a Poisson distribution [](#poisson).

<!-- > Numbered equations may be defined using the [math directive or in line](https://mystmd.org/guide/math). Equations defined with the math directive may be reference in the text by label. -->

```{math}
:label: poisson

p(x)=\frac{e^{-\lambda} \lambda^{x}}{x !}
```

Where $\lambda$ is the number of eruptions per year, $\lambda=\frac{1}{79}$ in this case. The probability of a future eruption in the next $t$ years can be calculated by:

```{math}
:label: probability

p_e = 1-\mathrm{e}^{-t \lambda}
```

So following the 1971 eruption the probability of an eruption in the following 50 years — the period ending this year — was 0.469. After the event, the number of eruptions per year moves to $\lambda=\frac{1}{75}$ and the probability of a further eruption within the next 50 years (2022-2071) rises to 0.487 and in the next 100 years, this rises again to 0.736.

## Magma Reservoirs

<!-- > You may [add citations two ways](https://mystmd.org/guide/citations). First, you may simply insert a markdown link to a DOI like so: [](10.1093/nar/22.22.4673). No additional bibliographic information is required for this approach; the reference will be looked up by DOI and added implicitly to the references. Alternatively, you may provide the bibliography directly as `references.bib` BibTeX file, then embed the citation by BibTeX key in your text using the `@cite2023` or `[@cite2023; @cite2023b]` for narrative or parenthetical citations, respectively. The following paragraph provides an example of this. A single paper may combine both DOI and BibTeX citations. -->

Studies of the magma systems feeding the volcano, such as @marrero2019 has proposed that there are two main magma reservoirs feeding the Cumbre Vieja volcano; one in the mantle (30-40km depth) which charges and in turn feeds a shallower crustal reservoir (10-20km depth).

```{figure} images/reservoirs.png
:name: reservoirs
:align: center
:width: 100%

Proposed model from @marrero2019.
```

In this paper, we look at recent seismicity data to see if we can see evidence of such a system action, see [Figure %s](#reservoirs).

# Dataset

<!-- > All data used in the notebook should be present in the `data/` folder so notebooks may be executed in place with no additional input. -->

The earthquake dataset used in our analysis was generated from the [IGN web portal](https://www.ign.es/web/resources/volcanologia/tproximos/canarias.html) this is public data released under a permissive license. Data recorded using the network of Seismic Monitoring Stations on the island. A web scraping script was developed to pull data into a machine-readable form for analysis. That code tool [is available on GitHub](https://github.com/stevejpurves/ign-earthquake-data) along with a copy of recently updated data.

