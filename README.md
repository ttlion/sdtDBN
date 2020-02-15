# What is sdtDBN?

This website contains an overview on the main sdtDBN functionalities.

tDBN is a Java program that creates a Dynamic Bayesian Network (DBN) from user multivariate longitudinal data, having polynomial time complexity in the number of attributes and observations. The complete implementation and functionalities of tDBN are publicly available [here](http://josemonteiro.github.io/tDBN/), being the Theorical background of tDBN explained in the following article:


>José L Monteiro, Susana Vinga, and Alexandra M Carvalho.
>Polynomial-time algorithm for learning optimal tree-augmented dynamic Bayesian networks.
>In UAI, pages 622–631, 2015. http://auai.org/uai2015/proceedings/papers/329.pdf


tDBN only allows learning a tDBN using dynamic data and does not allow to make inference on the created DBN. sdtDBN solves this issues, being an extension of tDBN to learn a DBN using both dynamic and static data and allowing the user to make inference on the learned DBN.

# Theoretical background of sdtDBN

sdtDBN was developed in the context of the Master's Thesis on Electrical and Computer Engineering of Tiago Leão, at Instituto Superior Técnico, Lisbon. The Thesis is available at **Aqui por ou link dps para a tese ou link para eventual artigo que se escreva**, in which all theorical background of sdtDBN is explained.

# Program release and libraries

## Current release

The program is currently in version 0.0.1 and can be downloaded [here](https://google.com). The program comes in an executable jar and its usage is explained and exemplified i in this webpage.

## Libraries

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

The arguments of the previous usage concern all the arguments of the tDBN program plus the new arguments of sdtDBN, for learning DBNs also with static attribute and to make inference in the learned DBN.

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

### Files with dynamic attributes

por aqui os inputs dynamic

### Files with static attributes

por aqui os inputs dynamic

### File with variables and respective timesteps to make inference

por aqui ficheiro


## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/ttlion/webPage_sdtDBN/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ttlion/webPage_sdtDBN/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
