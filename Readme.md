# CHEAHA Conda Env Setup

[Cheaha](rc.uab.edu)

New job composer .sh script

``` 
  # !/bin/bash
  # SBATCH --partition=pascalnodes
  # SBATCH --gres=gpu:1
  # SBATCH --mem-per-cpu=4000
  module load cuda10.0/toolkit
  module load Anaconda3

  FOLDER=/data/user/$USER/nbotw
  URL=https://gitlab.rc.uab.edu/rc-data-science/horovod-environment.git
  if [ ! -d "$FOLDER" ] ; then
      git clone "$URL" "$FOLDER"
  conda env create -f /data/user/$USER/nbotw/nbotw.yml --name nbotw
  else
      cd $FOLDER
      git pull "$URL"
      conda env update -n nbotw -f /data/user/$USER/nbotw/nbotw.yml
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
--notebook-dir=/data/user/$USER/nbotw
```

For partition, specify

```
pascalnodes
```