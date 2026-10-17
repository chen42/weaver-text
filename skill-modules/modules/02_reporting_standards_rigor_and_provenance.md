# Module 02: Reporting standards, rigor, and provenance

**Applies to:** Journal manuscripts and grant proposals. Focus on reporting standards, transparency, and data provenance during writing, rather than raw computational mechanics.

## 1. Determine the applicable reporting standard

For a reporting audit or full-production task, identify the study design and applicable reporting standards. Distinguish standards required by the target from recommended reporting practices. For focused edits, consult relevant items without requiring a project-wide audit or a new compliance file.

Record selected standards, versions, applicable extensions, and whether each is required or recommended in `guidelines/requirements.md` when maintaining a requirements record. Save each official checklist or standard consulted under `guidelines/source/`, including during a review, and record its source and access date. Verify the current official checklist rather than treating the table below as a complete or current specification. Grant rigor requirements depend on the agency and mechanism.

| Study design | Standard | Focus |
|---|---|---|
| Randomized controlled trial | CONSORT | Parallel group trial reporting |
| Clinical trial protocol | SPIRIT | Protocol content and schedule of evaluations |
| Observational study | STROBE | Cohort, case-control, and cross-sectional studies |
| Systematic review or meta-analysis | PRISMA | Transparent identification, screening, and synthesis |
| Animal research in vivo | ARRIVE | Ethical approval, housing, blinding, sample size, welfare |
| Biological materials and design | MDAR | Materials, design, analysis, and reporting in life sciences |
| Clinical prediction model | TRIPOD | Multivariable model development and validation |
| Diagnostic accuracy | STARD | Sensitivity, specificity, and index test evaluation |
| Case report | CARE | Clinical case presentation and timeline |
| Qualitative research | COREQ / SRQR | Interviews, focus groups, and thematic synthesis |
| Quantitative PCR | MIQE | Primer sequences, efficiency, controls, normalizers |
| Artificial intelligence in medicine | TRIPOD-AI / CONSORT-AI | Clinical AI model validation and trials |

Follow the governing standard rather than general habits. Note any required checklist items that are missing as author queries.

## 2. Rigor and transparency elements in writing

Report the following parameters where applicable to the design and requested scope. Distinguish completed procedures from proposed plans and missing information from procedures that were not performed:

- **Subject details**: Inclusion and exclusion criteria, recruitment sources, demographic variables, attrition rates, and the final analyzed sample size ($N$).
- **Randomization and blinding**: State the method of randomization, allocation concealment, and whether experimenters, animal caretakers, and outcome assessors were blinded to group assignments.
- **Experimental, observational, and analysis units**: Identify the unit assigned to treatment, the unit measured, and the unit used for inference. Distinguish independently sampled biological units from repeated or technical measurements. Culture wells, litters, and tissue slices are not inherently independent or technical replicates; their roles depend on biological source, treatment assignment, and nesting. Report clustering and repeated measurements accurately, and flag possible pseudoreplication rather than silently changing the analysis.
- **Pre-specified versus exploratory analysis**: Clearly label primary pre-specified endpoints, secondary planned comparisons, and post-hoc exploratory observations.
- **Data exclusions**: Report the exact number of excluded subjects, samples, or data points, along with the pre-established criteria used for exclusion.
- **Preclinical behavioral protocols**: For operant, locomotor, and other behavioral procedures, report the apparatus and manipulanda (for example, levers or nosepokes), schedule of reinforcement, timeout and session-termination criteria, and infusion parameters (dose, volume, rate, and route) where relevant. State drug form (salt or free base), vehicle composition, pH, and the interval between administration and testing. Describe housing and husbandry conditions that affect behavior, including the light cycle, ambient conditions, group or single housing, food restriction, and handling or habituation procedures.
- **Genetic, genomic, and omics studies**: For association and sequencing studies, report the analysis population, the genotyping or sequencing platform, and sample quality-control criteria such as call rate, minor allele frequency, Hardy-Weinberg equilibrium, and missingness. State how population structure was handled, for example with principal components or mixed models, and give the significance threshold with its justification, such as a genome-wide threshold or a false discovery rate. Name the repositories and file types for deposited raw and processed data, for example FASTQ, BAM, VCF, or count matrices.

## 3. Statistical reporting standards in prose and tables

Present statistical results with enough information to evaluate effect magnitude, uncertainty, and the analysis performed. Do not rely on isolated p-values. Apply reporting appropriate to the actual design, test, or model; not every analysis has a test statistic, degrees of freedom, group comparison, or frequentist confidence interval.

This skill audits and presents supplied statistical results. Query missing estimates, intervals, test parameters, or power calculations. Do not compute them, reconstruct an analysis, or change its method. When a reanalysis is needed, recommend that the author perform it.

When a required value is missing, write an author query that names the quantity needed, the comparison or model it belongs to, and the reporting format the target requires. Phrase it as a task that whoever holds the data or runs the analysis can execute, so the value can be returned and inserted. Do not perform the analysis, generate the number, or prescribe a particular script, package, or tool.

### Analysis-appropriate reporting parameters

