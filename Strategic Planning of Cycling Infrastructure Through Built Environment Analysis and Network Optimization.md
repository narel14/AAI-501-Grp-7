**Strategic Planning of Cycling Infrastructure Through Built Environment Analysis and Network Optimization**  
Group 7:   Marston Ward.   
Nelson Arellano.

The project addresses the challenge of equity in micromobility, aiming to transform a city into a safer and more accessible environment for cyclists, a truly bike-friendly city. The system will begin by diagnosing the current cycling infrastructure to identify “bike lane deserts”: areas with high potential for bicycle use (due to residential, commercial, or recreational density) but lacking safe and connected cycling routes. Using unsupervised clustering, the system will objectively map these underserved areas.

Rather than merely drawing a path, the system will act as an “infrastructure planner,” proposing the most strategic new bike lanes and connections. The goal of these proposals will be to maximize connectivity impact, efficiently linking isolated zones with the existing bike lane network and key points of interest.

*Urban Feature Extraction and Characterization Module*  
This initial module is responsible for collecting and processing data at the neighborhood or grid-cell level. It will use OSMnx to build a detailed profile of each urban area, focusing on quantifying existing infrastructure and relevant urban characteristics.

*Underserved Area Identification Module (Clustering)*  
This module applies machine learning to identify “bike lane deserts.” It analyzes the profiles generated in the previous step to cluster zones with similar attributes and detect areas with a mismatch between high cycling potential and low infrastructure availability.

Algorithms to Explore:

K-Means: Used to segment the city into general typologies (e.g., "well-served commercial," "residential with bike lanes," "underserved residential"). The cluster representing underserved areas will be the target for the next stage.

DBSCAN: Investigated for its ability to detect anomalies and form clusters with complex shapes. It is well-suited for identifying disconnected “islands” of cells lacking infrastructure, treating them as cohesive targets for intervention.

*Infrastructure Proposal Module (Network Optimization)*  
This final module designs solutions to make the city more bike-friendly. Instead of proposing just one route, the goal is to identify the most impactful new bike lanes.

Algorithms to Explore:

Shortest Path Analysis (Dijkstra’s Algorithm): Implemented using OSMnx, this algorithm will be used to find the most direct candidate route from each underserved zone to the nearest point in the existing bike network. These are the most natural candidates for new bike lane extensions.

Betweenness Centrality Analysis: A widely-used measure in the literature to assess the importance of nodes or edges in network flows. It will be used predictively—by simulating the addition of a candidate route to the network and recalculating centrality scores to evaluate improvements in connectivity and flow. Routes that produce the largest centrality gains will be prioritized.

Custom Impact Scoring Algorithm: A scoring system will be developed to rank candidate bike lane proposals. Each score will consider:

* The amount of residential population connected in underserved areas  
* The number of points of interest (POIs) newly made accessible  
* Construction feasibility (favoring wide or low-speed streets)

**Related Course Topics:**

*Heuristic Search*  
This includes A\* and Dijkstra algorithms, both of which are fundamental for optimizing routes over road network graphs. A\* is particularly relevant when a heuristic is incorporated, such as Euclidean or Manhattan distance.

*Classification*  
This can be applied to predict, for example, whether a street is “congested” or not, or to classify areas as urban or rural based on features such as population density, number of connections, etc.

*Clustering*  
This is central to the module for identifying underserved areas (“bike lane deserts” or “transport deserts”). Algorithms like K-Means or DBSCAN can group areas with similar characteristics.

*Regression*  
It can be used to predict continuous variables such as travel time, traffic level, or cycling density based on various attributes of the network.

**Examples of Expected Behaviors of the System or Problems Addressed**

The system should be able to identify underserved urban zones (e.g., neighborhoods lacking proper bike lane access or bus routes) through unsupervised clustering algorithms such as K-Means or DBSCAN, based on features extracted from OpenStreetMap data via OSMnx.

