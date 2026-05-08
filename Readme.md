# Project Overview: PrecisionBio—An Industrial-Grade scRNA-seq Analysis Pipeline for COVID-19

## 1. Project Positioning
**PrecisionBio** is an automated single-cell transcriptomics (scRNA-seq) analysis platform specifically designed for COVID-19 clinical cohort data. More than just a collection of bioinformatics scripts, this project is an industrial-grade production line integrating automated environment auditing, sampled data validation, reference genome construction, and multi-dimensional quality control. It effectively addresses core pain points in clinical big data processing, such as limited computational resources, confusing reagent versions, and difficulties in asset management.

## 2. End-to-End Architecture
The project consists of four core technical modules, forming a closed loop from "raw data" to "QC audit reports":

* **Module 1: Environmental Foundation & Automated Audit (Step 0 - 0.5)**: Establishes a standardized operational space and ensures the collaborative stability of Python libraries, bioinformatics toolchains, and cloud storage through "smoke testing."
* **Module 2: Reference Genome Dual-Index Construction (Step 1 - 1.5)**: Builds a human genome T2G mapping dictionary using a "local compute + cloud sync" strategy to establish a high-precision alignment benchmark.
* **Module 3: Sampled Data Audit & Precision Quantification (Step 2.1 - 2.3)**: Implements a pioneering "200MB Header Sampling" strategy to rapidly inspect Read 1 structures, automatically identify 10x Genomics chemistry versions (v2/v3), and complete preliminary alignment.
* **Module 4: Multi-Dimensional QC & Asset Restoration (Step 3.1 - 3.3.3)**: Performs precision auditing at both cell and gene levels, restores gene nomenclature via ID remapping, and generates publication-quality QC reports.

## 3. Technical Stack & Highlights
**Technical Stack**: Python 3, Scanpy, kb-python (Kallisto/Bustools), Pandas, Seaborn, Linux Shell.

**Engineering Strategies**:
* **Resource-Sensitive Design**: Achieves rapid iteration for massive datasets through data sampling, significantly lowering hardware barriers.
* **Defensive Programming**: Embeds audit checkpoints throughout the entire pipeline—enforcing checks on file sizes, matrix sparsity, and mapping rates—to prevent wasted computation.
* **Asset Management System**: Utilizes an object-oriented Config center to achieve complete decoupling of code and paths, supporting seamless cross-platform migration.

## 4. Deliverables
Upon completion of the pipeline, the project produces the following core assets:
* **Standardized Expression Matrix**: A single-cell object stored in .h5ad format, including restored Gene Symbol labels.
* **Multi-Dimensional QC Atlas**: Includes Knee Plots (empty droplet filtering), Mapping Efficiency analysis, and "Three-in-One" QC audit distribution charts.
* **Technical Metadata Report**: Detailed records of sample sequencing depth, library versions, and gene matching statistics.

## 5. Application Value (Commercial & Scientific)
* **Rapid Clinical Response**: Enables pre-auditing of new samples within minutes to quickly determine if sample quality meets operational standards.
* **Foundation for Cross-Cohort Integration**: The standardized remapping workflow clears obstacles caused by inconsistent identifiers, facilitating the integration of diverse COVID-19 public datasets (e.g., Cell Atlas).
* **High-Reliability Assurance**: Industrial-grade audit logic ensures every step of the data analysis is traceable, significantly enhancing the credibility of biological conclusions.

**Project Status**: Environment validation and sampled testing workflows are complete.
**Target Scenarios**: Clinical sequencing services, secondary mining of public single-cell data, and bioinformatics pipeline prototyping.

---

# Module 1: Environment Initialization & System Audit (Step 0 - 0.5)

## 1. Module Overview
This module is responsible for constructing an industrial-grade foundation for single-cell analysis. Through automated scripting, it handles dependency deployment, cloud storage mounting, 和 standardized project path configuration. It further performs environmental compliance auditing to ensure stability and reproducibility for subsequent high-intensity computational tasks.

## 2. Core Functional Summary
* **Automated Environment Deployment**: One-click integration of core components such as Scanpy and kb-python, eliminating manual configuration conflicts.
* **Persistent Storage Architecture**: Decouples data from compute resources by mounting Google Drive, ensuring the permanent preservation of massive analytical assets.
* **Standardized Configuration Management**: Utilizes an Object-Oriented Programming (OOP) approach via a Config class to uniformly manage data, indices, and result paths, enhancing project portability.
* **End-to-End Smoke Testing**: Enforces mandatory auditing of Python libraries, system-level bioinformatics toolchains, and disk I/O permissions to eliminate hidden operational risks.

## 3. Technology Stack & Engineering Capabilities
**Technical Tools**: Python 3, Scanpy, kb-python (Kallisto/Bustools), Google Colab system integration.
**Engineering Practices**: Professional logging systems (Logging), Object-Oriented Programming (OOP), automated script auditing, and defensive programming for exception handling.

