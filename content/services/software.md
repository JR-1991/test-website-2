---
title: "For software developers"
date: 2018-11-28T15:14:39+10:00
featured: true
draft: false
weight: 4
---
Want to implement **EnzymeML** read and write functionalities in your software? Here
you have somes ideas to inspire your team.

## EnzymeML documents

**EnzymeML** follows the Standards of Reporting Enzymology Data (STRENDA) [Guidelines](https://www.beilstein-institut.de/en/projects/strenda/guidelines/), a comprehensive set of metadata describing reaction conditions and kinetic models. **EnzymeML** is written in eXtensible Markup Language (XML). It builds on the well-established Systems Biology Markup Language ([SBML](http://sbml.org/)) and includes information about the enzyme, the substrate(s) and product(s), the reaction conditions, the selected kinetic model, and estimated kinetic parameters (find the XML schema definition [here](https://github.com/EnzymeML/PyEnzyme/tree/main/xsd)). The measured time course of substrate or product concentrations are stored in a comma-separated values (CSV) formatted file. The XML- and the CSV file are combined into a single EnzymeML document using the widely-used [OMEX format](http://co.mbine.org/specifications/omex.version-1.pdf)

## Application Programming Interface (API)

You can implement **EnzymeML** read and write functionalities into your software application (electronic lab notebooks, laboratory information management systems, modelling platforms, or database) by using the EnzymeML Application Programming Interface (API), either as a python library to be implemented locally with your software, as a RESTful API to be implemented locally,  or via a RESTful API installed on our webserver.

## How to interact with the API

We start from a EnzymeML document which contains the experimental conditions (protein sequence of the enzyme, enzyme concentration, temperature, inital substrate concentration, time course of substrate). The goal is to read in the time course data in a modelling tool, to estimate kinetic parameters, and to add the kinetic parameters and the selected kinetic model to the EnzymeML document

1. Application (e.g. modelling tool)    sends an EnzymeML document (example here) and a request for reading time course data and enzyme concentration (example here) to the API  (URL:....)
2. The API extracts the requested information (e.g. time course data and enzyme concentration) from the EnzymeML document and sends back a JSON file (template here) to the application (e.g. modelling tool)
3. The modelling tool reads in the information from the JSON file, defines a model (e.g. Michaelis-Menten) and estimates kinetic parmeters by fitting the time course data
4. The modeling tool writes the selected model and estimated parameters  to a JSON file and sends it to the API, together with the EnzymeML document
5. The API inserts the selected model and estimated parameters into the EnzymeML documents and sends it back

As a result, the EnzymeML document does not only contain the experimentally measure data, but also the model and the estimated kinetic parameters. One experimental dataset might be modelled by many different kinetic models, therefore the EnzymeML document might contain different kinetic models and the respective parameters together with a single experimental dataset.

### Resources

* Download the python library from the [EnzymeML Github](https://github.com/EnzymeML/PyEnzyme/)
* The RESTful API is packaged within [DOCKER ](https://www.docker.com/)to facilitate a local installation - In order to integrate our API [download](https://hub.docker.com/r/enzymeml/pyenzyme) our docker image and use our [documentation](https://enzml.sloppy.zone/swagger-ui/).
* Use the publicly available RESTful API at [https://enzml.sloppy.zone](https://enzml.sloppy.zone/swagger-ui/). Please note, we are using security standards such as SSL and several backend checks to make sure your data wont be exposed. On top of that, your wont reside on our servers and is immediately removed.
