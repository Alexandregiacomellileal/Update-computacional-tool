# Integrated approach for wind turbine grounding resistance estimation: Bridging clamp-on ground meter, computational simulations, and machine learning.

## Overview
This directory contains sub-algorithms and Excel spreadsheet files with data frames used by the authors in developing the proposed solution. Each module (sub-algorithm) performs a specific task, and when combined, the modules form the complete algorithm named 'Proposed_solution.py.' Similarly, all the Excel files contain data frames that collectively contribute to the formatting of the 'Database.xml' file.

## Files

1. **allat25khz_capac.acp:**
   - ATP file for computer simulation of the high-frequency method in case study's grounding system.

2. **allat25khzcap_sbn_results.xlsx:**
   - Excel spreadsheet with 3300 samples of input and output vectors from the high-frequency method simulation in case study's grounding system.

3. **dataframe_sbn_mutua_varia_rf_e_rp.xlsx:**
   - Excel spreadsheet with 11000 samples of input and output vectors from the clamp-on ground meter method simulation in case study's grounding system.

4. **sbn_error_boxplot_high_frequency_cap.py:**
   - Python algorithm to automate data insertion and removal in ATP software for high-frequency measurement circuit simulation.

5. **sbn_varia_Rf_e_Rp_e_k_com_mutua_all_cap_111143.py:**
    - Python algorithm to automate data insertion and removal in ATP software for clamp-on ground meter measurement circuit simulation.

6. **sbn_varios_algoritmos_error_boxplot_mutua_variando_rf_e_rp.py:**
    - Python algorithm containing machine learning techniques to predict turbine grounding resistance from clamp-on meter readings.

7. **sbnallmutuacap.acp:**
    - ATP file for computer simulation of the clamp-on ground meter method in case study's grounding system.



