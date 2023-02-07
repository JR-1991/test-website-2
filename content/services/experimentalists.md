---
title: "For experimentalists"
date: 2018-11-28T15:15:26+10:00
featured: true
draft: false
weight: 2
---


How can EnzymeML help you to manage your experimental data?

EnzymeML was developed to support data acquisition, data analysis, and sharing of data by providing a standardized exchange format for enzymatic data. EnzymeML follows the Standards of Reporting Enzymology Data (STRENDA) [Guidelines](https://www.beilstein-institut.de/projekte/strenda/), a comprehensive set of metadata describing reaction conditions and kinetic models. EnzymeML is written in eXtensible Markup Language (XML).

It builds on the well-established Systems Biology Markup Language ([SBML](http://sbml.org/)) and includes information about the enzyme, the substrate(s) and  product(s), the reaction conditions, the selected kinetic model, and estimated kinetic parameters. The measured time course of substrate or product concentrations are stored in a comma-separated values (CSV) formatted file. The XML- and the CSV file are combined into a single EnzymeML document using the widely-used [OMEX format](http://co.mbine.org/specifications/omex.version-1.pdf).

The typical user is not expected to read or write EnzymeML documents directly, but to use software to generate EnzymeML documents, which are then used as a standardised exchange format to transfer data between applications. Therefore, an Application Programming Interface (API) was developed to read, write, and edit EnzymeML documents.

The API is a Python library ([PyEnzyme on GitHub](https://github.com/EnzymeML/PyEnzyme)), which can be installed locally, or can be accessed as a RESTful Web service. This Web service can be used by any application such as an electronic laboratory notebook (ELN), a modelling platform, or a specialized database to read or write EnzymeML documents. Upon reading, writing, and editing of EnzymeML documents, the API controls data completeness and consistency, such as checking that scalar properties such as pH are within a given range. Additional validation tools control compatibility with SBML or with minimum requirements of applications such as STRENDA DB, SABIO-RK, or COPASI.

### Why managing experimental data with EnzymeML?

1. Measured time course data on substrate and/or product concentrations is saved in the same document with metadata about the enzyme and the reaction conditions. This faciliates replicability and reproducibility of experimental assays.
2. **EnzymeML** documents are standardized, so their format is independent of the experimental scientist. Documents are machine- and human-readable. Markup languanges (ML) are specifically designed for machines, and therefore they are not optimally for user reading. **EnzymeML** follows internationally recognized standards ([SBML](http://sbml.org/), [MathML](https://www.w3.org/Math/)). An application programming interface (API) allows for the easy integration of applications for data visualization and modeling.
3. Modelling data (kinetic rate law, kinetic parameters) can be added into the same **EnzymeML** document. Multiple models can be applied to the same dataset.
4. **EnzymeML** documents can be considered as a micropublication, because it contains data and metadata. By assigning a digital object identifier ([DOI](https://www.doi.org/)) to **EnzymeML** documents, they can be easily referenced.



## Currently implemented functionalities



#### Data acquisition

An EnzymeML document includes information about the reaction conditions (e.g. enzyme, substrates, products, pH, temperature) and the measured concentrations of substrate or product at different time points. Currently, we provide two alternatives routes on how to create an EnzymeML document:

* by filling in the EnzymeML spreadsheet (download [here](https://www.dropbox.com/s/bigaq2l1vynr13k/EnzymeML_Template.zip?dl=1)) and converting it to an EnzymeML document via upload using our [EnzymeML template conversion page](https://enzml.sloppy.zone/template/upload).
* by the graphical user  interface [BioCatHub](https://biocathubangular.herokuapp.com/).


#### Data modelling

As second step, the EnzymeML document generated upon data acquisition is used as starting point for modelling the enzyme kinetics.
Currently, we provide three alternatives routes on how to model the kinetics from experimental data:

* by a simple Michaelis-Menten fitting procedure using our [RESTful API modeling endpoint](https://enzml.sloppy.zone/swagger-ui/#/Model%20EnzymeReaction/get_model).
* by defining a kinetic model and estimating parameters using a Jupyter Notebook.

#### Data integration

Finally, the complete data of the enzyme catalyzed reaction (reaction conditions, time course data, selected kinetic model, estimated kinetic parameters) is uploaded to an EnzymeML Dataverse or to a specialized database such as SABIO-RK:

* Upload to SABIO-RK
* Creation of a dataset in an EnzymeML Dataverse. Please contact us for assistance with the implementation of an EnzymeML Dataverse in your local Dataverse installation. Visit our [page dedicated to database providers](https://enzymeml.org/services/database/) for further information.


