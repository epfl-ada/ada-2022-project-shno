
# Hollywood's social structure

### Abstract

Is Hollywood’s social network composition unique or do other movie industries follow suit ? Hollywood is the most famous movie production industry in the world. It has a reputation of being a high-class, exclusive and hard to get in environment. Having a good network is undoubtedly very important to make it there. Clubs, communities and social dynamics between actors, directors, and producers take shape within this environment. \
What are the specifities of the composition and shape of the Hollywood social network ? Are they unique and part of its “identity” or is it a social network that all movie industries follow / or are bound to (Bollywood, Chinawood being other major movie industries). \
Through a “co-stardom graph” showing actors who played in the same movies, we will look at its evolution over time and compute different graph metrics (centrality,…), run cluster analysis and compare these metrics across different industries.

### Research Questions
- Is an actor's success determined by his connections ?
- What are the main communities inside Hollywood's network ?
- What are the most powerful and influential actors and directors ?
- Is there a difference between men and women in their influence on writing, directing and acting ?
- Is Hollywood's environment representative of the whole cinematographic industry ?

### Datasets

- Additional Dataset 1 : IMDb Datasets

Dataset contain the following files : titles.akas.tsv, titles.basic.tsv, title.crew.tsv, titles.episode.tsv, titles.principles.tsv, name.basics.tsv.
In the case of our study, we want to extract from it the list of movies with the actors/directors/writers that played in/directed/wrote, and the list of actors/directors/writers with the movies they played in/directed/wrote. 
For that we would process the title.akas/basics/crew/principles and name.basics

- Additional Dataset 2 : Movielens Full Dataset

After analysis of this dataset, we observed a significant overlap with the IMDb dataset, that we judged to be more complete and thus decided against using it.

### Methods

#### Step 0: Data scraping and pre-processing

##### 0.A : Outlier and missing value correction using IMDb datset values

We observed in our analysis that some values in the CMU dataset are missing, erroneous or in the wrong unit. In this case, we should use the IMDb dataset values to fill them for ovelapping movies.

##### 0.B : IMDb datset merging

We merge the IMDb dataset and the CMU dataset to extend the data

#### Step 1: Data Transformation : Build co-stardom graphs : actor-to-actor and movie-to-movie

The way we are going to explore the data of this CMU repo augmented by some potentially other datasets, is first of all through building a co-stardom network.
A costardom network is essentially a collaboration graph of film actors. The nodes represent movie star actors and two nodes are linked if the two-stars have starred in the same movie.
We can add a weight to the link, the weight being the number of times two actors have performed together. This would be our first actor-to-actor graph.

We can similarly construct a movie-to-movie graph which could reveal interesting insights.
In such a graph, a node would be a movie and two nodes would be linked if they share some of the cast members. If we deem it necessary, we can
consider only the "important" people of the cast.

#### Step 2: Filter out the graph nodes below a certain degree and the graph edges below a certain weight

#### Step 3: Network analysis

##### 3.A : **Community detection**  
A network is said to have community structure if the nodes of the network can be easily grouped into sets of nodes such that each set of nodes is densely connected internally. A known algorithm to give us insights on this problem is the Girvan-Newman algorithm : it detects communities by progressively removing edges from the original network. The connected components of the remaining network are the communities    

##### 3.B: **Clustering based on actor attributes**  
The idea would be to use an algorithm that regroup actors with similar features we extracted and engineered in the preprocessing part.
The fact that actors have categorical features prevent us from using a K-means clustering as the Euclidean distance is not well
defined for categorical features. For this issue, we might use K-modes that mixes the Hamming distance for categorical data and Euclidean distance

#### Step 4: Build an ego network graph between actors to describe and index the variation among actors in the way they are embedded in « local » social structures.

#### Step 5: Compute and visualize network metrics to highlight the power and influence of individuals

- Explore the existence of more than one type of relationship between two actors through computing multiplexity.
- Explore the tendency for actors to have more ties with other actors that are close geographically with propinquity.
- Determine positional advantages/disadvantages of individuals from structural holes. This will help to think abut how and why the ways that an actor is connected affect its constraints and opportunities.
- Understand which actors/directors/writers are the most important in the flow of the network, by computing betweenness/closeness/degree centrality.
- Compute to which degree actors/directors/writers tend to cluster together, computing the clustering coefficient.

#### Step 6: Build website and redact datastory

### Proposed Timeline from 03 Dec until 23 Dec 2022

#### 03 Dec - 09 Dec

Step 1: Build co-stardom graphs : actor-to-actor and movie-to-movie \
Step 2: Filter out the graph nodes below a certain degree and the graph edges below a certain weight

#### 10 Dec - 16 Dec

Step 3: Network analysis \
Step 4: Build an ego network graph between actors to describe and index the variation among actors in the way they are embedded in « local » social structures.

#### 17 Dec - 23 Dec

Step 5: Compute and visualize network metrics to highlight the power and influence of individuals \
Step 6: Build website and redact datastory

### Team Organization
| Name | GitHub | Contribution |
| :--- | :--- | :--- |
|Omar El Malki   | [omarelmalki](https://github.com/omarelmalki) | Step1:Actor-to-actor graph, Step2:Filtering, Step6:Datastory |
|Hamza Hassoune | [hamzahass](https://github.com/hamzahass) | Step1:Movie-to-movie graph, Step5:Metrics, Step6:Datastory |
|Saged Bounekhel | [sonusiety](https://github.com/sonusiety) | Step4:Ego Network, Step6:Website, Step6:Datastory |
|Ouerghemi Naël  | [ghemDD](https://github.com/ghemDD) | Step3:Network Analysis, Step6:Datastory |

