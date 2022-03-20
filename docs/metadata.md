# Metadata
Metadata is a instance of one data model and used to describe the related data. Data Model is the central method of organization of all data artifacts and is composed of interconnected entities (similar with Directed Acyclic Graph, DAG).

## Data Model定义

Nodes, Properties, and Edges

- Each entity (also named as node) has a set of properties.
- Properties are key-value pairs associated with an entity.
- Properties cannot be nested, which means that the value must be numerical, boolean, or a string, and cannot be another key-value set. Properties can be either required or optional.
- Edges define relationships between entities, and the multiplicity of those relationships (e.g. one-to-one, one-to-many, many-to-many).
- Category, also named as super entity, is used to organize a set of related entities. such as `Clinical`, `Biospecimen`, `Data File`, `Administrative`.

```
# Entity Category & Entity & Properties
|- [Entity Category] Administrative
|        |- [Entity] Project
|        |- [Entity] Center
|        |- [Entity] Program
|        |- [Entity] Source Site
|- [Entity Category] Donor
|        |- [Entity] Donor
|- [Entity Category] Clinical
|        |- [Entity] Generic
|        |- [Entity] Diagnosis
|        |- [Entity] Molecular Test
|        |- [Entity] Pathology
|        |- [Entity] Image
|        |- [Entity] Treatment
|        |- [Entity] Demographic
|        |- [Entity] Exposure
|        |- [Entity] Family History
|        |- [Entity] Follow-Up
|- [Entity Category] Biospecimen
|        |- [Entity] Slide
|        |- [Entity] Tissue
|        |- [Entity] Cell
|        |- [Entity] Sample (DNA/RNA/Small RNA/Protein/Metabolite/Peptides/...etc.)
|        |- [Entity] Aliquot
|        |- [Entity] Library
|- [Entity Category] Data File
|        |- [Entity] Slide Image
|        |- [Entity] Pathology Report
|        |- [Entity] Sequencing Data (Level 1)
|        |- [Entity] Methylation Array
|        |- [Entity] Analysis Metadata File
|        |- [Entity] Experiment Metadata File
|        |- [Entity] ...
|        |- [Entity] Profiling Data (Level 3)
|- [Entity Category] Workflow(also named as Pipeline/App)
|        |- [Entity] Workflow
```

```
# Edges / Links / Relationships
# The relationship must be direct, so the selection of a group entities, two entities, is crucial for track the related relationship between the entities.
# 建立关系的实体间必须存在直接关系，否则将导致关系错乱
|- [Edge] Program-Project
|- [Edge] Project-Donor
|- [Edge] Source Site-Donor
|- [Edge] Source Site-Sample
|- [Edge] ...
```

## Data Types and File Formats