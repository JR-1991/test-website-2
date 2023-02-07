---
title: "For database providers"
date: 2018-11-28T15:14:39+10:00
featured: true
draft: false
weight: 4
---


How can EnzymeML help you to publish results and to exchange data?

EnzymeML is a flexible data model for biocatalysis and enzymology capable to completely describe an experiment in a machine-readable format. In order to handle and integrate EnzymeML in your database, we provide our software solution PyEnzyme, which can be either installed locally or reached via several endpoints of our [REST-API](https://enzml.sloppy.zone/swagger-ui/).

## Currently implemented functionalities

### Validation of minimal requirements and upload to SABIO-RK

PyEnzyme as well as our REST-API provide an interface to validate incoming EnzymeML documents to comply with the minimal requirements necessary for a succesful upload to your database. Besides that, we also offer a complete validation report, such that you are able to provide all the important informations to your user if a dataset does not comply. With our long-term partner database SABIO-RK we already established a workflow to perform validation and subsequent upload to the database. The validation is performed in conjunction with a template decribing all mandatory as well as optional EnzymeML fields required for #a successfull upload.

In order to integrate EnzymeML validation to your database, please follow our instructions:

1. Download our [EnzymeML-Validation template](https://www.dropbox.com/s/yji9dfsu92g265h/EnzymeML_Validation_Template_V1.xlsx?dl=1)
2. Use given fields and dropdown menues to specify your minimal requirements
3. Upload your template to our [Validation-Template conversion page](https://enzml.sloppy.zone/validate/upload)
4. Download the resulting JSON template and deploy it on your server
5. On validation using our [REST-API](https://enzml.sloppy.zone/swagger-ui/#/Validate%20EnzymeML/get_validate) or PyEnzyme provide the URL to your JSON template

### Creation of a dataset in an EnzymeML Dataverse

Dataverse installations provide a modern and modular approach to databases, offering flexibility and stability at the same time. Hence, we developed a Dataverse compliant metadata-block schema, such that you can easily integrate EnzymeML to your own Dataverse installation. In collaboration with FoKUS-Team from the University of Stuttgart, we already established a seamless process chain from an EnzymeML archive to a dataverse entry. Our REST-API offers an automatic upload to your dataverse in conjunction with out validation interface.

You provide a dataverse installation and want to integrate EnzymeML? Please feel free to contact our support in order to assist you.

### Future Developments

Collaboration with SABIO-RK, STRENDA DB, UniProt/Enzyme Portal, Dataverse
