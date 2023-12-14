# Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning.

## Overview
This repository contains a systematic solution for analyzing the grounding system of a wind turbines. The proposed solution involves a sequence of tasks depicted in Fig1.pdf. The approach integrates technical documentation analysis, parameter survey, electrical circuit modeling, sensitivity studies, and machine learning to predict turbine grounding resistances.

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
    - Use the trained model to predict the resistances R<sub>f for the $n$ turbines based on clamp-on method readings during wind farm periodic inspections Z<sub>med.

________________________________________________________________________________________________________________________

## Files

1. **3300_clamp_on_direct_test_input_parameters.xlsx:**
   - Excel spreadsheet with 3300 input vector samples for simulating the clamp-on ground meter method.

2. **3300_high_frequency_test_input_parameters.xlsx:**
   - Excel spreadsheet with 3300 input vector samples for simulating the high-frequency method.

3. **allat25khz_capac.acp:**
   - ATP file for computer simulation of the high-frequency method.

4. **allat25khzcap_sbn_results.xlsx:**
   - Excel spreadsheet with 3300 samples of input and output vectors from the high-frequency method simulation.

5. **circuito_4_artigo_atp_hf.pdf:**
   - PDF file with the equivalent circuit's figure for the high-frequency measurement method.

6. **circuito_4_artigo_atp_cgm.pdf:**
   - PDF file with the equivalent circuit's figure for the clamp-on ground meter measurement method.

7. **dataframe_sbn_mutua_varia_rf_e_rp.xlsx:**
   - Excel spreadsheet with 11000 samples of input and output vectors from the clamp-on ground meter method simulation.

8. **resultados_obtidos_4_artigo.xlsx:**
   - Excel spreadsheet containing the final results.

9. **sbn_error_boxplot_high_frequency_cap.py:**
   - Python algorithm to automate data insertion and removal in ATP software for high-frequency measurement circuit simulation.

10. **sbn_varia_Rf_e_Rp_e_k_com_mutua_all_cap_111143.py:**
    - Python algorithm to automate data insertion and removal in ATP software for clamp-on ground meter measurement circuit simulation.

11. **sbn_varios_algoritmos_error_boxplot_mutua_variando_rf_e_rp.py:**
    - Python algorithm containing machine learning techniques to predict turbine grounding resistance from clamp-on meter readings.

12. **sbnallmutuacap.acp:**
    - ATP file for computer simulation of the clamp-on ground meter method.

## Usage

To apply this systematic approach to your wind farm grounding system analysis, follow the steps outlined in the respective sections of the codebase. Detailed instructions for each file can be found within their specific directories.




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
