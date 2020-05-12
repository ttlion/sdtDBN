# Website description 

This website contains an overview of the main functionalities of the sdtDBN implementation and explains the sdtDBN program's usage.

# What are sdtDBNs?

## Previous Work - tDBNs

The tDBN implementation is a Java program that creates a Dynamic Bayesian Network (DBN) from user multivariate longitudinal data, having polynomial-time complexity in the number of attributes and observations. The complete implementation and functionalities of the tDBN framework are publicly available at the [tDBN webpage](http://josemonteiro.github.io/tDBN/), being the theoretical background of tDBNs explained in the following article:


>José L Monteiro, Susana Vinga, and Alexandra M Carvalho.
>Polynomial-time algorithm for learning optimal tree-augmented dynamic Bayesian networks.
>In UAI, pages 622–631, 2015. [http://auai.org/uai2015/proceedings/papers/329.pdf](http://auai.org/uai2015/proceedings/papers/329.pdf)


## sdtDBNs as an extension of tDBNs

tDBNs only allow learning DBNs from dynamic data and do not allow neither to make inference on the created tDBNs nor to have restrictions in the structure of the learned DBNs. The sdtDBN framework solves all these issues, providing the following capabilities not available in the tDBN framework:

  - Learning DBNs from both dynamic and static data;
  - Allowing a user to make inference on the learned DBNs;
  - Giving the possibility for a user to define restrictions (prior knowledge) in the learned networks, forcing some relations either to exist or not to exist.

# Theoretical background of sdtDBNs

The sdtDBN program was developed in the context of the Master's Thesis in Electrical and Computer Engineering of Tiago Leão, at Instituto Superior Técnico, Lisbon. The Thesis is available at ***Thesis document or written article yet to be inserted here***, in which all theorical background of sdtDBNs is rigorously explained.

# Current release and external libraries

## Current release

The program is currently in its version v0.0.1 and can be downloaded [here](sdtDBN_v0_0_1.jar). The program comes as an executable jar and its usage is explained and exemplified in this webpage.

## External libraries

Just as the tDBN implementation, the sdtDBN implementation uses two external libraries:

- [opencsv](http://opencsv.sourceforge.net/), for parsing CSV files;

- [Apache Commons CLI](http://commons.apache.org/proper/commons-cli/), for parsing command line options.


# Graphical User Interface (GUI) of the sdtDBN program

While this website explains how to use the sdtDBN program using the command line, there is also a GUI available. Check [https://ttlion.github.io/sdtDBNsGUI/](https://ttlion.github.io/sdtDBNsGUI/), where details on how to use the developed GUI are provided, together with the most recent version of the GUI.

# Program usage

The usage of the sdtDBN program can be found by running

```
java -jar sdtDBN_v0_0_1.jar
```

The previous command will produce the following usage of the program:

```
usage: sdtDBN
 -b,--numStaticParents <int>                             Maximum number of
                                                         static parents of
                                                         a certain node
                                                         (default = 2).
 -c,--compact                                            Outputs network
                                                         in compact
                                                         format, omitting
                                                         intra-slice
                                                         edges. Only works
                                                         if specified
                                                         together with -d
                                                         and with
                                                         --markovLag 1.
 -d,--dotFormat                                          Outputs network
                                                         in dot format,
                                                         allowing direct
                                                         redirection into
                                                         Graphviz to
                                                         visualize the
                                                         graph.
 -fromFile,--fromObjFile <file>                          File with the
                                                         serialized object
                                                         of the sdtDBN.
 -i,--inputFile <file>                                   Input CSV file to
                                                         be used for
                                                         network learning.
 -inf,--inferenceFile <file>                             File with
                                                         variables to
                                                         perform inference
                                                         on.
 -infFmt,--inferenceFormat <file>                        Format to present
                                                         inference. Can be
                                                         distrSampl, to
                                                         give only a value
                                                         sampled according
                                                         to the
                                                         distribution;
                                                         mostProb, to give
                                                         only the most
                                                         probable value;
                                                         or distrib, to
                                                         give the full
                                                         distribution, for
                                                         each attribute
                                                         specified (where
                                                         distrSampl is
                                                         applied to
                                                         intermmediate
                                                         nodes). Default
                                                         is distrSampl.
 -is,--inputStaticFile <file>                            Input CSV file
                                                         with static
                                                         features to be
                                                         used for network
                                                         learning.
 -m,--markovLag <int>                                    Maximum Markov
                                                         lag to be
                                                         considered, which
                                                         is the longest
                                                         distance between
                                                         connected
                                                         time-slices.
                                                         Default is 1,
                                                         allowing edges
                                                         from one
                                                         preceding slice.
 -mA_dynPast,--mustAppear_dynPast <file>                 File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t'<t that
                                                         must be parents
                                                         of each Xi[t].
 -mA_dynSame,--mustAppear_dynSameTimestep <file>         File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t that must
                                                         be parents of
                                                         each Xi[t].
 -mA_static,--mustAppear_static <file>                   File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         static nodes that
                                                         must be parents
                                                         of each Xi[t].
 -mNotA_dynPast,--mustNotAppear_dynPast <file>           File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t'<t that
                                                         cannot be parents
                                                         of each Xi[t].
 -mNotA_dynSame,--mustNotAppear_dynSameTimestep <file>   File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t that
                                                         cannot be parents
                                                         of each Xi[t].
 -mNotA_static,--mustNotAppear_static <file>             File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         static nodes that
                                                         cannot be parents
                                                         of each Xi[t].
 -ns,--nonStationary                                     Learns a
                                                         non-stationary
                                                         network (one
                                                         transition
                                                         network per time
                                                         transition). By
                                                         default, a
                                                         stationary DBN is
                                                         learnt.
 -o,--outputFile <file>                                  Writes output to
                                                         <file>. If not
                                                         supplied, output
                                                         is written to
                                                         terminal.
 -obs,--obsFile <file>                                   File with the
                                                         observations
                                                         where inference
                                                         should be done.
 -obsStatic,--obsStaticFile <file>                       File with the
                                                         static
                                                         observations to
                                                         make inference.
 -outInf,--outputInferenceFile <file>                    Writes inference
                                                         output to <file>.
                                                         If not supplied,
                                                         inference output
                                                         is written to
                                                         terminal.
 -p,--numParents <int>                                   Maximum number of
                                                         parents from
                                                         preceding
                                                         time-slice(s).
 -pm,--parameters                                        Learns and
                                                         outputs the
                                                         network
                                                         parameters.
 -r,--root <int>                                         Root node of the
                                                         intra-slice tree.
                                                         By default, root
                                                         is arbitrary.
 -s,--scoringFunction <arg>                              Scoring function
                                                         to be used,
                                                         either MDL or LL.
                                                         MDL is used by
                                                         default.
 -sp,--spanning                                          Forces
                                                         intra-slice
                                                         connectivity to
                                                         be a tree instead
                                                         of a forest,
                                                         eventually
                                                         producing a
                                                         structure with a
                                                         lower score.
 -t,--trajectory <int>                                   Timestep until
                                                         which trajectory
                                                         is to be
                                                         determined.
 -tf,--outputTrajectoryFile <file>                       Writes predicted
                                                         trajectories to
                                                         <file>. If not
                                                         supplied, output
                                                         is written to
                                                         terminal.
 -toFile,--toObjFile <file>                              File in which the
                                                         serialized object
                                                         with the sdtDBN
                                                         should be stored.
```

The previous usage has all the arguments of the original tDBN program plus the new arguments of the sdtDBN program.

As the [tDBN webpage](http://josemonteiro.github.io/tDBN/) already explains the usage of the proper arguments of the tDBN framework, in this webpage it is described the usage of the arguments used only in the sdtDBN framework, which are the following:

```
 -b,--numStaticParents <int>                             Maximum number of
                                                         static parents of
                                                         a certain node
                                                         (default = 2).
 -fromFile,--fromObjFile <file>                          File with the
                                                         serialized object
                                                         of the sdtDBN.
 -inf,--inferenceFile <file>                             File with
                                                         variables to
                                                         perform inference
                                                         on.
 -infFmt,--inferenceFormat <file>                        Format to present
                                                         inference. Can be
                                                         distrSampl, to
                                                         give only a value
                                                         sampled according
                                                         to the
                                                         distribution;
                                                         mostProb, to give
                                                         only the most
                                                         probable value;
                                                         or distrib, to
                                                         give the full
                                                         distribution, for
                                                         each attribute
                                                         specified (where
                                                         distrSampl is
                                                         applied to
                                                         intermmediate
                                                         nodes). Default
                                                         is distrSampl.
 -is,--inputStaticFile <file>                            Input CSV file
                                                         with static
                                                         features to be
                                                         used for network
                                                         learning.
 -mA_dynPast,--mustAppear_dynPast <file>                 File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t'<t that
                                                         must be parents
                                                         of each Xi[t].
 -mA_dynSame,--mustAppear_dynSameTimestep <file>         File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t that must
                                                         be parents of
                                                         each Xi[t].
 -mA_static,--mustAppear_static <file>                   File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         static nodes that
                                                         must be parents
                                                         of each Xi[t].
 -mNotA_dynPast,--mustNotAppear_dynPast <file>           File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t'<t that
                                                         cannot be parents
                                                         of each Xi[t].
 -mNotA_dynSame,--mustNotAppear_dynSameTimestep <file>   File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         dynamic nodes
                                                         from t that
                                                         cannot be parents
                                                         of each Xi[t].
 -mNotA_static,--mustNotAppear_static <file>             File that, for
                                                         each node Xi[t],
                                                         contains the
                                                         static nodes that
                                                         cannot be parents
                                                         of each Xi[t].
 -obs,--obsFile <file>                                   File with the
                                                         observations
                                                         where inference
                                                         should be done.
 -obsStatic,--obsStaticFile <file>                       File with the
                                                         static
                                                         observations to
                                                         make inference.
 -outInf,--outputInferenceFile <file>                    Writes inference
                                                         output to <file>.
                                                         If not supplied,
                                                         inference output
                                                         is written to
                                                         terminal.
 -t,--trajectory <int>                                   Timestep until
                                                         which trajectory
                                                         is to be
                                                         determined.
 -tf,--outputTrajectoryFile <file>                       Writes predicted
                                                         trajectories to
                                                         <file>. If not
                                                         supplied, output
                                                         is written to
                                                         terminal.
 -toFile,--toObjFile <file>                              File in which the
                                                         serialized object
                                                         with the sdtDBN
                                                         should be stored.
```

The usage of the arguments not in the previous list should be checked at the [tDBN webpage](http://josemonteiro.github.io/tDBN/).

# Input files

## Input files' extension

All input files must be given as CSV files (comma-separated values).

## Input files to learn an sdtDBN from data and make inference in the learned sdtDBN

The sdtDBN program learns DBNs with dynamic and static attributes from observations of several attributes, finding the relations that maximize a certain score. With an sdtDBN learned, inference can be made, to estimate the values of the attributes in certain timesteps. 

It is presented next the format of the files with observations of dynamic and static attributes and the format of the file with the attributes in which inference should be made. 

At the end of the webpage, there are provided some [Illustrative examples][exMenu]. [Example 1][ex1] shows how to learn an sdtDBN from input data. [Example 2][ex2] provides an example where inference is made on certain attributes. [Example 3][ex3] displays how to estimate a trajectory of all attributes. [Example 4][ex4] joins [Examples 2 and 3][exMenu].

### Files with observations of dynamic attributes

All files with observations of dynamic attributes should follow the following format:

- The first line should be the header, where the first value must be some identification tag and the remaining values should be each attribute's name together with the proper timestep, using the notation "attName__timestep".

  - The order of the attributes and timesteps must obey the following rules:
    - Each timestep must have all its attributes in consecutive positions;
    - The order of the attributes must be the same in all timesteps.
  - Example for two attributes and two timesteps: 
    - **id,attNameX__0,attNameY__0,attNameX__1,attNameY__1**

- In each of the remaining lines, the first position must be the subject identifier and the remaining positions must be the values of the attributes in the respective timesteps, in the order defined in the header line.

- Missing values should be marked either by not writing anything or by putting "?".

An example file with observations of dynamic attributes is presented next. In this file, there are 2 attributes and 3 timesteps. There are missing values at **attX\[2\]** of **subject 20** and at **attY\[1\]** of **subject 21**.

```
id,attX__0,attY__0,attX__1,attY__1,attX__2,attY__2
20,3,-1,8,0,?,3
21,4,2,3,,2,-8
```

#### Arguments that use files with observations of dynamic attributes

- **-i**: File with the dynamic observations used to learn the DBN;

- **-obs**: File with dynamic observations of the subjects in which inference is going to be made.


### Files with observations of static attributes

All files with observations of static attributes should follow the following format:

- The first line should be the header, where the first value must be some identification tag and the remaining values must be each attribute's name.
  
- In each of the remaining lines, the first position must be the subject's identifier and the remaining positions must be the values of the static attributes, in the order defined in the header line.
  - The user must guarantee that every subject in the static file exists, with the same id, in the respective dynamic file:
      - Subjects in **-is** file should exist in **-i** file;
      - Subjects in **-obsStatic** file should exist in **-obs** file;
      - There may be subjects in the dynamic files that are not in the respective static files, but the opposite cannot be true!

- Missing values should be marked either by not writing anything or by putting "?".

An example file with observations of static attributes is presented next. In this file, there are 4 attributes. There are missing values at **attC** of **subject 20** and at **attW** of **subject 21**.

```
id,attA,attC,attD,attW
20,A,,e,0
21,B,2,4,?
```

#### Arguments that use files with observations of static attributes

- **-is**: File with the static observations used to learn the DBN. If not given, the program will learn a tDBN, without static features. If given, the program will learn an sdtDBN, with static and dynamic features;

- **-obsStatic**: File with static observations of the subjects in which inference is going to be made.


### File with variables and respective timesteps to make inference

The file with the variables and respective timesteps in which inference should be made must follow the following format:

- There must be two values per line, separated by ",":
  - The first value should be the dynamic attribute's name;
  - The second value should be the timestep.

- All attributes' names specified in this file must exist in the dynamic attributes' files. The timesteps may not exist in the dynamic attributes' files: in that case, if the learned network was defined to be stationary, values will be predicted until the specified timestep, according to the learned network structure.

An example file where the program would make inference for **attX\[2\]** and **attY\[3\]** is presented next.

```
attX,2
attY,3
```

#### Argument with variables and respective timesteps to make inference

- **-inf**: File with variables and respective timesteps to make inference.



## Input files to make restrictions in the relations of the sdtDBN

The user may desire to obtain the sdtDBN that maximizes a certain score when considering only the sdtDBNs structures that include some restrictions in the relations between nodes. 

There are three types of relations in an sdtDBN: 
1. Relations between dynamic nodes in different timesteps;
2. Relations between dynamic nodes in the same timestep;
3. Relations between static and dynamic nodes.

For each of the aforementioned types of relations, the user can specify if a certain relation between two nodes must exist or cannot exist.

The structure of the files used to make restrictions in the network is presented next. [Example 6][ex6] provides a situation with restrictions on each one of the previously mentioned types of relations of the sdtDBN.


#### Files with restrictions on parents in the same timestep or on static parents

The files with restrictions on parents in the same timestep or on static parents should follow the following format:

- There must be at least three values per line, separated by ",":
  - The first value should be the timestep of the child node being considered;
  - The second value should be the name of the attribute of the child node being considered;
  - Each remaining value should be the name of an attribute that either must be or cannot be parent of the node specified by the first two values of the line.

- All nodes specified in this file should be valid (the names of the attributes must have been specified in the dynamic or static attributes' files and the timesteps must be valid timesteps of the sdtDBN to be learned).

The same file can specify either forbidden or mandatory relations, according to the argument of the program in which the file is introduced. 

Using **attX** and **attY** as dynamic attributes and **attA** and **attB** as static attributes, some examples are given next.

Regarding restrictions on parents in the same timestep, a file having the lines

```
2,attX,attY
3,attY,attX
```

refers to the following relations:
- **attY\[2\] 🠪 attX\[2\]**;
- **attX\[3\] 🠪 attY\[3\]**.

According to the argument in which the file is inserted, it can define one of two options:
  - If provided as the argument with forbidden parents from the same timestep, it would define that the relations could not exist;
  - If provided as the argument with mandatory parents from the same timestep, it would define that the relations had to exist.


Regarding restrictions on static parents, a file having the lines

```
2,attX,attA,attB
3,attY,attB
```

refers to the following relations:
- **attA 🠪 attX\[2\]**;
- **attB 🠪 attX\[2\]**;
- **attB 🠪 attY\[3\]**.

According to the argument in which the file is inserted, it can define one of two options:
  - If provided as the argument with forbidden static parents, it would define that the relations could not exist;
  - If provided as the argument with mandatory static parents, it would define that the relations had to exist;


#### Files with restrictions on parents from previous timesteps

The files with restrictions on parents from previous timesteps should follow the following format:

- There must be at least four values per line, separated by ",":
  - The first value should be the timestep of the child node being considered;
  - The second value should be the name of the attribute of the child node being considered;
  - The remaining values should be given as pairs, where:
    - The first element of each pair should be the name of the attribute that either must be or cannot be parent of the node specified by the first two values of the line.
    - The second element of each pair should define "how many timesteps is the parent behind the child". Rigorously: the distance between the child node's timestep (first value of the line) and the timestep of the parent to which the restriction applies.

- Each line must have an even number of values (the first two define the child node and each parent node from previous timesteps is defined by a pair of values).

- All nodes specified in this file should be valid (the names of the attributes must have been specified in the dynamic attributes' file and the timesteps must be valid timesteps of the sdtDBN to be learned).

- The distance between nodes must be an integer value with absolute value between 1 and the Markov lag (including both 1 and the Markov lag). This distance can be given as a positive or negative number (the program always uses the absolute value).

The same file can specify either forbidden or mandatory relations, according to the argument of the program in which the file is introduced.

For example, a file having the lines

```
2,attX,attY,-2,attX,-1
3,attY,attX,-1,attY,-1
```

refers to the following relations:
- **attY\[0\] 🠪 attX\[2\]**;
- **attX\[1\] 🠪 attX\[2\]**;
- **attX\[2\] 🠪 attY\[3\]**;
- **attY\[2\] 🠪 attY\[3\]**.

According to the argument in which the file is inserted, it can define one of two options:
  - If provided as the argument with forbidden parents from previous timesteps, it would define that the relations could not exist;
  - If provided as the argument with mandatory parents from previous timesteps, it would define that the relations had to exist;


#### Arguments that allow the user to make restrictions in the relations of the sdtDBN 

- **-mA_dynPast**: File specifying, for any desired node of the sdtDBN, the nodes that must be its parents from previous timesteps.
- **-mA_dynSame**: File specifying, for any desired node of the sdtDBN, the node that must be its parent from the same timestep (only one node, because the intra-slice connectivity must be a tree. If, for a certain node, the user specifies more than one mandatory parent of the same timestep, the program chooses the connection that maximizes the global score of the sdtDBN).
- **-mA_static**: File specifying, for any desired node of the sdtDBN, the nodes that must be its static parents.
- **-mNotA_dynPast**: File specifying, for any desired node of the sdtDBN, the nodes that cannot be its parents from previous timesteps.
- **-mNotA_dynSame**: File specifying, for any desired node of the sdtDBN, the nodes that cannot be its parents from the same timestep.
- **-mNotA_static**: File specifying, for any desired node of the sdtDBN, the nodes that cannot be its static parents.


## Files to store and retrieve an sdtDBN object

When making inference on an sdtDBN, the user may desire to make inference multiple times, while keeping the same sdtDBN. In this situation, there is no need for the program to learn the sdtDBN each time the user makes inference, as the sdtDBN stays the same. 

In order to allow a user to perform inference several times on the same learned sdtDBN, two arguments were created: **-toFile** and **-fromFile**, each one being a filename.

The argument **-toFile**, when given, saves the sdtDBN object (by serializing it) in a file with the name given in this argument. 
- For example, if specified **-toFile obj_example_out.txt**, the program saves the object with the learned sdtDBN in the file **obj_example_out.txt**, for future use.

The argument **-fromFile**, when given, gets the sdtDBN object from the file with the name given in this argument. 
- For example, if specified **-fromFile obj_example_in.txt**, the program reads the sdtDBN object from the file **obj_example_in.txt** (ignoring, if given, all other program's arguments related to sdtDBN structure and parameter learning).

To get an example regarding storing and reading an sdtDBN to/from a file, check [Example 5][ex5]. 

# Illustrative examples
[exMenu]: #illustrative-examples

The examples provided next were already mentioned in the explanations of the proper input files. The examples cover the following situations:

1. [Example 1][ex1] illustrates how to learn an sdtDBN from input data with dynamic and static observations;
2. [Example 2][ex2] allows to understand how to make inference on desired attributes;
3. [Example 3][ex3] presents how to estimate a trajectory of all attributes;
4. [Example 4][ex4] combines Examples 2 and 3;
5. [Example 5][ex5] shows how to store an sdtDBN in a file and how to retrieve an sdtDBN stored in a file;
6. [Example 6][ex6] offers a situation where an sdtDBN is learned with restrictions.

## Example 1: Learning an sdtDBN with dynamic and static attributes
[ex1]: #example-1-learning-an-sdtdbn-with-dynamic-and-static-attributes

This example focuses on the learning component of the program, introducing how to learn a DBN also with static attributes (original tDBN framework only learned networks with dynamic attributes). 

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): File with observations of dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): File with observations of static attributes for learning.

To learn a stationary sdtDBN with 1 as the Markov lag, a maximum of 1 dynamic parent from the previous time slice and a maximum of 1 static parent per node, the following command can be run:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1
```

The obtained output when running the previous command line is:

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

To get a graphical representation of the learned sdtDBN, the argument **-d** can be used, just as in the tDBN framework, as illustrated next:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -d | dot -Tpng -o fig_example1.png
```

The previous command line would output the following graph:

![Image](fig_example1.png)

To learn the parameters of the created DBN, the argument **-pm** can be used. By running the command line

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -pm
```

the resulting output would be:


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

## Example 2: Inference on specific attributes of a learned sdtDBN with dynamic and static attributes
[ex2]: #example-2-inference-on-specific-attributes-of-a-learned-sdtdbn-with-dynamic-and-static-attributes

Following the sdtDBN learned in [Example 1][ex1], inference can be made on that sdtDBN. In this example, it is explained how to make inference on a specific attribute at a specific timestep.

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): File with observations of dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): File with observations of static attributes for learning;
- [example2_dynamic_inf.csv](example2_dynamic_inf.csv): File with the dynamic observations of the subjects where inference is to be made;
- [example2_static_inf.csv](example2_static_inf.csv): File with the static observations of the subjects where inference is to be made;
- [example2_infVars.csv](example2_infVars.csv): File with the dynamic attributes and respective timesteps where the user desires to make inference for the given subjects.

When making inference, one of three inference modes can be selected with the argument **-infFmt**:

- **-infFmt distrSampl**: This mode will present, for each **attribute\[timestep\]** where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), a randomly sampled value for each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)). 
  - Each value is randomly sampled according to the probability distribution of each **attribute\[timestep\]**, given the observations of the proper subject.

- **-infFmt mostProb**: This mode will present, for each **attribute\[timestep\]** where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), the most probable value for each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)).

- **-infFmt distrib**: This mode will present, for each **attribute\[timestep\]** where inference was defined (file [example2_infVars.csv](example2_infVars.csv)), the conditional distribution of the learned network, for each subject specified (files [example2_dynamic_inf.csv](example2_dynamic_inf.csv) and [example2_static_inf.csv](example2_static_inf.csv)). 
  - In intermediate nodes, the values are estimated by getting a random sample of the node's value, according to its probability distribution, given the observations of the proper subject.

If there are cases where inference is not possible because the parent nodes' values are not given in the observations' files and cannot be determined by the model, the program will inform that inference is not possible on those specific cases, producing **null** (in **-infFmt mostProb**) or **-1** (in **-infFmt distrib**).

If specifying **-infFmt distrSampl**, the following command line should be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt distrSampl
```

The resulting output would be, for example (the output may vary, because there is the random component):

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

The obtained output would be:

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

The resulting output would be, for example (the output may vary, because there is the random component):

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

If wanting the output of the inference to be written in a specific file, the user needs to provide the file to be created in the **-outInf** argument. For example,

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt distrib -outInf outputExample2.csv
```

would write the inference output to the file [outputExample2.csv](outputExample2.csv) (creating it if needed).


## Example 3: Getting an estimated trajectory
[ex3]: #example-3-getting-an-estimated-trajectory

Also following the sdtDBN learned in [Example 1][ex1], it is explained in this example how the user can estimate a trajectory of all attributes until a certain timestep, given observations of some subjects.

The files used for this example are the following:

- [example1_dynamic.csv](example1_dynamic.csv): File with observations of dynamic attributes for learning;
- [example1_static.csv](example1_static.csv): File with observations of static attributes for learning;
- [example2_dynamic_inf.csv](example2_dynamic_inf.csv): File with the dynamic observations of the subjects where inference should be made;
- [example2_static_inf.csv](example2_static_inf.csv): File with the static observations of the subjects where inference should be made.

To get the estimated trajectories, the user needs to define the maximum timestep in the argument **-t**. 

The user can also use the argument **-infFmt** to specify how the values of the nodes are determined from the probability distributions:
  - If using **-infFmt mostProb**, the values selected for each node are always the most probable ones, given the observations of each subject;
  - Otherwise, the values are randomly sampled according to the probability distribution of each node, given the observations of each subject. 

For example, if the user wants to determine the most probable trajectory of all attributes until **timestep 5**, the following command can be inserted:

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -t 5 -infFmt mostProb
```

The previous command would provide the following output:

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

As can be seen in **b\[0\]** and **a\[1\]** of **subject 3**, the program does not provide any estimations where those estimations cannot be determined (if the parent nodes are not specified in the observations and cannot be estimated by the model).

If wanting the output of the estimated trajectories to be written to a specific file, the user needs to give the file to be created in the **-tf** argument. For example,

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -t 5 -infFmt mostProb -tf outputExample3.csv
```

would write the estimated trajectories to the file [outputExample3.csv](outputExample3.csv) (creating it if needed).

## Example 4: Getting an estimated trajectory and also making inference on specific attributes
[ex4]: #example-4-getting-an-estimated-trajectory-and-also-making-inference-on-specific-attributes

The program allows the user to do [Examples 2 and 3][exMenu] at the same time. For example, by running

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

which is the combined output of [Examples 2 and 3][exMenu].

The user may also specify two different output files, one for the result of the inference on certain attributes and the other for the output of the estimated trajectories. This can be done by using simultaneously the arguments specified in [Examples 2 and 3][exMenu], **-outInf** and **-tf**, respectively. For example,

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5 -outInf outputExample2.csv -tf outputExample3.csv
```

would write the respective outputs to the files [outputExample2.csv](outputExample2.csv) and [outputExample3.csv](outputExample3.csv), as in [Examples 2 and 3][exMenu].


## Example 5: Storing/reading an sdtDBN object to/from a file
[ex5]: #example-5-storingreading-an-sdtdbn-object-tofrom-a-file

As explained previously in the webpage, the argument **-toFile** allows an sdtDBN object to be stored in a file, while the argument **-fromFile** allows an sdtDBN object to be read from a file. This example explains how to use these two arguments.

Regarding the argument **-toFile**, every time this argument is used, the learned sdtDBN is saved in the according file. When this argument is used, the program always learns the sdtDBN's parameters, so that the file where the sdtDBN is saved also has the proper parameters of the learned sdtDBN.

Regarding the argument **-fromFile**, every time this argument is used, the program retrieves the sdtDBN object stored in the according file. This sdtDBN can then be used to perform inference, as explained in the previous examples.

Following [Example 1][ex1], where an sdtDBN was learned, the argument **-toFile** can be used to save the learned sdtDBN in a file. Therefore, by running

```
java -jar sdtDBN_v0_0_1.jar -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -toFile obj_saved.txt
```

the program does everything explained in [Example 1][ex1] and also saves the learned sdtDBN in a file named **obj_saved.txt**, which the program creates.

Having this sdtDBN object saved in a file, the argument **-fromFile** can be used to retrieve the sdtDBN. For example, by running 

```
java -jar sdtDBN_v0_0_1.jar -fromFile obj_saved.txt
```

the program would output the sdtDBN stored in the file **obj_saved.txt**, which means that the output would be the same as the output presented in [Example 1][ex1] (plus the parameters of the learned sdtDBN).

The arguments **-toFile** and **-fromFile** can be combined with the several situations presented in the previous examples.


For instance, given the context of [Example 4][ex4] and assuming that the sdtDBN learned from [Example 1][ex1] was previously saved in the file **obj_saved.txt**, then, by running 

```
java -jar sdtDBN_v0_0_1.jar -fromFile obj_saved.txt -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5
```

the program will present the same output as in [Example 4][ex4] (plus the parameters of the sdtDBN).

When the argument **-fromFile** is given, if there are other arguments regarding sdtDBN learning, they are ignored. For example, if running

```
java -jar sdtDBN_v0_0_1.jar -fromFile someSavedDBN.txt -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1
```

the program will present the sdtDBN stored in the file **someSavedDBN.txt**, ignoring the remaining arguments.

This generalizes to situations where inference is made. For example, if there is an sdtDBN saved in **someSavedDBN.txt**, being this sdtDBN different from the sdtDBN of [Example 1][ex1], then, when running

```
java -jar sdtDBN_v0_0_1.jar -fromFile someSavedDBN.txt -i example1_dynamic.csv -is example1_static.csv -p 1 -s ll -m 1 -b 1 -obs example2_dynamic_inf.csv -obsStatic example2_static_inf.csv -inf example2_infVars.csv -infFmt mostProb -t 5
```

the output would not be the same as the output of [Example 4][ex4], because the **-fromFile** argument is given, so the program reads the sdtDBN stored in the file **someSavedDBN.txt**, thus ignoring the arguments **-i**, **-is**, **-p**, **-s**, **-m** and **-b**, as these arguments are relative to sdtDBN structure and parameter learning.

## Example 6: Learning an sdtDBN with restrictions
[ex6]: #example-6-learning-an-sdtdbn-with-restrictions

This example demonstrates how to introduce constraints in the network structure when learning an sdtDBN from input data.

The files used for this example are the following:

- [example6_dynamic.csv](example6_dynamic.csv): File with observations of dynamic attributes for learning;
- [example6_static.csv](example6_static.csv): File with observations of static attributes for learning;
- [example6_mandatory_dynPast.csv](example6_mandatory_dynPast.csv): File specifying, for any desired node of the sdtDBN, the nodes that must be its parents from previous timesteps;
- [example6_mandatory_dynSame.csv](example6_mandatory_dynSame.csv): File specifying, for any desired node of the sdtDBN, the node that must be its parent from the same timestep;
- [example6_mandatory_static.csv](example6_mandatory_static.csv): File specifying, for any desired node of the sdtDBN, the nodes that must be its static parents;
- [example6_forbidden_dynPast.csv](example6_forbidden_dynPast.csv): File specifying, for any desired node of the sdtDBN, the nodes that cannot be its parents from previous timesteps;
- [example6_forbidden_dynSame.csv](example6_forbidden_dynSame.csv): File specifying, for any desired node of the sdtDBN, the nodes that cannot be its parents from the same timestep;
- [example6_forbidden_static.csv](example6_forbidden_static.csv): File specifying, for any desired node of the sdtDBN, the nodes that cannot be its static parents;

Using the observations from [example6_dynamic.csv](example6_dynamic.csv) and [example6_static.csv](example6_static.csv), the following command can be run to learn a non-stationary sdtDBN with Markov lag of 2, a maximum per node of 2 parents from previous timesteps and a maximum per node of 2 static parents:

```
java -jar sdtDBN_v0_0_1.jar -i example6_dynamic.csv -is example6_static.csv -sp -p 2 -s ll -m 2 -b 2 -ns
```

The obtained sdtDBN when running the previous command is:

```
-----------------

a[0] -> a[2]
a[0] -> b[2]
a[0] -> c[2]


c[2] -> a[2]
a[2] -> b[2]

y -> c[2]
z -> c[2]

-----------------

a[1] -> a[3]
a[1] -> b[3]
a[1] -> c[3]


c[3] -> a[3]
a[3] -> b[3]
```

Note that the learned network has more relations than the ones used in the previous examples, which was done to show how to introduce several restrictions in a network.

The user can specify restrictions to the network by using the proper files. For demonstration, the used files introduce the following restrictions:
- File [example6_mandatory_dynPast.csv](example6_mandatory_dynPast.csv):
  - **a\[2\]** must have **a\[1\]** and **b\[0\]** as parents from previous timesteps;
  - **c\[2\]** must have **c\[0\]** as parent from previous timesteps;
  - **c\[3\]** must have **b\[2\]** as parent from previous timesteps;
- File [example6_mandatory_dynSame.csv](example6_mandatory_dynSame.csv):
  - **b\[2\]** must have **c\[2\]** as parent from the same timestep;
  - **c\[3\]** must have **a\[3\]** as parent from the same timestep;
- File [example6_mandatory_static.csv](example6_mandatory_static.csv):
  - **a\[2\]** must have **x** and **y** as static parents;
  - **c\[3\]** must have **z** as static parent;
  - **b\[3\]** must have **x** as static parent;
- File [example6_forbidden_dynPast.csv](example6_forbidden_dynPast.csv):
  - **a\[2\]** cannot have neither **a\[0\]** nor **c\[1\]** as parents from previous timesteps;
  - **c\[3\]** cannot have **a\[1\]** as parent from previous timesteps;
  - **b\[3\]** cannot have **a\[1\]** as parent from previous timesteps;
- File [example6_forbidden_dynSame.csv](example6_forbidden_dynSame.csv):
  - **a\[2\]** cannot have **c\[2\]** as parent from the same timestep;
  - **b\[3\]** cannot have **a\[3\]** as parent from the same timestep;
- File [example6_forbidden_static.csv](example6_forbidden_static.csv):
  - **c\[2\]** cannot have neither **y** nor **z** as static parents.

To learn an sdtDBN with the same structure as the one shown before in this example, but with the specified restrictions, the user should run the following command:

```
java -jar sdtDBN_v0_0_1.jar -i example6_dynamic.csv -is example6_static.csv -sp -p 2 -s ll -m 2 -b 2 -ns -mA_dynPast example6_mandatory_dynPast.csv -mA_dynSame example6_mandatory_dynSame.csv -mA_static example6_mandatory_static.csv -mNotA_dynPast example6_forbidden_dynPast.csv -mNotA_dynSame example6_forbidden_dynSame.csv -mNotA_static example6_forbidden_static.csv
```

The sdtDBN obtained would then be:

```
-----------------

b[0] -> a[2]
a[0] -> b[2]
c[0] -> c[2]

a[1] -> a[2]

b[2] -> a[2]
c[2] -> b[2]

x -> a[2]
y -> a[2]

-----------------

a[1] -> a[3]
b[1] -> b[3]

b[2] -> c[3]

c[3] -> b[3]
a[3] -> c[3]

x -> b[3]
z -> c[3]
```

It can be noticed that the previous sdtDBN satisfies all the introduced restrictions.


<!---
# Program Efficiency

### TODO: Efficiency of static parents and of inference (falar com Prof. Alexandra sobre isto!)

Ja esta escrito no documento da tese... vale a pena por aqui um resumo?


# References

Meter algumas referencias bibliograficas?

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
-->
