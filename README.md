<div align="center" style="font-family: charter;">
  <h1>Decoding Urban Industrial Complexity:<br>Enhancing Knowledge-Driven Insights via IndustryScopeGPT</h1>

<p align="center">
    <a href="https://dl.acm.org/doi/abs/10.1145/3664647.3681705">
        <img alt="Web" src="https://img.shields.io/badge/Web-ACMMM-orange"></a>
    <a href="https://arxiv.org/abs/xxx">
        <img alt="Paper" src="https://img.shields.io/badge/Paper-Arxiv-green"></a>
    <a href="https://www.youtube.com/watch?v=5X-Il5Ndkao&t=1661s">
        <img alt="YouTube" src="https://img.shields.io/badge/YouTube-Subscribe-red?logo=youtube"></a>        
         
</p>


<img src="assets/figure1.png" width="93%"/>

</div>


----

## ✏️ Hightlights
- **Top Open-Source Urban Knowledge Graph Dataset**
  
IndustryScopeKG is the first and largest open-source, multimodal large-scale knowledge graph dataset. It integrates geospatial data such as street view images, points of interest, and crowd activities, along with socio-economic data including company information, real estate prices, and population statistics. The dataset contains 2,232,037 entities and 51,684,939 triples.
<p align="center">
<img src="assets/figure4.jpg" width="95%"/>
</p>

- **First Application of LLM in Industrial Park Planning and Operations**

The IndustryScopeGPT framework was developed to enhance the planning, action, and reasoning capabilities of large language models (LLMs) in industrial park planning and operations. This framework represents the first integration of large language models with spatial computing and dynamic reasoning on graph databases that incorporate external geospatial data, marking the first exploration of such applications in industrial park planning and operations.
<p align="center">
<img src="assets/figure5.jpg" width="91.5%"/>
</p>

## 📰 Updates
- **`2024/10/28`**  We’re thrilled to share that our work, [Decoding Urban Industrial Complexity: Enhancing Knowledge-Driven Insights via IndustryScopeGPT](https://dl.acm.org/doi/abs/10.1145/3664647.3681705), has been published by the ACM MM 2024 conference. We are profoundly grateful for the contributions of all the contributors to this work！
- **`2024/07/23`**  We are honored to share and present our work at the [MIT Media Lab-City Science Lab Community Meeting](https://www.youtube.com/watch?v=5X-Il5Ndkao&t=1661s). For more details, please visit the City Science Lab website: [Design and Data-Driven Hybrid Community Building](https://www.media.mit.edu/events/design-and-data-driven-hybrid-community-building-city-science-lab-shanghai/).

## 🔗 IndustryscopeKG Data

The **raw dataset** is available for download from:

- **[Kaggle](your-kaggle-link)**
- **[Google Drive](your-google-drive-link)**

For seamless integration, we recommend using **Neo4j** to analyze and interact with the knowledge graph.

---

## 🛠️ Getting Started with Neo4j

We provide a **Neo4j Docker Image** to simplify the process of setting up and working with the IndustryScopeKG dataset.

### Step 1: Install Docker

Ensure you have Docker installed on your system. For installation instructions, visit [Docker's official website](https://www.docker.com/).

### Step 2: Start Neo4j with IndustryScopeKG

Run the following command to start a Neo4j container with the dataset preloaded:

```bash
docker run -d \
  --name industryscope-neo4j \
  -p 7474:7474 -p 7687:7687 \
  -e NEO4J_AUTH=neo4j/password \
  -v /path/to/your/induscopekg-data:/data \
  neo4j:latest
```

Replace ```/path/to/your/induscopekg-data``` with the path to the directory containing the dataset.

**Default credentials**:
- **Username**: `neo4j`
- **Password**: `password` (you can customize this in the `NEO4J_AUTH` variable).

---

### Step 3: Access Neo4j

1. Open your browser and navigate to: [http://localhost:7474](http://localhost:7474).
2. Login with the credentials you set (`neo4j/password`).

---

### Step 4: Import IndustryScopeKG into Neo4j (If needed)

Run the following Cypher commands in the Neo4j browser to load the dataset:

```cypher
LOAD CSV WITH HEADERS FROM 'file:///path/to/your/induscopekg-data.csv' AS row
CREATE (e:Entity {id: row.entity_id, name: row.entity_name, type: row.entity_type})
```

Replace the file path (```file:///path/to/your/induscopekg-data.csv```) with the actual location of your dataset CSV file.

### 🌟 Usage Notes
The dataset can be used standalone or integrated into your projects. It works particularly well with graph-based reasoning frameworks.
For LLM-based planning and operations, the dataset complements the IndustryScopeGPT framework, providing a dynamic and insightful environment for urban and industrial research.

#### Example Queries
Here’s an example Cypher query to find all connections for a specific entity:

```
MATCH (e:Entity)-[r]->(related:Entity)
WHERE e.name = 'Industrial Park A'
RETURN e, r, related
```


#### Annotated data format

The Annotation file VIVA_annotation.json contains a list of json objects, with each json representing a sample. For each key:

- image_url: The original url of the image, representing the situation;
- action_list: The action candidates in Level-1 Task;
- answer: The correct answer candidate;
- values: The human values in the Level-2 value inference task;
- reason: The reason in the level-2 reason generation task.


---

## 🧪 Experiments
### Model Prediction
Please check the scripts and instructions under the folder ```scripts```

### Evaluation
- [ ] To do


## 🤗 Citation 

If our work sparks your interest or helps your research, a little cite would mean a lot!

```bibtex
@inproceedings{10.1145/3664647.3681705,
author = {Wang, Siqi and Liang, Chao and Gao, Yunfan and Liu, Yang and Li, Jing and Wang, Haofen},
title = {Decoding Urban Industrial Complexity: Enhancing Knowledge-Driven Insights via IndustryScopeGPT},
year = {2024},
isbn = {9798400706868},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3664647.3681705},
doi = {10.1145/3664647.3681705},
abstract = {Industrial parks are critical to urban economic growth. Yet, their development often encounters challenges stemming from imbalances between industrial requirements and urban services, underscoring the need for strategic planning and operations. This paper introduces IndustryScopeKG, a pioneering large-scale multi-modal, multi-level industrial park knowledge graph, which integrates diverse urban data including street views, corporate, socio-economic, and geospatial information, capturing the complex relationships and semantics within industrial parks. Alongside this, we present the IndustryScopeGPT framework, which leverages Large Language Models (LLMs) with Monte Carlo Tree Search to enhance tool-augmented reasoning and decision-making in Industrial Park Planning and Operation (IPPO). Our work significantly improves site recommendation and functional planning, demonstrating the potential of combining LLMs with structured datasets to advance industrial park management. This approach sets a new benchmark for intelligent IPPO research and lays a robust foundation for advancing urban industrial development. The dataset and related code are available at https://github.com/Tongji-KGLLM/IndustryScope.},
booktitle = {Proceedings of the 32nd ACM International Conference on Multimedia},
pages = {4757–4765},
numpages = {9},
keywords = {industrial park planning and operation, large language model agent, urban design and planning, urban knowledge graph},
location = {Melbourne VIC, Australia},
series = {MM '24}
}


```




