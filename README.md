# Artifact of FLACK for ICSE21 Artifact Evaluation
This is the artifact for ICSE21 submission 295 "FLACK: Counterexample-Guided Fault Localization for Alloy Models". The artifact is publicly available at https://doi.org/10.6084/m9.figshare.13439894.v6

### Structure of flack/
- benchmark/alloy/ : Alloy models from AlloyFL

- benchmark/large/ : large real-world Alloy models

- src/alloy/       : modified Alloy by adding Pardinus to KodKod

- src/flack/       : source code of FLACK

- libs/            : sat solvers libraries

- solvers/         : solvers dynamic link libraries

- AlloyFL/         : replication package to compare with AlloyFL


# Execution Instructions
### Run in Docker(Recommended)
  1. Get Docker(https://www.docker.com/)
  2. In directory "flack/", build the docker image use "docker build -t flack ."
  3. Run docker use "docker run -it flack"
  4. Generate table 3 use "flack icse21", result will be written to result.cvs (please note that the ranking information is missing and has to be manually checked, and due to the randomness of solvers, the numbers may be slightly different)
  5. Run FLACK on a single model use "flack loc -f path/to/model -m #/of/instances" 

### Build from source
  1. Requirement:
	- Linux
	- bash
  	- Java 8
	- Maven
  2. In directory ```flack/```, build project use ```mvn clean package```
  3. Generate table 3 use "java -Djava.library.path=solvers -cp ./libs/*:./target/flack-1.0-jar-with-dependencies.jar icse21"
  4. In directory flack/, run FLACK on one model use "java -Djava.library.path=solvers -cp ./libs/*:./target/flack-1.0-jar-with-dependencies.jar loc -f /path/to/model -m #/of/instances"

# Compare with AlloyFL
For more details, please check AlloyFL paper and its git repo( https://github.com/kaiyuanw/AlloyFLCore )
We also include a distribution in our package, to run AlloyFL on the benchmark:
  1. Go to flack/AlloyFL/
  2. Build AlloyFL use "mvn clean package"
  3. Run AlloyFL on all models use "java -Djava.library.path=sat-solvers -cp lib/*:target/aparser-1.0.jar alloyfl.hybrid.HybridAverageFaultLocator", the total runtime for AlloyFL takes about 80 minutes
