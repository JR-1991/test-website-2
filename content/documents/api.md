---
title: 'Application Programming Interface'
date: 2018-02-22T17:01:34+07:00
featured: true
draft: false
weight: 2
---

An application programming interface (API) which consists of two libraries, the Python library 
[PyEnzyme](https://github.com/EnzymeML/PyEnzyme/tree/main), and the [REST-API](https://enzml.sloppy.zone/swagger-ui), which support reading, writing, editing, merging, 
and visualization of **EnzymeML** documents.

## API description

The API uses the [SBML](http://model.caltech.edu/) syntax and naming conventions which are familiar
to enzymologists to be implemented into **EnzymeML**. The basic concept of the two libraries is the 
usage of multiple dictionaries, in which proteins, reactants, units, and reactions are stored. They 
are indexed by internal IDs to prevent duplicates and ensure that they can always be traced back 
from reactions and vice versa. This allows an application to load multiple **EnzymeML** documents 
and filter them by user-defined properties, such as all reactions in which a certain reactant 
participates.

All functions were optimised to require no further knowledge of [Python](https://www.python.org/), such that users only have to adapt to the EnzymeML syntax.