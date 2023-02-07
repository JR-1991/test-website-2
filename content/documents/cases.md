---
title: 'Use cases'
date: 2018-02-22T17:01:34+07:00
featured: true
draft: false
weight: 3
---

To illustrate the power of **EnzymeML**, we illustrate selected applications for experimental enzymologists, 
system biology modelers, and software developers.  More applications are available in our EnzymeML 
preprint, which can be downloaded in our [Publications](/documents/publications/) page.

## Creating EnzymeML documents from spreadsheets

In the absence of a standard format, experimentalists typically store their experimental time course data in 
a spreadsheet following an ad hoc structure. Recently, a CSV-formatted spreadsheet, the 
[BioCatNet](https://doi.org/10.1002/biot.201800183) template, was proposed to store and report experimental 
data on enzyme-catalyzed reactions according to the 
[STRENDA Guidelines](https://www.beilstein-institut.de/en/projects/strenda/guidelines/). An application specific 
[API](/documents/api), [TL_BioCatNet](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Examples/ThinLayers/TL_BioCatNet.py), 
can be used to convert the BioCatNet spreadsheet, containing time course data on substrate and product concentration 
and comprehensive information as the reaction conditions, to **EnzymeML**. 

To illustrate how to create EnzymeML from an Excel spreadsheet, you can start by downloading an 
[Excel spreadsheet](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Resources/Examples/ThinLayers/BioCatNet/DMBA_selfligation.xlsx) 
for the lyase-catalyzed self-ligation of 3,5-dimethoxybenzaldehyde. By running the thin API layer, it will map 
each object in the spreadsheet to an **EnzymeML** object such as *Protein*, *Reactant*, or *Reaction* and adds 
it to the *EnzymeMLDocument* object by a simple add-function. The backend code takes care of validating data 
types and provides programming language primitives to append information to the respective dictionary. After 
successful mapping and validation, the API object layer is then written to an EnzymeML document by calling the 
*EnzymeMLWriter* function. 

## Creating EnzymeML documents from STRENDA DB entries
[STRENDA DB](https://www.beilstein-strenda-db.org/strenda/index.xhtml) is a comprehensive database on enzyme-catalyzed 
reactions, which includes information on reaction conditions and kinetic parameters. The [EnzymeML API](/documents/api) 
can be used to create an **EnzymeML** document from a STRENDA DB entry via a STRENDA DB-specific thin API layer 
[TL_STRENDA](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Examples/ThinLayers/TL_Strenda.py) to the object 
layer using the [PyEnzyme](https://github.com/EnzymeML/PyEnzyme/tree/main) library.

To illustrate how to create EnzymeML documents from STRENDA DB entries, you can take STRENDA DB entry 
[3IZNOK](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Resources/Examples/ThinLayers/STRENDA/Generated/3IZNOK_TEST/3IZNOK_TEST.omex) 
containing information on kinetic studies of the tryptophan biosynthesis using the TrpB2o enzyme 
from Arabidopsis thaliana. By running the thin API layer, it will map each object in the STRENDA DB 
to an EnzymeML object. The backend code takes care of validating data types. After 
successful mapping and validation, the API object layer is then written to an 
[EnzymeML document](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Resources/Examples/ThinLayers/STRENDA/3IZNOK_TEST.xml).

## Kinetic modelling of EnzymeML data by COPASI
[COPASI](http://copasi.org/) is a modelling and simulation environment. Using the [PyEnzyme](https://github.com/EnzymeML/PyEnzyme/tree/main) 
library and a COPASI-specific thin API layer, [TL_COPASI](https://github.com/EnzymeML/PyEnzyme/blob/main/pyenzyme/Examples/ThinLayers/TL_COPASI.py), 
the time course data (measured concentrations of substrate or product) can be loaded into COPASI. Within COPASI, different 
kinetic laws can be applied, kinetic parameters are estimated, and plots are generated to assess the result. The selected 
kinetic model and the estimated kinetic parameters can then be added to the **EnzymeML** document.

To illustrate the above application, we generated time course data from STRENDA DB entry 3IZNOK and imported to COPASI. 
The data was then simulated by applying the Michaelis-Menten model equation and the kinetic parameters 
(k<sub>cat</sub> = 0.015 s-1, K<sub>M</sub> = 0.01  mM) over a time interval of 200 seconds.  First, the time course data of each replicate 
was exported via the *exportReplicates*-function, inherited by every reaction object, to a Pandas Dataframe. Next, the 
dataframe was saved to a tab-separated file and columns defined via the 
[COPASI API](https://github.com/EnzymeML/PyEnzyme/tree/main/pyenzyme/Resources/Examples/ThinLayers/COPASI/3IZNOK_TEST/COPASI). 
In this way, COPASI is able to map every dataset to their respective reactants. The **EnzymeML** document was then written 
to a string and parsed together with the TSV file by the COPASI API for modeling. As a result, both estimated 
Michaelis-Menten kinetic parameters v<sub>max</sub> = 0.149 µM and K<sub>M</sub> = 0.0099 mM as well as the equation were instantiated by 
the KineticModel class and written to the **EnzymeML** document via the reactions setModel method. Finally, the **EnzymeML** 
document was written to a [file](https://github.com/EnzymeML/PyEnzyme/tree/main/pyenzyme/Resources/Examples/ThinLayers/COPASI/3IZNOK_TEST). 
It should be noted, that alongside the programmatic parameter estimation, a .cps file was created to be used within the 
COPASI GUI. Hence, a broad spectrum of models could be used to describe the kinetics as well.  

