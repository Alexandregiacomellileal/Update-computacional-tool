This is the file folder for the article titled "Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning".

Ensuring the safety of personnel and equipment in wind farms requires continuous monitoring of the grounding resistance of wind turbine generators throughout the wind farm's lifespan. Conventional methods for measuring grounding resistance are infeasible during periodic maintenance of onshore wind farms due to setup complexity and high costs. This study presents a robust methodology that bridges the clamp-on ground meter method, computational simulations, and machine learning for accurate and efficient wind farm grounding resistance estimation, addressing key challenges in the field. In the context of a real Brazilian wind farm complex, our solution demonstrates a substantial improvement, boasting a 58.2\% reduction in average error compared to conventional methods. This approach enhances the overall practicality and safety for workers involved in measurements and leads to a noteworthy 80\% reduction in test execution time.

The proposed solution, depicted in Fig1.pdf , involves a systematic sequence of tasks. Initially, the process begins by accessing the technical documentation of the wind farm's grounding system. Following this, a comprehensive survey of the parameters necessary for calculating the components of the equivalent electrical circuit is conducted. Next, an appropriate electrical circuit model is chosen for the wind farm's grounding system. To account for variations and uncertainties, a sensitivity study is performed on parameters influencing the grounding resistance and capacitance of turbines and horizontal electrodes. Tolerance ranges are defined, considering factors such as construction non-conformities or soil and electrode deterioration. A sample vector $\textbf{P}$ is generated, with each element representing a specific grounding resistance or capacitance of a turbine or horizontal electrode. An element representing the parameter $k$ is also included to replicate the mutual coupling effect between the turbine and horizontal electrodes during clamp-on ground meter measurements. Uniform distributions are used to generate vector elements within their corresponding tolerance ranges set by the sensitivity study. The equivalent circuit of the grounding system is then loaded based on the values from the sample vector $\textbf{P}$. Subsequently, a computational simulation of the clamp-on method is performed in the equivalent electrical circuit. Instrument reading values are obtained in each turbine, resulting in an output sample vector Zmed. This process is repeated $m$ times to generate input-output pairs stored in a database $D_{m\times2n}$. The database is then utilized to train a machine-learning model. The trained model undergoes validation and testing to ensure accuracy and reliability. Finally, the trained model is used to predict the values of the resistances $R_{fest}$ for the $n$ turbines based on the readings obtained via the clamp-on method during wind farm periodic inspections $Z_{med}$ This systematic approach ensures a logical progression from data collection and circuit modeling to machine learning application, facilitating accurate predictions of turbine grounding resistances. The details of each stage of the process are presented as follows.

# Wind Farm Grounding System Analysis

## Overview

This repository contains a systematic solution for analyzing the grounding system of a wind farm. The proposed solution involves a sequence of tasks depicted in Figure~\ref{fig:methodflow}. The approach integrates technical documentation analysis, parameter survey, electrical circuit modeling, sensitivity studies, and machine learning to predict turbine grounding resistances.

## Methodology

The process follows these key stages:

1. **Access Technical Documentation:**
   - Start by accessing the technical documentation of the wind farm's grounding system.

2. **Parameter Survey:**
   - Conduct a comprehensive survey of parameters necessary for calculating components of the equivalent electrical circuit.

3. **Circuit Modeling:**
   - Choose an appropriate electrical circuit model for the wind farm's grounding system.

4. **Sensitivity Study:**
   - Perform a sensitivity study on parameters influencing grounding resistance and capacitance, considering variations and uncertainties.

5. **Sample Vector Generation:**
   - Generate a sample vector $\textbf{P}$ with elements representing specific grounding resistances or capacitances, including a parameter $k$ for mutual coupling effects.

6. **Equivalent Circuit Loading:**
   - Load the equivalent circuit based on values from the sample vector $\textbf{P}$.

7. **Computational Simulation:**
   - Perform a computational simulation of the clamp-on method in the equivalent electrical circuit.

8. **Database Generation:**
   - Repeat the process to generate input-output pairs stored in a database $\mathbb{D}_{m\times2n}$.

9. **Machine Learning:**
   - Utilize the database to train a machine-learning model, followed by validation and testing.

10. **Prediction:**
    - Use the trained model to predict the resistances $\textbf{R}_{fest}$ for the $n$ turbines based on clamp-on method readings during wind farm periodic inspections $\textbf{Z}_{med}$.

## Usage

To apply this systematic approach to your wind farm grounding system analysis, follow the steps outlined in the respective sections of the codebase.




The files contained in this folder are:

1) 3300_clamp_on_direct_test_input_parameters.xlsx => Excel spreadsheet containing 3300 input vector samples for simulation of clamp-on ground meter method in case study's grounding;

2) 3300_high_frequency_test_input_parameters.xlsx   => Excel spreadsheet containing 3300 input vector samples for simulation of high-frequency method in case study's grounding;

3) allat25khz_capac.acp => ATP file for computer simulation of the high-frequency method in case study's grounding;

4) allat25khzcap_sbn_results.xlsx  => Excel spreadsheet containing 3300 samples of input and output vectors resulting from the simulation of the high-frequency grounding method in the case study's grounding;

6) circuito_4_artigo_atp_hf.pdf => equivalent circuit's figure of high-frequency measurement method in the case study wind farm;

7) circuito_4_artigo_atp_cgm.pdf => equivalent circuit's figure of clamp-on ground meter measurement method in the case study wind farm;

8) dataframe_sbn_mutua_varia_rf_e_rp.xlsx => Excel spreadsheet containing 11000 samples of input and output vectors resulting from the simulation of the clamp-on ground meter method in the case study's grounding;

9) resultados_obtidos_4_artigo.xlsx => Excel spreadsheet containing the final results;

10) sbn_error_boxplot_high_frequency_cap.py => algorithm in Python to automate data insertion and removal in ATP software (High frequency measurement circuit simulation);

11) sbn_varia_Rf_e_Rp_e_k_com_mutua_all_cap_111143.py => algorithm in Python to automate data insertion and removal in ATP software (Clamp-on ground meter measurement circuit simulation);

12) sbn_varios_algoritmos_error_boxplot_mutua_variando_rf_e_rp.py => Python algorithm containing machine learning techniques to predict turbine grounding resistance from clamp-on meter readings

13) sbnallmutuacap.acp => ATP file for computer simulation of the clamp-on ground meter method in case study's grounding;
