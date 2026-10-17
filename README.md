# @'

# \# baron-track

# 

# AI-assisted traceability recovery between software requirements and C source code, with human review.

# 

# \## Overview

# 

# baron-track is a personal open-source project exploring how local language models and semantic search can help engineers recover missing requirement-to-code links.

# 

# For each C function, the tool will rank candidate requirements and provide scores to support review. An engineer will accept or reject each proposed link before exporting a validated trace matrix.

# 

# \*\*Status:\*\* Under development — Phase 0: project scaffold. The features below describe the planned implementation.

# 

# \## Planned capabilities

# 

# \- Parse software requirements from CSV, including multiline descriptions.

# \- Extract C functions with their source files and line ranges.

# \- Generate function summaries using a local language model.

# \- Rank candidate requirements using semantic similarity.

# \- Export candidate links and reviewed traceability matrices.

# \- Identify requirements and functions without accepted links.

# \- Flag low-scoring suggestions for review.

# \- Provide a Streamlit interface for accepting or rejecting links.

# 

# Similarity scores are ranking signals, not calibrated probabilities of correctness. Missing links are review findings, not automatic proof of missing or unintended functionality.

# 

# \## Public dataset

# 

# The initial dataset comes from NASA's core Flight System Health and Safety application:

# 

# https://github.com/nasa/HS

# 

# To prepare the local dataset:

# 

# 1\. Download the HS source repository.

# 2\. Place `docs/hs\_FunctionalRequirements.csv` in `inputs/srd/`.

# 3\. Copy the C source and header files from `fsw/` into `inputs/code/`, preserving their directory structure.

# 4\. Record the source revision used so that results can be reproduced.

# 

# The requirements CSV uses the following columns:

# 

# \- `Summary`

# \- `Requirement ID`

# \- `Description`

# \- `Rationale`

# 

# NASA source files and requirements are stored locally in the ignored `inputs/` folder. They are not distributed with this repository.

# 

# \## Project structure

# 

# &#x20;   baron-track/

# &#x20;   ├── inputs/              # Local public dataset; ignored by Git

# &#x20;   │   ├── srd/

# &#x20;   │   └── code/

# &#x20;   ├── src/

# &#x20;   │   └── baron\_track/     # Python package

# &#x20;   ├── tests/              # Automated tests

# &#x20;   ├── outputs/            # Reports, matrices and caches; ignored by Git

# &#x20;   ├── requirements.txt

# &#x20;   ├── .gitignore

# &#x20;   ├── LICENSE

# &#x20;   └── README.md

# 

# This is the target layout for Phase 0.

# 

# \## Planned technology stack

# 

# \- Python 3.11+

# \- tree-sitter for C function extraction

# \- Ollama for local language model inference

# \- sentence-transformers for embeddings

# \- pytest for automated tests

# \- Ruff for code quality checks

# \- Streamlit for human review

# 

# Project data will be processed locally. No cloud inference API will receive requirements or source code.

# 

# \## Roadmap

# 

# \- \[ ] Phase 0 — Scaffold, documentation and first passing test

# \- \[ ] Phase 1 — Requirements and C parsers with JSON exports

# \- \[ ] Phase 2 — Local summaries and candidate link ranking

# \- \[ ] Phase 3 — Evaluation against manually reviewed reference links

# \- \[ ] Phase 4 — Trace matrices, gap reports and review interface

# 

# Evaluation will compare embeddings of raw code with embeddings of generated summaries, using precision@k and recall@k.

# 

# Setup and usage commands will be documented as each phase becomes operational.

# 

# \## Scope and limitations

# 

# This project explores traceability practices relevant to safety-critical software engineering and DO-178C workflows.

# 

# It is a portfolio prototype, not a qualified verification tool or evidence of DO-178C compliance. AI-generated suggestions require engineering review, and direct requirement-to-function links do not replace the full lifecycle traceability required by a project.

# 

# Only public data is used. Employer and client data, templates and documents are excluded.

# 

# \## Attribution and license

# 

# The intended license for original baron-track code is Apache-2.0; adding the license file is part of Phase 0.

# 

# The NASA cFS Health and Safety application is a separate upstream project. Its copyright, license and attribution notices must be preserved when using the dataset.

# 

# baron-track is an independent project and is not affiliated with or endorsed by NASA.

# '@ | Set-Content -Path README.md -Encoding utf8

