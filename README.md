# Psychometric Data Analysis Tool

## Overview
This Python-based program is developed to analyze psychometric data collected in my research. It automates data processing and psychometric analysis to quantify how mice integrate sensory signals and make decisions in a vibrotactile stimulus detection task. The program compares **unilateral and bilateral performance**, where one side receives a constant sub-threshold stimulus while the other varies in intensity (0-1). As my research progresses, the program will evolve to incorporate optogenetic inhibition experiments to assess how different brain areas influence perception and decision-making.

## Objectives
This program streamlines behavioral data analysis, enabling efficient and accurate processing of results. The **raw behavioral data is collected using a LabVIEW program developed by my lab mate, PhD student Michael Sokoletsky**. The tool automates psychometric curve fitting based on **signal detection theory (SDT)**, computing sensory thresholds and comparing unilateral and bilateral conditions. It establishes a structured pipeline for analyzing data and will later support optogenetic inhibition experiments.

## Methodology

- **Data Loading and GUI**
  - The program allows the user to select a base folder and automatically loads MATLAB files matching the given mouse ID and day range.
  - It ensures correct directory navigation, checking whether the provided base folder already contains the mouse ID before appending it to the path.
  - Built with Tkinter, the GUI simplifies data selection and execution, ensuring correct file handling and preventing manual input errors.

- **Data Extraction & Preprocessing**
  - Relevant variables such as trial types, stimulus strengths, and optogenetic stimulation details are extracted.
  - Rounding errors in stimulus strengths are corrected, and maximum intensity values as well as sub-threshold levels are identified to ensure accurate categorization.
  - The data is compiled into a structured DataFrame for further analysis.

- **Psychometric Analysis**
  - Trials are categorized into unilateral and bilateral conditions, where the non-dominant side remains at a fixed sub-threshold intensity, and detection performance is assessed across varying stimulus intensities.
  - **psignifit**, a third-party Python package, is used for **nonlinear regression analysis** of psychometric functions. Specifically, the **Weibull function** is applied to model the probability of a correct response based on stimulus intensity, allowing for precise estimation of sensory thresholds.
  - If there is insufficient data for analysis, the program generates an error message prompting the user to select more files.

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

