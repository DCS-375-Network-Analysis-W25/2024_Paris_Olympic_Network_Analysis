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


## 3. Data 
150–200 words

&nbsp;&nbsp;&nbsp;&nbsp;Now let’s talk about data. As mentioned in introduction, datasets are from [kaggle.com](https://www.kaggle.com/) and are called `athletes.csv` (all participants) and `medallists.csv` (all medal winners) from [Paris 2024 Olympic Summer Games](https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games?select=medallists.csv). `athletes.csv` contains variables such as `name`, `gender`, `country`, `disciplines`, `events`, `birth date`, `occupation`, `education`, etc.  `medallists.csv` has information about `medal_date`, `medal_type`, `name`, `country`, etc. In the data cleaning phase, I removed special characters such as brackets, quotation marks from `disciplines` and `events` . Also, I created a new dataset that contains only the variables that I plan to use. 

&nbsp;&nbsp;&nbsp;&nbsp; After the data cleaning, I applied several network analysis skills learned in the DCS375 course. First, I created several bipartite graphs, countries connected to disciplines, athletes connected to disciplines or events, and athletes connected to medal types (Dormann, 2025). These bipartite networks were projected into one-mode graphs. country–country (shared disciplines), athlete–athlete (shared medals), and event–event (shared athletes). Graph objects were constructed with `igraph::graph_from_adjacency_matrix()` or `graph_from_edgelist()`, and layouts were generated using `layout_with_fr()` for force-directed visualization. Edge weights reflect shared attributes (e.g., number of common disciplines or medal types), and vertex sizes are scaled based on node strength. I also computed centrality measures (degree, strength, eigenvector, betweenness) to analyze which countries, athletes, or events played the most central roles within their respective networks.

## 4. Methodology, Visualizations, and Analysis
250-300 words

After the data cleaning, I applied several network analysis skills learned in the DCS375 course. I have created a bipartite network, unimodal visualizations, projected unipartite network, 1-mode network, and barplot. I have also used statistical analysis for the 1-mode network. Here are methodologies for each visualization.  

1. **Athlete–Country Bipartite Network**  
Using `frame2webs()` from the `bipartite` package, I constructed a bipartite graph connecting athletes to their respective countries and disciplines. This two-mode network highlights participation patterns across nations. The `plotweb()` function was used for visualization, with label rotation, node scaling, and color customization to improve clarity.

![Histogram of "horse"](num_athletes_vs_top_country.png)

However I have noticed that we cannot able to see some nodes because they are too small. To reduce noise, I grouped countries with 15 or fewer athletes into a collective “Other Countries” node. 

![Histogram of "horse"](num_athletes_vs_top_country.png)

Observations: We observed that There are many participants in Athletics and Swimmings from many countries. We also see that there are many participants from the countries like US, France, China, Australia, Japan, and Spain. I have also found that there are many countries that have only sent 15 or less athletes because "Other Countries" node is thick. 

3. **Unimodal Projection of the Bottom 20 Atheletes Participating Countries**  
I created a projection of the country–discipline bipartite matrix into a country–country graph using matrix multiplication. Two countries are connected if their athletes competed in at least one shared discipline. I filtered for countries with more than 10 disciplines to focus on active NOCs and scaled edge widths based on the number of shared disciplines. Central countries were highlighted in red to represent top participation breadth.

4. **Athlete–Medal Type Network and Clustering**  
By creating a bipartite graph between athlete names and medal types, I projected this into a 1-mode network connecting athletes who won the same type of medal. Using `igraph::cluster_louvain()`, I performed community detection to identify clusters of athletes who frequently appear in similar medal categories. This helped uncover discipline-based grouping and medal clustering trends.

5. **Event Collaboration in Athletics**  
Focusing on the Athletics discipline, I built an event–event network by projecting a bipartite graph of athletes and events. After splitting multiple events per athlete using `separate_rows()`, I created a network where events are connected if an athlete competed in both. Centrality metrics such as degree, strength, and eigenvector centrality were calculated to find the most structurally important events within the Athletics network.

6. **Barplots of Athlete Representation by Country**  
I used `ggplot2` to create horizontal bar plots showing the number of athletes from each country. One plot showed the top 20 countries by participation, while another showed the bottom 20. These visualizations provided context for understanding the structure of the collaboration networks and guided decisions about which countries to highlight or combine in later graphs.

Each visualization was paired with interpretation and statistical measures to help reveal broader structural dynamics at the athlete, event, and country levels in the Olympic data.

## 5. Interpretation & Takeaways
100-150 words

## 6. Conclusion
100 words
