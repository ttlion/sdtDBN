# Website description 

This website contains an overview on the main sdtDBN program functionalities and explains the sdtDBN program usage.

# What are sdtDBNs?

## Previous Work - tDBNs

The tDBN implementation is a Java program that creates a Dynamic Bayesian Network (DBN) from user multivariate longitudinal data, having polynomial time complexity in the number of attributes and observations. The complete implementation and functionalities of tDBN are publicly available [here](http://josemonteiro.github.io/tDBN/), being the Theoretical background of tDBN explained in the following article:


>José L Monteiro, Susana Vinga, and Alexandra M Carvalho.
>Polynomial-time algorithm for learning optimal tree-augmented dynamic Bayesian networks.
>In UAI, pages 622–631, 2015. [http://auai.org/uai2015/proceedings/papers/329.pdf](http://auai.org/uai2015/proceedings/papers/329.pdf)


## sdtDBNs as extension of tDBNs

tDBNs only allow learning tDBNs using dynamic data and do not allow to make inference on the created tDBNs. sdtDBNs solve these issues, being an extension of tDBNs, to learn DBNs using both dynamic and static data and allowing the user to make inference on the learned DBNs.

# Theoretical background of sdtDBNs

The sdtDBN program was developed in the context of the Master's Thesis on Electrical and Computer Engineering of Tiago Leão, at Instituto Superior Técnico, Lisbon. The Thesis is available at **Thesis document or written article yet to be inserted here**, in which all theorical background of sdtDBNs is properly explained.

# Current release and libraries

## Current release

The program is currently in version 0.0.1 and can be downloaded [here](sdtDBN_v0_0_1.jar). The program comes in an executable jar and its usage is explained and exemplified in this webpage.

## External libraries

Just as tDBN, the sdtDBN implementation uses two external libraries:

- [opencsv](http://opencsv.sourceforge.net/), for parsing CSV files;

- [Apache Commons CLI](http://commons.apache.org/proper/commons-cli/), for parsing command line options.


# How to use the sdtDBN program?

## Program usage

The usage of the sdtDBN program can be found by running:

```
java -jar sdtDBN_v0_0_1.jar
```

Running the aforementioned command will produce the following usage of the program:

```
usage: sdtDBN
 -b,--numStaticParents <int>            Maximum number of static parents
                                        of a certain node (default = 2).
 -c,--compact                           Outputs network in compact format,
                                        omitting intra-slice edges. Only
                                        works if specified together with
                                        -d and with --markovLag 1.
 -d,--dotFormat                         Outputs network in dot format,
                                        allowing direct redirection into
                                        Graphviz to visualize the graph.
 -fromFile,--fromObjFile <file>         File with the serialized object of
                                        the sdtDBN.
 -i,--inputFile <file>                  Input CSV file to be used for
                                        network learning.
 -inf,--inferenceFile <file>            File with variables to perform
                                        inference on.
 -infFmt,--inferenceFormat <file>       Format to present inference. Can
                                        be distrSampl, to give only a
                                        value sampled according to the
                                        distribution; mostProb, to give
                                        only the most probable value; or
                                        distrib, to give the full
                                        distribution, for each attribute
                                        specified (where distrSampl is
                                        applied to intermmediate nodes).
                                        Default is distrSampl.
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
                                        inference should be done.
 -obsStatic,--obsStaticFile <file>      File with the static observations
                                        to make inference.
 -outInf,--outputInferenceFile <file>   Writes inference output to <file>.
                                        If not supplied, inference output
                                        is written to terminal.
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
                                        to be determined.
 -tf,--outputTrajectoryFile <file>      Writes predicted trajectories to
                                        <file>. If not supplied, output is
                                        written to terminal.
 -toFile,--toObjFile <file>             File in which the serialized
                                        object with the sdtDBN should be
                                        stored.
```

The arguments of the previous usage concern all the arguments of the original tDBN program plus the new arguments of sdtDBN, for learning DBNs also with static attribute and to make inference in the learned DBN.

Therefore, in this webpage it is described the usage of the following input arguments:

```
 -b,--numStaticParents <int>            Maximum number of static parents
                                        of a certain node (default = 2).
 -fromFile,--fromObjFile <file>         File with the serialized object of
                                        the sdtDBN.
 -inf,--inferenceFile <file>            File with variables to perform
                                        inference on.
 -infFmt,--inferenceFormat <file>       Format to present inference. Can
                                        be distrSampl, to give only a
                                        value sampled according to the
                                        distribution; mostProb, to give
                                        only the most probable value; or
                                        distrib, to give the full
                                        distribution, for each attribute
                                        specified (where distrSampl is
                                        applied to intermmediate nodes).
                                        Default is distrSampl.
 -is,--inputStaticFile <file>           Input CSV file with static
                                        features to be used for network
                                        learning.
 -obs,--obsFile <file>                  File with the observations where
                                        inference should be done.
 -obsStatic,--obsStaticFile <file>      File with the static observations
                                        to make inference.
 -outInf,--outputInferenceFile <file>   Writes inference output to <file>.
                                        If not supplied, inference output
                                        is written to terminal.
 -t,--trajectory <int>                  Timestep until which trajectory is
                                        to be determined.
 -tf,--outputTrajectoryFile <file>      Writes predicted trajectories to
                                        <file>. If not supplied, output is
                                        written to terminal.
 -toFile,--toObjFile <file>             File in which the serialized
                                        object with the sdtDBN should be
                                        stored.
```

The usage for the arguments not in this list should be checked at the [tDBN webpage](http://josemonteiro.github.io/tDBN/).

## Input files formats

All input files must be given in comma-separated values (CSV) format.

### Files with dynamic attributes

All files with dynamic attributes should follow the following format:

- The first line should be the header, where the first value must be some identification tag and the remaining values should be each attribute name together with the proper timestep, in the form "attName__timestep".
  
- The order of the attributes and timesteps must conform to the following:
  - Each timestep must have all its attributes in consecutive positions
  - The order of the attributes must be the same in all timesteps
  - Example for two attributes and two timesteps: attNameX__0, attNameY__0, attNameX__1, attNameY__1

- In each of the remaining lines, the first position must be the subject identifier and the remaining positions must be the values of the attributes in the respective timesteps, in the order defined in the header line.

- Missing values should be marked either by not writing anything or by putting "?".

- An example file with dynamic attributes is presented next. In this file, there are 2 attributes and 3 timesteps. There are missing values at subject 20 in "attX__2" and at subject 21 in "attY__1".

```
id,attX__0,attY__0,attX__1,attY__1,attX__2,attY__2
20,3,-1,8,0,?,3
21,4,2,3,,2,-8
```

#### Arguments that use dynamic attributes

- **-i**: This argument should be the file with the dynamic observations used to learn the DBN;

- **-obs**: This argument should be the file with dynamic observations of the subjects in which inference is going to be made.


### Files with static attributes

All files with static attributes should follow the following format:

- The first line should be the header, where the first value must be some identification tag and the remaining values must be each attribute name.
  - It is important for the user to guarantee that a subject in the static file exists (with the same id) in the respective dynamic file:
    - Subjects in **-is** file should exist in **-i** file.
    - Subjects in **-obsStatic** file should exist in **-obs** file.
    - There may be subjects on the dynamic files that are not in the respective static files, but the opposite cannot be true!

- In each of the remaining lines, the first position must be the subject identifier and the remaining positions must be the values of the static attributes, in the order defined in the header line.

- Missing values should be marked either by not writing anything or by putting "?".

- An example file with static attributes is presented next. In this file, there are 4 attributes. There are missing values at subject 20 in "attC" and at subject 21 in "attW".

```
id,attA,attC,attD,attW
20,A,,e,0
21,B,2,4,?
```

#### Arguments that use static attributes

- **-is**: This argument should be the file with the static observations used to learn the DBN. If not given, the program will learn a tDBN, without static features. If given, program will learn a sdtDBN, with static and dynamic features;

- **-obsStatic**: This argument should be the file with static observations of the subjects in which inference is going to be made.

### File with variables and respective timesteps to make inference

The file with static attributes should follow the following format:

- There must be two values per line, separated by ",":
  - The first value should be the dynamic attribute name;
  - The second value should be the timestep.

- All attributes names specified in this file must exist in the dynamic attributes files. The timesteps may not exist in the dynamic attributes files: in that case, if the learned network was defined to be stationary, values will be predicted until the specified timestep, according to the learned network structure.

- An example file where the program would do inference for attX\[2\] and attY\[3\] is presented next.

```
attX,2
attY,3
```

#### Argument with variables and respective timesteps to make inference

- **-inf**: This argument should be the file with variables and respective timesteps to make inference.

## Files to store an sdtDBN object

When making inference on an sdtDBN, the user may desire to make inference multiple times, while keeping the same sdtDBN. In this situation, there is no need for the program to learn the sdtDBN each time the user makes inference, as the sdtDBN stays the same. Therefore, in order to allow a user to perform inference several times in the same learned sdtDBN, two arguments were created: **-toFile** and **-fromFile**. Each of these arguments consists of a filename.

The argument **-toFile**, when given, will save the sdtDBN object (by serializing it) in a file with the name given in this argument. For example, if specified **-toFile obj_example_out.txt**, the program saves the sdtDBN object in the file **obj_example_out.txt**, for future use.

The argument **-fromFile**, when given, will get the sdtDBN object from the file with the name given in this argument. For example, if specified **-fromFile obj_example_in.txt**, the program reads the sdtDBN object from the file **obj_example_in.txt**, ignoring, if given, all other program arguments related to sdtDBN structure and parameter learning.

To get an example regarding storing and reading an sdtDBN from a file, check **Example 5**. 

## Illustrative examples

### Example 1 - Learning a sdtDBN with dynamic and static attributes

This example focus only on the learning component of the program, introducing how to learn a DBN also with static attributes (original tDBN framework only learned networks with dynamic attributes). 

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): The file with dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): The file with static attributes for learning.

To learn a sdtDBN with markovLag=1, a maximum of 1 dynamic parent from the previous time slice and a maximum of 1 static parent per node, the following command can be run:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1
```

The output obtained is:

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]
```

To obtain a graphical representation, the argument "-d" can be used, just as in the tDBN framework, as illustrated next:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -d | dot -Tpng -o fig_example1.png
```

would output the following graph:

![Image](fig_example1.png)

To learn the parameters of the created DBN, the argument -pm can be used:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -pm
```

would obtain:


```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


a: [0.0, 1.0]
[x=1.0, b[0]=0.0, b[1]=0.0]: 1.000 0.000
[x=0.0, b[0]=0.0, b[1]=0.0]: 0.000 1.000
[x=1.0, b[0]=1.0, b[1]=0.0]: 0.000 1.000
[x=1.0, b[0]=0.0, b[1]=1.0]: 0.500 0.500
[x=0.0, b[0]=1.0, b[1]=0.0]: 1.000 0.000
[x=0.0, b[0]=0.0, b[1]=1.0]: 1.000 0.000
[x=1.0, b[0]=1.0, b[1]=1.0]: 0.500 0.500
[x=0.0, b[0]=1.0, b[1]=1.0]: 0.000 1.000

b: [0.0, 1.0]
[z=1.0, a[0]=0.0]: 0.000 1.000
[z=0.0, a[0]=1.0]: 1.000 0.000
[z=0.0, a[0]=0.0]: 1.000 0.000
[z=1.0, a[0]=1.0]: 0.500 0.500
```

### Example 2 - Inference of specific attributes on a learned sdtDBN with dynamic and static attributes

Following the sdtDBN learned in example 1, inference can be made in that sdtDBN. In this example, it is explained how to do inference on a specific attribute at a specific timestep.

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): The file with dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): The file with static attributes for learning;
- [example2_dynamic_inf.csv](example2_dynamic_inf.csv): The file with the dynamic observations of the subjects where inference is to be made;
- [example2_static_inf.csv](example2_static_inf.csv): The file with the static observations of the subjects where inference is to be made;
- [example2_infVars.csv](example2_infVars.csv): The file with the dynamic attributes and respective timesteps where the user desires to make inference for the given subjects.

When making inference, one of three options can be selected with the argument **-infFmt**:

- **-infFmt distrSampl**: This mode will present, for each attribute\[timestep\] where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), a randomly sampled value for each subject specified, according to the probability distribution of each attribute\[timestep\] given the observations of each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)).

