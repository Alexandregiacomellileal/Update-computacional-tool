# Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning.

## Overview
This repository contains a systematic solution for analyzing the grounding system of a wind turbines. The proposed solution involves a sequence of tasks depicted in methodology_flowchart.pdf. The approach integrates technical documentation analysis, parameter survey, electrical circuit modeling, sensitivity studies, and machine learning to predict turbine grounding resistances.

## Methodology

The proposed solution, depicted in methodology_flowchart.pdf, involves a systematic sequence of tasks. Initially, the process begins by accessing the technical documentation of the wind farm’s grounding system. Following this, a comprehensive survey of the parameters necessary for calculating the components of the equivalent electrical circuit is conducted. Next, an appropriate electrical circuit model is chosen for the wind farm’s grounding system. To account for variations and uncertainties, a sensitivity study is performed on parameters influencing the grounding resistance and capacitance of turbines and horizontal electrodes. Tolerance ranges are defined, considering factors such as construction non-conformities or soil and electrode deterioration. A sample vector $\textbf{P}$ is generated, with each element representing a specific grounding resistance or capacitance of a turbine or horizontal electrode. An element representing the parameter $k$ is also included to replicate the mutual coupling effect between the turbine and horizontal electrodes during clamp-on ground meter measurements. Uniform distributions are used to generate vector elements within their corresponding tolerance ranges set by the sensitivity study. The equivalent circuit of the grounding system is then loaded based on the values from the sample vector $\textbf{P}$. Subsequently, a computational simulation of the clamp-on method is performed in the equivalent electrical circuit. Instrument reading values are obtained in each turbine, resulting in an output sample vector **Z**<sub>med</sub>. This process is repeated $m$ times to generate input-output pairs stored in a database $\mathbb{D}_{m\times2n}$. The database is then utilized to train a machine-learning model. The trained model undergoes validation and testing to ensure accuracy and reliability. Finally, the trained model is used to predict the values of the resistances **R**<sub>f est</sub> for the n turbines based on the readings obtained via the clamp-on method during wind farm periodic inspections **Z**<sub>med </sub> . This systematic approach ensures a logical progression from data collection and circuit modeling to machine learning application, facilitating accurate predictions of turbine grounding resistances.

________________________________________________________________________________________________________________________

## Files

1. **methodology_flowchart:**
    - Flowchart of the proposed methodology.

2. **Proposed_solution.py:**
    - Python algorithm to automate data insertion and removal in ATP software specifically adapted for simulations of clamp-on and high-frequency ground meter measurement circuits. It also incorporates machine learning techniques to predict turbine grounding resistance based on clamp-on meter readings, utilizing data preprocessing, model training, and evaluation metrics to optimize predictive accuracy. Towards the conclusion, a boxplot error graph is generated, depicting the outcomes derived from the implementation of Clamp-on Ground Meter Method (CGM), High-Frequency Method (HFM), and the Proposed Method in the São Bento Complex (SBC) grounding system for comparative analysis of their effects.
   
3. **Database.xlsx:**
    - Excel spreadsheet featuring an extensive dataset designed for training, validation, and testing machine learning models. The dataset consists of 11,000 solution vectors, formed by concatenating the **P** vectors with their respective **Z**<sub>med </sub> vectors. In the machine learning pipeline, 70% of these vectors are allocated for training the model, ensuring a robust foundation for learning. The remaining 30% of vectors are dedicated to testing the trained model, as well as assessing the performance of the CGM and HFM measurement methods within the SBC framework. This division allows for a comprehensive evaluation of both the model's predictive capabilities and the effectiveness of measurement techniques in the specified context. 

4. **HFM.acp:**
   - ATP file for computer simulation of the high-frequency method in case study's grounding system.

5. **CGM.acp:**
    - ATP file for computer simulation of the clamp-on ground meter method in case study's grounding system.

6. **HFM_circuit.pdf:**
   - PDF file with the equivalent circuit's figure for the high-frequency measurement method in case study's grounding system.

7. **CGM_circuit.pdf:**
   - PDF file with the equivalent circuit's figure for the clamp-on ground meter measurement method in case study's grounding system.

8. **MAPE_results.xlsx:**
   - Excel spreadsheet containing the final results. 


________________________________________________________________________________________________________________________

## Usage

To apply this systematic approach to your wind farm grounding system analysis, follow the steps outlined in the respective sections of the codebase. Detailed instructions for each file can be found within their specific directories.

________________________________________________________________________________________________________________________

## Contact us:
Please send an email to: alexgiacomelli@yahoo.com

________________________________________________________________________________________________________________________

## Contributors:
UTFPR and LACTEC
