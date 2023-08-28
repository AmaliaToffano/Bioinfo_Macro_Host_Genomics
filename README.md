# Snakemake workflow: `Bioinfo_Macro_Host_Genomics`

[![Snakemake](https://img.shields.io/badge/snakemake-≥6.3.0-brightgreen.svg)](https://snakemake.github.io)
[![GitHub actions status](https://github.com/3d-omics/Bioinfo_Macro_Host_Genomics/workflows/Tests/badge.svg?branch=main)](https://github.com/3d-omics/Bioinfo_Macro_Host_Genomics/actions?query=branch%3Amain+workflow%3ATests)


A Snakemake workflow for  Short Variant Discovery in Host Genomes

## Usage

  ```
  #Test that it works:
  #Make sure you have installed snakemake, samtools and bcftools.
  #Clone the git repository in your terminal
  git clone git@github.com:3d-omics/Bioinfo_Macro_Host_Genomics.git
  #Change directory to the one you cloned in the previous step
  cd Bioinfo_Macro_Host_Genomics
  #Activate conda environment where you have snakemake
  conda activte Snakemake
  # Generate mock data
  bash workflow/scripts/generate_mock_data.sh
  #run the pipeline with the test data, it will download all the necesary software through conda. It should take less than 5 minutes.
  snakemake --use-conda --jobs 8 all
  ```


- Run it with your own data:
  - Edit `config/samples.tsv` with information regarding the reference you are using like in this example, you can put # in front of      a sample name if you don't want it to be analyzed

  <img width="1203" alt="image" src="https://github.com/3d-omics/Bioinfo_Macro_Host_Genomics/assets/103645443/3a0953d9-97d9-40c8-a984-d7e37ee8d143">

  -  Edit `config/features.yml` with information regarding the reference you are
    using like in this example.

  <img width="1211" alt="image" src="https://github.com/3d-omics/Bioinfo_Macro_Host_Genomics/assets/103645443/bda09503-1559-4447-a189-5b95350fb81e">

- Run the pipeline
     ```
     snakemake --use-conda --jobs 8 all
     #(slurm users), there is a script called run_slurm in the cloned directory that you can directly use to launch the pipeline on a slurm         cluster, you can modify the parameters or direclty execute it as it is
     ./run_slurm
     ```
## Features

- FASTQ processing with [`fastp`](https://github.com/OpenGene/fastp)
- Mapping with [`bowtie2`](https://github.com/BenLangmead/bowtie2)
- SAM/BAM/CRAM processing with [`samtools`](https://github.com/samtools/samtools) and [`picard`](https://github.com/broadinstitute/picard)
- Sample swap detection with [`gtcheck`](https://github.com/samtools/bcftools)
- SNP calling with [`GATK4`](https://github.com/broadinstitute/gatk)
- SNP annotation with [`SNPEff`](https://github.com/pcingola/SnpEff)

## DAG

![host_genomics_pipeline](./rulegraph.svg?raw=true)

## References

TBA