- **-infFmt mostProb**: This mode will present, for each attribute\[timestep\] where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), the most probable value for each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)).

- **-infFmt distrib**: This mode will present, for each attribute\[timestep\] where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), the conditional distribution of the learned network, for each subject specified. In intermediate nodes, the values are estimated by getting a random sample of the node's value, according to its probability distribution given the observations of each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)).

If there are cases where inference is not possible because the parent nodes values are not given in the observations files and cannot be determined by the model, the program will inform that inference is not possible on those specific cases, producing null (in **-infFmt mostProb**) or -1 (in **-infFmt distrib**).

If specifying **-infFmt distrSampl**, the following command line should be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt distrSampl
```

getting, for example, the following output (the output may vary, because there is the random component):

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


id,a[1],a[3],b[4],b[1]
1,0.0,0.0,1.0,1.0
2,0.0,0.0,0.0,0.0
3,null,0.0,0.0,1.0
```

If specifying **-infFmt mostProb**, the following command line should be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb
```

getting the following output:

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


id,a[1],a[3],b[4],b[1]
1,0.0,0.0,1.0,1.0
2,0.0,0.0,0.0,0.0
3,null,0.0,1.0,1.0
```

If specifying **-infFmt distrib**, the following command line should be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt distrib
```

getting, for example, the following output (the output may vary, because there is the random component):

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


Distributions a[1]:
id,0.0,1.0
1,1.000,0.000
2,1.000,0.000
3,-1,-1

Distributions a[3]:
id,0.0,1.0
1,0.500,0.500
2,1.000,0.000
3,0.500,0.500

Distributions b[4]:
id,0.0,1.0
1,0.500,0.500
2,1.000,0.000
3,0.000,1.000

Distributions b[1]:
id,0.0,1.0
1,0.000,1.000
2,1.000,0.000
3,0.000,1.000
```

