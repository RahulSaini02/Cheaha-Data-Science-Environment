# CHEAHA Conda Env Setup

[Cheaha](rc.uab.edu)

New job composer .sh script

``` 
#!/bin/bash
#SBATCH --partition=pascalnodes
#SBATCH --gres=gpu:1
#SBATCH --mem-per-cpu=4000

module load cuda10.0/toolkit
module load Anaconda3

FOLDER=/data/user/$USER/mldl
URL=https://github.com/RahulSaini02/Cheaha-Data-Science-Environment.git
if [ ! -d "$FOLDER" ] ; then
  git clone "$URL" "$FOLDER"
conda env create -f /data/user/$USER/mldl/packages.yml --name mldl
else
  cd $FOLDER
  git pull "$URL"
  conda env update -n nbotw -f /data/user/$USER/mldl/packages.yml
fi

```

Under environment setup, specify

```
# Load required modules
module load cuda10.0/toolkit
module load Anaconda3

```

Under Extra jupyter arguments, specify

```
--notebook-dir=/data/user/$USER/mldl
```

For partition, specify

```
pascalnodes
```
