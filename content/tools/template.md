---
title: 'EnzymeML Template'
date: 2022-09-22T17:01:34+07:00
featured: false
draft: false
weight: 4
---

# Tutorial and best practices

The EnzymeML Team provides a template in the commonly used spreadsheet format, which was designed to facilitate the report of biocatalytic and enzymatic data using EnzymeML. The template was designed such that valid OMEX archives can be created by submitting the resulting spreadsheet to the official conversion page found [here](https://enzymeml.sloppy.zone/template/upload).

This document will further explain the workflow and how to use the spreadsheet by giving best practices. For this, the next paragraph will further elucidate how to acquire the template, how to fill in data and finally how to convert it to EnzymeML.

## 1. Download the EnzymeML template

The EnzymeML template can be downloaded [here](https://enzymeml.sloppy.zone/template/download). Additionally an [example template](https://github.com/EnzymeML/PyEnzyme/raw/main/templates/EnzymeML_Template_Example.xlsm) is provided which demonstrates how a template should be filled.

Once downloaded, you can open the template with any commonly available spreadsheet application such as Microsoft Excel™ or OpenOffice Calc.

_Please note that this spreadsheet uses macros to ensure a pleasant and easy workflow. Thus it is necessary to enable these when opened with an application. Otherwise conversion cant be guaranteed._

## 2. Entering data

The EnzymeML template involves multiple sheets which correspond to parts that make up the EnzymeML data model. In the following the structure will briefly be broken down and explained.

{{< figure src="overview.png" >}}

_You can always review what kind of content a given column or row is expecting. By clicking the name you will see a pop-up that explains the content._

{{< figure src="info_popups.png" width="250" >}}

#### General Information

This sheet includes information about the dataset, such as title and authors as well as links to related information. If given, a DOI and PubMed ID can also be added here.

#### Vessels

Here you can define the vessels that were used in course of your experiment. It is possible to add multiple vessels. There is a dropdown cell for the **volume unit** from which you can choose the appropriate unit. Each vessel will receive a unique ID which later on will be refrenced by other sheets (more on that later).

#### Reactants / Proteins

Both sheets 'Reactants' and 'Proteins' allow you to describe the substances you have used in your experiment. It should be noted that **green** columns are mandatory and musst be filled for a successful conversion, while **yellow** ones are optional.

In the case of *vessel* it is important to make use of the given dropdown feature, which lists all the vessels previously defined. Here you can specify in which vessel the substance has been added. Same applies to the *constant* column which lets you choose from two values. Others are not valid and will result in a conversion error.

#### Reactions

In order to define a reaction you can enter conditions and reference the participating substances and enzymes. Conditions are entered in a similar fashion as in the previous sheets. Please also note that columns **temperature unit** and **reversible** are dropdown fields.

Educts, Products, Enzymes and Modifiers are entered via a dropdown menu, which allows you to select multiple entries. Simply choose an entry and click on it, which will be added to the cell. Repeat the step until all necessary reaction elements are entered. See the following image for a valid example.


{{< figure src="reaction_entering.png" width="700" >}}

#### Data

The data sheet combines metadata and time-course data of your experiment. Here you can enter multiple experiment runs, their corresponding initial concentrations and the measured data. Different experiments can be organized by making use of *Experiment IDs* with which you refer to a certain run.

For the sake of demonstration, lets assume we have set up two experiments, where we alter the substrate (pyruvate) concentration. First, lets document the first run, with the following specifications:

**Experiment ID: "1"**

- **Time column**
  - Type: Time[sec]
  - Scope: 0-540 seconds
- **Pyruvate**
  - Type: Concentration
  - Initial concentration: 100 mmole / l
- **CO2**
  - Type Concentration
  - Initial concentration: 0 mmole / l
- **Acetaldehyde**
  - Type: Concentration
  - Initial concentration: 0 mmole / l)

{{< figure src="data_metadata.png" width="1000" >}}

Please note, that a **time column** is mandatory and conversion will fail if its missing. As shown in the example, the time column does not have to include any concentration metadata. Furthermore, protein initial concentrations need to be included in all other rows than time.

{{< figure src="data_rawdata.png" width="1000" >}}

Measurement data can now be entered in the blue columns to the right. These are expected to be entered **horizontally** as shown in the above figure. Entering values is not mandatory and can be left out if no measurements have been done.


{{< figure src="experiment_two.png" width="1000" >}}


The process is repeated with all other experiments, which are distinguished by different Experiment IDs. It is important to note, that each experiment can not have multiples of a substance. Hence, if you are documenting replicates, please add these as other experiments.

#### Kinetic Models

Finally, when all data has been entered, you can now specify kinetic models for modelling. This is done by first specifiying the reaction that is modeled using teh dropdown. In the next step you can enter the mathematical equation corresponding to the model as well as the substances involved. Lastly, you can enter estimated parameters in the optional yellow columns.


{{< figure src="models.png" width="1200" >}}

Please note that it is best practice to use **IDs rather than names** when defining an equation. For this, a table on the right-hand side lists all IDs present. 

## 3. Convert the template to EnzymeML

Once you've entered all relevant data, the template can be converted to EnzymeML by upload to the [EnzymeML Template conversion page](https://enzymeml.sloppy.zone/template/upload). When submitted, you will receive an OMEX archive that can now be used for a variety of workflows such as modelling, publication or visualisation.

{{< figure src="conversion.jpeg" width="500" >}}