# Combat Network Dataset Generator

This project contains a Jupyter Notebook for generating complex combat network datasets that simulate different node types (Reconnaissance, Decision, Influence) and their interrelationships. These datasets can be used to research network resilience, attack strategies, and performance evaluation.

## Project Overview

The notebook implements the following functionality:

1. **Combat Network Modeling**:
   - Creates directed graphs with three node types (Reconnaissance S, Decision D, Influence I)
   - Defines node attributes (CAs, CAd, CAi) representing combat capabilities
   - Randomly generates connection relationships between nodes

2. **Combat Effectiveness Calculation**:
   - Implements S_G function to calculate overall network combat effectiveness
   - Defines Q function to calculate rescaled combat capability index
   - Implements get_num_large function to compute largest connected component size

3. **Attack Strategy Simulation**:
   - Multiple attack types: Max Degree, Random, Priority Recon Node, etc.
   - Three reconstruction strategies: No Reconstruction, Random Reconstruction, Structural Similarity Reconstruction
   - Two evaluation metrics: ANC (Network Connectivity) and ANOC (Combat Capability)

4. **Dataset Generation**:
   - Generates 100 combat networks with identical topology but different node attributes
   - Saves networks in GML format files

## Dataset Characteristics

- **Node Distribution**:
  - 55 Reconnaissance nodes (S)
  - 12 Decision nodes (D)
  - 30 Influence nodes (I)
  
- **Connection Relationships**:
  - S→S: 70 edges
  - S→D: 26 edges
  - D→D: 26 edges
  - D→I: 36 edges
  - D→S: 20 edges
  - I→S: 38 edges

- **Node Attributes**:
  - Reconnaissance capability (CAs): Normal distribution (μ=0.5, σ=0.07)
  - Decision capability (CAd): Normal distribution (μ=0.5, σ=0.07)
  - Influence capability (CAi): Normal distribution (μ=0.5, σ=0.07)
  - All attribute values clipped to [0,1] range

# Comparison of robustness metrics and Impact of collaborative reconfiguration strategy on CSoS robustness

This Jupyter Notebook performs comparative analysis of robustness metrics and evaluates the impact of collaborative reconfiguration strategies on Complex System of Systems (CSoS) robustness.

## Notebook Functionality

The notebook implements the following analytical workflow:

1. **Data Loading**:
   - Loads robustness metric data from JSON files in `/data2` directory
   - Processes two main categories of metrics:
     - Operation Capability Metrics (PMA, RA, PSA, PDA, PIA)
     - Connectivity Metrics (suffixed with `_C`)
   - Handles multiple configurations:
     - Base configurations (PMA, RA, PSA, PDA, PIA)
     - MSNC (Multi-System Node Configuration)
     - RNC (Reconfigurable Node Configuration)
     - MCNC (Multi-Component Node Configuration)

2. **Robustness Metric Comparison**:
   - Performs comparative analysis of:
     - ANC (Average Network Connectivity)
     - ANOC (Average Network Operational Capability)
   - Generates dual-axis plots comparing:
     - Operation Capability (left axis, blue line with circle markers)
     - Connectivity (right axis, red line with diamond markers)
   - Highlights critical failure points (operation capability/connectivity ≤ 0.05)
   - Annotates failure thresholds (f_N values)

3. **Visualization Features**:
   - Creates publication-ready figures (300 DPI PNG)
   - Implements consistent visual styling:
     - Operation Capability: Blue line with circle markers
     - Connectivity: Red line with diamond markers
   - Adds critical failure annotations:
     - Triangle markers for connectivity failure points
     - Square markers for operation capability failure points
     - Vertical dashed lines at failure thresholds
   - Saves output figures with standardized naming convention (e.g., pk-PMA, pk-RA_RNC)

## Analysis Characteristics

- **Metric Configurations**:
  - 4 base metric types (PMA, RA, PSA, PIA)
  - 3 enhanced configurations per base (MSNC, RNC, MCNC)
  - Total: 16 distinct configurations analyzed
  
