# Sry-delta figure notebooks

- `Figure4_pyGenomeTracks.ipynb`: four aligned ChIP-seq / gene / Micro-C locus panels.
- `insulation_plots.ipynb`: four manuscript insulation plots at 400 bp resolution with a 1.2 kb window, with optional recalculation from balanced maps.

Launch Jupyter from this directory. Install the analysis packages in the notebook's Python environment. The original insulation workflow used Python 3.10, cooler 0.9.3, cooltools 0.7.1, deepTools 3.5.5, pyBigWig 0.3.22 and numpy 1.26.4, plus pandas, matplotlib and Pillow. Fig. 4 used pyGenomeTracks 3.8. A compatible environment must also contain pyBigWig for track range calculations.

## Input layout

```text
data/
  *.bed                      # Original peak BED files with the supplied filenames
  *.bigwig                   # ChIP tracks matched by Galaxy prefixes in Fig. 4
  mcool/
    AllWT_MJP_balanced.mcool
    larval_brain_merge.mcool
  annotations/
    dmel-all-r6.59.gtf
  101626/
    cluster2 embryo CellGen prom prox elements.bed
  output/insulation/          # Required only for cached-score mode
    interval_manifest.tsv
    matrices/
      plot1_left_window1200bp.mat.gz
      ...                    # All eight plot1–plot4 left/right matrices
```

`SRY_DATA_DIR` overrides `data/`; `SRY_MCOOL_DIR` overrides its `mcool/` subdirectory; `SRY_GTF` overrides the gene annotation path. These are optional environment variables; paths can also be edited in the configuration cells. Outputs remain relative to the configured data directory as specified in each notebook.

For insulation, the default `REBUILD_FROM_MAPS = False` uses saved matrices. Set it to `True` to reproduce scores and matrices from the supplied balanced 400 bp maps and peak BEDs. Fig. 4 requires 100 bp and 200 bp map resolutions. Map and interval coordinates must use the same assembly and compatible chromosome names.

Input datasets are not included in these copies. Before publication, provide public data accessions/download instructions for both maps, peak and motif BEDs, boundary intervals and ChIP bigWigs. The exact input filenames are retained for provenance. See notebook documentation for calculation details and balancing-QC considerations.


