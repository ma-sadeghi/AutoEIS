# AutoEis.py
------------
AutoEis is a Python package to automatically propose statistical plausible equivalent circuit models (ECMs) for electrochemical impedance spectroscopy (EIS) analysis. The package is designed for researchers and practitioners in the fields of electrochemical analysis, including but not limited to explorations of electrocatalysis, battery design, and investigations of material degradations.

Please be aware that the current version is only the beta test and has not been formally realized. If you find any bug and any suggestions, please [file an issue](https://github.com/AUTODIAL/Auto_Eis/issues) or directly [pull requests](https://github.com/AUTODIAL/Auto_Eis/pulls). We would really appreciate any contributions from our commmunity. 

## Installation
---------------
The easiest way to install this package is using pip install from [pypi](https://pypi.org/project/AutoEis/)
```bash
pip install AutoEis
```

## Dependencies
---------------
Because AutoEis uses functions from the julia package [equivalentcircuit.jl](https://github.com/MaximeVH/EquivalentCircuits.jl) designed by MaximeVH, it requires a installation of julia programming language

AutoEis requires:
-   **Python programming language (>=3.7)**
- - NumPy (>=1.20)
- - Matplotlib (>=3.3)
- - Pandas (>=1.1)
- - impedance (>=1.4)
- - regex (>=2.2)
- - arviz (>=2.2.1)
- - numpyro (>=0.9)
- - dill (>=0.3.4)
- - PyJulia (>=0.5.7)
- - IPython (>=7.19.0)
- - jax (>=0.3.9)

-   **Julia programming language (>=1.7.0)**
- - equivalentcircuit (>=0.1.3)
- - CSV
- - DataFrame
- - Pandas
- - PyCall
- - DelimitedFiles
- - StringEncodings

## Workflow
------------
The schematic workflow of AutoEis is shown below:
![Workflow](https://github.com/AUTODIAL/Auto_Eis/blob/main/AutoEis_workflow.png)
It contains: data pre-processing, ECM generation, circuit post-filtering, Bayesian inference and model evaluation process. Through this workflow, AutoEis can prioritize the statistical optimal ECM and also retains suboptimal models with lower priority for subsequent expert inspection.

## Usage
-------------
To enable the interaction between python and julia, please set the julia executable path at first.
```bash
# import AutoEIS and its dependencies
import AutoEis as ae

# define the path of julia program
j = ae.set_julia (r"D:\Julia-1.7.2\bin\julia.exe")
```
Then by calling the function `initialize_julia()`, AutoEis will automatically install julia's dependencies. *(This step is only required for your first time using AutoEis)*
```bash
# initialize the julia environment and download the dependencies
ae.initialize_julia()
```
Now you are good to load your data and perform all analysis with one function
```bash
# set the parameter of plots
ae.set_parameter()

# Load the data
data_path = "Test_data.txt"
df = ae.load_data(data_path)
frequencies = ...
reals = ...
imags = ...
measurements = reals + 1j*imags

# Perform automated ECM generation and evaluation
ae.EIS_auto(impedance=measurements,freq=frequencies,data_path=data_path,iter_number=100,plot_ECM=False)
```
An example that demonstrate how to use AutoEis is attached [here](https://github.com/AUTODIAL/Auto_Eis/blob/main/Example_AutoEIS.ipynb). 
