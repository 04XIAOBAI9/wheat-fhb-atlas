# WheatFHB Atlas website audit — 2026-09-03

Application: v0.5.1. Frozen scientific data: v0.5.0 (unchanged).

This audit checks website behavior, coordinate consistency, and disclosure of evidence limits. It is **not** a new systematic literature search or a full-text scientific re-review of every paper. September candidate papers remain outside the formal dataset pending Song Yiran's review.

## Critical findings and containment

| Stored record | Stored physical interval (bp) | Atlas chromosome length (bp) | Current action |
|---|---|---|---|
| LR-2025-XNXY-QFhba-5D.2-1 | 5D:469523881–573814149 | 566080677 | Excluded from interactive map, proximity and batch overlap |
| LR-2025-XNXY-QFhbp-7A | 7A:708138840–747197703 | 736706236 | Excluded from interactive map, proximity and batch overlap |
| oQTL-485 | 5D:430036700–676713200 | 566080677 | Excluded from interactive map, proximity and batch overlap |

The first two records cite [PMC11989977](https://pmc.ncbi.nlm.nih.gov/articles/PMC11989977/). Their stored endpoints cannot be reconciled with the atlas chromosome lengths as currently represented. This audit does not establish whether the origin is the published table, reference-version attribution, marker mapping, or database curation. No claim about author conduct or paper validity is made. Values are retained, not clipped or relabelled to another assembly.

The new interactive evidence layer therefore contains **232**, not 234, usable records. The historical original-QTL layer contains **623** drawable records; its frozen inventory still contains 624. The 77 hcmQTL and 118 sMQTL pass this boundary check. Passing bounds alone is not biological validation.

All prior aggregate enrichment, sensitivity and follow-up rankings were computed from the original freeze. They have **not been rerun** after this quarantine, are folded under an archived-results control, and must not be cited as current 232-record results. Original release files and hashes remain unchanged for traceability.

There is a separate temporal-independence limitation: newly curated studies date from 2019–2026, whereas the historical meta-QTL publication dates to 2021. “Newly curated” is not equivalent to later publication or exclusion from the historical meta-analysis. Membership and population reuse must be checked before calling an overlap out-of-time validation. The section heading and explanation now make this distinction.

Two other coordinate representations were misleading:

- TaHRC: 3B:3–9 Mb is explicitly stored as a locus anchor, not the gene body.
- TraesCS3B03G1226500: 3B:753–754 Mb is a candidate interval anchor whose gene-model equivalence is pending.

Neither anchor is now plotted as a gene or used in proximity calculations. Their bibliographic records and original ranges remain accessible through search. The 17 exact RefSeq gene models nominated through omics remain candidates, not fine-mapping or causal evidence.

## Functional corrections

- Single-coordinate query `3B:1000 bp` previously became `1000 Mb` on the live website. Unit parsing is now explicit, bounded and integer-bp validated. Zero, malformed, inverted and out-of-bounds queries fail visibly. Single unitless integers mean bp; legacy interval syntax `3B:3-9` means Mb, as stated beside search.
- CSV/TSV parsing supports named/reordered columns and quoted CSV cells; IDs and comma-grouped coordinates inside quoted cells are preserved. Missing, zero and fractional-bp positions are not coerced into valid SNPs.
- BED accepts only 1-bp, zero-based half-open SNP intervals. Broad BED ranges are rejected rather than silently replaced by midpoint SNPs. VCF accepts standard SNV rows, not indels.
- Deduplicated coordinates retain an audit trail. Complete invalid/duplicate-row diagnostics can be downloaded. Results clear on editing input, changing format or withdrawing assembly confirmation. Upload failures are explicit; maximum file size is 10 MB.
- Coverage and overlap now use consistent inclusive integer-bp endpoints, including point records.
- Small/moderate batches use a one-sided exact Poisson-binomial tail. An explicit operation threshold permits a labelled continuity-corrected normal approximation only when its mean/variance checks pass; unsupported cases have no estimated P. The null remains independent, chromosome-uniform positions: **not LD-adjusted and not an array/callable-site background**. P values are exploratory, not confirmatory evidence.
- “Independent hit regions” was corrected to “Distinct hit records.” A record count is not a count of independent studies or biological loci.
- Overlapping map records receive separate lanes instead of being overdrawn in two/four recycled lanes. Dense tracks scroll. The decorative fixed central centromere was removed because no verified centromere coordinate was supplied.
- Gene/locus lookup also works in the bibliography; the full source list is searchable and titles are no longer truncated. Crossref search links are clearly discovery aids, not verified DOI/full-text links.
- Share links preserve bp-level view precision, language, enabled layers and trait/material filters. Malformed query windows are bounded; clipboard failures have a fallback message.
- Runtime chromosome lengths are derived from the integer `lengthBp` field rather than the freeze's rounded `lengthMb` display field; terminal bases are no longer lost from zoom limits or coverage denominators.
- The map snapshot, full frozen evidence table and currently usable new-locus download are distinguished. A downloadable runtime audit records quarantine, omitted gene anchors, application version and metric checks.
- Latin/numerals use Times New Roman with local CJK fallbacks; very small explanatory labels were enlarged. Mobile overflow and several untranslated controls were corrected. Trait labels remain source-reported, not falsely harmonized across incompatible resistance-type nomenclatures.

## Journal metrics

Publisher pages checked on 2026-09-03:

- [Nature Genetics](https://www.nature.com/ng/journal-impact): 25.5, explicitly labelled 2025.
- [Nature Plants](https://www.nature.com/nplants/journal-impact): 15.0, explicitly labelled 2025.
- [Frontiers in Plant Science](https://www.frontiersin.org/journals/plant-science/about): 5.9 displayed; the inspected facts section does not specify its metric year.
- [The Crop Journal, publisher issue page](https://www.sciencedirect.com/journal/the-crop-journal/vol/9/issue/4): 5.6 displayed; the metric year is not specified in the inspected page. The issue's publication year is not the JIF year.

Where a year could not be checked it is explicitly unconfirmed. Other old metric/year pairs are retained in expandable “pending review” items, not presented as freshly verified values. Bibliographic export separates frozen metrics from this audit's checked values. JIF is never used as a locus-evidence score.

## Verification and remaining boundaries

Automated regression tests cover coordinate units/errors, reordered and quoted CSV, pasted inputs, invalid/duplicate rows, BED/VCF semantics, inclusive union coverage, exact probability tails against exhaustive enumeration, non-overlapping lane packing, gene-anchor semantics, frozen counts, source references, map-to-release IDs and the known quarantine set. TypeScript, lint and GitHub Pages production build are checked separately.

Browser checks include reproducing the old bp/Mb error on the live site; corrected single-coordinate and example-batch analysis; actual CSV file upload with a quoted ID, one invalid row and one duplicate; gene-anchor display and candidate-gene bibliography lookup; chromosome switching; Chinese/English controls; and a 390×844 mobile viewport.

Not claimed complete: exhaustive literature retrieval, direct DOI resolution for 113 historical title-search records, arbitrary genome-wide gene annotation lookup, validated cross-assembly conversion, LD-/platform-matched enrichment, full harmonization of trait definitions, and recalculation of the quarantined frozen aggregate analyses. No literature-submission portal, PWA or domestic mirror was added, in accordance with the user's exclusions.