Upon identifying those zones, the system is expected to propose efficient new infrastructure connections, such as:

* The shortest path between the underserved area and the nearest point on the existing bike lane or bus network (using Dijkstra or A\*).  
* Routes that maximize network connectivity, by simulating how proposed new links improve the betweenness centrality of the transportation graph.

The system should support classification tasks such as determining whether a given street is likely to be congested or suitable for cycling, based on road attributes (speed limit, lane width, street type), using models like Random Forests.

**The Issues We Expect to Focus On**

* Data Quality and Completeness: OpenStreetMap data can vary in detail and accuracy across cities. Ensuring consistent, usable features is critical for effective modeling.

* Scalability of Graph-Based Algorithms: Algorithms like Dijkstra and A\* require loading the entire road network into memory, which may be challenging for large cities or national-scale projects.

* Clustering Interpretability: Selecting appropriate features and the number of clusters (for K-Means) or density thresholds (for DBSCAN) can greatly impact the reliability of the identified underserved zones

* A complex challenge is moving from diagnosis to proposing realistic solutions. The problem is not just to find the shortest path, but to define what makes a new bike lane "good." Our focus will be on developing a multi-criteria optimization model that balances often conflicting objectives:

* Maximize coverage: How many people will benefit?  
* Improve connectivity: How well does the new route integrate with the existing network?  
* Ensure feasibility: Is it realistically possible to build a bike lane on that specific street?

  The main emphasis will be on incorporating real-world constraints into the proposal module. Instead of simply suggesting the geometrically shortest path, the system will need to consider factors such as speed limits, street types, and road width to ensure that the proposed solutions are not only optimal in a model but also practical and safe for real-world implementation.


**Core Papers and Resources**

* Boeing, G. (2025). Modeling and Analyzing Urban Networks and Amenities With OSMnx. Geographical Analysis. [https://doi.org/10.1111/gean.70009](https://doi.org/10.1111/gean.70009)  
  * Updated guide on the capabilities of OSMnx. We will use it for extracting data on bike lanes and points of interest, calculating network metrics such as centrality, and visualizing results.  
* Senturk, I. F., & Kebe, G. Y. (2019). A novel shortest path routing algorithm for wireless data collection in transportation networks. En 2019 4th International Conference on Computer Science and Engineering (UBMK) (pp. 280-285). IEEE. [https://doi.org/10.1109/UBMK.2019.8907167](https://doi.org/10.1109/UBMK.2019.8907167)  
  * This article offers both a conceptual and practical solution for connecting our "underserved areas." The paper addresses the "Traveling Salesman Problem with Neighborhoods" (TSPN), which seeks the shortest route not to exact points, but to regions. The main challenge identified is that a zone has infinitely many potential entry points, making a brute-force analysis of all possibilities computationally infeasible. To solve this, the authors propose a simple and effective heuristic: first, calculate the shortest path to the center of the area, and then use the point where that path intersects the boundary of the region as the optimal connection point. We can directly adapt this methodology for our project by using it to efficiently determine the most logical route for a new bike lane connecting a “bike desert” to the existing primary cycling network.


  
**List of contributions**

| Task | Nelson | Marston |
| ----- | :---: | :---: |
| Project proposal | ✔️  | ✔️  |
| 1\. Load OSMnx data |  | ✔️ |
| 2\. Exploratory Data Analysis (EDA) | ✔️ |  |
| 3\. K-Means Clustering Algorithm |  | ✔️ |
| 4\. DBSCAN Clustering Algorithm | ✔️ |  |
| 5\. Dijkstra’s Algorithm |  | ✔️ |
| 6\. Betweenness Centrality Analysis | ✔️ |  |
| 7\. Custom Impact Scoring Function (Design \+ Eval) | ✔️  | ✔️ |

Both of us are eager to learn how to implement pathfinding algorithms and machine learning tools, we are equally committed to supporting the majority of the work areas. Therefore, responsibility is shared across each task, even if individual leadership is designated in specific components.

