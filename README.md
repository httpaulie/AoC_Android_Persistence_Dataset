# Unveiling Confusion in Android Data Persistence Libraries
This repository contains the dataset for the paper: **"Unveiling Confusion in Android Data Persistence Libraries"**.
## Overview
The research investigates the prevalence, evolution, and performance impact of Atoms of Confusion (ACs) within the Android data persistence ecosystem. ACs are small, syntactically valid code patterns that frequently lead to misinterpretation. Our study covers four major libraries: SQLite, Room, Realm, and ObjectBox.
## Dataset Structure
The dataset is organized into three main folders corresponding to the studies presented in the paper:
### `study_1_prevalence/`
Contains the static analysis results for the latest stable versions of the four libraries.
* **Languages**: Java and C/C++.  
* **Tools Used**: BOHR (for Java) and AtomFinder (for C/C++).  
* **Files**:
  * `result_java_raw_study1.xlsx`: Raw AC detection counts for Room, Realm, ObjectBox and SQLite.
  * `result_c_raw_study1.xlsx`: Raw AC detection for SQLite and Realm native components.
  * `result_processed_study1.xlsx`: Processed data for analysis, including normalized density data ($AC/KLOC$) and propagation rates ($R_{prop}$).
 
### `study_2_evolution/`
A dataset tracking the evolution of ACs in SQLite over a decade (2015–2025).
  * **Scope**: Analysis of stable releases from version 3.10.0 to 3.50.0 and the current master branch.
  * **Languages**: Java and C/C++.  
  * **Tools Used**: BOHR (for Java) and AtomFinder (for C/C++).  
  * **Files:**
    * `result_java_raw_study2.xlsx`: Raw AC detection counts in Java for SQLite versions.
    * `result_c_raw_study2.xlsx`: Raw AC detection in C/C++ for SQLite versions.
    * `result_processed_study1.xlsx`: Processed data for analysis, including accumulation rates and density variations ($\Delta D_{ac}$).
   
### `study_3_performance/`
Data from controlled micro-benchmarks evaluating the performance of the five most frequent ACs found in SQLite.
  * **Languages**: C/C++.  
  * **Tools Used**: Nanobench (for CPU) and Valgrind (for Memory).
  * **Evaluated Atoms**: Post-increment, Conditional Operator, Infix Operator Precedence, Implicit Predicate, and Omitted Curly Braces.  
  * **Files:**
    *  `csv/cpu/`: High-resolution timing and instruction metrics (ns/op, IPC, etc.) collected via Nanobench.
    *  `csv/memory/`: Memory footprint analysis (reads/writes and cache misses) collected via Valgrind.
  #### Methodological Summary
  * **Environment:** Benchmarks were compiled with g++ with optimization flag -O0.  
  * **Reliability:** Each benchmark was executed 30 times, with high-noise runs (error > 5%) automatically rejected.  
  * **Analysis:** Statistical significance was determined using a two-tailed Student's t-test ($p < 0.05$).
