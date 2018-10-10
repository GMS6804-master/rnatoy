RNA-Seq toy pipeline 
======================

A proof of concept of a RNA-Seq pipeline intended to show Nextflow
scripting and reproducibility capabilities.

[![nextflow](https://img.shields.io/badge/nextflow-%E2%89%A50.24.0-brightgreen.svg)](http://nextflow.io)
[![Build Status](https://travis-ci.org/nextflow-io/rnatoy.svg?branch=master)](https://travis-ci.org/nextflow-io/rnatoy)

How execute it using UFRC
-------------------------

1) Login to UFRC

2) Load Singularity 

    ml singularity

3) Pull the required Docker image in /home/<user>/singularity as shown below: 

   singularity pull docker://nextflow/rnatoy:1.3`


4) Upload GitHub repository in /home/<user>/rnatoy as shown below:
 

   curl  https://github.com/nextflow-io/rnatoy.git 
	
	
5) Modify main.nf file: line 33-36 as shown below:

params.reads = "/home/<user>/rnatoy/data/ggal/*_{1,2}.fq"
params.annot = "/home/<user>/rnatoy/data/ggal/ggal_1_48850000_49020000.bed.gff"
params.genome = "/home/<user>/rnatoy/data/ggal/ggal_1_48850000_49020000.Ggal71.500bpflank.fa"
params.outdir = 'results'


6) Change directory to /home/<user>/rnatoy as shown below:
 
cd /home/<user>/rnatoy

7) Run the nextflow script inside the singularity image as shown below:

nextflow run main.nf -with-singularity /home/djlemas/singularity/rnatoy-1.3.simg
    
    