- **Effect estimates and uncertainty**: Report interpretable estimates for primary outcomes or comparisons with the uncertainty measure used in the analysis. State the interval type and level, such as a 95% confidence interval or a Bayesian credible interval. Do not impose a different inferential framework during editing.
- **Test or model details**: Report test statistics and degrees of freedom when applicable, together with p-values, estimates, or other outputs appropriate to the analysis. Exact, permutation, Bayesian, and other methods may require different information.
- **Analyzed sample sizes**: Report the number of independent units and relevant group or outcome-specific sample sizes. Distinguish these from repeated observations, clusters, and technical measurements.
- **Center and spread definitions**: Always identify the measure of central tendency and dispersion and define abbreviations such as SD or SEM (for example, mean with standard error of the mean [SEM], or median with interquartile range). Never report bare "$X \pm Y$" values without stating what the center and spread represent.
- **Multiple comparison correction**: When reporting multiple testing, name the specific adjustment applied (for example, Bonferroni, Holm-Bonferroni, Benjamini-Hochberg false discovery rate).
- **Software version**: Name the analysis package and version in the Methods section (for example, R version 4.4.1 or GraphPad Prism version 10.2).

### Banned statistical phrasing and anti-patterns

- Avoid "trending toward significance," "marginally significant," or "approaching significance." Determine statistical significance using the prespecified threshold and applicable multiplicity procedure, not an assumed $0.05$ cutoff. If the criterion is not met, report the estimate and uncertainty without treating a nonsignificant result as evidence of equivalence or absence of an effect.
- Never use "significant" as an informal synonym for "large," "important," or "substantial." Reserve "statistically significant" for test results that cross the pre-specified alpha threshold.
- Do not use asterisks as the only report of a statistical result. Provide analysis-appropriate estimates, uncertainty, and test details in the text, legend, or linked table. Include degrees of freedom only when applicable.
- Never report $p = 0.000$. Use the available numerical precision, scientific notation, or a justified bound such as $p < 0.001$; do not invent additional precision.
- Avoid "n.s." without reporting the underlying test value and group sample sizes.

Statistical significance does not equal biological or clinical importance. State the magnitude of the effect and its uncertainty, then interpret what that magnitude means biologically.

## 4. Resource identifiers and accessions

Provide persistent, standardized identifiers for key research materials and public datasets:

- **Research Resource Identifiers (RRIDs)**: Include RRIDs for key antibodies, animal strains, cell lines, and software where available or required. Verify identifiers against the resource record; do not invent an RRID when none exists.
- **Cell line authentication**: In the Methods section, state the source, authentication method (for example, short tandem repeat profiling), passage number, and mycoplasma testing status.
- **Public data accessions**: Provide database names and accession numbers for high-throughput sequencing (GEO, SRA), structural data (PDB, EMDB), proteomics (PRIDE), or clinical registries (ClinicalTrials.gov NCT identifier).
- **Ethics approvals**: State the institutional animal care and use committee (IACUC) protocol approval number or institutional review board (IRB) approval number and approving body.

## 5. Supplied-result provenance

Store supplied findings, statistical outputs, and result tables in `results/`. When a provenance record is needed, preserve an existing inventory or create `results/README.md` from `skill-modules/templates/results_manifest.md`. Consult **Module 08** for capture formats and checksums, and Module 01 for intake logging. Record:

- Result name or identifier, provider or custodian, source, version, and date received.
- Local file path, checksum, units, group labels, and sample-size definitions where supplied.
- Applicable licensing or use restrictions, distinguishing personal retrieval from redistribution.
- Analysis method, model, estimates, uncertainty measures, and relevant software details already available in the supplied outputs. Query missing details; do not reconstruct or run the analysis.
- The figure panels, table rows, and text claims supported by each result.
- Any unresolved discrepancy or author query, and the location of the external analysis record or dataset when relevant.

Preserve the supplied outputs unchanged and keep revisions or annotations separate. Do not create a raw-data or derived-data hierarchy. Source datasets and analysis workflows can remain in their original projects or repositories; document their locations when needed to trace a claim. Recording provenance does not authorize new statistical calculations.

## 6. Availability statements

Formulate clear, compliant availability statements required for publication and grant compliance:

- **Data availability**: State repository name, persistent DOI or accession, or the exact process for qualified researchers to request access.
- **Code availability**: Provide the public repository URL, release tag, and software license for analysis and visualization scripts.
- **Materials availability**: State terms for sharing plasmids, antibodies, or animal lines, including uniform material transfer agreement requirements.

## 7. Grant-specific rigor requirements

For grant proposals, separate scientific design recommendations from administrative requirements. Confirm the agency, mechanism, and current solicitation before specifying headings, attachments, or terminology.

- **Rigor of prior research**: Evaluate the strengths and weaknesses of the preliminary or published evidence underlying the proposal where relevant.
- **Scientific rigor of proposed design**: Describe controls, randomization, blinding, experimental units, and sample size rationale as appropriate to the design. Query missing calculations rather than generating them during writing.
- **Biological variables**: Address sex, age, genetic background, and other variables relevant to the design. Use agency-specific terms such as SABV when applicable.
- **Resource authentication**: Describe validation of key resources where relevant. Require a separate attachment only when the governing instructions call for one.
- **Data management and sharing**: Follow the applicable agency's plan requirements, naming, repository policies, timelines, and metadata standards. Do not treat NIH terminology or attachment rules as universal.
