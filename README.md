<h1 align="center">2024 Paris Olympic Network Analysis</h1>

#### Jangmin Song  
#### Professor Carrie Diaz Eaton  
#### DCS375 Network Analysis  
#### April 18th 2025  

## 1. Introduction  
200 words

&nbsp;&nbsp;&nbsp;&nbsp;The Summer Olympic Games is the largest international sport event, which is held every four years. There are more than 10,000 athletes from around the world. These athletes train for years to represent their nations on a global stage and compete for excellence in their respective disciplines. In 2024, the Olympics game was held in Paris three years after 2020 Tokyo Olympics that happened in 2021 due to COVID-19 pandemic. There is a dataset in [kaggle.com](https://www.kaggle.com/) called [Paris 2024 Olympic Summer Games](https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games?select=medallists.csv), which contains all the data of Athletes,  They also offer a rich dataset for exploring global athletic participation, collaboration, and structural patterns across countries and disciplines. This project uses network analysis methods to investigate athlete and country relationships based on shared events, medal achievements, and cross-discipline participation. 

&nbsp;&nbsp;&nbsp;&nbsp;The central questions of this project are the follwings:
- How are athletes socially connected through shared Olympic disciplines and events?
- Which countries act as central hubs in the global sports network?
- Do certain disciplines foster more interconnection between athletes or countries?

&nbsp;&nbsp;&nbsp;&nbsp;I used the language `R` for this project mainly using `bipartite`, `igraph`, and `ggplot2` packages. By visualizing and analyzing these relationships through bipartite graphs, one-mode projections, and centrality metrics, we will find the structural dynamics within the Olympic system that go beyond surface-level competition results.

## 2. Background and Significance
100–150 words

&nbsp;&nbsp;&nbsp;&nbsp;The Olympic Games are not only a platform for international competition but also a representation of global athletic development and cultural investment in sports. Countries have different numbers of how many athletes they send and what disciplines they participate in. I hypothesized that we can potentially find some deeper patterns about the features of athletic ministries in each country and accessibility.

&nbsp;&nbsp;&nbsp;&nbsp;Network analysis can help us to find out these questions. By building the networks, and visualizing the relationships between athletes, countries, and disciplines as networks, we can explore who are connected, how central certain nodes are, and where clusters of similarity or collaboration might happen. Concepts like bipartite graphs, degree centrality, and community detection, which was learned through **DCS 375 Network Analysis** allow us to map these interactions and quantify research in ways traditional medal counts do not. This project applies those techniques to the 2024 Paris Olympics to better understand the collaborative structure of global athletics.


## 3. Data and Methodology
150–200 words

&nbsp;&nbsp;&nbsp;&nbsp;Now let’s talk about data. As mentioned in introduction, datasets are from [kaggle.com](https://www.kaggle.com/) and are called `athletes.csv` (all participants) and `medallists.csv` (all medal winners) from [Paris 2024 Olympic Summer Games](https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games?select=medallists.csv). `athletes.csv` contains variables such as `name`, `gender`, `country`, `disciplines`, `events`, `birth date`, `occupation`, `education`, etc.  `medallists.csv` has information about `medal_date`, `medal_type`, `name`, `country`, etc. 

&nbsp;&nbsp;&nbsp;&nbsp;In the data cleaning phase, I removed special characters such as brackets, quotation marks from `disciplines` and `events`. Also, I created a new dataset that contains only the variables that I plan to use. 



## 4. Analysis & Visualizations 
250-300 words

## 5. Interpretation & Takeaways
100-150 words

## 6. Conclusion
100 words
