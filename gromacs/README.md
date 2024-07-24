# Gromacs Metadata Extractor

This is the script that extracts the metadata from the molecular dynamics simulations.

This code is also deployed at https://gmxmetadump.biodata.ceitec.cz/, where it is possible to obtain metadata after uploading a TPR file without need to install or run local scripts.

## Dependencies

- Gromacs software with `dump` utility (gmx dump)
- Python 3.8 and greater

## Usage

How to use the `Gromacs Metadata Extractor` software.

### Docker container

#### Build a container
```bash
docker build -t gmxdump-container .
```

#### Run the container with mounted data folder

##### For interactive run
```
docker run -v /path/to/your/tpr_files:/data -it gmx-container
```

and then

```
python3 /opt/gmx-dump/extract.py --tpr_files /data/your_simulation.tpr
```

##### For non-interactive

```
docker run --rm -v /path/to/your/tpr_files:/data gmxdump-container python3 /opt/gmx-dump/extract.py --tpr_files /data/your_simulation.tpr
```


### Basic usage from CLI

```bash
pytohn3 extract.py --tpr_file <path to TPR file>
```

#### Available Arguments

| Argument      | Description                              | Example                          |
|---------------|------------------------------------------|----------------------------------|
|   --tpr_file  |   Path to the TPR file                   |  --tpr_file <path_to_TPR_file>   |
|   --cpt_file  |   Path to the CPT file                   |  Unnused at the moment           |
|   --gro_file  |   Path to the GRO file                   |  Unnused at the moment           |
|   --format    |   Format of output metadata <json/yaml>  |  --format json                   |
|   --debug     |    Print debug information <true/false>  |  --debug true                    |

### As Python module
Use for automatization from own Python scripts.

```python
from GromacsMetadataExtractor import MetadataExtractor

extractor_object = MetadataExtractor(tpr_file[, gro_file[, cpt_file[, debug]]])
metadata = extractor_object.run().export()
# Print `metadata` dictionary
print(metadata)
```

#### Methods

| Method                       | Description                         |
|------------------------------|-------------------------------------|
|   run()                      |   Runs the metadata parser          |
|   print(format=<json/yaml>)  |   Prints the metadata to STDOUT     |
|   export()                   |   Returns dictionary with metadata  |

#### Example of advanced usage

See `paralel_run.py`

# Authors
Adrián Rošinec - adrian@ics.muni.cz    
Ondřej Schindler - ondrej.schindler@mail.muni.cz

# License

BSD 3-Clause License, see LICESNE file

Copyright (c) 2023, CEITEC and CERIT-SC, Masaryk University.
All rights reserved.
