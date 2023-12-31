<img width="1666" alt="image" src="https://github.com/Alexandregiacomellileal/Update-computacional-tool/assets/96079504/d40874aa-487c-4722-abfe-1cff32cfbd77">


# Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning.

## Overview
This repository contains a systematic solution for analyzing the grounding system of a wind turbines. The proposed solution involves a sequence of tasks depicted in Figure 1. The approach integrates technical documentation analysis, parameter survey, electrical circuit modeling, sensitivity studies, and machine learning to predict turbine grounding resistances.

## Methodology

The proposed solution, depicted in Figure 1, involves a systematic sequence of tasks. Initially, the process begins by accessing the technical documentation of the wind farm’s grounding system. Following this, a comprehensive survey of the parameters necessary for calculating the components of the equivalent electrical circuit is conducted. Next, an appropriate electrical circuit model is chosen for the wind farm’s grounding system. To account for variations and uncertainties, a sensitivity study is performed on parameters influencing the grounding resistance and capacitance of turbines and horizontal electrodes. Tolerance ranges are defined, considering factors such as construction non-conformities or soil and electrode deterioration. A sample vector $\textbf{P}$ is generated, with each element representing a specific grounding resistance or capacitance of a turbine or horizontal electrode. An element representing the parameter $k$ is also included to replicate the mutual coupling effect between the turbine and horizontal electrodes during clamp-on ground meter measurements. Uniform distributions are used to generate vector elements within their corresponding tolerance ranges set by the sensitivity study. The equivalent circuit of the grounding system is then loaded based on the values from the sample vector $\textbf{P}$. Subsequently, a computational simulation of the clamp-on method is performed in the equivalent electrical circuit. Instrument reading values are obtained in each turbine, resulting in an output sample vector **Z**<sub>med</sub>. This process is repeated $m$ times to generate input-output pairs [**Z**<sub>med</sub> ; **R**<sub>f</sub>] stored in a database $\mathbb{D}_{m\times2n}$ , being $n$ the numbers of turbines of the wind farm. The database is then utilized to train a machine-learning model. The trained model undergoes validation and testing to ensure accuracy and reliability. Finally, the trained model is used to predict the values of the resistances **R**<sub>f est</sub> for the n turbines based on the readings obtained via the clamp-on method during wind farm periodic inspections **Z**<sub>med </sub> . This systematic approach ensures a logical progression from data collection and circuit modeling to machine learning application, facilitating accurate predictions of turbine grounding resistances.
________________________________________________________________________________________________________________________
**Figure 1**
<img src="https://github.com/Alexandregiacomellileal/Update-computacional-tool/assets/96079504/ed3d7942-49a0-43e3-82a9-214a72362053" width="500" height="375">
_______________________________________________________________________________________________________________________

## Files

1. [[methodology_flowchart.pdf](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/methodology_flowchart.pdf)]
    - Flowchart of the proposed methodology.

