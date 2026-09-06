# Historical meta-QTL curation correction — 2026-09-07

Application v0.5.5; immutable data freeze v0.5.0. This audit concerns database transcription and interpretation, not scientific misconduct or independent biological validation.

## Source and access limits

Zheng et al., Meta-QTL analysis of Fusarium head blight resistance in wheat. DOI: https://doi.org/10.1016/j.cj.2020.10.006

Table 1 (77 records) and Table 2 (17 candidate genes) were checked against indexed PDF text. Direct PDF retrieval returned 404 and page rendering was unavailable; this is not a visual PDF inspection. Supplementary Table S5 (118 records) and marker tables S6/S7 were inspected from locally retained extracts, with marker counts also checked against the retained workbooks during the preceding audit. Exact original-QTL membership and independence of the reconstructed candidate sources remain unverified.

## Corrections

1. **Sequence meta-QTL coordinates:** the previous database used the physical span of the two flank markers as its display interval. In 33/118 records the stored peak lies outside that flank span. The current overlay instead uses the explicit published physical-interval field in Table S5, at its printed Mb precision, for all 118 records. The old flank span and peak are retained separately. No outer-marker envelope, arbitrary padding, or assembly conversion is performed. A peak outside the printed interval is flagged without assuming its cause. For example, sMQTL-5A-7 is printed as 644–662 Mb; the separately stored peak is 662.3605 Mb. The application does not expand 662 to include the peak.
2. **Convergence counts:** 26 hcmQTL/linked sequence-meta-QTL pairs have different counts in Table 1 and Table S5. The selected record now displays its own count and table name. Both values are disclosed when they differ. The difference is not resolved by choosing the larger number. Candidate source-entry counts do not establish distinct articles or independent replications.
3. **Shared markers:** slash-separated interval labels were previously skipped. Marker IDs are now assigned to every explicitly named interval and deduplicated within each interval. hcmQTL-19/20/29/30 SSR counts are 213/311/172/84 and 660K CAPS/dCAPS counts are 46/63/76/54. These eight corrected fields agree with Table 1. Shared membership is traceable to the source row and is not globally additive.
4. **Unresolved marker-count differences:** S6 gives SSR 240 for hcmQTL-12 and 177 for hcmQTL-28, versus Table 1 values 80 and 160. S7 gives 271 CAPS designs for hcmQTL-12 versus 126 in Table 1. S7 rows for hcmQTL-41/42/43 were not found, while Table 1 lists 28/36/97. Absence is not zero. Both source conventions remain visible; no claim of author error is made. Designs are not labelled experimentally validated markers. S8/820K is not included in these counts.

## What did not change

- The historical atlas and evidence-release JSON files remain byte-identical. Their old values require the current overlay for use.
- Gene-model coordinates do not become fine-mapping intervals or causal evidence. Table 2 nomination is not independent functional validation.
- Wide original-QTL projections are not automatically rejected merely because they exceed 200 Mb.
- RefSeq v1.1 gene annotation on the v1.0 assembly is not an assembly mismatch by itself.
- Archived analysis summaries have not been recomputed and must not be treated as current results.
- The 110 unresolved historical source-identity entries remain pending; this release does not claim complete literature coverage.

## Reproducibility

`2026-09-07-historical-markers.json` records source hashes and summary counts. `2026-09-07-historical-marker-rows.json` additionally records marker-ID membership and one-based extracted-table row numbers, without redistributing primer sequences. The in-page AUDIT download records current sequence intervals, old flank spans, peaks and count differences. Current full-atlas JSON retains these per-record fields. Exported Mb/bp values cannot supply precision absent from the source.

All checks are limited to the stated inputs. Successful software tests do not establish completeness of the literature or correctness of the underlying biological results.
