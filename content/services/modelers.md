---
title: "For modelers"
date: 2018-11-28T15:15:34+10:00
featured: true
draft: false
weight: 3
---


How can EnzymeML help you developing, implementing and analysing models?

An EnzymeML document provides the complete experimental information including the enzyme concentration, the initial concentrations of substrates, products, or inhibitors, and the measured concentrations of substrate or product at different time points. It might also provide a preferred kinetic model or alternative kinetic models. The model consists of a kinetic law which determines the temporal changes in the concentration of substrates, products, or enzyme as a function of measured concentrations of substrates, products, and enzyme, and of kinetic parameters.

The modeler then selects a kinetic model given in the EnzymeML  document or generates a separate kinetic model, which is then used to estimate the kinetic parameters by fitting the time course of substrate or product concentrations as predicted from the model to the experimentally determined time courses. Fitting is done for a set of initial conditions such as a range of initial substrate concentrations and enzyme concentrations. A model might also include the effect of pH or temperature.

The major advantage of EnzymeML to the modeler is the completeness and interoperability of the experimental data.
Finally, the estimated parameters are added to the EnzymeML document, which then contains the complete information on the experiment: the reaction conditions, the time course of substrates and products, the selected kinetic model, and the estimated kinetic parameters.

## Currently implemented functionalities

### A simple Michaelis-Menten fitting procedure provided by the EnzymeML API

In order to model your experimental data described in your EnzymeML document, simply provide the archive alongide the reaction and reactants you want to model to our RESTful API. You will receive a new archive incuding the estimated parameters. For further information please consider reading our [documentation](https://enzml.sloppy.zone/swagger-ui/#/Model%20EnzymeReaction/get_model).
