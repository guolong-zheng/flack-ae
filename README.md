# Artifact of FLACK for ICSE21 Artifact Evaluation
This is the artifact for ICSE21 submission 295 "FLACK: Counterexample-Guided Fault Localization for Alloy Models". The pre-print of the paper is availabe at  **[paper](https://github.com/guolong-zheng/flack-ae/blob/main/paper.pdf)**. The artifact is publicly available at **[DOI](https://doi.org/10.6084/m9.figshare.13439894.v6)**.

### Structure of flack/
- benchmark/alloy/ : Alloy models from AlloyFL

- benchmark/large/ : large real-world Alloy models

- src/alloy/       : modified Alloy by adding Pardinus to KodKod

- src/flack/       : source code of FLACK

- libs/            : sat solvers libraries

- solvers/         : solvers dynamic link libraries

- AlloyFL/         : replication package to compare with AlloyFL


# Execution and Reproduce Instructions
### Run in Docker(Recommended)
  1. Get Docker(https://www.docker.com/)
  2. In directory ```flack/```, build the docker image use ```docker build -t flack .```
  3. Start docker image use ```docker run -it flack```
  4. Generate TABLE III use ```flack icse21```, the whole process takes aoubt one or two minutes, and result will be written to result.cvs (please note that the ranking information can not be generated automatically and has to be checked manually. Due to the randomness of Alloy, the numbers may be slightly different)
  5. Generate TABLE IV use ```flack loc -f bnechmark/large/ -m 5```, this process takes about 30 minutes
  6. Run FLACK on a single model use ```flack loc -f path/to/model -m #/of/instances``` 

### Build from source
  1. Requirement:
	- Linux
	- bash
  	- Java 8
	- Maven
  2. In directory ```flack/```, build project use ```mvn clean package```
  3. Generate TABLE III use ```java -Djava.library.path=solvers -cp ./libs/*:./target/flack-1.0-jar-with-dependencies.jar icse21```, this will finish in one or two minutes
  4. Generate TABLE IV use ```java -Djava.library.path=solvers -cp ./libs/*:./target/flack-1.0-jar-with-dependencies.jar loc -f benchmark/large/ -m 5```, this may take about 30 minutes 
  5. In directory flack/, run FLACK on a single model use ```java -Djava.library.path=solvers -cp ./libs/*:./target/flack-1.0-jar-with-dependencies.jar loc -f /path/to/model -m #/of/instances```

### TABLE V: Compare with AlloyFL
For more details, please check AlloyFL paper and its git repo( https://github.com/kaiyuanw/AlloyFLCore )
We also include a distribution in our package, to run AlloyFL on the benchmark:
  1. Go to ```flack/AlloyFL/```
  2. Build AlloyFL use ```mvn clean package```
  3. Run AlloyFL on all models use ```java -Djava.library.path=sat-solvers -cp lib/*:target/aparser-1.0.jar alloyfl.hybrid.HybridAverageFaultLocator```, the total runtime for AlloyFL takes about 80 minutes
