# Welcome to cobra's documentation!

# cobra


Details see [notebook](https://github.com/ss-lab-cancerunit/cobra-junfan/tree/master/notebook)

# Setup
Note that it is highly recommended to use `pip install .` (install) and `pip install -e .` (developer install) to install packages, as invoking setup.py directly will do the wrong things for many dependencies, such as pull prereleases and incompatible package versions, or make the package hard to uninstall with pip.

```
pip install -r requirements.txt
python setup.py install
```
User should also install bedtools and fimo toolbox

# Usage
```
cobra -h
------------------------------------------------------------------
    init            Extract the chip-seq information
    check           check if the initialisation has been done
    run             run the model

optional arguments:
  -h, --help        show this help message and exit
  --version, -v     show program's version number and exit
------------------------------------------------------------------

```
## cobra init

```
linux> cobra init -h
usage: cobra init [-h] [--human] [--mouse] [--input_dir INPUT_DIR]
                  [--output OUTPUT] [--motif_windows MOTIF_WINDOWS]
                  [--windows WINDOWS] [--meme MEME] [--work_dir WORK_DIR]
                  [--dbscan] [--no-dbscan] [--fimo] [--no-fimo]

optional arguments:
  -h, --help            show this help message and exit
  --human               Species selection
  --mouse               Species selection
  --input_dir INPUT_DIR, -i INPUT_DIR
                        ChIP-seq narrawpeak file directory
  --output OUTPUT, -o OUTPUT
                        Generate the chip.csv file with score
  --motif_windows MOTIF_WINDOWS, -mw MOTIF_WINDOWS
                        The window size to calculate the chip peak score
  --windows WINDOWS, -win WINDOWS
                        The window size to calculate the chip peak score
  --meme MEME           meme file
  --work_dir WORK_DIR, -d WORK_DIR
                        work directory
  --dbscan, -db         dbscan switch on
  --no-dbscan, -nodb    dbscan switch off
  --fimo, -fimo         motif filtering switch on
  --no-fimo, -nofimo    motif filtering switch off
```

## cobra run
Run gaussian mixture model and generate csv output.
```
linux> cobra run -h

usage: cobra run [-h] [--rna RNA [RNA ...]] [--rna_dir RNA_DIR] [--chip CHIP]
                 [--output_dir OUTPUT_DIR]

optional arguments:
  -h, --help            show this help message and exit
  --rna RNA [RNA ...], -r RNA [RNA ...]
                        RNA input filename
  --rna_dir RNA_DIR, -rd RNA_DIR
                        RNA input directory
  --chip CHIP, -c CHIP  ChIP input filename
  --output_dir OUTPUT_DIR, -o OUTPUT_DIR
                        Output filename
```

# git setup
In order to have a better log system for git commit,
I used packge named commitizen. It seems to be a json tool. [More details](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)
## install package
```
npm install -g commitizen
```

## set up envir for your current git repo dir
```
# init package.json
npm init --yes
# Angular commit message format
commitizen init cz-conventional-changelog --save --save-exact
```
