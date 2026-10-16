# Third-party material and license scope

This repository mixes the owner's own work with material that belongs to other
people. This file says which is which. It is a good-faith inventory, not legal advice.

## What the MIT license covers

The [MIT License](LICENSE) applies to the original material written for this
repository:

- `README.md`, `DOCKER.md`, `THIRD_PARTY_NOTICES.md`
- `requirements.txt` and `requirements-assignments.txt`
- the code and notes written for `Big_Data_Platforms_Lecture1.ipynb` through
  `Big_Data_Platforms_Lecture11.ipynb`

It gives no rights over the underlying content those notes are about. The text of the
lecture notebooks paraphrases the lecture slides, and the slides stay the property of
their authors.

## What it does not cover

Everything below belongs to its original owner and keeps whatever terms the owner set.
Nothing in this repository changes those terms. Where the terms are unknown, that is
stated; treat unknown as "all rights reserved" until you've checked.

### Course materials

| Path | Owner | Notes |
|------|-------|-------|
| `Lectures/lecture1.pdf` … `lecture11.pdf` | Keijo Heljanko, University of Helsinki (lecture 11 also Ilari Maarala) | Lecture slides. Included for personal study. Redistribution needs the authors' permission. |
| `Assignments/**/*.ipynb` | Course staff, University of Helsinki | Homework notebooks. Terms not stated. |
| `Assignments/Introduction to Spark + RDD Programming/BigDataPlatforms.pdf` | Course staff, University of Helsinki | The homework guide. Terms not stated. |

### Datasets in `Assignments/`

Credits below are taken from the notebooks themselves. Samples in this repo are
extracts of the original data.

| Folder | Data | Source named in the notebook | Terms |
|--------|------|------------------------------|-------|
| `RDD/` | `allCountries_sample.txt` | GeoNames, `download.geonames.org/export/dump/allCountries.zip` | GeoNames data is published under Creative Commons Attribution 4.0; credit GeoNames. Check [geonames.org](https://www.geonames.org/) for the current terms. |
| `RDD/` | `countrycodes.csv`, `hotel_data.txt`, `testdata.txt` | Not stated | Unknown. Supplied with the assignment. |
| `Intro/` | `shakespeare.txt` | Not stated | The plays are old and in the public domain, but the terms of this particular edition are not stated. |
| `dataframe/` | `2008_*.csv` | Airline on-time data for 2008, from Harvard Dataverse (`dataverse.harvard.edu`, datafile 1374917) | See the terms on the Dataverse record. |
| `dataframe/` | `airports.csv`, `carriers.csv`, `testdata.csv` | Not stated; probably supporting files for the same airline data | Unknown. |
| `Mllib/` | `randomsample*.data`, `testData.data` | A gaming-data sample hosted at `cs.hut.fi/u/arasalo1/resources/` | Unknown. Supplied with the assignment. |
| `Graphframes/` | `socialgraph_*.dat` | UMN Foursquare dataset (`201309_foursquare_dataset_umn`, Internet Archive) | See the terms at the source. |
| `Extra/` | `sampleTracks.txt` | The Million Song Dataset (Bertin-Mahieux, Ellis, Whitman and Lamere, ISMIR 2011), `millionsongdataset.com` | See the terms at the source. |
| `Extra/` | `users.txt`, `sampleUsers.txt`, `randomusers.txt` | Not stated | Unknown. Supplied with the assignment. |
| `StructuredStreaming/` | `data/`, `data2/` (`MOCK_DATA*.json`) | Synthetic records supplied with the assignment; the file names match the default export names of the Mockaroo generator | Unknown. |

The small `jupyter.png`, `example.png` and `example_bothConnections.png` images inside
the assignment folders come with the assignments.

### Figures in `images/`

The figures used by the lecture notebooks come from the lecture slides and from the
sources the slides credit. Examples include charts on sequencing cost (National Human
Genome Research Institute, Illumina), CPU trends (Herb Sutter), and storage prices (Our
World in Data); the RAID diagrams from Wikipedia's *Standard RAID levels* article and
the Amdahl's law illustration from Wikipedia; the MapReduce data-flow figures from the
Yahoo! Developer Network tutorial; photographs of Google datacenters; and figures on
BigTable, Dynamo, ZooKeeper, HDFS, HBase and Facebook's storage systems, which come
from the papers and documentation the slides cite.

Each keeps its original copyright and license:

- some, such as Wikipedia illustrations and Our World in Data charts, are openly
  licensed and need attribution (for example CC BY or CC BY-SA);
- others, such as figures from papers and company photographs, are not openly licensed.

The notebooks credit the source of each figure where the slides do. If you reuse a
figure, go back to its original source and check its terms first.

### Software this repo uses but does not contain

These are installed from their own distributions and keep their own licenses: Apache
Spark and PySpark (Apache License 2.0), Jupyter, NumPy, pandas, Matplotlib and
setuptools. The course Docker image (`hainingt/big_data_platforms:2026`) is provided
by the course staff and carries the licenses of its contents; it is not part of this
repository.

## Corrections and takedowns

If you own something here and want it credited differently, relicensed, or removed,
open an issue on the repository and it will be dealt with promptly.
