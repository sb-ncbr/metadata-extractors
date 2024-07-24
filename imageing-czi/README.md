# About

This Docker container is to facilitate the extraction of metadata from CZI images using bftools. The container includes all necessary dependencies and provides a streamlined environment for working with CZI image files. By utilizing this Docker image, users can efficiently manage and process CZI metadata without the hassle of manual software installations and configurations and this could be used also in automatic workflows and pipelines.

# Usage

## Build a container

```
docker build -t bftools-container .
```

## Run the container with mounted data folder

### For interactive run
```
docker run -v /path/to/your/images:/data -it bftools-container
```

and then

```
bfconvert -noflat -omexml-only -format json /data/your_image.czi /data/metadata.json
```

### For non-interactive

```
docker run --rm -v /path/to/your/images:/data bftools-container bfconvert -noflat -omexml-only -format json /data/your_image.czi /data/metadata.json
```
