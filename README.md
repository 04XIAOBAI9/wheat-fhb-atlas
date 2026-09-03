# WheatFHB Atlas

张翠军课题组的小麦赤霉病抗性区间公益性证据图谱。作者及维护人：宋一然。

Public website: <https://04XIAOBAI9.github.io/wheat-fhb-atlas/>

Application **v0.5.2** (2026-09-03) corrects coordinate parsing, file import, exploratory enrichment, map rendering and evidence disclosures. The scientific freeze remains **v0.5.0**: 52 study units, 653 locus records, 524 screening records and 11 lifecycle records. A new boundary audit quarantines two of the original 234 strict-primary loci and one of the 624 historical original QTL. The interactive map and overlap analysis now use **232 usable new loci and 623 drawable original QTL**, with historical meta-QTL kept separate.

Original frozen tables and hashes remain downloadable unchanged. **Earlier aggregate enrichment, sensitivity results and priority rankings have not been recalculated after quarantine; they are archived, not current findings.** Newly curated 2019–2026 evidence is not automatically independent out-of-time validation of a 2021 meta-analysis. Exact candidate-gene coordinates are not causal evidence, and coarse gene anchors are no longer drawn as gene bodies.

Read the [2026-09-03 audit](audits/2026-09-03-website-audit.md). Current usable loci and runtime quarantine are downloadable separately through the website. Batch P values use an independent chromosome-uniform null and are exploratory, not LD-/array-adjusted. Source PDFs, supplements, and temporary notes are not redistributed. Pending September literature is not included without Song Yiran's review.

This repository contains generated public website files and versioned release artifacts. The maintainable source repository and research workspaces are kept separately.

The [second-pass audit](audits/2026-09-03-second-pass.md) documents complete proximity results, safe manual view editing, bp-precise/filter-aware exports, and heatmap legends with embedded bin counts. Data files and archived scientific analyses remain unchanged.

Coordinates are displayed against IWGSC Chinese Spring RefSeq v1.0. Unsupported assembly conversions, genetic-only loci, alien introgressions, and excluded broad/uncertain records are never silently forced into the primary physical-coordinate layer. Journal impact factor is display metadata only and is never used as an evidence weight.

Latin letters and numerals use Times New Roman, with Chinese glyphs falling back to locally available CJK fonts.
