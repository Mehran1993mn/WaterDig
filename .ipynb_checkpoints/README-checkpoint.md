# DP00BC26 Methods in data in water digitalization and sustainable management 2026
This repository contains code sprints for Water Digitalization, a methods course for DigitaL Waters PhD pilot students.

Introduction to data science methods for environmental analysis. Topics covered include reproducible scientific computing (bash scripting for data management, git for version control, GitHub for code collaboration and distribution); open geospatial data sources; common structures of environmental data; space/time applications of supervised machine learning (in R and Python); reproducible computational pipelines; repository design and publication; and best practices for high-performance computing using a JupyterHub virtual research environment.

To use this repository: 
1. Log onto GitHub.com using your registered email and password
2. Click “Fork” in the upper right corner.
3. Use git clone to copy it into the DIWA DataLab
4. Identify the code sprint assigned for the day
5. Work through the code to the best of your ability.
6. To submit, push any modifications to the assignment to your forked repository (git add, git commit, git push)


New assignments and solution keys will be added weekly, so we'll be working through upstream pulls and merges in class.

To install required packages to run notebooks in this repository, first use terminal to create a new conda environment named "waterdig:"

    conda create --name waterdig 
    
Activate this environment (note, on your PC you will use `conda activate` instead of `source activate`:

    source activate waterdig  

Install all packages listed in the requirements.txt file:

    pip install requirements.txt 
    
Enable the "waterdig" environment to be discoverable as a kernel in Jupyter Notebooks:

    python -m ipykernel install --user --name=myenv --display-name "waterdig" 

When you open notebook in this repository, select "waterdig" as a kernel using the upper righthand menu.


Did these resources help your research? Spread the word! Preferred citation: 

[Carter, E., Hultquist, C., & Wen, T. (2023). GRRIEn analysis: a data science cheat sheet for earth scientists learning from global earth observations. Artificial Intelligence for the Earth Systems, 2(2), 220065.](https://journals.ametsoc.org/downloadpdf/view/journals/aies/2/2/AIES-D-22-0065.1.pdf) 
