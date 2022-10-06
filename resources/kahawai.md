---
layout: page
title: "The Kahawai reporting system"
author: "David Middleton"
---

# The Kahawai reporting system

The Kahawai reporting system facilitates **reproducible research** using data from fisheries databases. Using a continuous integration and delivery approach, the Kahawai system:

- streamlines the generation of reports, creating **efficiency**
- encourages sharing and collaboration, building a culture of **openness**
- allows activity to be checked and audited, ensuring **confidence** in the use of data and in the results delivered.

## Components

The Kahawai system consists of two key components:

- an instance of the *Gateaux* continuous deployment system for data science
- a series of databases containing fisheries data.

### Gateaux

Gateaux manages the production of reports that are defined entirely by code committed to the Github version control system. Many types of code are supported, but common examples are SQL for querying databases, R and python for analysing data, and LaTeX and markdown for producing reports.

Gateaux runs the code for a report on cloud computing resources to create outputs. Outputs may be a report, such as a PDF document, data prepared as a CSV file, or detailed simulation output resulting from running a model.

Each time the code for a report is run, a new job is created. Gateaux keeps a record of each job, and the outputs that are created. This ensures that the full history of each report is accessible.

### Databases

The Kahawai system provides users (subject to authorisation and access control procedures) with access to a range of databases. These are generally SQL databases running on a PostgreSQL server with the PostGIS extensions to facilitate spatial queries.

The majority of the Kahawai databases are reporting databases; that is, they are curated copies of data designed support fisheries data analyses, rather than databases designed for maintenance of original data. These reporting databases are themselves built by as Kahawai reports, from a variety of source data.

#### The kahawai database

The *kahawai database* is a curated reporting database built from data extracts provided by Fisheries New Zealand. In particular, the kahawai database's *edw* schema maintains a copy of statutory catch, efforts and landings data from New Zealand fisheries.

A key part of the kahawai database build process is the application of standard *grooming rules* that identify, and then flag or fix, known issues with the source data. The kahawai database also implements standard *catch allocation* procedures that allocate trip-resolution landings data back to the individual fishing events within a trip.

The kahawai database thus provides a standardised implementation of a range of data analysis procedures that have been developed over time and accepted as best practice by Fisheries New Zealand's Fisheries Assessment Working Groups.
