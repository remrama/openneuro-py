# openneuro-py

A Python client for accessing [OpenNeuro](https://openneuro.org)
datasets.

![openneuro-py in action](https://raw.githubusercontent.com/hoechenberger/openneuro-py/main/openneuro-py.gif)

## Installation

```shell
# via conda:
conda install -c conda-forge openneuro-py
# or via pip:
pip install openneuro-py
```

## Jupyter and IPython support

To get basic support for Jupyter Lab, Jupyter Notebook, IPython interactive
sessions, and VS Code's interactive Jupyter interface, you will also need to
install `ipywidgets`:

```shell
# via conda:
conda install -c conda-forge ipywidgets
# or via pip:
pip install ipywidgets
```

## Basic usage – command line interface

### Getting help

```shell
openneuro-py --help
openneuro-py download --help
openneuro-py login --help
```

### Download an entire dataset

```shell
openneuro-py download --dataset=ds000246
```

### Specify a target directory

To store the downloaded files in a specific directory, use the
`--target_dir` switch. The directory will be created if it doesn't exist
already.

```shell
openneuro-py download --dataset=ds000246 \
                      --target_dir=data/bids
```

### Continue an interrupted download

Interrupted downloads will resume where they left off when you run the command
again.

## Advanced usage – command line interface

### Exclude a directory from the download

```shell
openneuro-py download --dataset=ds000246 \
                      --exclude=sub-emptyroom
```

### Download only a single file

```shell
openneuro-py download --dataset=ds000246 \
                      --include=sub-0001/meg/sub-0001_coordsystem.json
```

Note that a few essential BIDS files are **always** downloaded in addition.

### Download or exclude multiple files

`--include` and `--exclude` can be passed multiple times:

```shell
openneuro-py download --dataset=ds000246 \
                      --include=sub-0001/meg/sub-0001_coordsystem.json \
                      --include=sub-0001/meg/sub-0001_acq-LPA_photo.jpg
```

### Use an API token to log in

To download private datasets, you will need an API key that grants you access
permissions. Go to OpenNeuro.org, My Account → Obtain an API Key. Copy the key,
and run:

```shell
openneuro-py login
```

Paste the API key and press return.

## Basic usage – Python interface

```python
import openneuro as on
on.download(dataset='ds000246', target_dir='data/bids')
```
