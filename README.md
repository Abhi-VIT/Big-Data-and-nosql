# Big Data & NoSQL — Lab Report (README)

**Repository / Report:** `BigData_Report.docx`

---

## 📘 Project Overview
This repository contains a lab report and supporting scripts/notebooks that explore **Big Data and NoSQL technologies**, including:

- **Neo4j** (graph database & Cypher)
- **MongoDB** (document DB & aggregation)
- **Hadoop / Cloudera** (HDFS, MapReduce, Pig, HBase)
- Practical lab exercises: HR survey, flight dataset analysis, library (books) analysis, and Hadoop exercises.

The full lab report (with explanations, example queries, dataset links, and results) is included in `BigData_Report.docx`.

---

## 📂 Contents (High Level)
- **Introduction** and background on Neo4j, MongoDB, Hadoop (Cloudera)
- **Lab 1:** Neo4j Experiments (HR dataset, friendships, employees, departments)
- **Lab 2:** Flight Dataset — Cypher queries and APOC import scripts
- **Lab 3:** MongoDB — Books, issues, members (aggregation examples)
- **Lab 4:** MongoDB demographic queries
- **Lab 5–7:** Hadoop / Cloudera — HDFS commands, Pig scripts, MapReduce, and HBase
- **Conclusion & References**

---

## 🧩 Datasets & Links
Datasets referenced in the report:

| Category | Files / Description |
|-----------|--------------------|
| **Neo4j (HR)** | `departments.csv`, `employees.csv`, `friendships.csv`, `persons.csv` |
| **Neo4j (Flights)** | `flights.csv`, `countries.csv`, `airports.csv`, `airlines.csv` |
| **MongoDB (Library)** | `books.json`, `issues.json`, `members.json` |
| **Hadoop** | HDFS command examples, Pig scripts, MapReduce jobs |

> Check the report for exact GitHub links and paths.

---

## ⚙️ Requirements
Install and configure the following before running the exercises:

- **Neo4j** (with APOC plugin)
- **MongoDB** + **MongoDB Compass**
- **Hadoop / Cloudera QuickStart VM**
- **HBase** (for advanced labs)
- **Python 3.x** (for mappers/reducers)
- Command-line tools: `curl`, `jq`, `git`

---

## 🚀 How to Use
1. Open `BigData_Report.docx` to read the full lab writeups and queries.
2. Download the referenced datasets (CSV/JSON) and place them in the correct directories.
3. Follow each lab’s instructions as described below:

### Neo4j
```cypher
MATCH (a:Person {name:'Alice'})-[:FRIENDS_WITH]->(f:Person)<-[:FRIENDS_WITH]-(b:Person {name:'Bob'})
RETURN DISTINCT f.name AS mutualFriend;
```

### MongoDB
```js
db.books.aggregate([
  { $unwind: "$authors" },
  { $group: { _id: "$authors", count: { $sum: 1 } } },
  { $sort: { count: -1 } },
  { $limit: 1 }
]);
```

### Hadoop / Pig
```bash
pig -x local myscript.pig
cat input.txt | ./wordcount_mapper.py | sort | ./wordcount_reducer.py
```

### HBase
```bash
hbase shell
create 'orders', {NAME=>'HEADER'}, {NAME=>'DETAILS'}
put 'orders','row1','HEADER:order_status','shipped'
scan 'orders'
```

---

## 📁 Recommended Folder Structure
```
/data/                    # raw CSV/JSON datasets
/neo4j/                   # Cypher scripts & APOC imports
/mongodb/                 # mongoimport scripts & queries
/hadoop/                  # MapReduce mappers/reducers, Pig scripts
/docs/BigData_Report.docx # main report
```

---

## 🧠 Notes & Assumptions
- Ensure inferred relationships like `MANAGES` are created before running advanced Cypher queries.
- Neo4j APOC imports assume CSV files are placed in the `import/` directory.
- Each query and output example is interpreted in the report.

---

## 📚 References
- [Neo4j Documentation](https://neo4j.com/docs/)
- [MongoDB Documentation](https://www.mongodb.com/docs/)
- [Apache Hadoop](https://hadoop.apache.org/)
- [HBase](https://hbase.apache.org/)

---

## ✍️ Author
**Abhishek Kumar**  
*Reg No:* 24MSD7017

---

## ⚖️ License
Include your preferred license (e.g., MIT) before publishing publicly.

---
