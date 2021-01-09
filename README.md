# Blasting using DIAMOND with a Snakemake workflow in Docker

Steps to run:

### Get the image

Build snakemake image by using dockerfile in this reposirotry: 
> docker build --pull --rm -f "5_MyContainer\Dockerfile" -t thomasbtf/diamond_snakemake:latest "5_MyContainer"

Or download image via docker hub:
> docker pull thomasbtf/diamond_snakemake

### Build DIAMOND search in a Snakemake workflow

Create Snakemake workflow (preferably in a dedicated git repository) of the following structure

    ├── .gitignore
    ├── README.md
    ├── LICENSE.md
    ├── workflow
    │   ├── rules
    │   │   ├── module1.smk
    │   │   └── module2.smk
    │   ├── envs
    │   │   ├── tool1.yaml
    │   │   └── tool2.yaml
    │   ├── scripts
    │   │   ├── script1.py
    │   │   └── script2.R
    │   ├── notebooks
    │   │   ├── notebook1.py.ipynb
    │   │   └── notebook1.r.ipynb
    │   ├── report
    │   │   ├── plot1.rst
    │   │   └── plot2.rst
    │   └── Snakefile
    ├── config
    │   ├── rules
    │   └── some-sheet.tsv
    ├── results
    └── resources

### Run the workflow in the container


Run snakemake project in the container with a mounted volume:

> docker run -it -v <path/to/snakemake/project>:/tmp/data thomasbtf/diamond_snakemake

e.g.

> docker run -it -v d:\docker_volume\snakemake_ecoli_genome_swissprot:/tmp/data thomasbtf/diamond_snakemake