- **Critical Failure Analysis**:
  - Operation capability threshold: ≤ 0.05
  - Connectivity threshold: ≤ 0.05
  - Failure points annotated with f_N values
  - Comparative failure progression across configurations

- **Visualization Standards**:
  - Global font: Times New Roman
  - Color scheme:
    - Operation Capability: Tab:blue (#1f77b4)
    - Connectivity: Tab:red (#d62728)
  - Marker styles:
    - Operation Capability: Circle (○)
    - Connectivity: Diamond (◇)
  - Failure markers:
    - Connectivity failure: Hollow black circle (◯)
    - Capability failure: Hollow black square (□)

## Usage Instructions
1. Place precomputed JSON metric files in `/data2` directory
2. Run cells sequentially to:
   a) Import required libraries
   b) Load metric data
   c) Generate comparative plots
3. Output figures automatically save in execution directory
4. File naming convention: pk-{configuration}.png

## Output Applications
- Comparative robustness assessment across configurations
- Failure threshold analysis for critical systems
- Visualization of degradation patterns under different configurations
- Validation of reconfiguration strategy effectiveness
- Publication-ready figures for academic research

# KDE, radar map and heatmap

This project contains a Jupyter Notebook for analyzing combat network resilience under different attack strategies and reconstruction methods. The toolkit evaluates network performance using metrics like ANC (Normalized Connectivity) and ANOC (Normalized Operational Capability), and generates comprehensive visualizations.

## Project Overview

The notebook implements the following functionality:

1. **Performance Metrics Calculation**:
   - Computes ANC and ANOC values from simulation results
   - Calculates statistical measures (mean, standard deviation, confidence intervals)
   - Performs ANOVA and Kolmogorov-Smirnov tests for significance analysis

2. **Visualization Methods**:
   - Bubble heatmaps with custom color schemes and scaling
   - Radar charts for strategy comparison
   - Kernel Density Estimation (KDE) plots with statistical annotations
   - Combined multi-plot visualizations

3. **Attack Strategy Analysis**:
   - Five attack types: RA, PMA, PSA, PDA, PIA
   - Four reconstruction methods: No Reconstruction, RNC, MSSNC, MFSNC
   - Comparative analysis of attack/reconstruction combinations

## Dataset Characteristics

- **Data Sources**:
  - Raw simulation results: `results.xlsx` and `results2.xlsx`
  - Processed metrics: `average2.xlsx` containing mean values

- **Metric Calculation**:
  - ANC: Normalized size of largest connected component
  - ANOC: Normalized combat capability index
  - Values clipped to [0,1] range for consistency

## Visualization Gallery

1. **Bubble Heatmap**:
   - Compares attack strategies (columns) vs reconstruction methods (rows)
   - Bubble size represents ANOC value magnitude
   - Custom color schemes per attack type
   - Saved as `split_bubble_heatmap_custom_ranges.png`

2. **Radar Charts**:
   - Shows ANOC values across five attack types
   - Four charts for different reconstruction methods
   - Saved as `Radar_Charts.png`

3. **KDE Plots**:
   - 20 density plots comparing different conditions
   - Includes statistical annotations:
     - Mean ± standard deviation
     - 95% confidence intervals
     - ANOVA and KS-test results
   - Combined in 5x4 grid as `pk ANC or ANOC`

## Usage Instructions

1. **Data Preparation**:
   - Place simulation results in `results.xlsx` and `results2.xlsx`
   - Generated averages will be saved in `average2.xlsx`

2. **Visualization Generation**:
   - Run all cells sequentially
   - Outputs include:
     - Performance metric values printed in console
     - Three main visualization types
     - 20 individual KDE plots

3. **Customization**:
   - Adjust color schemes in `color_schemes` dictionary
   - Modify axis ranges in `ranges` dictionary
   - Configure statistical parameters in KDE plot section

Note: Requires Python 3.8+ with pandas, numpy, seaborn, matplotlib, and scipy.