If wanting the output of the inference to be written to a specific file, the user only needs to provide the file to be created in the **-outInf** argument. For example:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt distrib -outInf outputExample2.csv
```

would write the previous inference output to the newly created file [outputExample2.csv](outputExample2.csv).


### Example 3 - Getting an estimated trajectory

Also following the sdtDBN learned in Example 1, it is now explained in this example how the user can determine an estimated trajectory of all attributes until a certain timestep, given certain observations of subjects.

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): The file with dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): The file with static attributes for learning;
- [example2_dynamic_inf.csv](example2_dynamic_inf.csv): The file with the dynamic observations of the subjects where inference is to be made;
- [example2_static_inf.csv](example2_static_inf.csv): The file with the static observations of the subjects where inference is to be made.

To get the trajectories, the user only needs to define the maximum timestep in the argument **-t**. 

The user can also use the argument **-infFmt** to specify how the values of the nodes are determined from the probability distributions. If using **-infFmt mostProb**, the values selected for each node are always the most probable given the observations of each subject. Otherwise, the values are randomly sampled according to the probability distribution of each node given the observations of each subject. 

For example, if the user wants to determine the most probable trajectory of all attributes until timestep 5, the following command can be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -t 5 -infFmt mostProb
```

which will output:

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


id,a__0,b__0,a__1,b__1,a__2,b__2,a__3,b__3,a__4,b__4,a__5,b__5
1,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,1.0,0.0,1.0
2,1.0,1.0,0.0,0.0,1.0,1.0,0.0,0.0,1.0,0.0,1.0,0.0
3,0.0,,,1.0,0.0,1.0,0.0,1.0,0.0,1.0,0.0,1.0
```

As can be seen in b\[0\] and a\[1\] of subject 3, the program simply does not provide any estimations where those estimations cannot be given (if the parent nodes are not specified in the observations and cannot be determined by the model).

If wanting the output of the estimated trajectories to be written to a specific file, the user only needs to give the file to be created in the **-tf** argument. For example:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -t 5 -infFmt mostProb -tf outputExample3.csv
```

