<img width="1666" alt="image" src="https://github.com/Alexandregiacomellileal/Update-computacional-tool/assets/96079504/d40874aa-487c-4722-abfe-1cff32cfbd77">


# Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning.

## Overview
This repository contains a systematic solution for analyzing the grounding system of a wind turbines. The proposed solution involves a sequence of tasks depicted in methodology_flowchart.pdf. The approach integrates technical documentation analysis, parameter survey, electrical circuit modeling, sensitivity studies, and machine learning to predict turbine grounding resistances.

## Methodology

The proposed solution, depicted in methodology_flowchart.pdf, involves a systematic sequence of tasks. Initially, the process begins by accessing the technical documentation of the wind farm’s grounding system. Following this, a comprehensive survey of the parameters necessary for calculating the components of the equivalent electrical circuit is conducted. Next, an appropriate electrical circuit model is chosen for the wind farm’s grounding system. To account for variations and uncertainties, a sensitivity study is performed on parameters influencing the grounding resistance and capacitance of turbines and horizontal electrodes. Tolerance ranges are defined, considering factors such as construction non-conformities or soil and electrode deterioration. A sample vector $\textbf{P}$ is generated, with each element representing a specific grounding resistance or capacitance of a turbine or horizontal electrode. An element representing the parameter $k$ is also included to replicate the mutual coupling effect between the turbine and horizontal electrodes during clamp-on ground meter measurements. Uniform distributions are used to generate vector elements within their corresponding tolerance ranges set by the sensitivity study. The equivalent circuit of the grounding system is then loaded based on the values from the sample vector $\textbf{P}$. Subsequently, a computational simulation of the clamp-on method is performed in the equivalent electrical circuit. Instrument reading values are obtained in each turbine, resulting in an output sample vector **Z**<sub>med</sub>. This process is repeated $m$ times to generate input-output pairs [**Z**<sub>med</sub>; **R**<sub>f</sub>] stored in a database $\mathbb{D}_{m\times2n}$, being $n$ the numbers of turbines of the wind farm. The database is then utilized to train a machine-learning model. The trained model undergoes validation and testing to ensure accuracy and reliability. Finally, the trained model is used to predict the values of the resistances **R**<sub>f est</sub> for the n turbines based on the readings obtained via the clamp-on method during wind farm periodic inspections **Z**<sub>med </sub> . This systematic approach ensures a logical progression from data collection and circuit modeling to machine learning application, facilitating accurate predictions of turbine grounding resistances.

________________________________________________________________________________________________________________________

## Files

1. **methodology_flowchart:**
    - Flowchart of the proposed methodology.

2. **Proposed_solution.py:**
   
    - Module 1 is designed to streamline the generation and control of extensive simulations of electrical circuits through a Python algorithm integrated with the Alternative Transient Program (ATP). The algorithm facilitates the creation of .atp simulation files, executes simulations, and transforms resulting waveforms (.pl4 files) into MATLAB (.mat) files. The algorithm systematically generates parameter vectors P, which are subsequently introduced into the clamp-on ground meter measurement equivalent electric circuit. It orchestrates the automation of data entry and extraction steps within the ATP software. All resulting input-output vector pairs [**P**; **Z**<sub>med </sub>] are cataloged in a dedicated database. Notably, the vectors **Z**<sub>med </sub> and **R**<sub>f</sub> (part of elements of **P**) assume a pivotal role as a foundational repository for Module 2, where machine learning models are developed based on this comprehensive dataset.

    - Module 2 introduces a Python algorithm leveraging advanced machine learning techniques to forecast turbine grounding resistance based on clamp-on meter readings. This algorithm capitalizes on the database established in Module 1, employing it for tasks such as data preprocessing, model training, and the assessment of evaluation metrics to enhance predictive accuracy. Within the machine learning pipeline, 70% of the vector pairs [**Z**<sub>med </sub>; **R**<sub>f</sub>] from the Module 1 database are allocated for training the model, ensuring a robust foundation for learning. The remaining 30% is reserved for testing the trained model, evaluating its performance, and constructing boxplot error graphs. These graphs depict the outcomes of implementing the Clamp-on Ground Meter Method (CGM) and the Proposed Method in the São Bento Complex (SBC) grounding system, providing a comparative analysis of their effects.

    - Module 3 features a Python algorithm designed to efficiently generate and manage extensive simulations of electrical circuits using ATP. This module is capable of creating .atp simulation files, executing simulations, and converting resulting waveforms (.pl4 files) into MATLAB files (.mat). Specifically tailored for the testing set separated in Module 2, the algorithm loads the **P** electrical parameter sample vectors, sequentially introducing them into the High-frequency ground meter measurement circuit. It then automates the essential steps of data insertion and extraction within the ATP software. All resulting input-output pairs are stored in a dedicated database, forming the foundation for comprehensive analysis. The algorithm's outcomes are visually represented through a box plot error graph. This graph encapsulates the results obtained from implementing the High-Frequency Method (HFM) in the São Bento Complex (SBC) grounding system, providing a clear comparative assessment of its impact.


    - To utilize this algorithm, users are required to download and install three essential software components: ATP, the pl42mat.exe converter, and Python. 
   
