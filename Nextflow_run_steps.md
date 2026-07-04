# How to use Nextflow:
1-Create the appropriate PlateMap file with the following script: `create_PlateMap.ipynb`

2-Create the Load_Data files with the following script: `create_load_data_nas.py` which can be found here: `home/dcmacho`

3-Run `create_load_data_nas.py` on the super computer with the following code:
`source ~/miniconda3/etc/profile.d/conda.sh && conda activate cell_analysis && python create_load_data_nas.py`
or simply run it directly from VScode

4-Create the samplesheet necessary to run NextFlow for each plate/timepoint with this script: `nextflow_samplesheet.ipynb`

Once the PlateMaps, Load_data_files and samplesheet are in your s3 directory, you **are ready to launch Nextflow!**

As before, if you are using different channels than the CQDM U2OS project, you have to create your **Illumination Correction cpippe**, save it where you like it and add it to the nextflow command line

5-Launch nextflow from the command line on the supercomputer or VS code.
To launch nextflow, you have to be here : `/home/dcmacho/pipelines/Saguaro-Biosciences-lembeddingscellprofileling`. If not, use this path after `nextflow run` (instead of the dot) in the nextflow command.
The command:
```bash
nextflow run /home/dcmacho/pipelines/Saguaro-Biosciences-lembeddingscellprofileling -profile docker --input /mnt/s3_results/IRIC/Phenotypic_screen_HY-L022-custom_U2OS/Remix2_rerun/samplesheet.csv --channels 'DNA CL640 CL488R CL488Y' --xgb_model_path /home/dcmacho/Documents/DeadCellClass/dead_cell_classifier_final.json --outdir /home/dcmacho/nextflow_res/ --NAS_folder /mnt/ugreen_nas_v3/clientsdata
```

*If your are using U2OS, you can use the xgb classifier, if another type of cells, no.

**If you want to see the help functions:
```bash
nextflow run /home/dcmacho/pipelines/Saguaro-Biosciences-lembeddingscellprofileling --help
```
***The reports are:
```bash
/home/dcmacho/nextflow_res/pipeline_info/your_report_ID
```

****The QC reports are here:
```bash
/home/dcmacho/nextflow_res/qc_plots
```

*****The logs to see how is every step running are here:
```bash
/home/dcmacho/pipelines/Saguaro-Biosciences-lembeddingscellprofileling/work/62/800819
```