## 4. Deliverables
* **Directory Assets**: An automatically generated, standardized project folder system (Data, Indices, Figures, Results).
* **Execution Reports**: A clear environment readiness checklist (Library & System Tooling Ready).
* **Project Foundation**: A stable workspace capable of directly supporting heavy downstream tasks such as alignment, dimensionality reduction, and clustering.

## 5. Expansion Directions
* **Environment Containerization**: Exportable as Conda or Docker environments to adapt to local High-Performance Computing (HPC) clusters.
* **Version Control**: Recommended "locking" of core library versions during the production phase to achieve absolute stability.
* **Dynamic Resource Awareness**: Scalable to include automatic detection of GPU/RAM status for dynamic allocation of computational threads.

---

# Module 2: Reference Genome Index Construction & Asset Audit (Step 1 - 1.5)

## 1. Module Overview
This module is responsible for establishing the "navigation map" for downstream single-cell analysis. It utilizes the kb-python engine to build a dual-index system (Kallisto Index and T2G mapping table) for the human reference genome. A key highlight of this module is the optimization of cross-device data migration logic, which overcomes transmission bottlenecks between cloud storage and local disks, while introducing a mandatory audit mechanism for data assets.

## 2. Core Functional Summary
* **Dual-Space Collaborative Construction**: Leverages high-speed local disk I/O for index computation, followed by automatic synchronization to Google Drive—balancing computational speed with data persistence.
* **Cross-Disk Transfer Integrity**: Employs the shutil module instead of simple file movement commands to guarantee the integrity of large (GB-scale) index files during cross-device migration.
* **Multi-Dimensional Asset Audit**: Performs physical auditing (file size) and content auditing (data format preview) on the generated .idx index and .txt mapping files.
* **Dictionary Structure Adaptation**: Deeply parses the T2G (Transcript-to-Gene) dictionary, supporting an 8-column rich format to provide a robust foundation for accurate Gene ID to Symbol mapping.

## 3. Technology Stack & Engineering Capabilities
**Technical Tools**: kb-python (Kallisto/Bustools), Pandas, Python system modules (os, shutil, subprocess).

**Engineering Practices**:
* **Local Caching Strategy**: Resolves network latency issues associated with large file R/W operations on cloud-mounted drives.
* **Automated Verification Stream**: Implements ls -lh style file system auditing directly via Python.
* **Rich Format Parsing**: Handles annotation data containing multi-dimensional information such as genomic coordinates and biological types.

## 4. Deliverables
* **Index Assets**: human_index.idx (core alignment file) and t2g.txt (transcript-to-gene mapping table).
* **Audit Reports**: Outputs regarding file sizes, total mapping entries, and previews of core columns (Gene ID / Symbol).
* **Alignment Foundation**: Provides high-precision reference standards for the subsequent quantitative analysis of raw FASTQ data.

## 5. Expansion Directions
* **Multi-Species Extension**: Quickly construct indices for mouse (mm10) or other model organisms by adjusting kb ref parameters.
* **Custom Annotation Integration**: Supports merging exogenous sequences (e.g., GFP, RFP, or viral sequences) into the reference genome to meet specific experimental needs.
* **Index Pre-loading**: Capability to create version snapshots for commonly used reference genomes, enabling instant reuse across multiple projects.

---

# Module 3: Precision Raw Data Audit & Quantitative Alignment (Step 2.1 - 2.3)

## 1. Module Overview
This module is responsible for transforming raw sequencing data (FASTQ) into gene expression matrices. Given the massive scale of industrial single-cell datasets (often tens of GBs) and limited computational resources, this module employs a "Header Sampling Audit" strategy. By retrieving only the first 200,000,000 bytes (approximately 200MB) of data as a sample, it enables rapid assessment of the sequencing library's quality and technical specifications.

## 2. Core Functional Summary
* **High-Speed Data Retrieval Strategy**: Utilizes the curl Range parameter to precisely extract the first 200,000,000 bytes of Read 1 and Read 2. This "sample-to-insight" approach significantly saves cloud storage space and download time, making it ideal for rapid pipeline validation under hardware constraints.
* **Automatic Technical Specification Identification**: Automatically identifies the 10x Genomics chemistry version (e.g., 26bp for v2, 28bp for v3) by precisely measuring the Read 1 length of the sampled data.
* **High-Throughput Alignment & Quantification**: Invokes the kb count engine based on the audited technical parameters (e.g., -x 10xv2) to generate the core product of single-cell analysis—the gene expression matrix.
* **Output Physical Audit**: Uses the MatrixAuditor module to perform integrity checks on the generated .mtx, .barcodes.txt, and .genes.txt files, providing preliminary statistics on captured cell and gene scales.

## 3. Technology Stack & Engineering Capabilities
**Technical Tools**: curl (Range requests), zcat, kb-python, Bash script integration.

