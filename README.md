# What is sdtDBN?

This website contains an overview on the main sdtDBN functionalities.

tDBN is a Java program that creates a Dynamic Bayesian Network (DBN) from user multivariate longitudinal data, having polynomial time complexity in the number of attributes and observations. The complete implementation and functionalities of tDBN are publicly available [here](http://josemonteiro.github.io/tDBN/), being the Theorical background of tDBN explained in the following article:


>José L Monteiro, Susana Vinga, and Alexandra M Carvalho.
>Polynomial-time algorithm for learning optimal tree-augmented dynamic Bayesian networks.
>In UAI, pages 622–631, 2015. http://auai.org/uai2015/proceedings/papers/329.pdf


tDBN only allows learning a tDBN using dynamic data and does not allow to make inference on the created DBN. sdtDBN solves this issues, being an extension of tDBN to learn a DBN using both dynamic and static data and allowing the user to make inference on the learned DBN.

# Theoretical background of sdtDBN

sdtDBN was developed in the context of the Master's Thesis on Electrical and Computer Engineering of Tiago Leão, at Instituto Superior Técnico, Lisbon. The Thesis is available at **Aqui por ou link dps para a tese ou link para eventual artigo que se escreva**, in which all theorical background of sdtDBN is explained.

# Program release and external libraries

## Current release

The program is currently in version 0.0.1 and can be downloaded [here](https://google.com). The program comes in an executable jar and its usage is explained and exemplified in this webpage.

## External libraries

Just as tDBN, the sdtDBN implementation uses two external libraries:

- opencsv (for parsing CSV files);

- Apache Commons CLI ( for parsing command line options)


# How to use the sdtDBN program?

## Program usage

The usage of the sdtDBN program can be found by running:

```
java -jar sdtDBN_v0.0.1.jar
```

Running the aforementioned command will produce the following usage of the program:

```
usage: tDBN
 -b,--numStaticParents <int>            Maximum number of static parents
                                        of a certain node (default = 2)
 -c,--compact                           Outputs network in compact format,
                                        omitting intra-slice edges. Only
                                        works if specified together with
                                        -d and with --markovLag 1.
 -d,--dotFormat                         Outputs network in dot format,
                                        allowing direct redirection into
                                        Graphviz to visualize the graph.
 -i,--inputFile <file>                  Input CSV file to be used for
                                        network learning.
 -inf,--inferenceFile <file>            File with variables to perform
                                        inference on
 -infFmt,--inferenceFormat <file>       Format to present inference. Can
                                        be mostProb or distrib, to give
                                        only the most probable value or
                                        the full distribution, for each
                                        attribute specified. Default is
                                        mostProb.
 -is,--inputStaticFile <file>           Input CSV file with static
                                        features to be used for network
                                        learning.
 -m,--markovLag <int>                   Maximum Markov lag to be
                                        considered, which is the longest
                                        distance between connected
                                        time-slices. Default is 1,
                                        allowing edges from one preceding
                                        slice.
 -ns,--nonStationary                    Learns a non-stationary network
                                        (one transition network per time
                                        transition). By default, a
                                        stationary DBN is learnt.
 -o,--outputFile <file>                 Writes output to <file>. If not
                                        supplied, output is written to
                                        terminal.
 -obs,--obsFile <file>                  File with the observations where
                                        inference should be done
 -obsStatic,--obsStaticFile <file>      File with the static observations
                                        to make inference
 -outInf,--outputInferenceFile <file>   File to write the inference
                                        performed
 -p,--numParents <int>                  Maximum number of parents from
                                        preceding time-slice(s).
 -pm,--parameters                       Learns and outputs the network
                                        parameters.
 -r,--root <int>                        Root node of the intra-slice tree.
                                        By default, root is arbitrary.
 -s,--scoringFunction <arg>             Scoring function to be used,
                                        either MDL or LL. MDL is used by
                                        default.
 -sp,--spanning                         Forces intra-slice connectivity to
                                        be a tree instead of a forest,
                                        eventually producing a structure
                                        with a lower score.
 -t,--trajectory <int>                  Timestep until which trajectory is
                                        to be determined
 -tf,--outputTrajectoryFile <file>      Writes predicted trajectories to
                                        <file>. If not supplied, output is
                                        written to terminal.
```

The arguments of the previous usage concern all the arguments of the original tDBN program plus the new arguments of sdtDBN, for learning DBNs also with static attribute and to make inference in the learned DBN.

Therefore, in this webpage it is described the usage of the following input arguments:
```
usage: tDBN
 -b,--numStaticParents <int>            Maximum number of static parents
                                        of a certain node (default = 2)
 -inf,--inferenceFile <file>            File with variables to perform
                                        inference on
 -infFmt,--inferenceFormat <file>       Format to present inference. Can
                                        be mostProb or distrib, to give
                                        only the most probable value or
                                        the full distribution, for each
                                        attribute specified. Default is
                                        mostProb.
 -is,--inputStaticFile <file>           Input CSV file with static
                                        features to be used for network
                                        learning.
 -obs,--obsFile <file>                  File with the observations where
                                        inference should be done
 -obsStatic,--obsStaticFile <file>      File with the static observations
                                        to make inference
 -outInf,--outputInferenceFile <file>   File to write the inference
                                        performed
 -t,--trajectory <int>                  Timestep until which trajectory is
                                        to be determined
 -tf,--outputTrajectoryFile <file>      Writes predicted trajectories to
                                        <file>. If not supplied, output is
                                        written to terminal.
```

The usage for the arguments not in this list should be checked at the [tDBN webpage](http://josemonteiro.github.io/tDBN/).

## Input files formats

All input files must be given in comma-separated values (CSV) format.

### Files with dynamic attributes

por aqui os inputs dynamic


#### Arguments that use dynamic attributes

- **-i**: This argument should be the file with the dynamic observations used to learn the DBN

- **-obs**: This argument should be the file with dynamic observations of the subjects in which inference is going to be made


### Files with static attributes

por aqui os inputs dynamic


#### Arguments that use dynamic attributes

- **-is**: This argument should be the file with the static observations used to learn the DBN. If not given, program will learn a tDBN, without static features. If given, program will learn a sdtDBN, with static and dynamic features

- **-obsStatic**: This argument should be the file with static observations of the subjects in which inference is going to be made

### File with variables and respective timesteps to make inference

por aqui ficheiro

#### Argument with variables and respective timesteps to make inference

- **-inf**: This argument should be the file with variables and respective timesteps to make inference

## Illustrative examples

### Example 1

#### Explicar o que exemplo faz

Por exemplo

### Example 2

#### Explicar o que exemplo faz

Por exemplo

### Example 3

#### Explicar o que exemplo faz

Por exemplo


# Program Eficiency

Talvez meter aqui algumas experiencias com datasets grandes e a variar o numero de pais estaticos

# References

Meter algumas referencias bibliograficas?

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
