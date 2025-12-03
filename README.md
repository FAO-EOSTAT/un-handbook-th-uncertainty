## UN Handbook - Chapter 10: Spatial map uncertainty estimation

This repository contains the reproducible analysis for Chapter 8 of the UN Handbook on quality control of training sets for agricultural statistics. The chapter demonstrates methods for quality control of training sets used in machine learning, focusing on improving sample quality and eliminating incorrectly labeled or low discriminatory samples.

### Getting started

Begin by cloning this repository to your local machine. Open a terminal and navigate to the directory where you want to store the project. Then run the following command to create a local copy of the repository.

```shell
git clone https://github.com/FAO-EOSTAT/un-handbook-th-uncertainty
```

After cloning, navigate into the project directory using `cd un-handbook-th-quality`. All subsequent commands should be executed from within this directory.

### Setting up the environment

The project uses Docker to ensure a consistent computational environment across different systems. The Docker image includes R version `4.4.1` with all necessary packages pre-installed, including the `sits` package for satellite image time series analysis.

You can obtain the Docker image in two ways. The simplest approach is to pull the pre-built image from Docker Hub. This image contains all dependencies and is ready to use immediately. Run the following command in your terminal to download it.

```shell
docker pull faoeostat/handbook:chp10
```

Alternatively, you can build the image locally from the Dockerfile. This approach is useful if you need to modify the environment or verify the build process. Navigate to the project directory and execute the build command. The build process installs all R packages specified in the `renv.lock` file, which may take several minutes depending on your system.

```shell
docker build -t "faoeostat/handbook:chp10" --file docker/Dockerfile .
```

### Running the analysis environment

Once you have the Docker image, start a container to run the analysis. The container runs RStudio Server, which provides a web-based interface for working with R. The command below starts the container in detached mode and maps port 8787 from the container to your local machine.

```shell
docker run \
    --name handbook-chp10 \
    --detach \
    --publish 8787:8787 \
    --env PASSWORD=rstudio \
    --volume ${PWD}:/home/rstudio/handbook faoeostat/handbook:chp10
```

After executing the command above, you can access RStudio by opening a web browser and navigating to [http://localhost:8787](http://localhost:8787). The default username is `rstudio` and the password is also `rstudio`.

### Opening the project

Once you have accessed RStudio in your browser, you need to open the project. The project files are available in the `handbook` directory, which is located in the RStudio user home directory. Navigate to this directory using the Files pane in RStudio. Then double-click on the `th_uncertainty.Rproj` file to open the project. This will configure RStudio with the correct working directory and project settings.

### Running the analysis

The main analysis is contained in the `analysis.qmd` file, which is a Quarto document that combines code, text, and results. Open this file in RStudio and review its contents to understand the workflow. To execute the analysis, render the Quarto document using the Render button in RStudio or by running it chunk by chunk.
