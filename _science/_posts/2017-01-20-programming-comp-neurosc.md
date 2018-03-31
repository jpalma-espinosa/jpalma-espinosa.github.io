---
layout: single
category: science
title: 'Good(?) programming practices in Computational Neuroscience'
date: 2017-01-20
permalink: /science/programming-comp-neurosc
tag: Neuroscience, LASCON, LACONEU, Science, python, The Algorithm
---

# Why? Oh, Lord, why?!
Yes, almost every time I have to read some piece of code written by me or other people, I ask myself the exact same question "Why, oh Lord WHY!?".  Why they(or I) used this name of variable? Why did I put the plotting stage in here?? Why I didn't comment my code, Oh, Lord, WHY!!??!.

Let's go a little back in the past, to understand the question that motivates this paragraph, and this entire post.

When I first entered into neuroscience, I started to write little pieces of code: for plotting data, take one or two statistical parameters and compare stuff, nothing fancy. 
When my interest (and the requirements from the PIs) arrised, I started to write more long and complex scripts and codes.  In that moment I realized that had troubles *writting good code* (I guess I still have them but hey!, I'm improving). When I went to [LASCON](http://sisne.org/?page_id=34&lang=en) I finally realized that I didn't know how to write a good piece of sofware.

On the other hand, my biological basis are not quite strong, so I often needed to use codes wrote by other researchers arround the world. Because of that, and the fact I was writting computational models of neurons ([compartmental models](http://www.scholarpedia.org/article/Rall_model#Compartmental_model) if you like), I ended up downloading a LOT of codes from [Model Database](https://senselab.med.yale.edu/modeldb/).
Why I make this clarification? Well, because ModelDB holds a whole library of computational models of neurons, where most of them are written in [NEURON](http://neuron.yale.edu/).  With NEURON you can write in hoc, python, or a mix of [both of them](https://www.neuron.yale.edu/neuron/static/new_doc/programming/python.html), and if you are not careful, you'll have a nice mess (I guess somebody would love to call it [entropy](https://en.wikipedia.org/wiki/Entropy_(order_and_disorder)))

So, the overall picture right now is: A guy who doesn't know how to write good software, reading a bunch of codes made by other people that came from the biological world and does not have the techniques to write good code. This makes a complete mess

# The journey begins
As I told in a previous [post](/science/SummerSchool), I learned a lot of techniques in computational neuroscience in LASCON.  That was my starting point for improving my coding and my workflow.  What I would try to do now is to put those things, hints and tricks in order, so the people that read this entry (yes, I'm talking to YOU!), could benefit for what I had ~~suffered~~ passed

## Workflow
The first thing that I discovered that I lacked, was a proper workflow. Something that could make me more productive at the time of starting a new project.  I read a lot of blogs (which unfortunatelly don't remember) that emphatizes on this matter(you can read a very defined, and complicated software engineering workflow [here](http://leansoftwareengineering.com/2009/06/08/workflow-patterns/)).

## Setting up the environment
In my working computer, create a folder inside my project folder, with the name of my current project. Within this new folder, I create 4 folders, which I will put my references, lab notebook([jupyter](http://jupyter.org/) based), the experiments that I will do and an aditional folder with some other documents related to the project (recipts, software licences, etc)

```Bash
cd javier/Projects
mkdir newProject
cd newProject
mkdir ref
mkdir ntbk
mkdir experiments
mkdir docs
```

Beware that the experiments folder is going to have a lot of folders also: code, data, plots, results, saved, and optional, mod.
In *code* I will put...yeah! the code that I will write (python, NEURON (using hoc), matlab, java, whatever).  As I work modelling biological behaviour, I need to have some biological data for developing and contrasting my models.  All of this data will be saved in *data* folder.  I guess that I don't need to explain the *plots* folder.  The *results* folder will have the FINAL results, separated by date (yup, in a subfolder named YYYYMMDD_HH_MM). *saved* is a temporal folder where I put the output of one simulation.  Often, my simulations spits a lot of information, which is usually voltage vectors, time vectors, and some other parameters.  The optional folder *mod* is for storing the channels or point process when I use NEURON (I will not define what a channel or point process is. You can search it on the [NEURON webpage](http://neuron.yale.edu/neuron/static/papers/nc2000/nmodl400.pdf)).

```Bash
cd experiments
mkdir code
mkdir data
mkdir plots
mkdir results
mkdir saved
mkdir mod
```

Now that I have my whole working structure, I will start a GitHub project in it.  GitHub is a great place for putting codes, it has a control version system, besides other things that you may read in their [webpage](https://github.com/).  [I use GitHub](https://github.com/jpalma-espinosa) because it helps in storing my code on the cloud, so I am sure that my work is not going to be lost by a power cut, aliens or explosions. So, every time I arrive to the lab, is easy as "git pull" and when leaving the lab, is easy as "git push origin master", and that's it!
(pro tip1: you can use [git lfs](https://git-lfs.github.com/) in order to store your pdf also ^_^!. Pro tip2: [GitHub loves students ;)](https://education.github.com/pack))


## Defining the model and the experiments
After (often simultaneously) reading papers (stored in the *ref folder*), I outline the model: What I want to study and what are going to be the experiments that I will do.  Usually this is a cyclic process, so you should better keep track on it. 
In the best case scenario, I start a project notebook(yup, in jupyter), outline the big picture and set up a list of experiments, with the respective changes in the control variables.  This will help me in track the results and answer possible akward results.  I put this notebook in the *ntbk folder*.


## Coding
Well, there is no much to write here, just do your code, BUT use good programming techniques (tips below)
Unless you use OOP (Object Oriented Programming), my codes are usually divided by blocks. The first one will have the parameters (found on the papers, often), then the routine or model, then the plotting part, then the output datafiles part and finally the parameters output which I will use then to compare my results.


## Lab Notebook
It costed me a lot to start a lab notebook, because...what protocols could you write in a computational neuroscientific experiment? Actually, there is a lot.  I write the values that certain variable has, also I keep track of the experiments that I did on the day, paste certains ideas on how to optimize the code, some math that I use in the code, preliminary results, etc.
I do all of this in jupyter notebooks (also, in ntbk folder)

# Coding tips
I wanted to talk first about my workflow schema, because I feel that just writing a bunch of coding tips without a context will be like [Metallica withouth the Hetfield's 'Yeah'](https://www.youtube.com/watch?v=1KccfZCojTY).  
Now that you have, more or less, an idea of what is my way of working, I hope that you will acknowledge that, if you don't have a proper order in what you do, you will end up with a LOT of entropy in your life.

## Comment your code
One of the best tips that I have read is *comment your fucking code!!*, yup, fucking included.  I have given myself a lot of headaches by trying to understand what the following does

```python
ss=[]
b = [2 4 6]
from aa in b
	ss.append(b*exp(-b/(100*aa))
```

Could have been easier to do this, instead?

```python
ss=[] #output array
b = [2 4 6] #conductance
from aa in b
	ss.append(b*exp(-b/(100*aa)) #some fancy output
```
or even better

```python
output=[]
somatic_conductance = [2 4 6]
from g in somatic_conductance:
	calculated_function = somatic_conductance*exp(-somatic_conductance/100*g) #from author et al., 2016
	output.append(calculated_function)
```

As you can see, it is always a good idea to comment your code, because our short term memory(the one we often use while programming), is way too volatile.  But is also a better idea to *self comment* the code.  Use significant *VariableNames* (or Variable_names, whatever your philosophical belief is).

## Divide and conquer
We are often too prone to write the *most powerfull great all time 100 real no fake working code* that we loose sight on what we want to do.  Draw yourself an idea of what you want to achieve with your code, what experiment does it replicates? what are the expected outputs?. With that answers, then make a drawing, using whatever is usefull for you, to describe the problem.  Then divide the problem in smaller and simpler tasks. Enumerate those tasks and THEN start to code.

## Print data out...always!
between your code, it is always a good idea to spit some output to your console, or whatever the source of communication you have with your code.  In that case you could know if your code hanged, killed itself, commited suicide or you are just a bad programmer.

```python
output=[]
somatic_conductance = [2 4 6]
print 'Somatic conductance created with %s elements created'&len(somatic_conductance)
from g in somatic_conductance:
	calculated_function = somatic_conductance*exp(-somatic_conductance/100*g) #from author et al., 2016
	output.append(calculated_function)
	print '%s stored in output, using %s value'&(calculated_function,g)
```

## Learn json and store your parameters
A [friend](https://twitter.com/redeyesdemon) solved me a great problem that I had.  For a specific project, I had a lot of parameters to do my simulation.  The problem was that I could not find a solution for storing them and compare several models with different set of parameters.
He suggested me to make a json array and save it into a textfile.
In Python you could do this easily with the json package

```python
import json
#Parameters
    grid={'Initial speed':stimuliSpeed[0], 'Final Speed':stimuliSpeed[-1],
          'Initial conductance':gmax[0],'Final conductance':gmax[-1]}

    with open(simPath+'aCsyn_simulation_parameters_%s.json'%net5module_aCsyn.to$
        json.dump(grid, fp)
```
Now I implement this, because, while discussing your results, it is always usefull to have the set of parameters you use to build your model.

# Final Words
This tips do work for me, however, I suggest you to find your own workflow and coding techniques. Feel free to comment them!

# Song of the day: The Algorithm - Floating Point
[![The Algorithm - Floating Point](https://i.ytimg.com/vi/fhGJOys5gcc/maxresdefault.jpg)](https://www.youtube.com/watch?v=fhGJOys5gcc)



# References
1. Rall W. (1977) Core conductor theory and cable properties of neurons. In Kandel, E.R., J.M. Brookhardt, and V.M. Mountcastle eds. Handbook of physiology, cellular biology of neurons. Bethesda, MD: American Physiological Society; 39-97.
2. Hines, M. L., Davison, A. P., & Muller, E. (2009). NEURON and Python. Frontiers in Neuroinformatics, 3, 1. http://doi.org/10.3389/neuro.11.001.2009
3. Schnell, S. (2015). Ten Simple Rules for a Computational Biologist’s Laboratory Notebook. PLoS Computational Biology, 11(9), e1004385.



