# Maitreya Labs

**Research software for canine cancer neoantigen discovery.**

Maitreya Labs is an independent project developing reproducible computational workflows for canine cancer research. Its long-term goal is to support personalized mRNA cancer vaccine design, starting with transparent identification and prioritization of neoantigen candidates.

This repository provides a public project overview. The implementation, research datasets, and analysis outputs are maintained separately and are not included here.

## The problem

Moving from tumor sequencing results to a reviewable list of peptide candidates involves multiple inputs, tools, and assumptions. Maitreya aims to make that process easier to inspect and reproduce, with explicit records of missing evidence, excluded candidates, and the inputs behind each result.

## Current prototype

The local Python prototype can:

- Read annotated tumor variants, gene expression, protein sequences, DLA alleles, and precomputed binding predictions.
- Generate peptide windows containing single amino-acid substitutions.
- Prioritize peptide candidates using a transparent, deterministic research score.
- Export candidate rankings, score components, exclusions, provenance, and HTML reports.
- Retain separate analysis runs and expose case operations through a CLI and an optional MCP server.
- Standardize public immunopeptidomics exports for quality review and comparison.

```text
Annotated variants + expression + proteins + DLA + binding predictions
                              |
                    Input validation
                              |
                  Mutant peptide generation
                              |
                 Evidence join and ranking
                              |
              Candidates + exclusions + report
```

## Design principles

**Reproducible computation.** Scientific scores are calculated by deterministic code. Language-model outputs and retrieved literature do not alter those scores.

**Traceable results.** Reports retain score components, limitations, parameters, and input/output hashes so a reviewer can inspect how a result was produced.

**Explicit uncertainty.** Missing predictions and unsupported variants are recorded rather than replaced with fabricated values.

**AI-assisted workflows.** The MCP interface allows external AI assistants to inspect cases, request analyses, and read recorded artifacts. Scientific validation remains a separate responsibility.

## Development stage

Maitreya is an early research prototype with a working analysis pipeline and automated tests. Synthetic cases exercise the software, while public-data processing supports preparation for future validation. These activities do not establish biological or clinical efficacy.

Current implementation: Python 3.12+, typed data models, CLI, optional MCP integration, TSV/JSON outputs, HTML reporting, pytest, and Ruff.

## Next milestones

- Verify public-data quality, sample metadata, and suitability for independent evaluation.
- Integrate and evaluate appropriate external DLA binding prediction workflows.
- Extend support for additional variant types and improve research reporting.
- Explore mRNA construct-design modules after candidate evaluation and review workflows are established.

## Research scope

Maitreya currently supports research candidate prioritization. Direct sequencing analysis, DLA typing, binding-predictor execution, mRNA construct optimization, and experimental validation are not implemented as a complete workflow.

The project is for research use only. It is not a diagnostic tool, treatment recommendation system, or manufacturing platform.