4. **Database.xlsx:**
    - Excel spreadsheet featuring an extensive dataset designed for training, validation, and testing machine learning models. The dataset consists of 11,000 solution vectors, formed by concatenating the **P** vectors with their respective **Z**<sub>med</sub> vectors. In the machine learning pipeline, 70% of these solution vectors are allocated for training the model, ensuring a robust foundation for learning. The remaining 30% of vectors are dedicated to testing the trained model, as well as assessing the performance of the CGM and HFM measurement methods within the SBC framework. This division allows for a comprehensive evaluation of both the model's predictive capabilities and the effectiveness of measurement techniques in the specified context. 

5. **HFM.acp:**
   - ATP file for computer simulation of the high-frequency method in case study's grounding system.

6. **CGM.acp:**
    - ATP file for computer simulation of the clamp-on ground meter method in case study's grounding system.

7. **HFM_circuit.pdf:**
   - PDF file with the equivalent circuit's figure for the high-frequency measurement method in case study's grounding system.

8. **CGM_circuit.pdf:**
   - PDF file with the equivalent circuit's figure for the clamp-on ground meter measurement method in case study's grounding system.

9. **MAPE_results.xlsx:**
   - Excel spreadsheet containing the final results.
  
10. **Supporting files:**
   - This directory contains sub-algorithms and Excel spreadsheet files with data frames used by the authors in developing the proposed solution. Each module (sub-algorithm) performs a specific task, and when combined, the modules form the complete algorithm named 'Proposed_solution.py.' Similarly, all the Excel files contain data frames that collectively contribute to the formatting of the 'Database.xlsx' file.

________________________________________________________________________________________________________________________

## Results 

| Turbine | Rf design | MAPECGM | MAPEHFM | MAPEProposed |
|---------|-----------|---------|---------|--------------|
| SB03    | 0.22      | 1426.11%| 0.93%   | 12.71%       |
| OD09    | 0.34      | 917.74% | 1.34%   | 12.20%       |
| OD13    | 0.42      | 165.70% | 6.78%   | 11.48%       |
| SB08    | 0.65      | 650.76% | 1.33%   | 9.97%        |
| SB15    | 0.74      | 803.87% | 0.87%   | 10.31%       |
| OD03    | 0.83      | 469.58% | 0.78%   | 5.54%        |
| SB04    | 1.01      | 294.36% | 3.23%   | 7.16%        |
| SB05    | 1.05      | 234.02% | 4.56%   | 8.20%        |
| SB13    | 1.11      | 733.55% | 1.48%   | 9.59%        |
| SB11    | 1.24      | 284.79% | 4.63%   | 9.61%        |
| SB10    | 1.39      | 169.36% | 5.89%   | 6.05%        |
| OD08    | 1.42      | 202.67% | 5.31%   | 8.17%        |
| SB01    | 1.88      | 93.04%  | 9.38%   | 5.23%        |
| OD01    | 2.39      | 115.68% | 12.41%  | 7.25%        |
| SB09    | 2.43      | 77.46%  | 15.68%  | 2.60%        |
| OD15    | 3.17      | 125.02% | 21.34%  | 6.61%        |
| SB07    | 3.18      | 134.64% | 7.60%   | 3.35%        |
| SB06    | 3.55      | 87.33%  | 4.62%   | 2.32%        |
| OD05    | 3.84      | 288.99% | 5.78%   | 6.48%        |
| OD02    | 4.03      | 29.66%  | 9.76%   | 2.75%        |
| SB12    | 4.46      | 87.29%  | 10.08%  | 4.07%        |
| SB02    | 5.78      | 17.70%  | 21.26%  | 3.29%        |
| SB14    | 6.44      | 12.64%  | 11.32%  | 2.13%        |
| OD10    | 12.14     | 20.86%  | 40.76%  | 3.49%        |
| OD11    | 12.99     | 16.39%  | 27.83%  | 3.49%        |
| OD12    | 15.48     | 22.03%  | 42.69%  | 3.99%        |
| OD04    | 17.60     | 16.67%  | 26.72%  | 3.38%        |
| OD07    | 20.59     | 20.74%  | 47.94%  | 3.10%        |
| OD14    | 27.66     | 16.04%  | 31.13%  | 2.91%        |
| OD06    | 45.22     | 19.84%  | 48.57%  | 3.24%        |



________________________________________________________________________________________________________________________

## Usage

To apply this systematic approach to your wind farm grounding system analysis, follow the steps outlined in the respective sections of the codebase. Detailed instructions for each file can be found within their specific directories.

________________________________________________________________________________________________________________________

## Contact us:
Please send an email to: alexgiacomelli@yahoo.com

________________________________________________________________________________________________________________________

## Contributors:
Federal University of Technology – Parana (UTFPR) and Institute of Technology for Development (LACTEC)





