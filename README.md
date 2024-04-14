# Genetic Algorithm for Inner Product Optimization Using a DNA Data Structure
-------
*By: Brett Balquist*
### This project was made for HackKu24 and was inspired by a talk given by NYU distinguished professor of mathematics Percy Deift about iterative algorithms and random data.
-------

# Key Components
-------
## DNA Data structure
-------
* As part of this project I created my own data structure which resembled DNA.
* The DNA class had inner classes of a right_backbone and left_backbone which consisted of quadruply linked sentinels which resembled the sugar phosphate backbone
* It also had AT and CG classes which consisted of quadruply linked nodes which resembled the Adenine and Thymine, and Cytosine and Guanine bases respectively.
* This made traversing, crossover, and mutation quite easy to code as a result of this data strucutre.

## Genetic Algorithm
-------
### Methods
---

* ### Crossover
    -------------
    * This function crosses two parents DNA and produces two children. This function occurs in nature during meiosis when chromosomes are lined up, which in this case are the $\mathbf{AT}$ and $\mathbf{CG}$ vectors respectively.
* ### Intialize Population
    -----------
    * This creates a population with a predetermined population size populated with DNA strands.
* ### Selection
    -----------
    * Selection takes the top 75% most fit of the population and creates a new population with them. This ensures that each next population is generally more fit than the previous generation.
* ### Mutation
    -----------
    * Mutation uses a standard mutation rate of 5% or a random rate if smaller against random values to determine the percentage of the population that is mutated. If random.random() generates a number less than mutation_rate, the condition evaluates to True, indicating that a mutation should occur. If random.random() generates a number greater than or equal to mutation_rate, the condition evaluates to False, indicating that no mutation should occur. The mutation then performs a multiplication of the curent entry against a value between 0.1 and 1.0 which will keep it inclusive within the sin domain.
* ### Evaluating Fitness
    -----------
    * Evaluating fitness stores the inner product value with the associated strand

## What is fitness?
-----------
Fitness is the function that you want to optuimize for. In stochastic algorithms this can mean a number of thngs including solving a maze, maximizing your ability to perform
a task based on certain parameters. In this scenario we are optimizing for inner product which in this scenario is the angle between two vectors,  $\mathbf{AT}$  and  $\mathbf{CG}$ respectively.
This means the lower the angle the more fit the gene is and the more likely it is to move onto the next generation.

## What is Inner Product?
-----------
## Inner Product and Angle Calculation
---------

Generall, the inner product is any calculation on a vector space s.t. $f: \mathbb{R}^n \to \mathbb{R}$

The inner product between two vectors $\mathbf{x}$ and $\mathbf{y}$ in a vector space can be used to calculate the angle $\theta$ between them using the formula:

In this project $\mathbf{x}$ and $\mathbf{y}$ signify the $\mathbf{AT}$ and $\mathbf{CG}$ sides respectively. These are the vectors that correspond to each vertical column of information in the DNA.

$$
\theta = \arccos\left( \frac{\mathbf{x} \cdot \mathbf{y}}{\|\mathbf{x}\| \|\mathbf{y}\|} \right)
$$

Where:
- $\mathbf{x} \cdot \mathbf{y}$ denotes the dot product (or inner product) between vectors $\mathbf{x}$ and $\mathbf{y}$.
- $\|\mathbf{x}\|$ and $\|\mathbf{y}\|$ represent the norms (or magnitudes) of vectors $\mathbf{x}$ and $\mathbf{y}$, respectively.

The dot product $\mathbf{x} \cdot \mathbf{y}$ is calculated as:

$$
\mathbf{x} \cdot \mathbf{y} = \sum_{i=1}^{n} x_i y_i
$$

Where $x_i$ and $y_i$ are the components of vectors $\mathbf{x}$ and $\mathbf{y}$, respectively.

The norms $\|\mathbf{x}\|$ and $\|\mathbf{y}\|$ are calculated as:

$$
\|\mathbf{x}\| = \sqrt{\sum_{i=1}^{n} x_i^2}
$$
$$
\|\mathbf{y}\| = \sqrt{\sum_{i=1}^{n} y_i^2}
$$

This was implemented in this project by using angles closer to 0 to signify a relatedness in vectors that was positive.

## Ths Complete Genetic Algorithm
----------
This section utilizes all the previous methods and the DNA data structure to construct a genetic algorithm that uses generations to tend towards a more fit population.

The length of a DNA strand, the size of the population, the number of generations, and the mutation rate are all passed as parameters.
From here an intial population is generated and then and then from that the fitness of each strand is evaluated and parents are generated.
Next, the parents are bread to produce two children and the children are possibly mutated and then appended to the new population.
From this new population we repreat this until the end of the selected number of generations.

Over this time the population grows more fit and the most fit is then selected from the final population completing the genetic algorithm.

## Applications
------
My understanding of this topic has much room to improve and so could the data structure and algorithm that I wrote. This could be used in a number of ways including
finding approximates for eigenvalues, maximizing data based on certain key metrics while retaining less information, or optimizing other vector metrics.

