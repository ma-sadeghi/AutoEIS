![example workflow](https://github.com/AUTODIAL/AutoEIS/actions/workflows/nightly.yml/badge.svg)

> [!CAUTION]
> _Want to get notified about major announcements/new features?_ Please click on "Watch" -> "Custom" -> Check "Releases". Starring the repository alone won't notify you when we make a new release. This is particularly useful since we're actively working on adding new features/improvements to AutoEIS. Currently, we might issue a new release every month, so rest assured that you won't be spammed.

# AutoEIS

## What is AutoEIS?

AutoEIS is a Python package that automatically proposes statistically plausible equivalent circuit models (ECMs) for electrochemical impedance spectroscopy (EIS) analysis. The package is designed for researchers and practitioners in the fields of electrochemical analysis, including but not limited to explorations of electrocatalysis, battery design, and investigations of material degradation.

AutoEIS is still under development and the API is not stable. If you find any bugs or have any suggestions, please file an [issue](https://github.com/AUTODIAL/AutoEIS/issues) or directly submit a [pull request](https://github.com/AUTODIAL/AutoEIS/pulls). We would greatly appreciate any contributions from the community.

## Installation

### Pip

Open a terminal (or command prompt on Windows) and run the following command:

```bash
pip install -U autoeis
```

Julia dependencies will be automatically installed at first import. It's recommended that you have your own Julia installation, but if you don't, Julia itself will also be installed automatically.

> **How to install Julia?** If you decided to have your own Julia installation (recommended), the official way to install Julia is via [juliaup](https://github.com/JuliaLang/juliaup). [Juliaup](https://github.com/JuliaLang/juliaup) provides a command line interface to automatically install Julia (optionally multiple versions side by side). Working with [juliaup](https://github.com/JuliaLang/juliaup) is straightforward; Please follow the instructions on its GitHub [page](https://github.com/JuliaLang/juliaup).

## Workflow

The schematic workflow of AutoEIS is shown below:

![AutoEIS workflow](https://raw.githubusercontent.com/AUTODIAL/AutoEIS/develop/assets/workflow.png)

It includes: data pre-processing, ECM generation, circuit post-filtering, Bayesian inference, and the model evaluation process. Through this workflow, AutoEis can prioritize the statistically optimal ECM and also retain suboptimal models with lower priority for subsequent expert inspection. A detailed workflow can be found in the [paper](https://iopscience.iop.org/article/10.1149/1945-7111/aceab2/meta).

## Usage

> [!WARNING]
> The envelope function, `perform_full_analysis`, has some issues since it was doing too much all at once. For now, we've deprecated it until it's made robust. The recommended way to use AutoEIS is the step-by-step approach anyway, since it gives more granular control. That said, since a one-stop-shop function is what many users, especially experimentlists, would like, we're working on making it robust. We'll update this page once the function is ready. **For now, please use the step-by-step approach**.

To use AutoEIS, you can either perform the circuit generation and Bayesian inference step by step or use the `perform_full_analysis` function to automate the whole process. Please visit our [examples'](https://autodial.github.io/AutoEIS/examples.html) page to learn how to use AutoEIS.

# Acknowledgement

The authors extend their heartfelt gratitude to the following individuals for their invaluable guidance and support throughout the development of this work: Prof. Jason Hattrick-Simpers, Dr. Robert Black, Dr. Debashish Sur, Dr. Parisa Karimi, Dr. Brian DeCost, Dr. Kangming Li, and Prof. John R. Scully.

The authors also wish to express their sincere appreciation to the following experts for engaging in technical discussions and providing valuable feedback: Dr. Shijing Sun, Prof. Keryn Lian, Dr. Alvin Virya, Dr. Austin McDannald, Dr. Fuzhan Rahmanian, and Prof. Helge Stein.

Special thanks go to Prof. John R. Scully and Dr. Debashish Sur for graciously allowing us to utilize their corrosion data as an illustrative example to showcase the functionality of AutoEIS. Their contributions have been immensely helpful in shaping this research, and their unwavering support is deeply appreciated.