**Engineering Practices**:
* **Resource Optimization Algorithm**: Solves hardware bandwidth and computational bottlenecks by limiting data traffic (200MB Sampling), enabling a "fail-fast/pass-fast" workflow.
* **Defensive Auditing**: Implements "data structure peeking" via peek_fastq prior to formal analysis to prevent large-scale computational failures caused by incorrect parameters.
* **Sparse Matrix Pre-processing**: Handles Matrix Market format sparse matrices to prepare data for downstream Scanpy analysis.

## 4. Deliverables
* **Data Snapshots**: Sampled FASTQ files stored on the local disk.
* **Technical Reports**: Clear identification of the sample's chemistry version (10xv2/v3) and expected alignment success rates.
* **Core Matrices**: The counts_unfiltered directory, containing the initial .h5ad object and sparse matrix triplet files.

## 5. Expansion Directions
* **Seamless Full-Scale Migration**: Once the workflow is validated via sampling, the formal analysis of full-scale data can be launched with a single click by simply removing the curl Range restriction.
* **Multi-Sample Parallelization**: Leverages the lightweight nature of this module to quickly pre-audit batch effects across dozens of samples.
* **QC Threshold Prediction**: Pre-set UMI and gene count thresholds for downstream filtering (QC) based on the expression distribution generated from the sampled data.

---

# Module 4: Multi-Dimensional Quality Control, Asset Restoration & Visual Audit (Step 3.1 - 3.3.3)

## 1. Module Overview
This module represents the critical "Precision Audit Phase" of the data analysis pipeline. Its core mission is to perform cell-level and gene-level quality assessments on the expression matrix produced in the previous stage. By utilizing Knee Plots for living cell filtration, auditing alignment efficiency, and remapping gene identifiers (ID to Symbol), this module ensures the accuracy of subsequent biological interpretations.

## 2. Core Functional Summary
* **Empty Droplet Filtration & Knee Plot (Step 3.1)**: Uses log-log transformation of UMI abundance rankings to intuitively distinguish real cells from ambient RNA noise.

<a href="./COVID_Project/results/figures/step3.1_knee_plot_SRR11038995.png">
  <img src="./COVID_Project/results/figures/step3.1_knee_plot_SRR11038995.png" width="400" alt="Knee Plot">
</a>

* **Multi-Dimensional Alignment Efficiency Analysis (Step 3.2.1 - 3.2.2)**: Parses alignment metadata to quantify the ratio of valid sequences via stacked bar charts, evaluating the overall quality of library construction.

<a href=“COVID_Project/results/figures/step3.2_mapping_efficiency_SRR11038995.png">
  <img src="COVID_Project/results/figures/step3.2_mapping_efficiency_SRR11038995.png" width="400">
</a>

* **Gene Identifier Remapping (Step 3.3.1 - 3.3.2)**: Converts abstract ENSG IDs into intuitive Gene Symbols, enabling the precise identification of mitochondrial genes (MT-).

<a href=“COVID_Project/results/figures/step3.3.3_qc_audit_fixed_SRR11038995.png">
  <img src="COVID_Project/results/figures/step3.3.3_qc_audit_fixed_SRR11038995.png" width="400">
</a>

* **Cell-Level Metric Re-Audit (Step 3.3.3)**: Synthesizes UMI counts, detected gene counts, and mitochondrial percentages to generate and archive "restored" high-resolution QC distribution plots.

## 3. Technology Stack & Engineering Capabilities
**Technical Tools**: Scanpy, Pandas, Matplotlib, Seaborn, JSON parsing.

**Engineering Practices**:
* **Data Dictionary Injection**: Implements an efficient ID-to-Symbol mapping algorithm with defensive filling for missing values.
* **Industrial-Grade Visualization**: Constructs professional statistical charts meeting publication standards (including Log-Log coordinate systems and high-DPI image exports).
* **Automated Metadata Auditing**: Programmatically extracts core metrics from alignment reports to minimize human error in data verification.

## 4. Result Notes (Critical Caveats)
* **Partial Data Representation**: It must be emphasized that because a 200MB data sampling strategy was adopted in Step 2, all metrics generated in this module (e.g., cell counts, total gene counts) represent only local features of the sample.
* **Trend Prediction**: Although the values are based on local sampling, the distribution characteristics (such as the shape of the Knee Plot curve and mitochondrial percentage distribution) are sufficient to evaluate the reliability of the experimental workflow and guide threshold settings for full-scale data filtration.
* **Asset Outputs**: Generates several key QC reports, including step3.1_knee_plot, step3.2_mapping_efficiency, and step3.3.3_qc_audit_fixed.

## 5. Expansion Directions
* **Adaptive Filtration Thresholds**: Introduce algorithms to automatically identify the "inflection point" (knee) of the curve for intelligent cell selection.
* **Interactive QC Dashboard**: Expand this audit workflow into an interactive interface, allowing for real-time adjustment of filtration parameters.
* **Dual-Modal Validation**: Automatically trigger apoptosis-score audits when high mitochondrial gene ratios are detected to further enhance the biological credibility of the data.