would write the previous estimated trajectories output to the newly created file [outputExample3.csv](outputExample3.csv).

### Example 4 - Getting an estimated trajectory and also making inference of specific attributes

The program allows the user to do examples 2 and 3 at the same time. For example, running:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5
```

the program would output:

```
Evaluating network with LL score.
Number of networks with max score: 18
Finding a maximum branching.
Network score: -2.772588722239781

-----------------

b[0] -> a[1]
a[0] -> b[1]

b[1] -> a[1]

x -> a[1]
z -> b[1]


id,a__0,b__0,a__1,b__1,a__2,b__2,a__3,b__3,a__4,b__4,a__5,b__5
1,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,1.0,0.0,1.0
2,1.0,1.0,0.0,0.0,1.0,1.0,0.0,0.0,1.0,0.0,1.0,0.0
3,0.0,,,1.0,0.0,1.0,0.0,1.0,0.0,1.0,0.0,1.0

id,a[1],a[3],b[4],b[1]
1,0.0,0.0,1.0,1.0
2,0.0,0.0,0.0,0.0
3,null,0.0,1.0,1.0
```

which is the output of examples 2 and 3.

The user may also specify two different output files, one for the result of the inference on certain attributes and the other for the output of the estimated trajectories. This is done with the arguments specified in examples 2 and 3, **-outInf** and **-tf**, respectively. For example:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5 -outInf outputExample2.csv -tf outputExample3.csv
```

