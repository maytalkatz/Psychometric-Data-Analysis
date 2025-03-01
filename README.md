# Psychometric Data Analysis Tool

## Overview
This Python-based program is developed to analyze psychometric data collected in my research. It automates data processing and psychometric analysis to quantify how mice integrate sensory signals and make decisions in a vibrotactile stimulus detection task. The program compares unilateral and bilateral perception performance, where one side receives a constant sub-threshold stimulus while the other varies in intensity (0-1). As my research progresses, the program will evolve to incorporate optogenetic inhibition experiments to assess how different brain areas influence perception and decision-making.

## Objectives
This program streamlines behavioral data analysis by automating psychometric curve fitting based on [Signal detection theory (SDT)](https://www.cns.nyu.edu/~david/handouts/sdt/sdt.html). It processes raw behavioral data collected via a LabVIEW program (developed by Michael Sokoletsky) to compute sensory thresholds and compare unilateral and bilateral conditions. The tool establishes a structured data analysis pipeline and is designed to support future experiments, including optogenetic inhibition studies.

## Program Workflow

- **Data Loading**
  - Automatically loads MATLAB files based on the selected base folder, mouse ID, and day range.
  - Verifies the directory structure and appends the mouse ID if needed.

- **Data Extraction & Preprocessing**
  - Relevant variables such as trial types, stimulus strengths, and optogenetic stimulation details are extracted.
  - Rounding errors in stimulus strengths are corrected, and maximum intensity values as well as sub-threshold levels are identified to ensure accurate categorization.
  - The data is compiled into a structured DataFrame for further analysis.

- **Psychometric Analysis**
  - Trials are categorized into unilateral and bilateral conditions, where the non-dominant side remains at a fixed sub-threshold intensity, and detection performance is assessed across varying stimulus intensities.
  - **psignifit**, a third-party Python package, is used for nonlinear regression analysis of psychometric functions. Specifically, the Weibull function is applied to model the probability of a correct response based on stimulus intensity, allowing for precise estimation of sensory thresholds.

- **Graphical User Interface (GUI)**
  - Built with Tkinter to simplify file selection and parameters insertion.
  - Works with any single mouse ID from the selected folder, making file browsing easier across different computers and locations while reducing manual input errors.
  - If there is insufficient data for analysis, the program generates an error message prompting the user to select more files.




### Psychometric Fitting with psignifit

This project uses [psignifit](https://github.com/wichmann-lab/psignifit/wiki) to fit psychometric curves to behavioral data using a Weibull sigmoid model in a Yes/No design. The toolbox estimates five key parameters:

- **Threshold:** The stimulus intensity at which performance reaches 50%.
- **Slope:** The steepness of the curve.
- **Lapse Rate:** The error rate at high intensities.
- **Guess Rate:** The baseline performance level (fixed via our options).
- **Shape Parameter:** Adjusts the curvature of the function.


This program configures psignifit with custom options ,such as a fixed guess rate based on baseline performance, to improve the robustness of the fit. 
This project includes a local copy of psignifit (version 0.1) in the repository. Although a newer version is available, it's recommended to use the provided version to ensure compatibility and reproducibility of the results.
if psignifit is downloaded separately, ensure its folder is placed in the same directory as the main program. 
For more details on psignifit and its implementation, please refer to the [official documentation](https://github.com/wichmann-lab/psignifit/wiki).


## Significance and Future Directions
This program enhances the efficiency and accuracy of analyzing large datasets, ensuring reproducible results in behavioral research. Currently, the analysis is limited to **'no optogenetic stimulation'** data, as there is not yet sufficient data from other conditions. Future updates will incorporate optogenetic inhibition analysis, enabling direct comparisons between **control** and manipulated conditions to determine how suppressing specific brain regions affects sensory integration and decision-making. Further improvements will expand SDT metrics, such as **sensitivity (d′) and decision criterion (c)**, to refine performance characterization.


## Usage
### Requirements
- **Python 3.10+**
- **Required Python Packages:** `numpy`, `pandas`, `matplotlib`, `scipy`, `psignifit`
- Install required dependencies using:
  ```bash
  pip install numpy pandas matplotlib scipy psignifit
  ```

### Running the Program
1. **Clone the repository:**
   ```bash
    git clone https://github.com/maytalkatz/Psychometric-Data-Analysis.git
    cd Psychometric-Data-Analysis

   ```
   Alternatively, download the project files manually.

2. **Run the program:**
   ```bash
   python psychometric_analysis.py
   ```
   Alternatively, you can run the program using the Run button in VSC. The program will open a GUI to assist with folder selection and parameter entry.

3. **Select Data:**
   - Choose the base folder containing `.mat` files.
   - Enter the **mouse ID** and **day range** for analysis.

4. **View the Output:**
   - The program will process data and generate psychometric curves.
   - If insufficient data is available, an error message will indicate the need to select more files.

### Testing the Code
The program includes built-in validation steps to ensure correct functionality. If unexpected results occur, check the following:
- **Folder Selection:** Ensure the correct folder containing `.mat` files is chosen.
- **Dependencies:** Verify that all required Python packages are correctly installed.
- **Sufficient Data:** Make sure enough days are selected for analysis. If necessary, increase the range of days included in the input.


#
This program was developed as a **final project** for a **basic programming skills in Python** course. Moving forward, it will be further developed to meet my research needs, integrating additional functionalities for more advanced psychometric analysis and expanding its capabilities to support optogenetic inhibition experiments.

