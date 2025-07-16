# Strategic Planning of Cycling Infrastructure Through Built Environment Analysis and Network Optimization

**Course:** AAI 501 Final Project  
**Team:** Group 7 (Marston Ward, Nelson Arellano)

## 1. Project Overview

This project develops a data-driven system to aid city planners in the strategic development of bike paths. Our approach focuses on identifying and addressing "bike lane deserts"—urban areas with high potential for bicycle use but lacking safe, connected cycling routes. By analyzing the built environment and applying network optimization algorithms, the system proposes high-impact infrastructure additions to enhance urban micro-mobility.

## 2. Problem Statement

Cycling adoption varies dramatically across cities and is heavily influenced by the quality of infrastructure. While cities like Copenhagen have achieved over 50% bicycle commuting, adoption in the United States remains in the low single digits. This project addresses the challenge of intelligently expanding cycling networks to make biking a safer and more viable transportation option.

## 3. Project Objectives

The system is designed to function as an "infrastructure planner" that will:

1. **Diagnose** current cycling infrastructure to identify underserved areas.
2. **Analyze** the urban environment using objective, data-driven clustering methods.
3. **Propose** strategic new bike lanes that maximize connectivity and impact.
4. **Optimize** connections between isolated residential zones and the existing bike network.

## 4. Technical Approach

Our solution is built on three core modules that process geospatial data, identify target areas, and propose optimized routes.

### Module 1: Urban Feature Extraction

- **Technology:** `OSMnx`
- **Purpose:** Collects and processes neighborhood-level data to quantify existing infrastructure density, extract relevant urban characteristics (e.g., points of interest, street types), and build detailed profiles of the urban area.

### Module 2: Underdeveloped Area Identification

- **Algorithms:** K-Means Clustering, DBSCAN
- **Purpose:** Applies unsupervised machine learning to the urban profiles to identify "bike lane deserts" by detecting mismatches between cycling potential and infrastructure availability.

### Module 3: Infrastructure Proposal

- **Algorithms:** Dijkstra's Shortest Path, Betweenness Centrality Analysis
- **Purpose:** Designs strategic solutions by finding the most efficient routes to connect underserved zones to the existing bike network. Proposals are ranked using a custom impact score based on population served, new POIs connected, and construction feasibility.

## 5. How to Run

1. **Clone the repository:**

    ```bash
        git clone [URL_to_your_repo]
        cd [repository_folder]
    ```

2. **Install dependencies:**

    ```bash
        pip install -r requirements.txt
    ```

3. **Run the main analysis script:**

    ```bash
        python main.py
    ```