would create the files [outputExample2.csv](outputExample2.csv) and [outputExample3.csv](outputExample3.csv), just as in examples 2 and 3.

### Example 5 - Storing and reading an sdtDBN object to/from a file

As explained previously in the webpage, the arguments **-toFile** and **-fromFile** were created so that, respectively, an sdtDBN object can be written in a file and an sdtDBN object can be read from a file. This example explains how to use these two arguments.

Following example 1, where an sdtDBN was learned, the argument **-toFile** can be used to save the learned sdtDBN in a file. Therefore, by running

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -toFile obj_saved.txt
```

the program does everything explained in example 1 and saves the learned sdtDBN in a file named obj_saved.txt, which the program creates.

Having this object saved in a file, the argument **-fromFile** can be used to get the saved sdtDBN. For example, by running 

```
java -jar sdtDBN_v0_0_1.jar -fromFile obj_saved.txt
```

the program would output the sdtDBN stored in the file obj_saved.txt, which means the output would be the same as the output presented in example 1 (plus the parameters of the learned sdtDBN, as explained next).

The arguments **-toFile** and **-fromFile** can be combined with the several situations presented in previous examples.

Regarding the argument **-toFile**, every time this argument is used, the sdtDBN learned is saved in the according file. When this argument is used, the program always learns the sdtDBN parameters, so that the file where the sdtDBN is saved also has the proper parameters of the learned sdtDBN.

Regarding the argument **-fromFile**, every time this argument is used, the program uses the sdtDBN stored in the according file. This sdtDBN can then be used to perform inference, as explained in the previous examples.

For instance, given the context of example 4 and assuming that the sdtDBN learned from example 1 was previously saved in the file obj_saved.txt, then, by running 

```
java -jar sdtDBN_v0_0_1.jar -fromFile obj_saved.txt -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5
```

the program will present the same output as in example 4 (plus the parameters of the sdtDBN).

It is important to mention that, when the argument **-fromFile** is given, if there are other arguments regarding sdtDBN learning, they are ignored. For example, if running

```
java -jar sdtDBN_v0_0_1.jar -fromFile someSavedDBN.txt -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1
```

the program will present the sdtDBN stored in the file someSavedDBN.txt, ignoring the remaining arguments.

This generalizes to situations where inference is made. For example, if there is an sdtDBN saved in someSavedDBN.txt which is different from the sdtDBN of example 1, then, by running

```
java -jar sdtDBN_v0_0_1.jar -fromFile someSavedDBN.txt -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5
```

the output would not be the same as the output of example 4. Because the **-fromFile** argument is given, the program reads the sdtDBN stored in the file someSavedDBN.txt, thus ignoring the arguments **-i**, **-is**, **-p**, **-s**, **-m** and **-b**, as these arguments are relative to sdtDBN structure and parameter learning.

# Graphical User Interface (GUI) of the sdtDBN program

### TODO: When GUI is finished some details will be given here, for now the most recent version of the GUI is provided to download for Windows as an EXE file


# Program Efficiency

### TODO: Efficiency of static parents and of inference (falar com Prof. Alexandra sobre isto!)

Ja esta escrito no documento da tese... vale a pena por aqui um resumo?

<!---
# References

Meter algumas referencias bibliograficas?

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
-->
