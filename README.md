# Update-computacional-tool

The proposed solution, involves a systematic sequence of tasks. Initially, the process begins by accessing the technical documentation of the wind farm's grounding system. Following this, a comprehensive survey of the parameters necessary for calculating the components of the equivalent electrical circuit is conducted. Next, an appropriate electrical circuit model is chosen for the wind farm's grounding system. To account for variations and uncertainties, a sensitivity study is performed on parameters influencing the grounding resistance and capacitance of turbines and horizontal electrodes. Tolerance ranges are defined, considering factors such as construction non-conformities or soil and electrode deterioration. A sample vector $\textbf{P}$ is generated, with each element representing a specific grounding resistance or capacitance of a turbine or horizontal electrode. An element representing the parameter $k$ is also included to replicate the mutual coupling effect between the turbine and horizontal electrodes during clamp-on ground meter measurements. Uniform distributions are used to generate vector elements within their corresponding tolerance ranges set by the sensitivity study. The equivalent circuit of the grounding system is then loaded based on the values from the sample vector $\textbf{P}$. Subsequently, a computational simulation of the clamp-on method is performed in the equivalent electrical circuit. Instrument reading values are obtained in each turbine, resulting in an output sample vector Zmed. This process is repeated $m$ times to generate input-output pairs stored in a database $\mathbb{D}_{m\times2n}$. The database is then utilized to train a machine-learning model. The trained model undergoes validation and testing to ensure accuracy and reliability. Finally, the trained model is used to predict the values of the resistances $\textbf{R}_{fest}$ for the $n$ turbines based on the readings obtained via the clamp-on method during wind farm periodic inspections $\textbf{Z}_{med}$. This systematic approach ensures a logical progression from data collection and circuit modeling to machine learning application, facilitating accurate predictions of turbine grounding resistances. The details of each stage of the process are presented as follows.



File descriptions:

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
