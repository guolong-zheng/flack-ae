# Installation
### Download Artifact
  1. Download the artifact from **[DOI](https://doi.org/10.6084/m9.figshare.13439894.v6)**
  2. Unzip using ```tar -xvf flack.tar.gz```
### Run in Docker(Recommended)
  1. Get Docker(https://www.docker.com/)
  2. In directory ```flack/```, build the docker image use ```docker build -t flack .```
  3. Start docker image use ```docker run -it flack```
  4. Run FLACK on a single model use ```flack loc -f path/to/model -m #/of/instances```. 
### Illustrative Example  
  Use ```flack loc -f benchmark/alloyfl/addr.als -m 5``` to run FLACK on ```addr.als``` with ```5``` pairs of instances, if successfully installed, the output will be:
  ```
  /flack/benchmark/alloyfl/addr.als:
example generation time:0.525
RANK LIST:
0: lone ((n . (b . listed))) 1.31
1: n in lookup[b,n] 1.30 
2: (n . ^((b . listed))) 1.30
3: l in lookup[b,n] 1.30 
4: !(n in lookup[b,n]) 1.30
5: l in (b . entry) 1.17 
6: l in lookup[b,n] => l in (b . entry) 1.00  => 
-------------------
analyze time(sec): 0.84
# rel: 1
# val: 3
# Slice Out: 10
# Total AST: 74
LOC: 21
evals: 368 | node: 6
===================
  ```
  Explaination of Output:
  | RANK LIST | The ranking list of suspicious expressions |
  | analyze time | Total runtime |
  | # rel        | Number of different relations |
  | # val        | Number of different values    |
  | # Slice out  | Number of AST nodes sliced out |
  | # Total AST  | Number of total AST nodes in the model | 
  | LOC          | Line of Code of the model   |
  | evals        | Number of instantiated expressions |
