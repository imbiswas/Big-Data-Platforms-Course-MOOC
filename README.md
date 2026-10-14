# Big Data Platforms: course notebooks and assignments

Study notebooks and assignment files for **Big Data Platforms** (DATA140031 MOOC,
3 ECTS, plus DATA140032 MOOC exam, 2 ECTS) at the University of Helsinki, 2026
edition. The lectures are given by Keijo Heljanko; lecture 11 is co-lectured with
Ilari Maarala.

This is a personal study repository. It is not an official course repository and
is not endorsed by the University of Helsinki or the course staff.

## What's here

```
.
├── Big_Data_Platforms_Lecture1.ipynb … Lecture11.ipynb   one study notebook per lecture
├── Lectures/                  lecture slides (lecture1.pdf … lecture11.pdf)
├── images/                    figures used by the notebooks
├── Assignments/               course-provided homework notebooks and datasets
│   ├── Introduction to Spark + RDD Programming/
│   │   ├── BigDataPlatforms.pdf   the course's homework guide (Docker setup, submission)
│   │   ├── Intro/                 intro.ipynb
│   │   └── RDD/                   GeoProcessor.ipynb
│   ├── dataframe/                 AirTrafficProcessor.ipynb
│   ├── Mllib/                     GamingProcessor.ipynb
│   ├── Graphframes/               SocialGraph.ipynb
│   ├── StructuredStreaming/       trail_camera.ipynb
│   └── Extra/                     MusicRecommender.ipynb
├── DOCKER.md                  how to run and submit the assignments
├── requirements.txt           Python packages for the lecture notebooks
├── requirements-assignments.txt   best-effort local setup for the assignments
├── LICENSE                    MIT, for the original material in this repo
└── THIRD_PARTY_NOTICES.md     what is not covered by that license, and who owns it
```

## Lecture notebooks

Each notebook turns one lecture into notes with worked explanations, small runnable
examples, and figures. The code cells are short simulations meant to make an idea
concrete (a Bloom filter, a vector clock, a compaction), not production code.

| # | Topics |
|---|--------|
| 1 | Course overview, cloud computing and its business drivers, why single machines stopped getting faster, Amdahl's law, scaling up vs. scaling out |
| 2 | MapReduce and Apache Spark: the MapReduce model, word count by hand, Spark's motivation, RDDs |
| 3 | Spark libraries and the RDD API, broadcast variables and accumulators, persistence levels, MapReduce recap, Hadoop and HDFS |
| 4 | Storage fault tolerance: RAID 0/1/5/6/10, the write hole, erasure codes, HDFS design decisions |
| 5 | Worked RAID reliability exercises, flash storage, RAM vs. disk vs. tape, RAMCloud, hot/warm/cold storage |
| 6 | ACID, the CAP theorem, two-phase commit, consensus (FLP, Paxos), Chubby, ZooKeeper, Raft |
| 7 | NoSQL data store families, BASE, Spanner, Bloom filters |
| 8 | BigTable and HBase: data model, SSTables, memtable, compactions, the LSM tree |
| 9 | Dynamo, consistent hashing, vector clocks, Cassandra and Riak, CRDTs, Jepsen testing |
| 10 | The cloud stack and its open-source equivalents, storage taxonomy, S3, Delta Lake, Kafka, Lambda architecture, HyperLogLog |
| 11 | Genomics case studies on Spark: PanGenSpark and SparkBeagle (not exam material) |

### Run them locally

You need Python and a Java runtime (PySpark needs one; Java 8, 11, 17 or 21 work with
Spark 3.5). Check with `java -version`.

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

All eleven notebooks were executed top to bottom in a fresh environment built from
`requirements.txt` (Python 3.12, Java 21). Lectures 2, 3 and 10 start a local Spark
session, so the first run of those is slower.

`pyspark` is pinned to 3.5.6 because that is the Spark version the course
documentation links to. On Python 3.12 or newer, PySpark 3.5 also needs
`setuptools`, which the requirements file includes.

## Assignments

The notebooks in `Assignments/` are the course's homework, with their sample data.
They are graded automatically against hidden tests, so the environment matters: the
supported way to work on and submit them is the course Docker image.

**See [DOCKER.md](DOCKER.md)** for the step-by-step instructions (install Docker,
pull the image, start Jupyter, submit, read the feedback).

| Folder | Notebook | What it covers |
|--------|----------|----------------|
| `Introduction to Spark + RDD Programming/Intro` | `intro.ipynb` | First steps with Spark |
| `Introduction to Spark + RDD Programming/RDD` | `GeoProcessor.ipynb` | RDD programming on GeoNames place data |
| `dataframe` | `AirTrafficProcessor.ipynb` | DataFrames and Spark SQL on 2008 US airline on-time data |
| `Mllib` | `GamingProcessor.ipynb` | Spark ML: feature preparation and logistic regression |
| `Graphframes` | `SocialGraph.ipynb` | Graph analysis with GraphFrames (motif finding, label propagation, PageRank) |
| `StructuredStreaming` | `trail_camera.ipynb` | Structured Streaming over JSON files |
| `Extra` | `MusicRecommender.ipynb` | Collaborative-filtering recommender on Million Song Dataset samples |

If you can't run Docker, `requirements-assignments.txt` gives a best-effort local
setup. In a test run it was enough for six of the seven notebooks to execute
(everything except `SocialGraph.ipynb`, which also needs GraphFrames and its matching
Spark package). The Docker image is still the environment that counts for grading.

## Licensing and attribution

The original material in this repository (this README, `DOCKER.md`, the requirements
files, and the code and notes written for the lecture notebooks) is released under the
[MIT License](LICENSE).

That license does **not** cover everything in the repo. The lecture slides, the
assignment notebooks, the datasets, and many of the figures belong to other people.
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) lists them, with sources and what is
and isn't known about their terms.

The text of notebooks 3–11 paraphrases the lecture slides, which remain the property
of their authors. The slides are the authoritative source; where a notebook and a
slide disagree, trust the slide.

## How the notebooks were made

Notebooks 3–11 were drafted with AI assistance (Claude, from Anthropic) working from
the lecture slides, and their code cells were run to check that they execute. The
notebooks may still contain mistakes, so check anything important against the slides.

## Contact

Open an issue on this repository. If you are the author or owner of something here
and would like it credited differently or removed, please say so in an issue.