2. [[Proposed_solution.py](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/Proposed_solution.py)]
  
    - This Python algorithm comprises three modules designed for generating, analyzing, and forecasting grounding resistance in electrical circuits using the Alternative Transient Program (ATP) and machine learning techniques.
      
    - Module 1 is designed to streamline the generation and control of extensive simulations of electrical circuits through a Python algorithm integrated with the Alternative Transient Program (ATP). The algorithm facilitates the creation of *.atp* simulation files, executes simulations, and transforms resulting waveforms *.pl4* files into MATLAB *.mat* files. The algorithm systematically generates parameter vectors P, which are subsequently introduced into the clamp-on ground meter measurement equivalent electric circuit. It orchestrates the automation of data entry and extraction steps within the ATP software. All input-output vector pairs [**P** ; **Z**<sub>med </sub>] are cataloged in a dedicated database. Notably, the vectors **Z**<sub>med </sub> and **R**<sub>f</sub> ($n$ elements of **P**) assume a pivotal role as a foundational repository for Module 2, where machine learning models are developed based on this comprehensive dataset.

    - Module 2 introduces a Python algorithm leveraging advanced machine learning techniques to forecast turbine grounding resistance based on clamp-on meter readings. This algorithm capitalizes on the database established in Module 1, employing it for tasks such as data preprocessing, model training, and the assessment of evaluation metrics to enhance predictive accuracy. Within the machine learning pipeline, 70% of the vector pairs [**Z**<sub>med </sub> ; **R**<sub>f</sub>] from the Module 1 database are allocated for training the model, ensuring a robust foundation for learning. The remaining 30% is reserved for testing the trained model, evaluating its performance, and constructing boxplot error graphs. These graphs depict the outcomes of implementing the Clamp-on Ground Meter Method (CGM) and the Proposed Method in the São Bento Complex (SBC) grounding system, providing a comparative analysis of their effects.

    - Module 3 features a Python algorithm designed to efficiently generate and manage extensive simulations of electrical circuits using ATP. This module is capable of creating .atp simulation files, executing simulations, and converting resulting waveforms *.pl4* files into MATLAB files *.mat*. Specifically tailored for the testing set separated in Module 2, the algorithm loads the **P** electrical parameter sample vectors, sequentially introducing them into the High-frequency ground meter measurement circuit. It then automates the essential steps of data insertion and extraction within the ATP software. All resulting input-output pairs are stored in a dedicated database, forming the foundation for comprehensive analysis. The algorithm's outcomes are visually represented through a box plot error graph. This graph encapsulates the results obtained from implementing the High-Frequency Method (HFM) in the São Bento Complex (SBC) grounding system, providing a clear comparative assessment of its impact.


    - To utilize this algorithm, users are required to download and install three essential software components: ATP, the pl42mat.exe converter, and Python. 
   
3. [[Database.xlsx](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/Database.xlsx)]
    - Excel spreadsheet featuring an extensive dataset designed for training, validation, and testing machine learning models. The dataset consists of 11,000 solution vectors, formed by concatenating the **P** vectors with their respective **Z**<sub>med</sub> vectors. In the machine learning pipeline, 70% of these solution vectors are allocated for training the model, ensuring a robust foundation for learning. The remaining 30% of vectors are dedicated to testing the trained model, as well as assessing the performance of the CGM and HFM measurement methods within the SBC framework. This division allows for a comprehensive evaluation of both the model's predictive capabilities and the effectiveness of measurement techniques in the specified context. 

4. [[HFM.acp](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/HFM.acp)]
   - ATP file for computer simulation of the high-frequency method in case study's grounding system.

5. [[CGM.acp](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/CGM.acp)]
    - ATP file for computer simulation of the clamp-on ground meter method in case study's grounding system.

6. [[HFM_circuit.pdf](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/HFM_circuit.pdf)]
   - PDF file with the equivalent circuit's figure for the high-frequency measurement method in case study's grounding system.

7. [[CGM_circuit.pdf](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/CGM_circuit.pdf)]
   - PDF file with the equivalent circuit's figure for the clamp-on ground meter measurement method in case study's grounding system.

8. [[MAPE_results.xlsx](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/MAPE_results.xlsx)]
   - Excel spreadsheet containing the final results.

9. [[Error_Boxplot.pdf](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/Error_Boxplot.pdf)]
    - Error boxplot graphs illustrating the performance variations among the clamp-on ground meter, high-frequency, and a proposed method when applied in the context of estimating the SBC's grounding resistance turbines. These boxplots provide a visual representation of the errors associated with each method, facilitating a comprehensive comparison and analysis between them.

10. [[Supporting files](https://github.com/Alexandregiacomellileal/Update-computacional-tool/tree/main/supporting%20files)]
   - This directory contains sub-algorithms and Excel spreadsheet files with data frames used by the authors in developing the proposed solution. Each module (sub-algorithm) performs a specific task, and when combined, the modules form the complete algorithm named [[Proposed_solution.py](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/Proposed_solution.py)]. Similarly, all the Excel files contain data frames that collectively contribute to the formatting of the [[Database.xlsx](https://github.com/Alexandregiacomellileal/Update-computacional-tool/blob/main/Database.xlsx)] file.

________________________________________________________________________________________________________________________

## Usage

To apply this systematic approach to your wind farm grounding system analysis, follow the steps outlined in the respective sections of the codebase. Detailed instructions for each file can be found within their specific directories.

________________________________________________________________________________________________________________________

## Contact us:
Please send an email to: alexgiacomelli@yahoo.com

________________________________________________________________________________________________________________________

## Contributors:
Federal University of Technology – Parana (UTFPR) and Institute of Technology for Development (LACTEC)





