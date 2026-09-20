# ThermoLink: Bridging disulfide bonds and enzyme thermostability through database construction and machine learning prediction

[English](README.md) | [简体中文](README.zh-CN.md)

Disulfide-bond and enzyme-thermostability records from the supplied ThermoLink-associated workbook. This repository contains data and documentation only. Statistics describe this workbook; equivalence to the final modeling dataset or current online database has not been verified.

Associated publication: Xu, R., et al. (2024). **ThermoLink: Bridging disulfide bonds and enzyme thermostability through database construction and machine learning prediction**. *Protein Science*, 33(9), e5097. [DOI: 10.1002/pro.5097](https://doi.org/10.1002/pro.5097).

## Files

- [Original Excel workbook](data/raw/ssbond_database.xlsx), preserved without modification.
- [CSV exports and summary](data/processed/), encoded in UTF-8. `summary.json` contains counts, missing-field checks, duplicate-ID checks, original headers, and the workbook SHA-256 checksum.

| Worksheet | Records | CSV |
|---|---:|---|
| All datasets | 442 | [all_datasets.csv](data/processed/all_datasets.csv) |
| Increase | 217 | [increase.csv](data/processed/increase.csv) |
| Decrease | 136 | [decrease.csv](data/processed/decrease.csv) |
| No Change | 28 | [no_change.csv](data/processed/no_change.csv) |
| Other | 28 | [other.csv](data/processed/other.csv) |

## Data dictionary

| CSV field | Excel column / header | Meaning |
|---|---|---|
| record_id | A / Index | Record identifier |
| reference_url | B / Reference_ID | Source reference URL |
| reference_id | C / Reference | Reference identifier, as supplied |
| protein | D / Protein | Protein name |
| organism | E / Organism | Source organism |
| uniprot_url | F / Uniprot ID_ID | UniProt URL |
| uniprot_id | G / Uniprot ID | UniProt accession |
| residue_i | H / AA | Residue at site i, as supplied |
| position_i | I / i | Site i, original numbering |
| residue_j | J / AA | Residue at site j, as supplied |
| position_j | K / j | Site j, original numbering |
| thermostability | L / Thermostability | Original outcome label |

## Processing and interpretation

CSV export standardizes column names, trims surrounding whitespace, and skips fully empty rows. Record order, labels, positions, and spelling are preserved; no imputation, merging, or relabeling is applied. Values are exported as text. Excel formatting is retained only in the original workbook.

The full sheet contains 244 `Increase`, 140 `Decrease`, 21 `No change`, 8 `Less 1`, and 29 records with other outcomes. The category sheets are not a complete, consistent partition of the full sheet. In particular, the No Change sheet contains 20 `No change` and 8 `Less 1` records. Do not concatenate all sheets or treat them as train/test splits.

Start from `all_datasets.csv` and document any study-specific filtering. Do not automatically reinterpret ambiguous labels or expression/activity outcomes as thermostability classes. Residue numbering has not been verified against sequences or structures.

No empty fields or duplicate record identifiers were found within individual sheets. These checks do not establish biological validity.

## Citation and licensing

Cite the associated paper above and consult the record-level reference fields for original experimental sources. A dataset redistribution license has not yet been specified. The publication license is not automatically applied to these data.
