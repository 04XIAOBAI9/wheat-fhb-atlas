# Website second-pass audit — 2026-09-03

Application v0.5.2; scientific data freeze v0.5.0 remains unchanged. This is a website regression and export audit, not a new literature search or a full scientific re-review.

## Findings corrected

1. **Hidden proximity results.** The page counted every nearby record but rendered only 18. Its note incorrectly characterized every omitted result as original/lower-tier evidence. All coordinate-usable results now render in the scrollable list, with explicit scope: all layers, independent of map display and trait/material filters; distance order is not evidence ranking. A query at `3B:1000 bp`, ±5 Mb, now shows all 41 of its 41 records. Empty results do not imply absence of published research.
2. **Manual inverted view silently changed the range.** With End=10 Mb, entering Start=11 Mb previously moved the view to 11–11.000001 Mb. Inputs now commit on blur/Enter, require integer-bp resolution and valid order/bounds, and retain the original window with a visible message on invalid input. Map labels and view CSV metadata retain six decimal Mb digits (1 bp).
3. **Export context was incomplete.** View CSV now records application version, exact view, enabled layers, filters and their limited scope. Heatmap SVG/PNG/print figures visibly retain layers, filters, freeze/application versions and binning. SVG metadata embeds all per-chromosome bin counts and reference lengths. Numeric color legends use a shared maximum. Each chromosome uses 48 relative-width bins, with different physical widths: the figure is a center-count map, not a per-Mb density, effect-size map or count of independent loci.
4. **Residual stale counts.** One bottom-of-page paragraph still claimed 234 current new loci; the all-layer batch mode described 624 raw QTL and called itself historical-only despite including new evidence. These now distinguish 232 usable new loci and 623 usable raw QTL from the immutable 234/624-record inventories. Historical summaries remain pending recalculation.
5. **Audit report precision.** The earlier audit table rounded oQTL-485 to approximately 430.04–676.71 Mb while labelling its entries as bp values. It now reproduces the exact stored range, 430036700–676713200 bp. The raw data and quarantine decision did not change.

## Checks

- 16 automated test groups: existing coordinate/parser/overlap/statistics/data-invariant tests plus manual boundary validation, figure metadata round-trip, exact numeric legend/empty input and safe handling of long/XML-sensitive filter strings.
- TypeScript, lint and the GitHub Pages production build checked separately.
- Actual browser downloads: runtime audit contains three quarantined records; usable-loci JSON contains 232 records, consistent with its declared count.
- Actual filtered SVG/PNG export for material `Wangshuibai`, layers `new,hcm,smqtl,genes`: 21 rows × 48 bins, 195 center counts, shared maximum 4. The SVG parses as XML and its embedded metadata preserves the filters; the PNG was visually inspected.
- Chinese and English proximity/batch controls checked. At a 390×844 viewport, the document client/scroll widths both measured 375 px (15 px scrollbar), with no page-level horizontal overflow. Computed body font starts with Times New Roman.

No September candidate papers were merged. No new locus-level scientific validation, cross-assembly conversion, LD-matched enrichment or rerun of frozen aggregate analyses is claimed. Source PDFs and supplements are not redistributed.
