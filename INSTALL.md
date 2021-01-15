# Installation
### Download Artifact
  1. Download the artifact from **[DOI](https://doi.org/10.6084/m9.figshare.13439894.v6)**
  2. Unzip using ```tar -xvf flack.tar.gz```
### Run in Docker(Recommended)
  1. Get Docker(https://www.docker.com/)
  2. In directory ```flack/```, build the docker image use ```docker build -t flack .```
  3. Start docker image use ```docker run -it flack```
  4. Run FLACK on a signle model use ```flack loc -f pa```
