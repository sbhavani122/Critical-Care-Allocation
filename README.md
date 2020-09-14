# critical_care_allocation
## final_code.rmd

The data file should be read in as covid_sample, and formatted with the following columns for each patient (each patient is a unique row): 
   1) age
   2) race: "Black", "Non-Hispanic White", "Hispanic"
   3) sofa_num: Numerical SOFA score
   4) died: 1 for died in the hospital, 0 for survived to hospital discharge
   5) wscore_ahrq: Elixhauser comorbidity score calculated using comorbidity package in R
   
Once the data is in the correct format, and is read into the final_code.rmd file, the file runs monte carlo simulations according to various allocation protocols and summarizes the results:   
1. Codes elixhauser (wscore_ahrq) into chronic disease categories  
2. Randomly samples 10,0000 patient populations
3. Applies several allocation rules under a scarcity condition (default 0.5)
    * Lottery: random assignment of ICU beds
    * Sickest-first: prioritization of patients with the highest SOFA score
    * Youngest-first: prioritization of the youngest patients
    * New York: categorical lower SOFA first, lottery for ties
    * Maryland: composite score based on SOFA and the presence of severe chronic disease, age as a tiebreaker
    * Penn:  composite score based on SOFA and the presence of major or  severe chronic disease, age as a tiebreaker
4. Outputs 2 files:
   a) "lives_comparison.csv" - Statistical comparison of allocation protocols
   b) "lives_saved.svg" - Violin plot comparing survival rate across the allocation protocols
