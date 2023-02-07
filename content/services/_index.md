---
title: 'What is EnzymeML'
intro_image: "images/about_overview.png"
intro_image_absolute: true
intro_image_hide_on_mobile: false
---

## What is EnzymeML?

EnzymeML is a free and open standard XML-based interchange format for comprehensive data on enzyme-catalyzed reactions. The purpose of EnzymeML is to store and exchange enzyme kinetics data between electronic lab notebooks, software tools, and databases. An EnzymeML document contains four types of data

* Experimental reaction conditions (protein sequence and concentration of enzyme; chemical structure and initial concentrations of substrates, products, inhibitors, additives; temperature; buffer and pH)

* Measured time courses of the concentration of substrates and products

* One (or more) kinetic model to analyse the time course data data

* Estimated kinetic parameters

Thus, an EnzymeML documents contains the measured data and the modelling results of a series of experiments, e.g. time course data for different initial substrate concentrations and their analysis by a Michaelis-Menten model. 

EnzymeML is compatible with the Systems Biology Markup Language (SBML). It continues to be evolved and expanded by an international community and is supported by the STRENDA Commission.

## How to write and read EnzymeML?

The typical user is not expected to read or write EnzymeML documents directly, but to use software to generate EnzymeML documents, which are then used as a standardised exchange format to transfer data between applications. Therefore, an Application Programming Interface (API) was developed as a RESTful Web service to enable tools for data acquisition, data modelling, or data publication to read, write, and edit EnzymeML documents. The tools communicate with the RESTful API by HTTP, JSON, and XML. An EnzymeML document is either a file (an OMEX archive which contains XML and CSV files) or a dataset in an EnzymeML Dataverse (a generic open-source data repository system with more than 60 installations worldwide).


 

EnzymeML is part of the FAIR biotope

* [FAIRsharing](https://fairsharing.org/search/?q=enzymeml)

 