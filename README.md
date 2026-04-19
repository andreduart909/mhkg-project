# mhkg-project

**Mental Health Knowledge Graph** — an open, reproducible knowledge graph of CNS drugs, their protein targets, and measured bioactivities, built from public databases (ChEMBL, DrugBank, UniProt) using Python, pandas, and RDKit.

## Status

🚧 **Active development — early stage.** This is an ongoing learning project documenting the construction of a domain-specific biomedical knowledge graph for psychiatric and neurological drugs. Built and maintained by a single contributor as part of a BSc Bioinformatics programme.

## Motivation

Computational approaches to CNS drug discovery face a distinctive challenge: psychiatric and neurological drugs interact with highly overlapping networks of receptors, transporters, and downstream pathways, often through polypharmacology. Representing these relationships as a structured graph enables downstream analyses — drug repurposing, off-target prediction, mechanism-of-action clustering — that flat tables don't support.

This project builds a transparent, reproducible knowledge graph focused on the CNS drug space, inspired by the schema design of [Hetionet](https://het.io) (Himmelstein et al., 2017) and the drug-centric structure of [DRKG](https://github.com/gnn4dr/DRKG).

## Current scope

- **Drugs**: approved and investigational psychiatric compounds filtered from ChEMBL (ATC code N — nervous system)
- **Targets**: human CNS proteins from UniProt (receptors, transporters, enzymes relevant to neurotransmission)
- **Bioactivities**: Ki, IC50, and EC50 values from ChEMBL with confidence score filtering
- **Indications**: drug-indication relationships where available

## Tech stack

- **Python 3.11+**
- **pandas, numpy** — data manipulation
- **RDKit** — cheminformatics, SMILES handling, molecular descriptors
- **chembl_webresource_client** — ChEMBL API access
- **Biopython** — UniProt / NCBI access
- **networkx** — graph construction and basic analyses
- **matplotlib, seaborn** — visualisation
- **Jupyter** — all analyses documented as notebooks

## Repository structure

```
mhkg-project/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/              # Downloaded from databases, untouched
│   ├── processed/        # Cleaned, filtered, ready for analysis
│   └── README.md         # Data sources, dates, versions
├── notebooks/
│   ├── 01_chembl_cns_drugs.ipynb       # Extract CNS drugs from ChEMBL
│   ├── 02_bioactivity_cleaning.ipynb   # Filter and standardise activity data
│   ├── 03_target_integration.ipynb     # Merge with UniProt targets
│   ├── 04_graph_construction.ipynb     # Build the knowledge graph
│   └── 05_exploratory_analysis.ipynb   # Basic graph statistics and visualisation
├── src/
│   └── mhkg/             # Reusable Python modules
└── docs/
    └── schema.md         # Graph schema documentation
```

## Running locally

```bash
git clone https://github.com/YOUR_USERNAME/mhkg-project.git
cd mhkg-project
conda create -n mhkg python=3.11
conda activate mhkg
pip install -r requirements.txt
jupyter lab
```

Start with `notebooks/01_chembl_cns_drugs.ipynb`.

## Data sources

All data is from public, freely accessible databases:

- **ChEMBL** (chembl.ebi.ac.uk) — bioactivity and drug data
- **UniProt** (uniprot.org) — protein target information
- **DrugBank** (drugbank.com) — structured drug profiles (academic access)
- **PubChem** (pubchem.ncbi.nlm.nih.gov) — complementary chemical data

Dataset versions and download dates are logged in `data/README.md` for reproducibility.

## Roadmap

- [x] Set up reproducible environment and repo structure
- [ ] Extract and clean ChEMBL CNS drug subset
- [ ] Integrate UniProt target metadata
- [ ] Build initial graph schema (nodes, edge types)
- [ ] Compute basic graph statistics (connectivity, centrality)
- [ ] Add visualisation of drug-target communities
- [ ] Extend with drug-drug interaction edges
- [ ] Document schema in structured format (Neo4j / RDF export)

## References

Key works informing this project:

- Himmelstein, D.S. et al. (2017). *Systematic integration of biomedical knowledge prioritizes drugs for repurposing.* eLife.
- Zitnik, M., Agrawal, M., Leskovec, J. (2018). *Modeling polypharmacy side effects with graph convolutional networks.* Bioinformatics.
- Bonner, S. et al. (2022). *A review of biomedical datasets relating to drug discovery: a knowledge graph perspective.* Briefings in Bioinformatics.
- Mendez, D. et al. (2019). *ChEMBL: towards direct deposition of bioassay data.* Nucleic Acids Research.

## About the author

André Ferreira — BSc Bioinformatics student at the Faculty of Sciences, University of Porto (FCUP). Background in pharmaceutical sciences (FFUP). Interests: computational chemistry, ML for drug discovery, CNS pharmacology, and scientific writing in both Portuguese and English.

- LinkedIn: linkedin.com/in/andreduart909
- Email: andreduartferreira@gmail.com

## Licence

This project is released under the MIT Licence. Data remain subject to the terms of their original sources.

## Contributing

Feedback, corrections, and suggestions are warmly welcome. Please open an issue or reach out directly.

---

*Last updated: April 2026*
