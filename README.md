# Benchbase Setup and Benchmarking Guide
=====================================================

## Virtual Machine Setup
To get started, create a virtual machine with the following specifications:

* CPU: 2 x Xeon E5-2660 v3 processors (10 cores each, 2.6Ghz or more)
* RAM: 256GB Memory (16 x 16GB DDR4 DIMMs)
* Disks: 1 x 900GB 10K SAS Drive

## Cloning Benchbase
Clone the Benchbase repository by running the following command:
```bash
git clone https://github.com/Preethi1609/benchbase.git
```

## Data Preparation and Setup
Choose the database you want to test on Benchbase and follow the corresponding setup instructions:

### Postgres
Version: PostgreSQL 12

Run `setup_scripts/postgres_init.sh` to install and set up Postgres.

### CockroachDB
Version: v24.1.0-alpha.5

Run `setup_scripts/cockroach_init.sh` to install and set up CockroachDB.

### Oracle RDBMS
Version: Oracle Database Express Edition (XE) version 21.3.0

Install Docker by running `setup_scripts/docker_init.sh`.

Follow the instructions in `docker/README.md` to set up Oracle RDBMS.


### Oracle Autonomous DB
Set up an Oracle Autonomous DB on Oracle Cloud Free Tier.

Add the IP of the VM to the Access Control List.

Change the connection from mTLS to TLS.

Create a DB user and get the DB connection string.

Update the config to connect to the DB using the JDBC interface.

### Data
The data need not be downloaded as it comes with benchbase setup

## Config changes made
TODO Saumya

## Building Benchbase
Run `setup_scripts/benchbase_init.sh` to build Benchbase.

## Running the Benchmark(Includes creating and loading tables and executing the benchmark)
Run the benchmark using the following command:

```bash
java -jar benchbase.jar -b tpcc -c config/postgres/sample_tpcc_config.xml --create=true --load=true --execute=true
```

Replace the workload and config file with the desired DB config file and workload.


## Application and code
Built with and for Java 21

Visualization scripts in Python3

Libraries used: 

- Pandas and Matplotlib for visualization
- Benchbase uses SLF4J for logging

Build tool:
- Maven

## Visualizing Results
Place the generated results in the `results` directory and run the scripts in the [notebook](https://github.com/Preethi1609/benchbase/blob/main/results/visualization/vis_results.ipynb) to visualize the benchmark results.

## Code written by us
Includes scirpts to setup and run databases, scripts to setup and run benchbase, scripts to setup the environment(like installing docker), scripts to visualize results, config changes and documentation.

## Credit

This repository is a fork of the BenchBase project, which was originally developed by CMU DB group.

D. E. Difallah, A. Pavlo, C. Curino, and P. Cudré-Mauroux, "OLTP-Bench: An Extensible Testbed for Benchmarking Relational Databases," PVLDB, vol. 7, iss. 4, pp. 277-288, 2013.
